# Computer Science

### Algorithms and Data structures
- Data structures
    - Vector
        - Allocates more memory (capacity) when the size surpasses the capacity. Normally allocates double the previous capacity. If the memory has to be allocated in another location, the vector data has to be copied (actually calls the copy constructor!) to the new location.
        - Because it continuously allocates memory on insertions, the performance on insertions can degrade.
        - Memory is contiguous -> More cache usage -> Storing objects instead of pointers can be better for cache usage
        - Optimization: Use `vector::reserve` to avoid allocations on insertion.
        - Optimization: Avoid calling copy constructor on insertion with `vector::push_back` which happens because the element is in the stack and needs to be copied to the memory allocated by the vector. An optimization is to use `vector::emplace_back` instead as it creates the element in the memory allocated by the vector, avoiding a copy. 
        - Optimization: Instead of using `erase`, use `swap` and `pop_back` (erase with last swap) whenever possible.
        - Complexity of `insert`/`erase` (particular index): O(M), where M is the number of elements moved (i.e., distance between `pos` and `end` of the container)
        - Complexity of `push_back`/`pop_back`: O(1)
        - Complexity of access: O(1)
        - Complexity of search: O(N)
    - List (case of doubly linked list)
        - Uses more memory than vectors
        - Less cache friendly since the memory is not necessarily contiguous
        - Easy to insert anywhere since all it does is change what the pointers point to
        - Random access is slower than a vector since it has to go through the pointers to access the desired index
        - Complexity of `insert`/`erase`: O(1)
        - Complexity of `push_back`/`push_front`/`pop_back`/`pop_front`: O(1)
        - Complexity of access: O(N)
        - Complexity of search: O(N)
    - Set
        - Sorted container of unique objects
        - Complexity of `insert`: O(logN), can be O(1) if the position is right after/before the hint
        - Complexity of `erase`: O(1), position must be given
        - Complexity of search: O(logN)
        - Implemented as a [binary search tree](https://www.geeksforgeeks.org/binary-search-tree-set-1-search-and-insertion/), usually a Red-Black Tree  
    - Map
        - Sorted container of key-value pairs
        - Complexity of `insert`: O(logN), can be O(1) if the position is right after/before the hint
        - Complexity of `erase`: O(1), position must be given
        - Complexity of search: O(logN)
        - Complexity of access: O(logN)
        - Implemented as a [binary search tree](https://www.geeksforgeeks.org/binary-search-tree-set-1-search-and-insertion/), usually a Red-Black Tree
    - Hash
        - Implementation requires a hash function which is applied to the element to be inserted. The container can be an array.
        - Collisions can be handled in different ways:
            - Probing - Find next available index (subsequent searches start at the hash index and continues through the same path as probing, if the element in the index does not match)
            - Linked lists - Each entry is a linked list to each the element is added (subsequent searches loop through the list)
        - Lookup is O(1) if there are no collisions, then it depends on the collision-handling process (worst case of O(size))
        - Insertion / Removal: Average O(1); Worst-case O(size)
    - Deque
        - Double-ended queue
        - Memory is not contiguous
        - Implemented as multiple arrays of equal and fixed size linked together
        - On average, insertions are faster than vector because it doesn't perform full container copies when more space has to be allocated. At most, it creates another array to store the new element
        - Complexity of `insert`/`erase`: O(M), where M is the number of elements moved (i.e., minimum distance between `pos` and either `end` or `begin` of the container)
        - Complexity of `push_back`/`push_front`/`pop_back`/`pop_front`: O(1)
        - Complexity of access: O(1), slower than vector because it performs two-pointer dereference (one for getting the correct array and another for getting the element) instead of one as in vector
        - Complexity of search: O(N)
    - Graphs
        - Strongly connected: if every vertex is reachable from every other vertex
        - Biconnection: if any one vertex were to be removed, the graph will remain connected
    - [Big-O Cheat Sheet](https://www.bigocheatsheet.com/)

- Algorithms
    - Graph algorithms
        - Depth-first traversal
        ```js
        function dfs(G, v) {
            let S be a stack
            S.push(v)
            while S is not empty do
                v = S.pop()
                if v is not labelled as discovered then
                    label v as discovered
                    for all edges from v to w in G.adjacentEdges(v) do 
                        S.push(w)
        }
        ```
        - Bread-first traversal
        ```js
        function bfs(G, v) {
            let Q be a queue
            label v as discovered
            Q.enqueue(v)
            while Q is not empty do
                v = Q.dequeue()
                for all edges from v to w in G.adjacentEdges(v) do
                    if w is not labelled as discovered then
                        label w as discovered
                        Q.enqueue(w)
        }
        ```
        - Maximum flow (e.g., Ford-Fulkerson): finding a feasible flow through a graph that obtains the maximum possible flow rate
        - Minimum spanning trees (e.g., Prism): subset of the edges of a graph that connects all the vertices together, without any cycles and with the minimum possible total edge weight
        - Shortest path (e.g., Dijkstra): finding a path between two vertices in a graph such that the sum of the weights of its constituent edges is minimized
        - Euler circuit: path in a graph that visits every edge exactly once (allowing for revisiting vertices); when impossible, find the smallest number of graph edges to duplicate (or the subset of edges with the minimum possible total weight) so that the resulting multigraph has an Eulerian circuit

    - Sorting
        - [Bubble Sort](https://www.youtube.com/watch?v=nmhjrI-aW5o)  
        Swap J with J+1 if the former is bigger. Repeat for all entries with each pass reducing the limit of J to N-I-1, where I goes from 0 to N-1. Bigger values bubble to the end.
        - [Quick Sort](https://www.youtube.com/watch?v=PgBzjlCcFvc)  
        Choose a pivot (last element). Loop J and if the value is smaller than the pivot, I++ and swap A[I] with A[J] until the pivot. Swap A[I+1] with the pivot. At this point, the pivot is placed in its final position, everything on the left is smaller and everything on the right is bigger. Repeat the process for each sub-array.
        - [Merge sort](https://www.youtube.com/watch?v=JSceec-wEyw)  
        Split into sub-arrays until each has 2 elements. Merge each with the next on the tree (if smaller write into position and move on, else stay in the same spot). Repeat for each level of the tree.
        - [Counting Sort](https://www.youtube.com/watch?v=7zuGmKfUt7s)  
        Count each object, accumulate counts, place in that position while decrementing.
        - [Radix Sort](https://www.youtube.com/watch?v=nu4gDuFabIM) (only numbers)

    - Strings
        - Exact / approximated matching
        - Compression
    
    - Problem-solving methods
        - Dynamic programming  
        Avoid repeating sub-problems (e.g., backpack problem, fibonacci)
        - Greedy algorithms
        - Backtracking algorithms  
        Trial and error problems, exploring and looking for the solution (e.g., coin problem)
        - Divide and conquer
    - Recursion vs Iteration
        - Recursion requires more stack memory
        - Recursion can be easier to implement and to use without additional data structures

### Artificial Intelligence
- Graphs
    - Weak methods
        - Uniform Cost  
        Explore nodes bread-first, but with a priority queue where `cost = currentCost + transitionCost`.
        - Iterative Deepening  
        Explore nodes depth-first, but only up to a maximum depth which is increased on each iteration.  
    - Informed methods
        - Hill Climbing  
        Greedy algorithm (explore the best adjacent node, until there aren't any nodes better). Not optimal (get's stuck in local maxima)
        - Simulated Annealing  
        Random choice of a state. If the state is better, explore it. Otherwise, there is still a probability to choose it (e^(-|deltaE / Temperature|)). Lower the temperature.
        - Evolutionary algorithms
        - A*  
        Mix between Uniform Cost and Greedy. The cost function is the sum between the cost to the successor C(S,S') = c(S) + c(S') and the heuristic of the successor H(S,S') = h(S').  
    - Adversarial methods  
        - Minimax  
        If on a maximizer level, apply minimax to its successors and the value for the node is the maximum value of its successors. If on a minimizer level, apply minimax to its successors and the value for the node is the minimum value of its successors.
            - Alpha Beta pruning  
            Alpha is the best value that the maximizer currently can guarantee at that level or above. Initially set to -Inf.  
            Beta is the best value that the minimizer currently can guarantee at that level or above. Initially set to +Inf.  
            Prune if alpha >= beta. 

- Game theory  
Game theory is the mathematical study of strategic decision-making among independent self-interested agents.  
Games can be cooperative/non-cooperative, symmetric/asymmetric, zero-sum/win-win, simultaneous/sequential, perfect/imperfect information, ...
    - Utility function: mapping from world states to real numbers
    - Strategies
        - Pure strategy: determines the exact action to play
        - Mixed strategy: assignement of a probability to each pure strategy
    
    - Payoff matrix:  
    <img width="250" height="250" src="https://i.imgur.com/ibUfVp0.png">
    
    - Dominant strategy: *Si* is dominant for player *i* if, no matter what strategy *Sj* agent *j* chooses, *i* will do at least as well playing *Si* as it would doing anything else. *Si* is dominant if it is *i*’s best response to all of agent *j*’s strategies.  
    Is always a Nash equilibrium.  
    <img width="250" height="250" src="https://i.imgur.com/CWrukVu.png">
    

    
    - Nash equilibrium:  
        - Two strategies *Si* and *Sj* are in (pure-strategy) Nash equilibirium if:  
            - assuming that agent *i* plays *Si*, agent *j* can do no better than play *Sj*, and
            - assuming that agent *j* plays *Sj*, agent *i* can do no better than play *Si*
        - Strategies *Si* and *Sj* are the best response to each other
        - Neither agent has any incentive to deviate from a Nash equilibrium  
    <img width="250" height="250" src="https://i.imgur.com/xFEvrX5.png">

    - Pareto efficiency:
        - There is no other outcome that improves one player’s utility without making someone worse off  
    <img width="250" height="250" src="https://i.imgur.com/6A2N0li.png">
    

- Behaviour Trees  
Data structure where you set the rules of how certain behaviours can occur and order in which they can execute. Normally an acyclic directed graph.  
    - Nodes:  
        - Root node
        - Composite nodes: control how the tree is processed
            - Selector: decides which child to execute based on some logic
                - Selects the first node that succeeds
                - Succeeds if one of its child nodes succeeds
                - Fails if all its child nodes fail
            - Sequence: execute its child nodes in sequence  
                - Fails (aborts) when a node fails
                - Succeeds if all its nodes succeed
        - Leaf nodes: AI behaviours/tasks/actions
        - Decorator nodes: conditional node
            - Can be notified of changes and abort nodes
        - Services: code that runs periodically
            - If any node below it is active, the service should update periodically
            - The interval between updates should have a deviation to avoid stacking a lot of updates on the same frame and causing performance issues. Instead, using deviation allows for a better distribution of updates across time.
    - Success and failure propagates up towards the root
    - Expensive to traverse on each tick
        - Cache a reference to the active node and that node will process the tick, when that node decides to end, the tree is re-evaluated
        - Events can trigger a re-evaluation of the node/tree
    - Blackboards: stores data regarding the current state of the world and the AI (e.g., player position, nearest vehicle, nearest cover); can be shared across multiple behaviour trees (memory efficient)
    - Finite State Machines
        - Good for simple logic
        - Less scalable -> having to think of all transitions from a state
        - Harder to debug
        - Less designer friendly
        - Less reusable
        - Can be core intensive
        - Good alternative -> Hierarchical Finite State Machines


### Parallel Computing
- Process (active entity -> code, data, program counter, registers, stack) vs Program (passive entity -> file content).
- Process vs thread:  
A process possesses the resources (files, memory) and a sequence of execution (thread). A thread is a lightweight process which shares resources like memory, files and I/O devices. Each thread has its own program counter and stack pointer.
- UNIX:
    - Processes
        - `fork()` creates a new process (child process) with a copy of the parent memory (in a new address space) and shares its files (does not load the program again). Both execute concurrently. Returns the PID of the child process in the parent process and 0 is returned in the child process.
        - `exec()` replaces the current process with a new process.
        - `getpid()` and `getppid()` return PID and PPID
        - `wait()` and `waitpid()` waits for all child process or for process with matching PID.
    - Threads
        - `pthread_create()` creates a thread which executes a routine.
        - `pthread_join()` suspends the calling thread until the argument thread terminates.
        - `pthread_cancel()` and `pthread_exit()` terminates a thread. `exit()` terminates all threads and `return` terminates the current thread.
        - `pthread_self()` returns the thread ID
    - Mutexes  
    Protect a critical section.  
        - Define a variable of type `pthread_mutex_t`, `pthread_mutex_init()` to create and `pthread_mutex_destroy` to destroy 
        - `pthread_mutex_lock()` to lock and `pthread_mutex_unlock()` to unlock the mutex
    Condition variables allow blocking of a thread until a condition is met:
        - Define a variable of type `pthread_cond_t`, `pthread_cond_init()` to create and `pthread_cond_destroy` to destroy
        - `pthread_cond_wait` to wait for a thread to signal with `pthread_cond_signal`
    - Signals  
    Notifications via software from keyboard (ctrl+c), hardware (invalid memory reference), kill command/function, software.  
    Responses include to ignore, handle (install signal handler), default (terminate/suspend/continue).  
        - Set response with `sigaction()`
        - Send signal with `kill()` (any process) or `raise()` (to the calling process)
- Shared memory vs Distributed memory


### Object-Oriented Programming
- SOLID
    - Single responsibility principle  
    A class should have one, and only one, reason to change  
    - Open-closed principle  
    Software entities like classes, modules and functions should be open for extension but closed for modification.  
    - Liskov's substitution principle  
    Derived types must be completely substitutable for their base types.
    - Interface segregation principle  
    Clients should not be forced to depend upon interfaces that they don't use.
    - Dependency inversion principle  
    Depend on abstractions, not on concretions.
- Principles
    - Encapsulation  
    Hiding of data implementation by restricting access to members variables, with each object keeping its state private.
    - Abstraction  
    Each object should only expose a high-level mechanism for using it. This mechanism should hide internal implementation details. It should only reveal operations relevant for the other objects.
    - Inheritance  
    Describe a new (derived) class based on an existing (base) class expressing "is-a" and/or "has-a" relationships.
    - Polymorphism  
    Static polymorphism is achieved using method overloading and dynamic polymorphism using method overriding.


### C/C++
- Templates  
A form of static polymorphism. The compiler creates the code for each type used. Avoids code duplication in the codebase.

- Exception handling  
Once an exception is thrown, the program looks for the next closest `catch` statement that can handle the exception. Once found, stack unwinding begins, destroying in reverse order all stack-allocated objects constructed from the beginning of the `try` block associated with the current `catch` handler.

- Inheritance Access  
    ![InheritanceAccess](https://media.geeksforgeeks.org/wp-content/cdn-uploads/table-class.png)

- Operator overload
```cpp
Box operator+(const Box& b) {
    Box box;
    box.length = this->length + b.length;
    box.breadth = this->breadth + b.breadth;
    box.height = this->height + b.height;
    return box;
}
```

- Lambdas  
Anonymous functions.  
Syntax: `[ captures ] ( params ) -> ret { body }`  
    - `captures` can be `&` (pass all variables by reference), `=` (pass variables all by copy), a list of variables or `this`.  
    - `params` is a parameter list  
    - `ret` is the return type  


- Keywords
    - Volatile  
    Qualifier applied to a variable to tell the compiler that the value of the variable may change at any time without any action from the code the compiler knows about, thus disabling some optimizations that could break the program. Use cases include global variables modified by an interrupt service routine or in a multi-threading, and memory-mapped peripheral registers.
    - Mutable  
    Used to denote that a member of a constant object may change its value.
    - Inline  
    If possible, the compiler replaces a call to the function with the actual code of the inline function, reducing overhead.
    - Explicit  
    Prefixing the explicit keyword to the constructor prevents the compiler from using that constructor for implicit conversions.
    - Static  
        - Static variable in local scope  
        Static variables when used in a local scope (e.g., inside a function) are initialized only once, and then they hold their value throughout execution (e.g., function calls). They have program lifetime.
        - Static member variable in class  
        Only one instance per class that is shared by all the objects. Initialized outside of class.
        - Static member function in class  
        Can only access static members.
        - Static global variable  
        Has file scope (can only be accessed in the file where it is created).
    - Friend  
    Can be applied to classes or member functions. Enables the function or class to access private members of the other class.
    - Auto: specifies that the type of the variable that is being declared will be automatically deduced from its initializer
    - Extern: Declares the *existence* of a variable without defining it. If used in a header, a source which includes it can use the variable. The variable still needs to be defined somewhere.

- Struct Packing / Padding
    - Each CPU Cycle can access only one word (4 bytes in 32-bit architectures). So if an `int` (4 bytes) is distributed in 2 words due to bad alignment before the int, then it will take 2 CPU cycles to read its value.
    - Padding is used as a solution to increase access performance
    - Disable padding with `#pragma pack(1)` which packs on the first byte.

- Smart pointer
    - Automate the process of deleting the allocated memory. 
    - Prefered method to create a smart pointer is to call the `std::make_*` function.
    - Unique pointer
        - It's a scoped pointer -> when it goes out of scope it's deleted.
        - Can't copy unique pointers
        - Only one reference to the object
        - Implemented as a stack object that once out of scope calls delete on the referenced object in the heap.
    - Shared pointer
        - Works by reference counting
        - Each assignment/copy increments the reference counter and whenever one goes out of scope it's decremented
        - When the reference counter reaches 0, the pointer is deleted
    - Weak pointer
        - Used with shared pointers
        - Assigning a shared pointer to a weak pointer does not increase/decrease the reference counter
        - Possible to query if the pointer is valid, because they might point to invalid memory if the shared pointer has been deleted

- Move semantics        
    - lvalues vs rvalues
        - `int i = 10`: `i` has a location (storage) while `10` doesn't.
        - `i` is a `lvalue` while `10` is a `rvalue`.
        - rvalues don't need to be a literal, can also be a result of a function that returns a temporary value (has no storage).
        - Exception being with const: a const lvalue reference can hold an rvalue (compiler probably creates a temporary variable)
        - `std::string fullName = firstName + lastName`: The sum is an rvalue while `fullName` is a lvalue
        - To accept only rvalues use two ampersands (&&)

    - `std::forward()` perfectly forwards with the same data type and value category 

    - Avoid unnecessary copies (especially when copying requires heap memory allocation)
    ```cpp
    String(const char* string) {
        m_Size = strlen(string);
        m_Data = new char[m_Size];
        memcpy(m_Data, string, m_Size);
    }

    // Used for temporary values
    String(String&& other) noexcept { // noexcept needed so the object is not left in unknown state
        // Move
        m_Size = other.m_Size;
        m_Data = other.m_Data;

        // Handle temporary string
        other.m_Size = 0;
        other.m_Data = nullptr;
    }

    ~String() {
        delete m_Data; // In temporary strings, it will delete nullptr
    }

    // Needs to support temporary values, else it will call the copy constructor
    Entity(String&& name) :
        m_Name(std::move(name)) {
            // std::move is needed to explicitly cast name to String&&
    }

    int main() {
        Entity entity = Entity(String("Hello")); // The argument is a temporary value
    }
    ```

- Binding
    - Static binding: In assembly, it's just calling the instruction at a fixed address
    - Dynamic binding: The compiler will generate a variable to hold the address of the instruction that will be called

- Virtual pointers and virtual tables  
```cpp
class A {
public:
    virtual void vf1();
    virtual void vf2();
    void f1();
    void f2();
private:
    int x;
    int y;
}

class B : public A {
public:
    virtual void vf1();
    void f1();
    void f3();
private:
    int z;
}
```  

Each class will have one virtual pointer that points to a virtual table and each entry in the vtable will point to virtual member function. `A` will have two entries (`A::vf1()` and `A::vf2()`) and `B` also has two entries (`B::vf1()` and `A::vf2()`).  
Calling a virtual function (dynamic binding / polymorphism) will result in `(*(p->vptr)[n])(p)` where `p` is a pointer to the object, `vptr` its virtual pointer and `n` the entry in the virtual table. The function is then called with parameter `p` which is the way of giving the function the `this` pointer.  
Functions (either virtual or not) are not present in the object. They exist in the code segment, unlike its data members.

- Mutex vs Atomic  
Atomic operations don't require a thread to block -> No deadlocks. Atomic may be faster.

- Casting
    - Static casts  
    It's a compile-time directive that creates a new variable resulting from the conversion to the new type.

    - Reinterpret casts  
    It is a compile-time directive which instructs the compiler to treat the expression as if it had the new type. In other words, that piece of memory is now treated as the new type.

    - Dynamic casts  
    Used for conversions between polymorphic types in run-time, i.e., to cast from a class to a derived class (the other way around can be done implicitly). Dynamic casts can be seen as a validation to the cast, using Runtime Type Information (RTTI) to know if the type matches. Dynamic casts can use the `typeid` operator which returns a `type_info` struct.  

    - Const cast  
    Removes the constness from a variable  

- Pre-compiled headers
    - Place all necessary headers that won't be changed constantly (for example std or libraries) in a header (`pch.h`).
    - Speeds up (subsequent) compilation times
    - g++ usage:
        - Create the `pch.h`
        - Compile the pch with `g++ pch.h`
        - The file `pch.h.gch` is created

- Evaluation order
    - Undefined behaviour for argument list  
    ```cpp
    int x = function( a(), b(), c() );
    ```
    It's undefined behaviour to assume any order of evaluation of `a()`, `b()` and `c()` as any permutation is valid.
    - Logic operators
        - operator `&&` evaluates left operand first and if the value is logically `false` then it avoids evaluating the right operand.
        - operator `||` evaluates left operand first and if the value is logically `true` then it avoids evaluating the right operand. 

- Memory  
![Memory](https://study.com/cimages/multimages/16/1724cf83-a8ad-4ad5-aeca-0311114a819c_memory_alloc_cpp.png)  
Stack size if fixed. Process crashes on stack overflow. Entries in the stack are added and removed automatically when entering or exiting their scope. With a full heap, allocators simply return null.  
Cache memory is usually implemented with SRAM (static random-access memory) while the main memory (Stack and Heap) uses DRAM (dynamic random-access memory)
    - Stack vs Heap  
    Both stored in RAM memory. The difference is in how the memory is allocated. Allocating memory in the stack simply increments the *stack pointer* with the respective number of bytes, making it extremely fast. Same logic for deallocating - the pointer is decremented (automatic at the end of its scope). Each process maintains a *free list* that keeps track of which blocks of heap memory are free/taken. To allocate memory on the heap, the request goes through the free list trying to find a free block of memory that can hold the number of required bytes, returning the address and recording information (the fact that it's occupied and by how many bytes). Therefore, memory management on the heap is considerably slower due to the increased overhead.  
    Allocation on the stack should be preferred, except when: (1) the lifetime of the object must be extended; (2) the amount of memory is too large for the stack. As stated, the most impactful aspect between stack and heap is the memory management (allocation and deallocation). However, the stack can also possibly provide slightly better cache usage than the heap, but that is usually negligible. 


### Game Development
- Transformation order: M = T * R * S, first scale, then rotate and finally translate. If you do not do it in that order, then a non-uniform scaling will be affected by the previous rotation, making your object look skewed. And the rotation will be affected by the translation, making the final position of your object very different from what the value of the translation would make you expect.

- Game data structures: Bounding Volume Hierarchies vs. Spatial Partitioning Hierarchies
    - Bounding Volume Hierarchies (BVH)  
    Each object has a bounding volume (AABB for example). The tree is a hierarchy of bounding boxes, where the bounding boxes of a node's children must fit inside the node's bounding box.
    - Spatial Partitioning Hierarchies (Quadtree/Octree/KD-tree/BSP)  
    Quadtrees/Octrees uniformly subdivide space as long as the number of objects inside a division is above a certain threshold.  
    KD-trees don't have to subdivide space regularly, but the splitting plane is still axis-aligned.  
    BSPs allow for irregular subdivisions of space with hyperplanes of arbitrary orientation.
    - Static scenes: Spatial Partitioning
    - Dynamic scenes: Bounding Volumes

- Coordinate systems  
![Coordinate systems](https://learnopengl.com/img/getting-started/coordinate_systems.png)

- Entity Component System (ECS)  
    - Having a solution with an array of entities where each has an array of components is not a perfect solution. It causes memory indirection and segmentation and thus more cache misses while also hindering multithreading.
    - Conceptually, all the engine needs are transforms, meshes, scripts, audio sources, physics bodies, etc. The data-oriented solution is to have an array of components per type of component.
    - This allows the engine to go through the arrays of component types, instead of going through the entities and its components.
    - This provides easier multithreading and better cache usage.
    - The entity still exists to associate components between themselves, so querying other components is still possible, but it could just be an ID.

    
### Common questions
1. Always check the data types for underflow/overflow
2. Difference between Structs and Classes  
They support the exact same features. The difference is the default accessibility (public in Structs and private in Classes, for inheritance and members). Convention dictates to use Structs for data objects and Classes for objects with methods.
3. Virtual Inheritance  
Ensure only one copy of a base class's member variables is inherited by grandchild derived classes.
4. Dreaded Diamond Problem (Multiple Inheritance)  
The ambiguity of multiple inheritance. Solutions include to override a method or call specifically by using Der1::method().
```
      Base
      /  \
     /    \
    /      \
  Der1     Der2
    \      /
     \    /
      \  /
      Join
```
5. Pure virtual functions make the class abstract (can't be instantiated).
6. Pass by value (copy constructor) vs reference
7. Reflection  
Reflection is a language's ability to inspect and dynamically call classes, methods, attributes, etc. at runtime. Not possible in C++.
