- C++标准库定义了5个类别的迭代器：
	- [[输入迭代器]]（input iterator）
	  logseq.order-list-type:: number
	  属于[[单通迭代器]]，用途是获取值，它常常用于控制台或网络的输入，我 们也用它从生成序列中取得数据。如果我们让输入迭代器向前移动，其所有副本就会失效。
	- [[输出迭代器]]（output iterator)
	  logseq.order-list-type:: number
	  属于[[单通迭代器]]，用途是写出值。它常常用于文件输出，向容器添加新值。输出迭代器的步进会令其副本失效。
	- [[前向迭代器]]（forward iterator）
	  logseq.order-list-type:: number
	  前向迭代器属于[[多通迭代器]]，用途是单向迭代持久化数据。虽然我们无法使前向迭代器逆转，返回过往的位置，但我们可以保存其居于某个位置时的副本，以提取早前访问过的元素。前向选代器会返回元素的真正引用，通过它可以进行读写两种操作（条件是目标元素属于非 const 值）。
	- [[双向迭代器]]（bidirectional iterator）
	  logseq.order-list-type:: number
	  属于[[多通迭代器]]，但它可以折返，可以访问前面的元素。
	- [[随机访问迭代器]] （random access iterator）
	  logseq.order-list-type:: number
	  随机访问迭代器属于[[多通迭代器]]，前向、后向移动皆可，但其移动距离不再限于单个元素，我们可以通过它的数组索引运算符，按偏移量直接访问目标元素。
-
-