# Intersection of Two Linked Lists - Step-by-Step Visualization

This carousel explains the two-pointer approach to finding the intersection node of two lists with different lengths.

````carousel
## Initial State
Two lists intersect at Node `8`. Pointer `A` starts at Head A, `B` starts at Head B.

```mermaid
graph LR
    subgraph List A
    A1((4)) --> A2((1))
    end
    
    subgraph List B
    B1((5)) --> B2((6))
    B2 --> B3((1))
    end
    
    subgraph Common
    C1((8)) --> C2((4))
    C2 --> C3((5))
    end
    
    A2 --> C1
    B3 --> C1

    style A1 fill:#f9f,stroke:#333,stroke-width:2px
    style B1 fill:#bbf,stroke:#333,stroke-width:2px
```
<!-- slide -->
## Moving Forward
Both move 1 step at a time. List B is longer, so pointer `A` will reach the end (`null`) first.

```mermaid
graph LR
    subgraph List A
    A1((4)) --> A2((1))
    end
    
    subgraph List B
    B1((5)) --> B2((6))
    B2 --> B3((1))
    end
    
    subgraph Common
    C1((8)) --> C2((4))
    C2 --> C3((5))
    end
    
    A2 --> C1
    B3 --> C1

    style A2 fill:#f9f,stroke:#333,stroke-width:2px
    style B2 fill:#bbf,stroke:#333,stroke-width:2px
```
<!-- slide -->
## Swap Tracks
When a pointer reaches `null`, it jumps to the head of the **OTHER** list.
- `A` reached null, so it jumps to `Head B`.
- `B` reached null shortly after, jumping to `Head A`.

By swapping tracks, both pointers will traverse the exact same total distance!

```mermaid
graph LR
    subgraph Pointers
    PA[A is now on List B]
    PB[B is now on List A]
    end
    
    subgraph List A
    A1((4)) --> A2((1))
    end
    
    subgraph List B
    B1((5)) --> B2((6))
    B2 --> B3((1))
    end
    
    subgraph Common
    C1((8)) --> C2((4))
    C2 --> C3((5))
    end
    
    A2 --> C1
    B3 --> C1

    style B2 fill:#f9f,stroke:#333,stroke-width:2px
    style A2 fill:#bbf,stroke:#333,stroke-width:2px
```
<!-- slide -->
## Intersection Found
Because they swapped tracks, they are now perfectly synced. They will meet exactly at the intersection node (`8`) at the same time.

```mermaid
graph LR
    subgraph Result
    result[Intersection at Node 8]
    end
    
    subgraph List A
    A1((4)) --> A2((1))
    end
    
    subgraph List B
    B1((5)) --> B2((6))
    B2 --> B3((1))
    end
    
    subgraph Common
    C1((8)) --> C2((4))
    C2 --> C3((5))
    end
    
    A2 --> C1
    B3 --> C1

    style C1 fill:#bfb,stroke:#333,stroke-width:3px
```
````
