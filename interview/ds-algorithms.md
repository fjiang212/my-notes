# Data Structure and Algorithms
http://www.programmeronrails.com/category/ds-algorithms/

## Data Structure
* [FIxed Size Array](http://www.programmeronrails.com/2015/11/13/fixed-size-array/)
    * Data Structure
    ```java
    int[] arr = new int[3];
    int arr[] = new int[3]; // or (less preferred)
    int[] arr = {v0, v1, v2};
    int arr[] = {v0, v1, v2}; // or (less preferred)
    ```
    * Performance
        * Fixed size array probably is the fastest data structure in most languages. For operations such as getting/setting values on an array by index, they could be completed in `O(1)` time.
        * The major downside of arrays is that the size of an array needs to be pre-defined. So if the size of the data can be changed, often we may need to define an array of of larger space than needed.

* [Dynamically Resizing Array](http://www.programmeronrails.com/2015/11/13/dynamically-resizing-array/)
    * Implementation (**`ArrayList`**)
    * Performance
        * A dynamically resizing array is an array that resizes itself as needed while still providing O(1) access. The basic idea is when the array is full, the array increases “its” size, often by doubling in size. Java has its own implementation of dynamic array – `ArrayList`.
       * As each doubling copies all the data in original array to a new array, it takes O(n) time. But for most cases, it is still O(1) access for set/get operations, and the worst case for memory space is 2n, which belongs to O(n) space.
    
* [String and StringBuffer](http://www.programmeronrails.com/2015/11/14/introduce-string-and-string-buffer/)
    * Comparison
        * String: Immutable
        * StringBuffer: Mutable, Synchonized and thread safe
        * StringBuilder: Mutable, non-synchonized, and not thread safe
    * Performance
        * Append to String will create a new String object.
        * Append to StringBuffer/StringBuilder will not create new object. 
    
* [Linked Lists](http://www.programmeronrails.com/2015/11/14/about-linked-lists/)
    * Implementation (**`Node`**)
    * Performance
        * Singly Link: Whenever we want to append a new node, we need to traverse the whole list to get to the tail node and it costs `O(n)` time. To reduce this, often we have a `‘tail’` reference pointing to the last node in the list. This reduces the append time to `O(1)`. However, if we need to insert a node after a specific node. We still need O(n) time to search that node. Deleting a node is similar to inserting a node after a sepecific node.
        * Double Linked List: For every node in a double linked list, except from the next node reference, there’s another node reference pointing to the previous node. Both the delete and insertAfter methods have O(1) time performance. Overall, double linked list is more flexible than singly linked list.

![alt text](images/LinkedList.PNG)

* [Hash Table](http://www.programmeronrails.com/2015/11/14/about-hash-tables/)

A hash table is a data structure that maps keys to values for highly efficient lookup. Every hash table has its hash function and an array to store the values.

* [Stack](http://www.programmeronrails.com/2015/11/14/about-stacks/)
    * Data Strusture: A stack is a container of objects that are inserted and removed according to the last-in first-out (LIFO) principle.
    * Implementation (**`Node`**)
    ```java
    class Stack {
      Node top;
      Object pop() {
         if(top != null) {
            Object item = top.data;
            top = top.next;
            return item;
         }
         return null;
      }
     void push(Object item) {
       Node t = new Node(item);
       t.next = top;
       top = t;
     }
     Object peek() {
       return top.data;
     }
   }
    ```
    
   * Performance: For all pop, push and peek methods, the time performance is O(1).

* [Queue](http://www.programmeronrails.com/2015/11/14/about-queues/)
    * Data Structure: A queue is a container of objects (a linear collection) that are inserted and removed according to the first-in first-out (FIFO) principle. Enqueue on the last node, Dequeue on the first node. 
    * Implementation (**`Node`**)
    
* [Representing Graph and Tree](http://www.programmeronrails.com/2015/11/14/representing-graphs-2/)    
    * Adjacency Lists: In adjacency lists, nodes are represented by objects. Each node has a list of references to other adjacent nodes.
    ```java
    class Node {
      Object item;
      ArrayList<Node> adjacentNodes;
      ...
   }
    ```
    * Matrix representation: Trees and graphs can also be represented by a double dimensional array where rows and columns represent the nodes and will use special values or actual edge cost as the values if they are connected.
    ```java
    int[][] g = {
     {0,1,1,1},
     {0,0,0,0},
     {0,0,0,0},
     {0,1,0,0},
   }
    ```

## Algorithms


## Leetcode
