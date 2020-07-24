# Data Structures and Algorithms

Here you'll find implementations of popular algorithms and data structures in Java language Swift, with brief explanations of how they work.

If you're a computer science student who needs to learn this stuff for exams -- or if you're a self-taught programmer who wants to brush up on the theory behind your craft -- this repository will definitely help!

😍 Suggestions and contributions are welcome! 😍


## How to use this repository?

The respository can be cloned or be downloaded as a zip file.

1. Install all Dependencies

    - [Download JDk](https://www.oracle.com/in/java/technologies/javase-downloads.html)
  
    - [Set the Environment Path Variable](https://www.java.com/en/download/help/path.xml)
  
    - [Downlod Eclipse](https://www.eclipse.org/downloads/packages/release/oxygen/3a/eclipse-ide-java-developers)
  
2. Open the folder in Eclipse

    * File -> Import -> Projects from or Archive -> Select Directory -> Select the Project -> Finish

   

## Important Resources

[Codechef CCDSAP Syllabus](https://www.codechef.com/certification/data-structures-and-algorithms/prepare). A syllabus to prepare to get certified in DSA by Codechef.

[GeeksforGeeks Gate Syllabus for Data Structures and Algorithms](https://www.geeksforgeeks.org/gate-cs-notes-gq/). Section 3: Algorithms, Section 4: Programming and Data Structures

**HackerEarth Tutorials and Problems:**

  - [Basic Programming](https://www.hackerearth.com/practice/basic-programming/).  
  - [Data Structure](https://www.hackerearth.com/practice/data-structures/).
  - [Algorithm](https://www.hackerearth.com/practice/algorithms/).

**Youtube Links:**

   - [Algorithm Tutorials by Abdul Bari](https://youtu.be/0IAPZzGSbME). 
   - [My Code School Data Structure Tutorial](https://youtu.be/92S4zgXN17o).


## Where to start?

[Array](https://github.com/tabassum-khan/Data-Structures-and-Algorithms/tree/master/array).

[Linked List](https://github.com/tabassum-khan/Data-Structures-and-Algorithms/tree/master/linkedList).

[Stacks](https://github.com/tabassum-khan/Data-Structures-and-Algorithms/tree/master/stacks).

[Queues](https://github.com/tabassum-khan/Data-Structures-and-Algorithms/tree/master/queues).

[Recursion](https://github.com/tabassum-khan/Data-Structures-and-Algorithms/tree/master/recursion).
    
    
## Linear Data Structures

### Array

- [Introduction to Arrays](https://github.com/tabassum-khan/Data-Structures-and-Algorithms/tree/master/array)

### Stack - Last in First Out

- [Implementing Stack using Array](https://github.com/tabassum-khan/Data-Structures-and-Algorithms/blob/master/stacks/StackArray.java).
- [Implementing Stack using Linked List](https://github.com/tabassum-khan/Data-Structures-and-Algorithms/blob/master/stacks/StackLL.java).


### Queues - First in First Out

- [Queue using Array]().
- [Queue using Linked List]().
- [Circular Queue]().
- [Priority Queue](). A queue where the most important element is always at the front.

### Hashing

- [Separate Chaining]().
- [Linear Probing]().
- [Quadratic Probing]().
- [Double Hashing]().


## Hierarchial Data Structures

### Tree

- [Tree](). A general-purpose tree structure.
- [Binary Tree](). A tree where each node has at most two children.
- [Binary Search Tree(BST)](). A binary tree that orders its nodes in a way that allows for fast queries.
- [Augmented BST](). 
- [Heap](). A binary tree stored in an array, so it doesn't use pointers. Makes a great priority queue.
- [Trie](). A special type of tree used to store associative data structures.


### Graph

- [Graph]().
- [BFS and DFS]().
- [Graph using Adajcency List]().
- [Graph using HashSets]().


## Algorithms

### Sorting

Basic Sorts:

  - [Insertion Sort]().
  - [Bubble Sort]().
  - [Selection Sort]().

Fast Sorts:

  - [Merge Sort](). 
  - [Quick Sort]().
  - [Hoare Quick Sort]().
  - [Heap Sort]().
  
Special Purpose Sorts:

- [Counting Sort]().
- [Radix Sort]().



### Searching

- [Linear Search](). Find an element in an array.
- [Binary Search](). Quickly find elements in a sorted array.
- [k-th Largest Element](). Find the k-th largest element in an array, such as the median.


### String Search

- [Brute-Force String Search](). A naive method.
- [Boyer-Moore](). A fast method to search for substrings. It skips ahead based on a look-up table, to avoid looking at every character in the text.


### Backtracking

- [Knights Tour]().
- [N Queens]().
- [Rat in a Maze]().
- [Subset Sum]().


### Greedy Algorithm

- [Activity Selection Problem]().
- [Job Sequencing]().
- [Optimal Merge Pattern]().
- [Huffman Coding]().
- [Fractional Knapsack]().
- [Egyptian Fraction]().
- [Bracket Balancing]().


## Useful Information

### Big O Notation

Big O notation is used to classify algorithms according to how their running time or space requirements grow as the input size grows. On the chart below you may find most common orders of growth of algorithms specified in Big O notation.

![Big-O Graph](/assets/big-o-graph.png)

Source: [Big O Cheat Sheet](https://www.bigocheatsheet.com/).


Below is the list of some of the most used Big O notations and their performance comparisons against different sizes of the input data.

| Big O Notation | Computations for 10 elements | Computations for 100 elements | Computations for 1000 elements  |
| -------------- | ---------------------------- | ----------------------------- | ------------------------------- |
| **O(1)**       | 1                            | 1                             | 1                               |
| **O(log N)**   | 3                            | 6                             | 9                               |
| **O(N)**       | 10                           | 100                           | 1000                            |
| **O(N log N)** | 30                           | 600                           | 9000                            |
| **O(N^2)**     | 100                          | 10000                         | 1000000                         |
| **O(2^N)**     | 1024                         | 1.26e+29                      | 1.07e+301                       |
| **O(N!)**      | 3628800                      | 9.3e+157                      | 4.02e+2567                      |

### Data Structure Operations Complexity

| Data Structure          | Access    | Search    | Insertion | Deletion  | Comments  |
| ----------------------- | :-------: | :-------: | :-------: | :-------: | :-------- |
| **Array**               | 1         | n         | n         | n         |           |
| **Stack**               | n         | n         | 1         | 1         |           |
| **Queue**               | n         | n         | 1         | 1         |           |
| **Linked List**         | n         | n         | 1         | n         |           |
| **Hash Table**          | -         | n         | n         | n         | In case of perfect hash function costs would be O(1) |
| **Binary Search Tree**  | n         | n         | n         | n         | In case of balanced tree costs would be O(log(n)) |
| **B-Tree**              | log(n)    | log(n)    | log(n)    | log(n)    |           |
| **Red-Black Tree**      | log(n)    | log(n)    | log(n)    | log(n)    |           |
| **AVL Tree**            | log(n)    | log(n)    | log(n)    | log(n)    |           |
| **Bloom Filter**        | -         | 1         | 1         | -         | False positives are possible while searching |

### Array Sorting Algorithms Complexity

| Name                  | Best            | Average             | Worst               | Memory    | Stable    | Comments  |
| --------------------- | :-------------: | :-----------------: | :-----------------: | :-------: | :-------: | :-------- |
| **Bubble sort**       | n               | n<sup>2</sup>       | n<sup>2</sup>       | 1         | Yes       |           |
| **Insertion sort**    | n               | n<sup>2</sup>       | n<sup>2</sup>       | 1         | Yes       |           |
| **Selection sort**    | n<sup>2</sup>   | n<sup>2</sup>       | n<sup>2</sup>       | 1         | No        |           |
| **Heap sort**         | n&nbsp;log(n)   | n&nbsp;log(n)       | n&nbsp;log(n)       | 1         | No        |           |
| **Merge sort**        | n&nbsp;log(n)   | n&nbsp;log(n)       | n&nbsp;log(n)       | n         | Yes       |           |
| **Quick sort**        | n&nbsp;log(n)   | n&nbsp;log(n)       | n<sup>2</sup>       | log(n)    | No        | Quicksort is usually done in-place with O(log(n)) stack space |
| **Shell sort**        | n&nbsp;log(n)   | depends on gap sequence   | n&nbsp;(log(n))<sup>2</sup>  | 1         | No         |           |
| **Counting sort**     | n + r           | n + r               | n + r               | n + r     | Yes       | r - biggest number in array |
| **Radix sort**        | n * k           | n * k               | n * k               | n + k     | Yes       | k - length of longest key |
