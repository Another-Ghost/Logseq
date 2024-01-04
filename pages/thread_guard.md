- 使用[[RAII]]等待[[线程]]完成
  ``` cpp
  class thread_guard
  {
    std::thread& t;
  public:
    explicit thread_guard(std::thread& t_):
    	t(t_)
    {}
    ~thread_guard()
    {
    	if(t.joinable()) // 1
    	{
    		t.join(); // 2
    	}
    }
    thread_guard(thread_guard const&)=delete; // 3
    thread_guard& operator=(thread_guard const&)=delete;
  };
  struct func;
  void f()
  {
    int some_local_state=0;
    func my_func(some_local_state);
    std::thread t(my_func);
    thread_guard g(t);
    do_something_in_current_thread();
  } // 4
  ```