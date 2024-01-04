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
-
-