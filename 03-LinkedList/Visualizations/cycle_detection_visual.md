# Detect Cycle (Floyd's Algorithm) - Step-by-Step Visualization

This carousel explains how **Floyd's Cycle Detection** algorithm works. If there is a cycle, the `fast` pointer (moving 2 steps) will eventually catch up and meet the `slow` pointer (moving 1 step) inside the cycle.

````carousel
## Initial State
- `slow = head (1)`
- `fast = head (1)`

*(Note: Node 5 points back to Node 3, creating a cycle)*

```mermaid
graph LR
    subgraph Pointers
    slow[slow: 1]
    fast[fast: 1]
    end

    1((1)) --> 2((2))
    2((2)) --> 3((3))
    3((3)) --> 4((4))
    4((4)) --> 5((5))
    5((5)) -.->|Cycle| 3
    
    style 1 fill:#f9f,stroke:#333,stroke-width:2px
```
<!-- slide -->
## Step 1
- `slow` moves 1 step to **2**
- `fast` moves 2 steps to **3**

```mermaid
graph LR
    subgraph Pointers
    slow[slow: 2]
    fast[fast: 3]
    end

    1((1)) --> 2((2))
    2((2)) --> 3((3))
    3((3)) --> 4((4))
    4((4)) --> 5((5))
    5((5)) -.->|Cycle| 3
    
    style 2 fill:#f9f,stroke:#333,stroke-width:2px
    style 3 fill:#bbf,stroke:#333,stroke-width:2px
```
<!-- slide -->
## Step 2
- `slow` moves 1 step to **3**
- `fast` moves 2 steps (`4` -> `5`) to **5**

```mermaid
graph LR
    subgraph Pointers
    slow[slow: 3]
    fast[fast: 5]
    end

    1((1)) --> 2((2))
    2((2)) --> 3((3))
    3((3)) --> 4((4))
    4((4)) --> 5((5))
    5((5)) -.->|Cycle| 3
    
    style 3 fill:#f9f,stroke:#333,stroke-width:2px
    style 5 fill:#bbf,stroke:#333,stroke-width:2px
```
<!-- slide -->
## Step 3
- `slow` moves 1 step to **4**
- `fast` moves 2 steps (`5` -> `3` -> `4`) to **4**

```mermaid
graph LR
    subgraph Pointers
    slow[slow: 4]
    fast[fast: 4]
    end

    1((1)) --> 2((2))
    2((2)) --> 3((3))
    3((3)) --> 4((4))
    4((4)) --> 5((5))
    5((5)) -.->|Cycle| 3
    
    style 4 fill:#bfb,stroke:#333,stroke-width:2px
```
<!-- slide -->
## Final State
`slow == fast` (Both are now at Node **4**). 
Since they met, a cycle is successfully detected! We return `true`.

```mermaid
graph LR
    subgraph Result
    result[Cycle Detected at Node 4!]
    end

    1((1)) --> 2((2))
    2((2)) --> 3((3))
    3((3)) --> 4((4))
    4((4)) --> 5((5))
    5((5)) -.->|Cycle| 3
    
    style 4 fill:#bfb,stroke:#333,stroke-width:2px
```
````
