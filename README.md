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
 // TreeNode parent; // point to this node's parent node
}
```

工业界应用：

​	Too many to list all:

​		eg: social network analysis

​			  Information indexing

​			  Information compression

#### tree traverse

1. Pre-order:





