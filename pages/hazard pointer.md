alias:: 危险指针, 风险指针

- ^^危险指针^^之所以称之为危险指针，是因为删除可能仍被其他线程引用的节点具有风险。如果其他线程确实持有对该节点的引用，并继续通过该引用访问节点，那么你将面临未定义行为。
  基本思想是，如果一个线程打算访问另一个线程可能想要删除的对象，它首先应该设置一个危险指针来引用该对象，通知另一个线程删除该对象确实具有风险。一旦不再需要该对象，危险指针便会被清除。如果你曾观看过牛津/剑桥赛艇比赛，你会看到类似的机制在比赛开始时使用：任何一只船的舵手都可以举手表示他们还没准备好。只要任一舵手举手，裁判就不得开始比赛。如果两位舵手都放下手，比赛就可以开始，但如果比赛尚未开始，舵手觉得情况有变，可以再次举手。
  当一个线程想要删除一个对象时，它必须首先检查系统中其他线程的危险指针。如果没有任何危险指针引用该对象，它就可以安全地删除。否则，必须留到以后处理。定期检查之前留下待以后处理的对象列表，看看其中是否有现在可以删除的对象。
  如此高层次的描述听起来相对直接，那么你如何在 C++ 中实现这一点呢？
  首先，你需要一个位置来存储你正在访问的对象的指针，即危险指针本身。这个位置必须对所有线程可见，你需要为可能访问数据结构的每个线程提供一个这样的位置。正确且高效地分配它们可能是一个挑战，所以我们暂时留到后面处理，并假设你有一个 `get_hazard_pointer_for_current_thread()` 函数，该函数返回对你的危险指针的引用。然后你需要在读取你打算解引用的指针时设置它——在这个案例中是从列表中读取头指针的值：
  你必须在 while 循环中执行此操作，以确保在读取旧头指针（1）和设置危险指针（2）之间节点没有被删除。在此窗口期间，没有其他线程知道你正在访问这个特定节点。幸运的是，如果旧头节点将被删除，头指针本身必须已经改变，因此你可以检查这一点，并继续循环，直到你知道头指针仍然具有你设置的危险指针的相同值（3）。这样使用危险指针的依据是，在引用的对象被删除后使用指针的值是安全的。如果你使用默认的 new 和 delete 实现，这在技术上是未定义行为，因此你需要确保你的实现允许这种用法，或者你需要使用允许这种用法的自定义分配器。
  现在你已经设置了危险指针，你可以继续执行 `pop()` 的其余部分，安心地知道没有其他线程会删除这些节点。好吧，几乎是：每次你重新加载 `old_head` 时，你需要在解引用新读取的指针值之前更新危险指针。一旦你从列表中提
  取了一个节点，你可以清除你的危险指针。如果没有其他危险指针引用你的节点，你可以安全地删除它；否则，你必须将其添加到稍后删除的节点列表中。以下列表显示了使用此方案实现 `pop()` 的完整实现。
  <!--Converted by ToLogseq-->
- 基本思想是，如果一个线程打算访问另一个线程可能想要删除的对象，它首先应该设置一个危险指针来引用该对象，通知另一个线程删除该对象确实具有风险。一旦不再需要该对象，危险指针便会被清除。
	- >如果你曾观看过牛津/剑桥赛艇比赛，你会看到类似的机制在比赛开始时使用：任何一只船的舵手都可以举手表示他们还没准备好。只要任一舵手举手，裁判就不得开始比赛。如果两位舵手都放下手，比赛就可以开始，但如果比赛尚未开始，舵手觉得情况有变，可以再次举手。
- 当一个线程想要删除一个对象时，它必须首先检查系统中其他线程的危险指针。如果没有任何危险指针引用该对象，它就可以安全地删除。否则，必须留到以后处理。定期检查之前留下待以后处理的对象列表，看看其中是否有现在可以删除的对象。
- ## 危险指针的实现
  首先，你需要一个位置来存储你正在访问的对象的指针，即危险指针本身。**这个位置必须对所有线程可见，你需要为可能访问数据结构的每个线程提供一个这样的位置**。正确且高效地分配它们可能是一个挑战，所以我们暂时留到后面处理，并假设你有一个 `get_hazard_pointer_for_current_thread()` 函数，该函数返回对你的危险指针的引用。然后你需要在读取你打算解引用的指针时设置它——在这个案例中是从列表中读取头指针的值：
  ``` cpp
  std::shared_ptr<T> pop()
  {
    std::atomic<void*>& hp = get_hazard_pointer_for_current_thread();
    node* old_head = head.load(); // 1
    node* temp;
    do
    {
      temp = old_head;
      hp.store(old_head); // 2
      old_head = head.load();
    } while (old_head != temp); // 3
    // ...
  }
  ```
  你必须在 `while` 循环中执行此操作，以确保在读取旧头指针（1）和设置危险指针（2）之间节点没有被删除。在此窗口期间，没有其他线程知道你正在访问这个特定节点。幸运的是，如果旧头节点将被删除，头指针本身必须已经改变，因此你可以检查这一点，并继续循环，直到你知道头指针仍然具有你设置的危险指针的相同值（3）。
  这样使用危险指针依赖的一点是：在引用的对象被删除后使用指针的值是安全的。如果你使用默认的 new 和 delete 实现，这在技术上是未定义行为，因此你需要确保你的实现允许这种用法，或者你需要使用允许这种用法的自定义分配器。
- 现在你已经设置了危险指针，你可以继续执行 `pop()` 的其余部分，安心地知道没有其他线程会删除这些节点。但每次你重新加载 `old_head` 时，你需要在解引用新读取的指针值之前**更新危险指针**。
  一旦你从 列表 中提取了一个节点，你可以清除你的危险指针。如果没有其他危险指针引用你的节点，你可以安全地删除它；否则，你必须将其添加到稍后删除的节点列表中。
- 以下代码显示了使用此方案实现 `pop()` 的完整实现。
  ``` cpp
  // an implementation of pop() using hazard pointers
  std::shared_ptr<T> pop()
      {
          std::atomic<void*>& hp=get_hazard_pointer_for_current_thread(); //获取当前线程的风险指针（指向还在被该线程引用的node）
          node* old_head=head.load();
          do // 如果compare_exchange_strong操作不成功（因为其他线程已经修改了head），那么外层循环会重复，过程重新开始。
          {
              node* temp;
              do // 1 直到将风险指针设为head指针
              {
                  temp=old_head;
                  hp.store(old_head);
                  old_head=head.load(); 
              } while(old_head!=temp); //用于将风险指针（hp）设置为栈的当前head。old_head与head不一致，则停止循环
          }
          while(old_head &&
          !head.compare_exchange_strong(old_head,old_head->next)); //用于尝试从栈顶删除节点，直到成功为止。它检查head的值是否仍然是old_head（即没有其他线程修改过head），则停止循环，更新old_head 为head->next 
          hp.store(nullptr); // 2 当声明完成，清除风险指针
          std::shared_ptr<T> res;
          if(old_head)
          {
              res.swap(old_head->data);
              if(outstanding_hazard_pointers_for(old_head)) // 3 在删除之前对风险指针引用的节点进行检查
              {
                  reclaim_later(old_head); // 4
              }
              else
              {
                  delete old_head; // 5
              }
              delete_nodes_with_no_hazards(); // 6
          }
          return res;
      }
  ```
- 首先，你已经将设置危险指针的循环移动到了外层循环内部，如果 compare-exchange 失败，将重新加载 `old_head` (1) 。这里你使用[[compare_exchange_strong()]]是因为你会在 `while` 循环内部进行操作：[[compare_exchange_weak()]]上的[[假性失败]]会导致不必要地重置危险指针。这确保了在你解引用 `old_head` 之前危险指针正确设置。
  一旦你声称该节点为你所拥有，你可以清除你的危险指针 (2) 。如果你确实得到了一个节点，你需要检查其他线程的危险指针是否引用它 (3) 。如果是这样，你还不能删除它，因此你必须将它放在稍后回收的列表中 (4) ；否则，你可以立即删除它 (5) 。最后，你检查了任何你不得不调用 `reclaim_later()` 的节点。如果这些节点不再有任何危险指针引用，你可以安全地删除它们 (6) 。任何仍有[[未解决风险指针]]的节点将留给下一个调用 `pop()` 的线程。
- 这些新功能——`get_hazard_pointer_for_current_thread()`、`reclaim_later()`、`outstanding_hazard_pointers_for()` 和 `delete_nodes_with_no_hazards()`——仍有很多细节隐藏在其中，让我们揭开幕后的帷幕，看看它们是如何工作的。
- `get_hazard_pointer_for_current_thread()` 用于将危险指针实例分配给线程的确切方案对程序逻辑并不重要（尽管它可以影响效率，稍后你会看到）。
  现在，你将采用一个简单的结构：一个固定大小的数组，包含^^线程 ID 和指针的对^^。`get_hazard_pointer_for_current_thread()` 然后遍历数组以找到第一个空闲插槽，并将该插槽的 ID 条目设置为当前线程的 ID 。当线程退出时，通过将 ID 条目重置为默认构造的 `std::thread::id()` 来释放插槽。以下列表显示了这一点。
- ``` cpp
  unsigned const max_hazard_pointers=100;
  
  struct hazard_pointer
  {
      std::atomic<std::thread::id> id;
      std::atomic<void*> pointer;
  };
  
  hazard_pointer hazard_pointers[max_hazard_pointers];
  
  class hp_owner
  {
      hazard_pointer* hp;
  
  public:
      hp_owner(hp_owner const&)=delete;
      hp_owner operator=(hp_owner const&)=delete;
  
      hp_owner():
          hp(nullptr)
      {
          for(unsigned i=0;i<max_hazard_pointers;++i)
          {
              std::thread::id old_id;
              if(hazard_pointers[i].id.compare_exchange_strong(old_id,std::this_thread::get_id())) // 6
              {
                  hp=&hazard_pointers[i];
                  break; // 7
              }
          }
          if(!hp) // 1
          {
              throw std::runtime_error("No hazard pointers available");
          }
      }
  
      std::atomic<void*>& get_pointer()
      {
          return hp->pointer;
      }
  
      ~hp_owner() // 2
      {
          hp->pointer.store(nullptr); // 8
          hp->id.store(std::thread::id()); // 9
      }
  };
  
  std::atomic<void*>& get_hazard_pointer_for_current_thread()  // 3
  {
      thread_local static hp_owner hazard; // 4 每个线程都有自己的风险指针 
      return hazard.get_pointer(); // 5
  }
  ```
- `get_hazard_pointer_for_current_thread()` 的实现本身看似简单（3）：它有一个类型为 `hp_owner` 的 `thread_local` 变量（4），该变量存储当前线程的危险指针。然后它从该对象返回指针（5）。
  其工作原理如下：每个线程第一次调用此函数时，会创建一个新的 `hp_owner` 实例。这个新实例的构造函数（1）搜索 `owner`/`pointer`对的表格，寻找没有`owner`的条目。它使用 `compare_exchange_strong()` 来检查是否有没有拥有者的条目，并尝试一次性声明它（2）。如果 `compare_exchange_strong()` 失败，意味着另一个线程拥有该条目，因此你继续移动到下一个。如果交换成功，你成功为当前线程声明了该条目，因此你存储它并停止搜索（3）。如果到达列表的末尾而没有找到空闲条目（4），那么使用危险指针的线程过多，因此会抛出异常。
- 一旦为给定线程创建了 `hp_owner` 实例，后续访问会快得多，因为指针被缓存，因此不必再次扫描表格。
- 当每个线程退出时，如果为该线程创建了 `hp_owner` 实例，则在它被销毁前，析构函数会将指针重置为 `nullptr` 并将所有者 ID 设置为 `std::thread::id()`，允许其他线程稍后重用该条目（5）。
- 有了这个 `get_hazard_pointer_for_current_thread()` 的实现，`outstanding_hazard_pointers_for()` 的实现就变得简单——扫描危险指针表，寻找引用的条目：
  ``` cpp
  bool outstanding_hazard_pointers_for(void* p)
  {
      for(unsigned i=0;i<max_hazard_pointers;++i)
      {
          if(hazard_pointers[i].pointer.load()==p)
          {
              return true;
          }
      }
      return false;
  }
  ``` 
  检查每个条目是否有拥有者甚至没有必要：未拥有的条目将具有空指针，因此比较将无论如何都会返回 `false`，这简化了代码。
- `reclaim_later()` 和 `delete_nodes_with_no_hazards()` 然后可以在一个简单的链表上工作；`reclaim_later()` 将节点添加到列表中，`delete_nodes_with_no_hazards()` 扫描列表，删除没有[[未解决危险]]的条目。下面的代码显示了这个实现。
- ```cpp
  template<typename T>
  void do_delete(void* p)
  {
      delete static_cast<T*>(p);
  }
  
  struct data_to_reclaim
  {
      void* data;
      std::function<void(void*)> deleter;
      data_to_reclaim* next;
  
      template<typename T>
      data_to_reclaim(T* p): // 1
          data(p),
          deleter(&do_delete<T>),
          next(0)
      {}
  
      ~data_to_reclaim()
      {
          deleter(data); // 2
      }
  };
  
  std::atomic<data_to_reclaim*> nodes_to_reclaim;
  
  void add_to_reclaim_list(data_to_reclaim* node) // 3
  {
      node->next=nodes_to_reclaim.load();
      while(!nodes_to_reclaim.compare_exchange_weak(node->next,node));
  }
  
  template<typename T>
  void reclaim_later(T* data) // 4
  {
      add_to_reclaim_list(new data_to_reclaim(data)); // 5
  }
  
  void delete_nodes_with_no_hazards()
  {
      data_to_reclaim* current=nodes_to_reclaim.exchange(nullptr); // 6
      while(current)
      {
          data_to_reclaim* const next=current->next;
          if(!outstanding_hazard_pointers_for(current->data)) // 7
          {
              delete current; // 8
          }
          else
          {
              add_to_reclaim_list(current); // 9
          }
          current=next;
      }
  }
  ```
- 首先，`reclaim_later()`是一个函数模板，而不是普通函数 <span>&#x2463;</span> 。这是因为危险指针是一种通用工具，所以你不希望它们仅用于栈节点。你已经使用`std:: atomic<void*>` 来存储指针。因此，你需要处理任何指针类型，但不能使用 `void*`，因为你希望在可以删除数据项时进行删除，而删除操作需要指针的实际类型。`data_to_reclaim` 的构造函数很好地处理了这个问题，如你稍后会看到；`reclaim_later()` 为你的指针创建一个新的 `data_to_reclaim` 实例并将其添加到回收列表中。`add_to_reclaim_list` <span>&#x2464;</span> 本身③是一个在列表头上的简单 `compare_exchange_weak()` 循环，就像你之前见到的那样。
- 回到 `data_to_reclaim` 的构造函数①：构造函数也是一个模板。它将要删除的数据存储为 `void*` 在 `data` 成员中，然后存储一个指向 `do_delete()` 适当实例化的指针——一个简单的函数，将给定的 `void*` 强制转换为所选指针类型，然后删除所指向的对象。`std::function<>` 安全地封装了这个函数指针，因此 `data_to_reclaim` 的析构函数可以通过调用存储的函数来删除数据。当将节点添加到列表时，不会调用 `data_to_reclaim` 的析构函数；当没有对该节点的危险指针时才会调用。这个职责在于 `delete_nodes_with_no_hazards()`。
- `delete_nodes_with_no_hazards()` 首先通过一个简单的 `exchange()`  <span>&#x2465;</span>  声明整个要回收的节点列表。这一步简单但至关重要，确保这是唯一试图回收这组节点的线程。其他线程现在可以自由地将进一步的节点添加到列表中，甚至尝试回收它们，而不会影响此线程的操作。
  然后，只要列表中仍有节点，你就会逐个检查它们，看看是否还有未解决的危险指针 <span>&#x2466;</span> 。如果没有，你可以安全地删除该条目（并清理存储的数据） <span>&#x2467;</span> 。否则，你将该项重新添加到列表中以便稍后回收 <span>&#x2468;</span> 。
- 尽管这个简单的实现确实可以安全地回收已删除的节点，但它给整个过程增加了相当大的开销。扫描危险指针数组需要检查 `max_hazard_pointers` 个原子变量，而且这在每次 `pop()` 调用时都会发生。原子操作本质上很慢——通常比桌面 CPU 上的等效非原子操作慢 100 倍——因此这使得 `pop()` 成为一个昂贵的操作。你不仅需要为即将移除的节点扫描危险指针列表，还要为等待列表中的每个节点进行扫描。这种操作成本太高了。显然，需要找到一种更好的方法来优化这个过程。
-
	- >危险指针的另一个缺点是它们受到 IBM 提交的专利申请的保护。虽然我相信该专利现在已经过期，但如果你在专利有效的国家/地区编写软件，最好找专利律师帮你核实这一点，或者确保有合适的许可安排。这是许多无锁内存回收技术的一个常见问题；这是一个活跃的研究领域，因此大公司正在尽可能地申请专利。你可能会问我为什么花了这么多页面讨论一种可能无法使用的技术，这是个很好的问题。首先，可能无需支付许可费即可使用该技术。例如，如果你在开发 GPL 授权的免费软件，你的软件可能受 IBM 的非主张声明的保护。其次，也是最重要的，这些技术的解释显示了编写无锁代码时需要考虑的一些重要问题，例如原子操作的成本。最后，有一项提案将危险指针纳入未来 C++ 标准的修订版，因此即使未来你希望能够使用编译器供应商的实现，了解它们的工作原理仍然有用。
	  那么，有没有可以用于无锁代码的未申请专利的内存回收技术？幸运的是，有一种这样的机制就是[[引用计数]]。