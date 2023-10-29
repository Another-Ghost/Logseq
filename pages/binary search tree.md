alias:: 二叉查找树, 二叉搜索树, ordered binary tree, 有序二叉树, sorted binary tree, 排序二叉树

- [[二叉查找树]]是指一颗[[空树]]或者具有如下性质的[[二叉树]]：
	- 若任意 *节点* 的 *左子树* 不 空，则左子树上所有节点的值均**小于**它的 *根节点* 的值；
	  logseq.order-list-type:: number
	- 若任意节点的 *右子树* 不空，则右子树上所有节点的值均**大于**它的根节点的值；
	  logseq.order-list-type:: number
	- 任意节点的左、右子树也分别为[[二叉查找树]]；
	  logseq.order-list-type:: number
- # ## 二叉查找树的查找算法
	- 在二叉查找树b中查找x的过程为：
		- 若b是空树，则搜索失败，否则：
		  logseq.order-list-type:: number
		- 若x等于b的根节点的数据域之值，则查找成功；否则：
		  logseq.order-list-type:: number
		- 若x小于b的根节点的数据域之值，则搜索左子树；否则：
		  logseq.order-list-type:: number
		- 查找右子树。
		  logseq.order-list-type:: number
	- ``` cpp
	  Status SearchBST(BiTree T, KeyType key, BiTree f, BiTree &p) {
	      // 在根指针T所指的二叉查找树中递归地查找其关键字等于key的数据元素，若查找成功，
	      // 则指针p指向该数据元素节点，并返回TRUE，否则指针指向查找路径上访问的最后
	      // 一个节点并返回FALSE，指针f指向T的双亲，其初始调用值为NULL
	      if (!T) { // 查找不成功
	          p = f;
	          return false;
	      } else if (key == T->data.key) { // 查找成功
	          p = T;
	          return true;
	      } else if (key < T->data.key) // 在左子树中继续查找
	          return SearchBST(T->lchild, key, T, p);
	      else // 在右子树中继续查找
	          return SearchBST(T->rchild, key, T, p);
	  }
	  ```
-