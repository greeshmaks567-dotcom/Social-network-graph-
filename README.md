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


CODE
#include <stdio.h>

#define V 6

char vertex[V] = {'A','B','C','D','E','F'};

int graph[V][V] = {
    {0,1,1,0,0,0},
    {1,0,0,1,1,0},
    {1,0,0,0,0,1},
    {0,1,0,0,0,0},
    {0,1,0,0,0,1},
    {0,0,1,0,1,0}
};

void bfs(int start)
{
    int visited[V] = {0};
    int queue[V];
    int front = 0, rear = 0;
    int i, u;

    visited[start] = 1;
    queue[rear++] = start;

    printf("BFS: ");

    while(front < rear)
    {
        u = queue[front++];
        printf("%c ", vertex[u]);

        for(i = 0; i < V; i++)
        {
            if(graph[u][i] && !visited[i])
            {
                visited[i] = 1;
                queue[rear++] = i;
            }
        }
    }

    printf("\n");
}

void dfs(int u, int visited[])
{
    int i;

    visited[u] = 1;
    printf("%c ", vertex[u]);

    for(i = 0; i < V; i++)
    {
        if(graph[u][i] && !visited[i])
            dfs(i, visited);
    }
}

void searchVertex(char key)
{
    int i, operations = 0;

    for(i = 0; i < V; i++)
    {
        operations++;

        if(vertex[i] == key)
        {
            printf("Vertex %c found\n", key);
            printf("Operations: %d\n", operations);
            return;
        }
    }

    printf("Vertex not found\n");
}

int main()
{
    int i, j;
    int visited[V] = {0};

    printf("Adjacency Matrix:\n");

    for(i = 0; i < V; i++)
    {
        for(j = 0; j < V; j++)
            printf("%d ", graph[i][j]);

        printf("\n");
    }

    printf("\nAdjacency List:\n");

    for(i = 0; i < V; i++)
    {
        printf("%c -> ", vertex[i]);

        for(j = 0; j < V; j++)
        {
            if(graph[i][j])
                printf("%c ", vertex[j]);
        }

        printf("\n");
    }

    printf("\nBFS starting from A:\n");
    bfs(0);

    printf("\nDFS starting from A:\n");
    dfs(0, visited);

    printf("\n\nSearch for E:\n");
    searchVertex('E');

    return 0;
}