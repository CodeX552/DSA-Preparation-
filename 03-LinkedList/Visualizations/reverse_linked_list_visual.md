# Reverse Linked List - Step-by-Step Visualization

Here is a step-by-step visual explanation of the Iterative Reverse Linked List algorithm. You can navigate through the carousel to see how the pointers (`prev`, `curr`, `next`) change at each step.

````carousel
## Initial State
Before the loop starts, we initialize our pointers:
- `prev = null`
- `curr = head (1)`

```mermaid
graph LR
    subgraph Pointers
    prev[prev: null]
    curr[curr: 1]
    end

    1((1)) --> 2((2))
    2((2)) --> 3((3))
    3((3)) --> N1((null))
    
    style 1 fill:#f9f,stroke:#333,stroke-width:2px
```
<!-- slide -->
## Step 1: Save next and reverse pointer
- `next = curr.next (2)` (Save the next node so we don't lose it)
- `curr.next = prev` (Point 1's next to null)

```mermaid
graph LR
    subgraph Pointers
    prev[prev: null]
    curr[curr: 1]
    next[next: 2]
    end

    1((1)) --> N2((null))
    2((2)) --> 3((3))
    3((3)) --> N1((null))
    
    style 1 fill:#f9f,stroke:#333,stroke-width:2px
    style 2 fill:#bbf,stroke:#333,stroke-width:2px
```
<!-- slide -->
## Step 1: Move pointers forward
- `prev = curr (1)` (Move prev to current)
- `curr = next (2)` (Move current to next)

```mermaid
graph LR
    subgraph Pointers
    prev[prev: 1]
    curr[curr: 2]
    end

    1((1)) --> N2((null))
    2((2)) --> 3((3))
    3((3)) --> N1((null))
    
    style 1 fill:#bbf,stroke:#333,stroke-width:2px
    style 2 fill:#f9f,stroke:#333,stroke-width:2px
```
<!-- slide -->
## Step 2: Save next and reverse pointer
- `next = curr.next (3)`
- `curr.next = prev (1)` (Point 2's next to 1)

```mermaid
graph LR
    subgraph Pointers
    prev[prev: 1]
    curr[curr: 2]
    next[next: 3]
    end

    2((2)) --> 1((1))
    1((1)) --> N2((null))
    
    3((3)) --> N1((null))
    
    style 2 fill:#f9f,stroke:#333,stroke-width:2px
    style 3 fill:#bbf,stroke:#333,stroke-width:2px
```
<!-- slide -->
## Step 2: Move pointers forward
- `prev = curr (2)`
- `curr = next (3)`

```mermaid
graph LR
    subgraph Pointers
    prev[prev: 2]
    curr[curr: 3]
    end

    2((2)) --> 1((1))
    1((1)) --> N2((null))
    
    3((3)) --> N1((null))
    
    style 2 fill:#bbf,stroke:#333,stroke-width:2px
    style 3 fill:#f9f,stroke:#333,stroke-width:2px
```
<!-- slide -->
## Step 3: Save next and reverse pointer
- `next = curr.next (null)`
- `curr.next = prev (2)` (Point 3's next to 2)

```mermaid
graph LR
    subgraph Pointers
    prev[prev: 2]
    curr[curr: 3]
    next[next: null]
    end

    3((3)) --> 2((2))
    2((2)) --> 1((1))
    1((1)) --> N2((null))
    
    style 3 fill:#f9f,stroke:#333,stroke-width:2px
```
<!-- slide -->
## Step 3: Move pointers forward
- `prev = curr (3)`
- `curr = next (null)`

```mermaid
graph LR
    subgraph Pointers
    prev[prev: 3]
    curr[curr: null]
    end

    3((3)) --> 2((2))
    2((2)) --> 1((1))
    1((1)) --> N2((null))
    
    style 3 fill:#bbf,stroke:#333,stroke-width:2px
```
<!-- slide -->
## Final State
The loop ends because `curr == null`. We return `prev` which is the new head of the reversed linked list!

```mermaid
graph LR
    subgraph Result
    head[New Head: 3]
    end

    3((3)) --> 2((2))
    2((2)) --> 1((1))
    1((1)) --> N2((null))
    
    style 3 fill:#bbf,stroke:#333,stroke-width:2px
```
````
