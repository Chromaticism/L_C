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