- `std::thread` 支持[[move]]，线程的所有权可以在函数外进行转移。
- [[std::thread]]的[[移动]]支持的一个好处是，你可以在[[thread_guard]]类的基础上进行构建，并让它拥有线程的所有权。这避免了在thread_guard对象比它引用的线程存活更久时可能产生的不愉快后果，同时也意味着**一旦所有权被转移到对象中，就没有人能够再[[join]]或 [[detach]]线程**。因为这主要是为了确保在退出作用域之前完成线程，所以将这个类命名为 `scoped_thread`。
  下面的代码中显示了实现，以及一个简单的例子。
- ``` cpp
  class scoped_thread
  {
    std::thread t;
  public:
    
    explicit scoped_thread(std::thread t_): // 1
    	t(std::move(t_))
    {
  	if(!t.joinable()) // 2
  		throw std::logic_error(“No thread”);
    }
    
    ~scoped_thread()
    {
      t.join(); // 3
    }
    
    scoped_thread(scoped_thread const&)=delete;
    scoped_thread& operator=(scoped_thread const&)=delete;
  };
  
  struct func; // 用local变量引用初始化的函数对象
  
  void f()
  {
  	int some_local_state;
  	scoped_thread t(std::thread(func(some_local_state))); // 4
  	do_something_in_current_thread();
  } // 5
  ```