alias:: 线程存储期, thread-local storage duration

- 该对象的存储在^^线程开始时^^分配，并在^^线程结束时^^释放。
- **每个线程都有其自己的对象实例**。
- 只有声明为[[thread_local]]的对象具有这种存储期。
- [[thread_local]]可以与 static 或 extern 一起出现以调整[[链接]]。