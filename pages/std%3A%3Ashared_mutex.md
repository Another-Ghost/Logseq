- #C++17
- `std::shared_mutex` 是 C++17 引入的一个[[同步原语]]，用于实现[[读写锁]]（Read-Write Lock）。它允许多个线程同时读取共享数据（共享锁定），但在写入数据时（独占锁定），只允许一个线程访问，以此确保数据的一致性和线程安全。
- ### 主要特点
	- **共享读取**：多个线程可以同时获取共享锁（读锁），允许它们同时读取共享资源。
	- **独占写入**：只有一个线程可以获取独占锁（写锁），用于写入或修改共享资源。在独占锁定期间，其他线程既不能读取也不能写入。
	- **提高性能**：通过允许多个读取操作同时进行，`std::shared_mutex` 可以提高并发程序的性能，特别是在读操作远多于写操作的场景中。
- ### 主要成员函数
	- **`lock`**：获取独占锁。如果锁已被其他线程以任何方式锁定，则当前线程将阻塞，直到能够获取锁为止。
	- **`unlock`**：释放独占锁。
	- **`lock_shared`**：获取共享锁。如果锁已被其他线程独占锁定，则当前线程将阻塞，直到能够获取共享锁为止。
	- **`unlock_shared`**：释放共享锁。
	- **`try_lock`**：尝试获取独占锁而不阻塞。如果锁立即可用，则获取锁并返回 `true`；否则，返回 `false`。
	- **`try_lock_shared`**：尝试获取共享锁而不阻塞。如果锁立即可用，则获取锁并返回 `true`；否则，返回 `false`。
- ### 使用示例
	- 下面是一个使用 `std::shared_mutex` 实现读写锁的示例：
	  
	  ```cpp
	  #include <iostream>
	  #include <shared_mutex>
	  #include <thread>
	  #include <vector>
	  
	  std::shared_mutex rwMutex;
	  int sharedData = 0;
	  
	  void readerFunction(int id) {
	    rwMutex.lock_shared();
	    std::cout << "Reader " << id << " sees shared data as: " << sharedData << std::endl;
	    rwMutex.unlock_shared();
	  }
	  
	  void writerFunction(int id) {
	    rwMutex.lock();
	    sharedData = id; // 模拟更新共享数据
	    std::cout << "Writer " << id << " updated shared data to: " << sharedData << std::endl;
	    rwMutex.unlock();
	  }
	  
	  int main() {
	    std::vector<std::thread> readers;
	    for (int i = 0; i < 5; ++i) {
	        readers.push_back(std::thread(readerFunction, i));
	    }
	  
	    std::vector<std::thread> writers;
	    for (int i = 0; i < 2; ++i) {
	        writers.push_back(std::thread(writerFunction, i + 1));
	    }
	  
	    for (auto& reader : readers) {
	        reader.join();
	    }
	    for (auto& writer : writers) {
	        writer.join();
	    }
	  
	    return 0;
	  }
	  ```
	  
	  在这个示例中，有多个读线程和写线程。读线程使用 `lock_shared` 获取共享锁来读取数据，而写线程使用 `lock` 获取独占锁来写入数据。这确保了在写线程更新数据时，读线程不能访问数据，从而防止了数据竞争和不一致的问题。
- ### 注意事项
	- 使用 `std::shared_mutex` 时要确保正确地配对 `lock`/`unlock` 和 `lock_shared`/`unlock_shared` 调用，以避免死锁或资源泄露。
	- 尽管 `std::shared_mutex` 提高了并发读取的性能，但它的使用和管理比单一的 `std::mutex` 更复杂。只有在确实需要同时读取操作的场景中才推荐使用。