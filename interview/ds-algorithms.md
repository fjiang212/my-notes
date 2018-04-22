# Data Structure and Algorithms
http://www.programmeronrails.com/category/ds-algorithms/

## Data Structure
* [FIxed Size Array](http://www.programmeronrails.com/2015/11/13/fixed-size-array/)
    * Initialization
    ```
    int[] arr = new int[3];
    int arr[] = new int[3]; // or (less preferred)
    int[] arr = {v0, v1, v2};
    int arr[] = {v0, v1, v2}; // or (less preferred)
    ```
    * Performance
        * Fixed size array probably is the fastest data structure in most languages. For operations such as getting/setting values on an array by index, they could be completed in `O(1)` time.
        * The major downside of arrays is that the size of an array needs to be pre-defined. So if the size of the data can be changed, often we may need to define an array of of larger space than needed.

* [Dynamically Resizing Array](http://www.programmeronrails.com/2015/11/13/dynamically-resizing-array/)
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
    
    
    
## Algorithms

## Leetcode
