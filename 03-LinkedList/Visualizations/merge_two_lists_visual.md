# Merge Two Sorted Lists - Step-by-Step Visualization

This interactive carousel explains how to merge two sorted linked lists using a **dummy** node and a `current` pointer.

````carousel
## Initial State
- Create a `dummy` node to hold the result.
- `current = dummy`
- `l1` points to the head of List 1 (`1`)
- `l2` points to the head of List 2 (`2`)

```mermaid
graph LR
    subgraph List 1
    L1_1((1)) --> L1_3((3))
    L1_3 --> L1_5((5))
    end
    
    subgraph List 2
    L2_2((2)) --> L2_4((4))
    L2_4 --> L2_6((6))
    end
    
    subgraph Result
    dummy((0 Dummy))
    end

    style L1_1 fill:#f9f,stroke:#333,stroke-width:2px
    style L2_2 fill:#bbf,stroke:#333,stroke-width:2px
    style dummy fill:#bfb,stroke:#333,stroke-width:2px
```
<!-- slide -->
## Step 1
- Compare: `l1.val (1) < l2.val (2)`
- Link: `current.next = l1`
- Move `l1` to `3`
- Move `current` to `1`

```mermaid
graph LR
    subgraph Lists Remaining
    L1_3((3)) --> L1_5((5))
    L2_2((2)) --> L2_4((4))
    L2_4 --> L2_6((6))
    end
    
    subgraph Result List
    dummy((0 Dummy)) --> L1_1((1))
    end

    style L1_3 fill:#f9f,stroke:#333,stroke-width:2px
    style L2_2 fill:#bbf,stroke:#333,stroke-width:2px
    style L1_1 fill:#bfb,stroke:#333,stroke-width:2px
```
<!-- slide -->
## Step 2
- Compare: `l2.val (2) < l1.val (3)`
- Link: `current.next = l2`
- Move `l2` to `4`
- Move `current` to `2`

```mermaid
graph LR
    subgraph Lists Remaining
    L1_3((3)) --> L1_5((5))
    L2_4((4)) --> L2_6((6))
    end
    
    subgraph Result List
    dummy((0 Dummy)) --> L1_1((1))
    L1_1 --> L2_2((2))
    end

    style L1_3 fill:#f9f,stroke:#333,stroke-width:2px
    style L2_4 fill:#bbf,stroke:#333,stroke-width:2px
    style L2_2 fill:#bfb,stroke:#333,stroke-width:2px
```
<!-- slide -->
## Step 3
- Compare: `l1.val (3) < l2.val (4)`
- Link: `current.next = l1`
- Move `l1` to `5`
- Move `current` to `3`

```mermaid
graph LR
    subgraph Lists Remaining
    L1_5((5))
    L2_4((4)) --> L2_6((6))
    end
    
    subgraph Result List
    dummy((0 Dummy)) --> L1_1((1))
    L1_1 --> L2_2((2))
    L2_2 --> L1_3((3))
    end

    style L1_5 fill:#f9f,stroke:#333,stroke-width:2px
    style L2_4 fill:#bbf,stroke:#333,stroke-width:2px
    style L1_3 fill:#bfb,stroke:#333,stroke-width:2px
```
<!-- slide -->
## Final Steps
The process continues appending the smaller node (`4`, then `5`, then `6`).
Once one list is empty, we simply append the remaining nodes of the other list directly to `current.next`.
The final merged sorted list starts at `dummy.next`!

```mermaid
graph LR
    subgraph Final Result
    dummy((0 Dummy)) --> L1_1((1))
    L1_1 --> L2_2((2))
    L2_2 --> L1_3((3))
    L1_3 --> L2_4((4))
    L2_4 --> L1_5((5))
    L1_5 --> L2_6((6))
    end
    
    style dummy fill:#ddd,stroke:#333,stroke-width:2px
```
````
