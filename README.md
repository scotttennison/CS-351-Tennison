# CS-351-Tennison
Computer Architecture Class
* William (Scott) Tennison
* Project 1
Which program is fastest? Is it always the fastest?
Alloca is the fastest. It isn't always the fastest, when node data size increases alloca is the slowest.
Which program is slowest? Is it always the slowest?
List is the slowest.  No, it is a little faster than alloca at bigger node data sizes.
Was there a trend in program execution time based on the size of data in each Node? If so, what, and why?
Yes. With the more data in the nodes, the longer it took to execute. With more data,more memory had to be used.
Was there a trend in program execution time based on the length of the block chain?
Yes. With longer block chains, the longer the execution time. 
Consider heap breaks, what's noticeable? Does increasing the stack size affect the heap? Speculate on any similarities and differences in programs?
One noticeable thing is that alloca stays at 69 heap requests no matter the length of the list, while the other three programs grow greatly.
Considering either the malloc.cpp or alloca.cpp versions of the program, generate a diagram showing two Nodes. Include in the diagram
the relationship of the head, tail, and Node next pointers.
show the size (in bytes) and structure of a Node that allocated six bytes of data
include the bytes pointer, and indicate using an arrow which byte in the allocated memory it points to.
# Node Structure Diagram — malloc.cpp / alloca.cpp

```mermaid
flowchart LR
    head([head]) --> Node1
    tail([tail]) --> Node2

    subgraph Node1["Node 1"]
        direction TB
        N1_next["next pointer — 8 bytes"]
        N1_bytes["bytes* pointer — 8 bytes"]
        N1_B0["B0"]
        N1_B1["B1"]
        N1_B2["B2"]
        N1_B3["B3"]
        N1_B4["B4"]
        N1_B5["B5"]
        N1_bytes --> N1_B0
        N1_B0 --- N1_B1 --- N1_B2 --- N1_B3 --- N1_B4 --- N1_B5
    end

    subgraph Node2["Node 2"]
        direction TB
        N2_next["next pointer — 8 bytes (nullptr)"]
        N2_bytes["bytes* pointer — 8 bytes"]
        N2_B0["B0"]
        N2_B1["B1"]
        N2_B2["B2"]
        N2_B3["B3"]
        N2_B4["B4"]
        N2_B5["B5"]
        N2_bytes --> N2_B0
        N2_B0 --- N2_B1 --- N2_B2 --- N2_B3 --- N2_B4 --- N2_B5
    end

    N1_next -- "next" --> Node2

    subgraph mem["Memory Source"]
        malloc["malloc.cpp → 22 bytes from HEAP"]
        alloca["alloca.cpp → 22 bytes from STACK"]
    end
```

> **Node size:** 8 (next) + 8 (bytes\*) + 6 (data) = **22 bytes total**
  
There's an overhead to allocating memory, initializing it, and eventually processing (in our case, hashing it). For each program, were any of these tasks the same? Which one(s) were different?
Each program went through the lists the same,since they all had the same hash value. 
The difference was how each node was allocated and constructed. Alloca used the stack while the other programs used the heap.
As the size of data in a Node increases, does the significance of allocating the node increase or decrease?
As the data in a node increases,the significance of allocating the node decreases. With more data the hashing and initializing times become bigger than the allocation times.
