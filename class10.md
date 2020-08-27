
# Stacks and Queues

## Stack

A stack is a linear data structure that stores items in a Last-In/First-Out (LIFO) or First-In/Last-Out (FILO) manner. In stack, a new element is added at one end and an element is removed from that end only. The insert and delete operations are often called push and pop.

![img](https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcToYm_ee6l4bYybKPwtL_13_ABsV8tNVZHEmQ&usqp=CAU)

### The functions associated with stack are:

* **empty()** – Returns whether the stack is empty – Time Complexity : O(1)
* **size()** – Returns the size of the stack – Time Complexity : O(1)
* **top()**– Returns a reference to the top most element of the stack – Time Complexity : O(1)
* **push(g)** – Adds the element ‘g’ at the top of the stack – Time Complexity : O(1)
* **pop()**– Deletes the top most element of the stack – Time Complexity : O(1)
* **Peek()** - When you peek you will view the value of the top Node in the stack.
* **IsEmpty** - returns true when stack is empty otherwise returns false.


## Queues 

![img](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-10/resources/images/Queue.PNG)

A queue is a collection of objects that supports fast first-in, first-out (FIFO) semantics for inserts and deletes. The insert and delete operations sometimes called enqueue and dequeue. Unlike lists or arrays, queues typically don’t allow for random access to the objects they contain.

Queues are similar to stacks and the difference between them is in removing items:

With a queue you remove the item least recently added (first-in, first-out or FIFO); and with a stack you remove the item most recently added (last-in, first-out or LIFO).

Performance-wise, a proper queue implementation is expected to take O(1) time for insert and delete operations. These are the two main operations performed on a queue and they should be fast in a correct implementation.

Queues have a wide range of applications in algorithms and to solve scheduling, as well as parallel programming problems.

There are various functions available in this module:

* **Enqueue** - Nodes or items that are added to the queue.
* **Dequeue** - Nodes or items that are removed from the queue. If called when the queue is empty an exception will be raised.
* **Front** - This is the front/first Node of the queue.
* **Rear** - This is the rear/last Node of the queue.
* **Peek** - When you peek you will view the value of the front Node in the queue. If called when the queue is empty an exception will be raised.
* **IsEmpty** - returns true when queue is empty otherwise returns false.


### Enqueue Operation

Queues maintain two data pointers, front and rear. Therefore, its operations are comparatively difficult to implement than that of stacks.

The following steps should be taken to enqueue (insert) data into a queue −

*Step 1* − Check if the queue is full.

*Step 2* − If the queue is full, produce overflow error and exit.

*Step 3* − If the queue is not full, increment rear pointer to point the next empty space.

*Step 4* − Add data element to the queue location, where the rear is pointing.

![img](https://www.tutorialspoint.com/data_structures_algorithms/images/queue_enqueue_diagram.jpg)

#### Code

Here is the pseudocode for the enqueue method:

    ALGORITHM enqueue(value)
    // INPUT <-- value to add to queue (will be wrapped in Node internally)
    // OUTPUT <-- none
    node = new Node(value)
    rear.next <-- node
    rear <-- node

### Dequeue Operation

Accessing data from the queue is a process of two tasks − access the data where front is pointing and remove the data after access. The following steps are taken to perform dequeue operation −

**Step 1** − Check if the queue is empty.

**Step 2** − If the queue is empty, produce underflow error and exit.

**Step 3** − If the queue is not empty, access the data where front is pointing.

**Step 4** − Increment front pointer to point to the next available data element.

![img](https://www.tutorialspoint.com/data_structures_algorithms/images/queue_dequeue_diagram.jpg)

#### Code

Here is the pseudocode for the dequeue method:

    ALGORITHM dequeue()
    // INPUT <-- none
    // OUTPUT <-- value of the removed Node
    // EXCEPTION if queue is empty

    Node temp <-- front
    front <-- front.next
    temp.next <-- null

    return temp.value

### Peek O(1)

When conducting a peek, you will only be inspecting the front Node of the queue.

Typically, you want to check isEmpty before conducting a peek. This will ensure that an exception is not raised. Alternately, you can wrap the call in a try/catch block.

#### Code

Here is the pseudocode for a peek

    ALGORITHM peek()
    // INPUT <-- none
    // OUTPUT <-- value of the front Node in Queue
    // EXCEPTION if Queue is empty

    return front.value