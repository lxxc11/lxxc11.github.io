# 树  
1.[各种树](#各种树)   
## 各种树   
1.`二叉树`:二叉树是每个结点最多有两个子树的一种树结构。在实际使用时会根据链表和有序数组等数据结构的不同优势进行选择。有序数组的优势在于二分查找，链表的优势在于数据项的插入和数据项的删除。
但是在有序数组中插入数据就会很慢，同样在链表中查找数据项效率就很低。综合以上情况，二叉树可以利用链表和有序数组的优势，同时可以合并有序数组和链表的优势，二叉树也是一种常用的数据结构。
二叉树由节点（node）和边组成。节点分为根节点、父节点、子节点;二叉树一个节点左子节点的关键字小于这个节点，右子节点关键字大于或等于这个父节点。  
2.`满二叉树`:深度为k且有2^k-1个结点的二叉树称为满二叉树(及每一层节点都满的)  
3.`完全二叉树`:设二叉树的深度为h，除第 h 层外，其它各层 (1～h-1) 的结点数都达到最大个数，
          第 h 层所有的结点都连续集中在最左边(及虽然最底层不满，但是按顺序排列的,也就是最下面一层的结点都集中在该层最左边的若干位置的二叉树)    
4.`二叉查找树(二叉排序树)(二叉搜索树)`:它是一 棵空树或（1）若左子树不为空，则左子树上所有结点的值均小于它的根节点的值
                                （2）若右子树不为空，则右子树上所有结点的值均大于它的根节点的值
                                （3）左右子树自己也是二叉排序树   
5.`平衡二叉树(AVL树)`:它是一 棵空树或它的左右两个子树的高度差的绝对值不超过1，并且左右两个子树都是一棵平衡二叉树。  
6.`红黑树`：红黑树是一棵二叉搜索树，它在每个节点增加了一个存储位记录节点的颜色，可以是RED,也可以是BLACK；通过任意一条从根到叶子简单路径上颜色的约束，红黑树保证最长路径不超过最短路径的二倍，因而近似平衡。  
具体性质如下：  
      (1)每个节点颜色不是黑色，就是红色  
      (2)根节点是黑色的  
      (3)如果一个节点是红色，那么它的两个子节点就是黑色的（没有连续的红节点）  
      (4)对于每个节点，从该节点到其后代叶节点的简单路径上，均包含相同数目的黑色节点  
7.`B树(B-树)`：B树（B-tree）是一种树状数据结构，它能够存储数据、对其进行排序并允许以O(log n)的时间复杂度运行进行查找、顺序读取、插入和删除的数据结构。B树，概括来说是一个节点可以拥有多于2个子节点的二叉查找树。   
8.`B+树`：B+树是B树的一种变形体，它与B树的差异在于：         
      (1)有K个子节点的节点必然有K个关键码  
      (2)非叶节点仅具有索引作用，元素信息均存放在叶节点中  
      (3)树的所有叶节点构成一个有序链表，可以按照关键码排序的次序遍历全部记录   
9.`LSM数(Log-Structured Merge Tree)`:B+ 树读性能好，但由于需要有序结构，当key比较分散时，磁盘寻道频繁，造成写性能较差。
   LSM 是将一个大树拆分成N棵小树，先写到内存（无寻道问题，性能高），在内存中构建一颗有序小树（有序树），随着小树越来越大，内存的小树会flush到磁盘上。当读时，由于不知道数据在哪棵小树上，因此必须遍历（二分查找）所有的小树，但在每颗小树内部数据是有序的。     