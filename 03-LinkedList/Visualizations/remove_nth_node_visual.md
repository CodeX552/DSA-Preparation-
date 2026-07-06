# Remove Nth Node From End - Step-by-Step Visualization

This carousel visualizes how to remove the Nth node from the end in a single pass using Fast-Slow pointers.

````carousel
## Initial State
Target: Remove **2nd** node from the end (Node 4).
We use a `dummy` node (0) to handle edge cases (like removing the head).
`fast` and `slow` both start at `dummy`.

```mermaid
graph LR
    subgraph Pointers
    slow[slow: 0]
    fast[fast: 0]
    end

    0((0 Dummy)) --> 1((1))
    1((1)) --> 2((2))
    2((2)) --> 3((3))
    3((3)) --> 4((4))
    4((4)) --> 5((5))
    5((5)) --> N((null))
    
    style 0 fill:#f9f,stroke:#333,stroke-width:2px
```
<!-- slide -->
## Step 1: Move fast N+1 steps ahead
N=2. We move `fast` 2+1 = **3** steps ahead (to Node 2).
This creates a gap of exactly N nodes between `slow` and `fast`.

```mermaid
graph LR
    subgraph Pointers
    slow[slow: 0]
    fast[fast: 2]
    end

    0((0 Dummy)) --> 1((1))
    1((1)) --> 2((2))
    2((2)) --> 3((3))
    3((3)) --> 4((4))
    4((4)) --> 5((5))
    5((5)) --> N((null))
    
    style 0 fill:#f9f,stroke:#333,stroke-width:2px
    style 2 fill:#bbf,stroke:#333,stroke-width:2px
```
<!-- slide -->
## Step 2: Move both until fast is null
We move both pointers 1 step at a time simultaneously.
When `fast` reaches `null`, `slow` will be exactly on the node **right before** the target node!

```mermaid
graph LR
    subgraph Pointers
    slow[slow: 3]
    fast[fast: null]
    end

    0((0 Dummy)) --> 1((1))
    1((1)) --> 2((2))
    2((2)) --> 3((3))
    3((3)) --> 4((4))
    4((4)) --> 5((5))
    5((5)) --> N((null))
    
    style 3 fill:#f9f,stroke:#333,stroke-width:2px
```
<!-- slide -->
## Step 3: Remove the Target Node
`slow` is at Node 3. We remove Node 4 by skipping it:
`slow.next = slow.next.next` (3 points directly to 5).
Node 4 is removed!

```mermaid
graph LR
    subgraph Result
    result[Node 4 Removed]
    end

    0((0 Dummy)) --> 1((1))
    1((1)) --> 2((2))
    2((2)) --> 3((3))
    3((3)) --> 5((5))
    5((5)) --> N((null))
    
    4((4 Removed))
    
    style 3 fill:#bfb,stroke:#333,stroke-width:2px
    style 4 fill:#f66,stroke:#333,stroke-width:2px
```
````
