# Heap
>💡 On Notion → [Heap](https://www.notion.so/Heap-39734a077ce946ff81eec793f2379ff7)
## **Introduction**

- A heap is a specific tree based data structure in which all the nodes of tree are in a specific order. They are hierarchical data structure.
- The maximum number of children of a node in the heap depends on the type of heap. However in the more commonly used heap type, there are at most 2 children of a note and it's known as a Binary heap.
- In binary heap, if the heap is a complete binary tree with N nodes, then it has has smallest possible height which is logN .
- **There can be two types of heap:**
    - **Max Heap:**
        
        > In this type of heap, the value of parent node will always be greater than or equal to the value of child node across the tree and the node with highest value will be the root node of the tree.
        > 
    - **Min Heap:**
        
        > In this type of heap, the value of parent node will always be less than or equal to the value of child node across the tree and the node with lowest value will be the root node of tree.
        > 

### Representation of Heap

![Heap representation](https://github.com/tabassum-khan/Data-Structures-and-Algorithms/raw/master/assets/heap.png)
>💡 Here we are only going to cover Binary Heap
---
## **Binary Heap**

- A Binary Heap is a Binary Tree with following properties:
    1. **It’s a complete tree.** All levels are completely filled except possibly the last level and the last level has all keys as left as possible. This property of Binary Heap makes them suitable to be stored in an array.
    2. **A Binary Heap is either Min Heap or Max Heap**. 
        1. In a **Min Binary Heap**, the key at root must be minimum among all keys present in Binary Heap. The same property must be recursively true for all nodes in Binary Tree. 
        2. **Max Binary Heap** is similar to MinHeap except the root must be maximum among all keys present in Binary Heap. The same property must be recursively true for all nodes in Binary Tree. 
- A Binary Heap is typically represented as an array. The root element will be at `arr[0]`. The relationship between the elements of the heap can be represented as:
    
    > Note : The indexing starts from 1 and not 0 to make indexing easier. Lets say that an element is at index 'i', then its
    > 
    > 1. Left child : 2*i
    > 2. Right child : 2*i + 1
    > 3. Parent : i/2
    
- **Applications**
    - [Heap Sort](https://github.com/tabassum-khan/Data-Structures-and-Algorithms/tree/master/trees.heap_sort.md)
    - [Priority Queues](https://github.com/tabassum-khan/Data-Structures-and-Algorithms/blob/master/queues/priority_queues.md)

## **Design and Implementation**

If we are going to implement binary heap, we will either implement a max heap or a min heap. We will see both of those implementation.

- The binary Heap will be created with the help of an array and its capacity and size will be declared.
    ```java
    private[] int heap;
    private int capacity;
    private int size;
    ```

### Operations on Binary Heap

- **insert() →** Inserting a new key takes **O(Log n)** time. We add a new key at the end of the tree. Then we traverse up to fix if the binary heap property has been violated.
- **getMin() / getMax()** → It returns the root element of Min Heap / Max Heap. The Time Complexity of this operation is **O(1).**
- **extractMin() / extractMax()** → Removes the minimum / maximum element from MinHeap. The Time Complexity of this Operation is **O(Log n)** as this operation needs to maintain the heap property (by calling heapify()) after removing the root.
- A simple binary heap can be implemented as:
    
    ```java
    public class BinaryHeap {
        private int[] heap;
        private int size;
        private int capacity;

        // initialise heap
        public BinaryHeap(int capacity){
            this.size = 0;
            heap = new int[ capacity+1];
            this.capacity = capacity;
        }

        public boolean isEmpty(){
            return size == 0;
        }

        public boolean isFull(){
            return size == capacity;
        }
        
        public void swap(int index1, int index2){
            int temp = heap[index1];
            heap[index1] = heap[index2];
            heap[index2] = temp;
        }
        
        public buildHeap(int[] arr){..}
        public heapify(int[] arr, int index, int size){...}
        public void insert(int key){..}
        public getMin(){...}
        public int extractMin(int[] heap){...}
    }
    ```
---

### Min Heap Implementation
---
**1. Insertion → O(Logn)**

- If heap is full, i.e if heap array has exhausted its full capacity, then return.
- Else, insert the element to the next empty slot.
- Now, after insertion, we should check if min heap property is being maintained i.e. every parent element must be less than its children.
- Since the element is added to the bottom of the tree, we move upwards and check if the inserted element is less than its parent. If it is, then we swap the parent and the child. We keep doing this until the property is satisfied or we have reached the root.
    
    ```java
    public void insert(int element){
        if (isFull())
            return;

        heap[++size] = element;
        int current = size;

        while (heap[current] < heap[current/2]) {
            swap(current, current/2);
            current = current/2;
        }
    }
    ```
    

**2. Get the minimum element: getMin() → O(1)**

- In Min Heap, the minimum element will be present at the root. The root is at index ‘1’ of the heap array.
    
    ```java
    public int getMin(){
        return heap[1];
    }
    ```

**3. Extract the minimum element: extractMin() → O(Logn)**

- In Min Heap, the minimum element will be present at the root. The root is at index ‘1’ of the heap array.
- We need to return this element as well as remove it. To delete the element, copy the last element to the root element and decrease size.
- Since the last element has been copied to the first element, we must heapify it to maintain the min heap property. Now it will only heapify till the new size.
    
    ```java
    public int extractMin(){ 
        // Get the min element
        int minElement = heap[1]

        // Replace root with last element and decrease its size
        heap[1] =  heap[size--]; 

        // heapify the root node 
        min_heapify(heap, 1, size); 

        return minElement; 
    }
    ```
   

**4. minHeapify() → O(Logn)**

- The most important step in the implementation of heap. This method will heapify the heap to min heap or max heap as defined. It takes 3 paramters
    - **arr[]** → which array to heapify
    - **int index** → from which index should it begin to heapify
    - **int size** → it will heapify the heap till the end of the heap (`size`)
- Suppose we have any heap with some elements. For any node that we select, we check with its left child and right child and find the smallest of the three. Then we swap the smallest node with the selected node if the selected node itself is not the smallest.
- Now do this for every node and we will have a min heap.
    
    ```java
    void min_heapify (int[] arr, int index, int size){
        int left  = 2*index; // left child
        int right = 2*index+1; // right child
        int smallest;

        if(left <= size && arr[left] < arr[index] )
             smallest = left;
        else
            smallest = index;

        if(right <= size && arr[right] < arr[smallest] )
            smallest = right;

        if(smallest != index){
            swap (index, smallest]);
            min_heapify (arr, smallest, size);
        } 
    }
    ```
    >💡 For an element to be placed at its right position, it will check with its parent and sibling and then swap if it is the smallest of the three. At most, any element at level ‘l’ will make ‘l’ swaps where l = number of levels.
    >
    >Now, maximum of nodes, n,  at any level, $'l'$, in a binary tree can be given by: $n = 2^l$. Hence, the time complexity for any element at level $'l'$ to be placed at its right position is $O(Logn)$

**5. buildHeap() → to build a min/max heap of any given array → O(nLogn)**

- We have a heap to store N elements indexed from 1 to N. They are currently not following the property of min heap. So we can use `min_heapify()` function to make a min heap out of the array.
- Now we know that by using `min_heapify()`, we can adjust a node of the heap array to its correct position. In order for the whole array to satisfy the min heap properties, wehave to `min_heapify()` every node to place it in its correct position.
- If we start from `index=1` , then we start from the first element and adjust it and we do this till the last element including leaf nodes. But, if you observe carefully, you will find that as you adjust from top to bottom, the leaf node automatically adjust themselves. Another way to think is that the leaf nodes have no children to compare themselves with. Hence, we only need to check till the level above leaf nodes.
- A N element heap stored in an array will have leaves indexed by N/2+1, N/2+2 , N/2+3 …. upto N. Hence, we ony have to iterate `min_heapify()` from `index=1` to `index=N/2`.
    ![image](https://user-images.githubusercontent.com/22317530/186902610-c6ef626f-7338-4383-af23-a54efa4a722f.png)
    
    ```java
   void build_minheap(int[] arr){
        this.size = arr.length-1;
        
        for( int i=1 ; i <= size/2 ; i++)
            min_heapify (arr, i, size);
            
        this.heap = arr;
    }
    ```
   >💡 To heapify an element, it takes O(Logn) time. Thus, to heapify ‘n’ elements it will take O(nLogn) time.

---

### Max Heap Implementation

---

**1. Insertion → O(Logn)**

- If heap is full, i.e if heap array has exhausted its full capacity, then return.
- Else, insert the element to the next empty slot.
- Now, after insertion, we should check if max heap property is being maintained i.e. every parent element must be larger than its children.
- Since the element is added to the bottom of the tree, we move upwards and check if the inserted element is larger than its parent. If it is, then we swap the parent and the child. We keep doing this until the property is satisfied or we have reached the root.
    
    ```java
    public void insert(int element){
        if (isFull())
            return;
        
        heap[++size] = element;
        int current = size;
        
        while (heap[current] > heap[current/2]) {
            swap(current, current/2);
            current = current/2;
        }
    }
    ```
 

**2. Get the maximum element: getMax() → O(1)**

- In Max Heap, the maximum element will be present at the root. The root is at index ‘1’ of the heap array.
    
    ```java
    public int getMax(){
        return heap[1];
    }
    ```
  

**3. Extract the minimum element: extractMax() → O(Logn)**

- In Max Heap, the maximum element will be present at the root. The root is at index ‘1’ of the heap array.
- We need to return this element as well as remove it. To delete the element, copy the last element to the root element and decrease size.nce the last element has been copied to the first element, we must heapify it to maintain the max heap property. Now it will only heapify till the new size.
    
    ```java
    public int extractMax(){ 
        // Get the last element and decrease size
        int maxElement = heap[1];

        // Replace root with last element and decrease size 
        heap[1] = heap[size--];

        // heapify the root node 
        max_heapify(heap, 1, size); 

        return maxElement; 
    }
    ```

**4. maxHeapify() → O(Logn)**

- The most important step in the implementation of heap. This method will heapify the heap to min heap or max heap as defined. It takes 3 paramters:
    - **arr[]** → which heap to heapify
    - **int index** → from which index should it begin to heapify
    - **int size** → it will heapify the heap till the end of the heap (`size`)
- Suppose we have any heap with some elements. For any node that we select, we check with its left child and right child and find the largest of the three. Then we swap the largest node with the selected node if the selected node itself is not the largest.
- Now do this for every node and we will have a max heap.
    
    ```java
    void max_heapify(int arr[] , int index, int size){
        int left  = 2*index; // left child
        int right = 2*index+1; // right child
        int largest;

        if(left <= size && arr[left] > arr[index] )
             largest = left;
        else
            largest = index;

        if(right <= size && arr[right] > arr[largest] )
            largest = right;

        if(largest != index){
            swap (index, largest);
            max_heapify (arr, largest, size);
        } 
    }
    ```
  

**5. buildHeap() → to build a min/max heap of any given array → O(nLogn)**

- We have an array to store N elements indexed from 1 to N. They are currently not following the property of max heap. So we can use `max_heapify()` function to make a max heap out of the array.
- Now we know that by using `max_heapify()`, we can adjust a node of the heap array to its correct position. In order for the whole array to satisfy the max heap properties, we have to `max_heapify()` every node to place it in its correct position.
- If we start from `index=1` , then we start from the first element and adjust it and we do this till the last element including leaf nodes. But, if you observe carefully, you will find that as you adjust from top to bottom, the leaf node automatically adjust themselves. Another way to think is that the leaf nodes have no children to compare themselves with. Hence, we only need to check till the level above leaf nodes.
- A N element heap stored in an array will have leaves indexed by N/2+1, N/2+2 , N/2+3 …. upto N. Hence, we ony have to iterate `max_heapify()` from `index=1` to `index=N/2`.
    
    ```java
    void build_maxheap (int[] arr){
        this.size = arr.length-1;
        
        for(int i = size/2 ; i >= 1 ; i-- )
          max_heapify (heap, i, size) ;
          
        this.heap = arr;
    }
    ```

