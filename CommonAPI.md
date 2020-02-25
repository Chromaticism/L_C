Common API:

Queue:
- LinkedList, ArrayBlockingQueue and PriorityQueue are the most common 	implementations.
- If any null operation is performed on BlockingQueues, NullPointerException is throw.
- BlockQueue have thread-safe implementations
- The Queues which are available in java.util package are Unbounded Queues
- The Queues which are available in Java.util.concurrent package are the Bounded Queues. 

Methods in Queue:
* add() — Add elements at the tail of the queue. 
* peek() — View the head of the queue without removing it, it will return NULL if the queue is empty
* element() — Is similar to peek(), It throw NoSuchElementException when the queue is empty
* remove() — remove and return the head of the queue. It throws exception 
* poll() — remove and return the head of the queue, return null if the queue is empty
* size() — return number of elements.
	
￼

Deque:
- The Deque is related to the double-ended queue that supports add or remove elements from either end of the data structure, it can be used as a queue (FIF)) or as a stack(LIFO). These are faster than Stack and LinedList.
- It provided the support of resizable array and helps in restriction-free capacity, so the grow the array according to the usage.
- Array dequeue prohibit the use of NULL element and do not accept any such element.
- Any concurrent access by multiple threads is not supported
- In the absence of external synchronization, Deque is not thread-sage.

Methods of Deque:
* add(element) : add an element to the tail
* addFirst(element) : Adds an element to the head.
* addLast(element) : Adds an element to the tail.
* offer(element) : Adds an element to the tail and return a boolean to explain if the insertion was successful.
* 
