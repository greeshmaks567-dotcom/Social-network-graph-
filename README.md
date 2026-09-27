# Social-network-graph-
# Social Network Graph

## Problem Statement

This project implements a small social network using graph data structures. The social network consists of six users represented by the vertices A, B, C, D, E, and F. The connections between the users are A-B, A-C, B-D, B-E, C-F, and E-F. The graph is implemented using two different representations: an Adjacency Matrix and an Adjacency List. The project performs Breadth First Search (BFS) and Depth First Search (DFS) starting from vertex A to demonstrate graph traversal. It also implements a search operation to locate a specified vertex and records the number of operations required. Finally, the project compares the two graph representations based on space requirements, traversal behaviour, search and edge-checking operations, and time complexity. Since the given social network has relatively fewer connections compared with the possible number of connections, it represents a sparse graph. Therefore, the Adjacency List requires less memory and is more suitable for representing this type of social network.

## Graph Connections

The connections in the social network are:

- A-B
- A-C
- B-D
- B-E
- C-F
- E-F

## Features

- Adjacency Matrix representation
- Adjacency List representation
- BFS traversal
- DFS traversal
- Vertex search operation
- Operation counting
- Space complexity comparison
- Time complexity comparison
- Edge-checking comparison

## BFS Traversal

Starting from vertex A:

`A → B → C → D → E → F`

## DFS Traversal

Starting from vertex A:

`A → B → D → E → F → C`

The exact DFS order can vary depending on the order in which adjacent vertices are stored.

## Complexity Analysis

| Operation | Adjacency Matrix | Adjacency List |
|---|---|---|
| Space | O(V²) | O(V + E) |
| BFS/DFS | O(V²) | O(V + E) |
| Edge checking | O(1) | O(degree) |
| Vertex search | O(V) | O(V) |

Where V is the number of vertices and E is the number of edges.

## Conclusion

The Adjacency List is more suitable for this sparse social network because it stores only the existing connections between users and requires O(V + E) space. In contrast, an Adjacency Matrix stores information for every possible pair of vertices and requires O(V²) space. The implementation demonstrates how different graph representations affect memory usage, traversal, searching, and edge-checking operations.

## How to Run

Compile the C program using:

```bash
gcc graph.c -o graph