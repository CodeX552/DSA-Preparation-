# Middle of Linked List - Step-by-Step Visualization

This interactive carousel explains the **Fast-Slow Pointer** technique to find the middle node of a linked list. `slow` moves 1 step at a time, while `fast` moves 2 steps.

````carousel
## Initial State
- `slow = head (1)`
- `fast = head (1)`

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
    5((5)) --> N((null))
    
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
    5((5)) --> N((null))
    
    style 2 fill:#f9f,stroke:#333,stroke-width:2px
    style 3 fill:#bbf,stroke:#333,stroke-width:2px
```
<!-- slide -->
## Step 2
- `slow` moves 1 step to **3**
- `fast` moves 2 steps to **5**

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
    5((5)) --> N((null))
    
    style 3 fill:#f9f,stroke:#333,stroke-width:2px
    style 5 fill:#bbf,stroke:#333,stroke-width:2px
```
<!-- slide -->
## Final State
`fast.next` is null, so the loop terminates.
`slow` is currently at node **3**, which is exactly the middle of the linked list!

```mermaid
graph LR
    subgraph Result
    result[Middle Node: 3]
    end

    1((1)) --> 2((2))
    2((2)) --> 3((3))
    3((3)) --> 4((4))
    4((4)) --> 5((5))
    5((5)) --> N((null))
    
    style 3 fill:#f9f,stroke:#333,stroke-width:2px
```
````
