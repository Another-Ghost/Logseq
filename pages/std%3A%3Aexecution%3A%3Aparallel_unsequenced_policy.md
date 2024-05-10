alias:: 非顺序策略, parallel unsequenced policy, std::execution::par_unseq

- 针对算法函数用到的各种迭代器、值和可调用对象，[[非顺序并行策略]]（parallel unsequenced policy）就其内存次序施加了最严格的限制，以便标准库最大程度发挥算法并行化的潜力。
- 如果令算法函数采用非顺序并行策略，它就会在多个线程上按乱序执行算法步骤，线程之间的操作将不服从代码流程的先后顺序。于是，单一线程上的内部操作可以交错执行。例如，第二项操作可以在第一项结束之前就开始。这些操作还能跨越多个线程执行：在第一个线程上启动，在第二个线程上执行其中一部分，在第三个线程上收尾。
- 如果我们令算法函数使用非顺序并行策略，那么，在不同的迭代器、值或可调用对象上的操作不得以任何形式同步，也不能借任何函数调用与别的函数或代码同步。
  其含义是，内部操作只能针对相关的元素，或可以通过该元素访问的数据。内部操作绝不可以更改线程之间的共享数据，或元素之间的共享状态。
- 选用非顺序策略可能会（根据具体实现来定）提高代码重排和交错执行任务的可能性，从而让运行库具有更大的潜力以改进性能，不过付出的代价是对代码要求更严格：不得采用同步方式访问或操作元素。换言之，如果是为了确保多线程访问数据的安全，我们不得使用互斥或原子变量， 或前文提及的其他同步机制 。相反，我们必须假定，算法函数本身不会从多个线程访问 相同的数据，也不会为了防止其他线程访问数据，而使用函数调用以外的同步方法。
- 代码清单 1 展示了一份代码，它可以采用 `std::execution::par` 策略，却无法采用 `std::execution::par_unseq` 策略。由于代码凭借内部互斥进行同步，因此试图采用 `std::execution::par_unseq` 策略会导致未定义行为。
  ```cpp
  //list 1
  class X{
      mutable std::mutex m;
      int data;
  public:
      X():data(0){}
      int get_value() const{
          std::lock_guard guard(m);
          return data;
      }
      void increment(){
          std::lock_guard guard(m);
          ++data;
      }
  };
  void increment_all(std::vector<X>& v){
      std::for_each(std::execution::par,v.begin(),v.end(),
          [](X& x){
              x.increment();
          });
  }
  
  ```
- 代码清单 2 展示了修改过的代码，它可以采用 `std:exccution::par_unseq` 策略。原来每个元素都具备一个互斥，本例将其改用单独一个互斥替代它们全部，这样一来整个容器都受它保护。
  ```cpp
  //list 2
  class Y{
      int data;
  public:
      Y():data(0){}
      int get_value() const{
          return data;
      }
      void increment(){
          ++data;
      }
  };
  class ProtectedY{
      std::mutex m;
      std::vector<Y> v;
  public:
  	void lock(){
           m.lock();
       }
  	void unlock(){
           m.unlock();
       }
       std::vector<Y>& get_vec(){
           return v;
       }
  };
  void increment_all(ProtectedY& data){
      std::lock_guard guard(data);
      auto& v=data.get_vec();
      std::for_each(std::execution::par_unseq,v.begin(),v.end(),
          [](Y& y){
              y.increment();
          });
  }
  ```
  在代码清单 2 中，代码对各个元素的访问并未采取同步操作，故 `std::execution::par_unseq` 策略可以安全使用。其缺点是这份代码的锁粒度太大，不像代码清单 1 中的锁粒度细分到元素级别。如果恰好出现了并发访问，而它来自算法函数调用以外，那该访问就会被迫等待，直到整个并行操作完成以后，该访问才会执行。
-