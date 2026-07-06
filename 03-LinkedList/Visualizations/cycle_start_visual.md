# Find Cycle Start Node - Step-by-Step Visualization

After detecting a cycle with Fast/Slow pointers, how do we find exactly **where** the cycle starts? This visualization explains the second phase of Floyd's Algorithm.

````carousel
## Step 1: Detect Cycle Meeting Point
First, we use Fast-Slow pointers to detect a cycle.
`fast` (2 steps) and `slow` (1 step) meet at Node `5` inside the cycle.

```mermaid
graph LR
    subgraph Pointers
    slow[slow: 5]
    fast[fast: 5]
    end

    1((1)) --> 2((2))
    2((2)) --> 3((3))
    3((3)) --> 4((4))
    4((4)) --> 5((5))
    5((5)) --> 6((6))
    6((6)) -.->|Cycle| 3
    
    style 5 fill:#f9f,stroke:#333,stroke-width:2px
```
<!-- slide -->
## Step 2: Reset one pointer to Head
We move `slow` back to the `head` (Node 1), while `fast` stays exactly at the meeting point (Node 5).

```mermaid
graph LR
    subgraph Pointers
    slow[slow: 1]
    fast[fast: 5]
    end

    1((1)) --> 2((2))
    2((2)) --> 3((3))
    3((3)) --> 4((4))
    4((4)) --> 5((5))
    5((5)) --> 6((6))
    6((6)) -.->|Cycle| 3
    
    style 1 fill:#f9f,stroke:#333,stroke-width:2px
    style 5 fill:#bbf,stroke:#333,stroke-width:2px
```
<!-- slide -->
## Step 3: Move both 1 step at a time
Both pointers now move **1 step at a time** (no more fast pointer).
- `slow` moves to 2
- `fast` moves to 6

```mermaid
graph LR
    subgraph Pointers
    slow[slow: 2]
    fast[fast: 6]
    end

    1((1)) --> 2((2))
    2((2)) --> 3((3))
    3((3)) --> 4((4))
    4((4)) --> 5((5))
    5((5)) --> 6((6))
    6((6)) -.->|Cycle| 3
    
    style 2 fill:#f9f,stroke:#333,stroke-width:2px
    style 6 fill:#bbf,stroke:#333,stroke-width:2px
```
<!-- slide -->
## Step 4: Both meet at Cycle Start!
- `slow` moves to 3
- `fast` moves from 6 to 3 (following the cycle)

They meet at Node **3**, which is the exact start of the cycle! We return this node.

```mermaid
graph LR
    subgraph Result
    result[Cycle Start Node: 3]
    end

    1((1)) --> 2((2))
    2((2)) --> 3((3))
    3((3)) --> 4((4))
    4((4)) --> 5((5))
    5((5)) --> 6((6))
    6((6)) -.->|Cycle| 3
    
    style 3 fill:#bfb,stroke:#333,stroke-width:2px
```
````
