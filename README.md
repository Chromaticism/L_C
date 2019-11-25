## Queue:

1. FIFO == first in first out
2. Usages: Breadth-First Search related problems
3. 典型问题：
   1. Tree printout by level
   2. Sliding window problems(Deque: double ends manipulation)

## Stack

LIFO == last in first out: like a  box

Eg: insertion order insertion order 1, 2, 3, 4, then in the stack, it looks like:

​	4

​	3

​	2

​	1 <--- bottom of the stack



 ### Four popular interview questions:

##### Q1: how could we implement a queue by using two stacks

​		stack1:

​		stack2: 

​	Solution1: 

​					stack1: To buffer all new elements

​					stack2:  To pop out 1st element  

​								case1: if stack2 is empty, them we move all element from stack1 to stack2

​								case2: if stack2 is not empty, then we call stack2.pop()

​					Time complexity:

​								Push() ---> O(1)

​								Pop() ---> O(n)

​						Amortized time completity = O(??)





什么问题往stack 考虑？

从左到右linear scan 一个 array/string 时，如果要不断回头看左边最新的元素，往往要用到stack

	1. Histogram 中找最大长方形
 	2. reverse polish notation 逆波兰表达式的计算， a * (b + c)  ----> abc* 
 	3. String de repeatedly deduplication,  cabba -----> can -----> c



##Linkedlist

Key points: 

 1. when you want to de-reference a ListNode, make sure it is not a NULL pointer

    ​	```

    ```java
    ListNode p = new ListNode(0);
    ...p->value
    p.value
    ```

2. Never ever lost the control of the head pointer of the Linkedlist

   for example : when you reverse the linkedlist .



Q1: Reverse a linkedlist, loop and recursive

Q2: Find the middle node of a linkedlist.

Q3: if a linkedlist has a circle

Q4: Insert a node in a sorted linked list

​	Be carefull about two cornor cases: head and tail.



Q5: How to merge two sorted linkedlist into one long sorted linkedlist 

​		DummyNode : when we want to append new elements to an initially empty linkedList, we do not have an initial head node. In this case, we can new a dummy node to act as a head node.



Q6:  N1 --> N2 --> N3 --> N4 --> N5 --> ... --> Nn --> NULL

​		(N1 --> Nn) --> (N2 --> Nn-1) --> ......

Q7: Partition list:

​		Given a linked list and a target value x, partition it such that all nodes less than x are listed before the nodes larger than or equal to target value x.( keep the priginal relative order of the nodes in each of the two partition.)

​		eg: 1 --> 6 --> 3 --> 2 --> 5 --> 2 -->null

​		target: 4

​		result: 1 -->3 -->2a -->2b -->6 -->5

​		Notice that 5 was pointed to 2, but then it is in the end, watch out that there is no circle in the linkedList.



## Binary Tree && Binary Search Tree

Definition: at most two children node.

```java
Class TreeNode {
	int value;
	TreeNode left;
	TreeNode right;
 // TreeNode parent; // point to this node's parent node, not common
}
```

工业界应用：

​	Too many to list all:

​		eg: social network analysis

​			  Information indexing

​			  Information compression

#### tree traverse

​							10

​						/	         \

​					5					15

​				/		\				/	\

​			2			7			12	20

​		/		\

​	null		null

1. Pre-order:

   10	5	2	7	15	12	20

   Implementation with recursion:

   Pre-order: 我把我自己放在最前面来打印/更改value...然后再左， 右

   ```java
   void preOrder(TreeNode root) {
     if(root == null) return; // base case
     System.out.println(root.value);
     preOrder(root.left);
     preOrder(root.right);
   }
   ```

   

2. In-order

   2	5	7	10	12	15	20

   ```java
   void inOrder(TreeNode root) {
     if(root == null) return; // base case
     inOrder(root.left);
     System.out.println(root.value);
     inOrder(root.right);
   }
   ```

   

3. Post-order

   2	7	5	12	20	15	10

   ```java
   void postOrder(TreeNode root) {
     if(root == null) return; // base case
     postOrder(root.left);
     postOrder(root.right);
     System.out.println(root.value);
   }
   ```

   

   **Trick: base case usually refers to the null ChildNode below the leaf node.** 

   

### Balanced binary tree:

Define:  is commonly defined as a binary tree inwhich the depth of the left and right subtrees of every node differ by 1 or less.

​									10

​								  /		\

​								5			15

​							/	\		   / 	 \

​						2		 7

### Complete binary tree:

Define: is a binary tree in which every level, except possibly the last, is completely filled, and all nodes are far left as possible.

​									10

​								  /		\

​								5			15

​							/	\		   / 	 \

​						2		 7  	12		null



### Binary Search Tree:

Define:  for every single node in the tree, the values in its left subtree are all smaller than its value, and the values in its right subtree are all larger than its value.

​										10

​								  /		\

​								5			15

​							/	\		   / 	 \

​						2		 7  	12		20

in order traversal : 2	5	7	10	12	15	20 will form an ascending order.

![Screen Shot 2019-11-19 at 11.36.41 PM](/Users/robinzhou/Desktop/Screen Shot 2019-11-19 at 11.36.41 PM.png)

#### Discussion:

1. Binary tree 往往是最常见的 和 recursion 结合最紧密的面试题目类型

2. Reasons: 

   1. 每层的node 具备的性质， 传递的值和下一层的性质往往一致， 比较容易定义 recursive rule.
   2. Base case(generally): null pointer under the leaf node
   3. Example1: int getHeight(Node root)
   4. Example2: 统计tree里有多少个node

3. Fundamental Knowledge:

   1. Traversal of a binary tree
   2. Definition:
      1. Balanced binary tree
      2. Complete binary tree
      3. Binary search tree(BST) 

   ```java
   // get height of a binary tree
   public int getHeight(TreeNode root) {
     if(root == null) {
       return 0;
     }
     int left = getHeight(root.left);
     int right = getHeight(root.right);
     return 1 + Math.max(left, right);
   }
   // Time = O(n) 走了每一个node
   // Space = O(n) 最坏linkedlist，the height of the tree , call stack
   
   
   ```

Q1: How to determine whether a binary tree is a balanced binaty tree?

```java
//This is not the best way
public boolean isBalanced(TreeNode root) {
  if(root == null) {
    return true;
  }
  int left = getHeight(root.left);
  int right = getHeight(root.right);
  if(Math.abs(left - right) > 1) {
    return false;
  }
  return isBalanced(root.left) && isBalanced(root.right);
}
```

​												root			第一层：O(n/2) + O(n/2) = O(n)

​						/													\

​			isBalanced(root.left) （getHeight 为 n/2 Node）O(n/2) |	isBalanced(root.right) 

​					/ 			\

isBalanced(root.left)	isBalanced(root.right) 

第二层： O(n/4) + O(n/4) + O(n/4) + O(n/4)  = O(n);

一共 log(n) 层： So Time is O(nlogn);



Q2: How to determine whether a binary tree is symmetric?

 														10

​								5													5

​					1				3								3						1

​			2		4		6		8					8		6				4		2



```java
//Helper function
boolean isSymmetric(TreeNode one, TreeNode two) {
  if(one == null && two == null) {
    return true;
  }else if (one == null || two == null) {
    return false;
  }else if(one.value !== two.value) {
    return false;
  }
  
  return isSymmetric(one.left, two.right) && isSymmetric(one.right, two.left);
}
```

Time : 每层比较n/2 为： O(n)

Space: height: O(n)



Q3: Let's assume if we tweak the child with rchild of an arbitrary node in a binary tree, then the structure of the tree are not changed. Then how can we determine whether two binary trees structures are identical?

```java
public boolean isIdentical(TreeNode one, TreeNode two) {
  if(one == null && two == null) {
    return true;
  }else if (one == null || two == null) {
    return false;
  }else if(one.value !== two.value) {
    return false;
  }
  
  return isIdentical(one.left, two.left) && isIdentical(one.right, two.right) 
    || isIdentical(one.left, two.right) && isIdentical(one.right, two.left) 
}
```



​				root 1 n Nodes															root 2 n Nodes

​		/	  					| 															|							\

IIden(LL, RL)			IIden(LR, RR)								IIden(LL, RR)				IIden(LR, RL)

/||\							/||\												/||\									/||\



Time: Thing about the binary:

​			1 2 4 8 .... 

​			1 4 16 64 .....

We only consider the last level node because it is larger than the sum of levels that above the last one,

So the time is O(4 ^ log2_n) == O(2 ^ log2 (n ^ 2)) = O(n^2),

Space: level of the tree so log(n).





**Binary Search Tree Questions:**

Q1: How do we determine a binary tree is a BST?

​												10   == root [-inf, + inf]

​											/			\

​									5[-inf, 10]		15[10, +inf ]

​							/				\					/		\

​						2					7[5, 10]	 12		20

Look at the range of a root,

```java
public Boolean isBSTHelper(TreeNode root, int min, int max) {
  if(root == null) {
    return true;
  }
  if(root.value > max || root.value < min) {
    return false;
  }
  
  return isBSTHelper(root.left, min, root) && isBSTHelper(root.right, root, max);
}
```



Time: 

Space: 



​		







