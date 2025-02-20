# Breadth-First Search (BFS)

## Overview
- Uses a **Queue (FIFO)**
- Explores **all neighbors first** before going deeper.
- **Best for finding shortest paths** in an unweighted graph.

## Complexity
- **Time Complexity:** O(V + E)  
- **Space Complexity:** O(V) (storing visited nodes and queue)

## BFS Algorithm
1. Start from a source node.
2. Mark it as visited and enqueue it.
3. Dequeue a node, process it, and enqueue all unvisited neighbors.
4. Repeat until the queue is empty.

## Implementation (C++)
```cpp
#include <iostream>
#include <vector>
#include <queue>

using namespace std;

void bfs(vector<vector<int>>& adj, int start) {
    int n = adj.size();
    vector<bool> visited(n, false);
    queue<int> q;
    
    visited[start] = true;
    q.push(start);
    
    while (!q.empty()) {
        int node = q.front();
        q.pop();
        cout << node << " ";
        
        for (int neighbor : adj[node]) {
            if (!visited[neighbor]) {
                visited[neighbor] = true;
                q.push(neighbor);
            }
        }
    }
}

int main() {
    vector<vector<int>> adj = {
        {1, 2},  // 0 -> 1, 2
        {0, 3, 4}, // 1 -> 0, 3, 4
        {0, 5, 6}, // 2 -> 0, 5, 6
        {1},       // 3 -> 1
        {1},       // 4 -> 1
        {2},       // 5 -> 2
        {2}        // 6 -> 2
    };

    bfs(adj, 0);
}
```

## Output (BFS starting from node 0):
```
0 1 2 3 4 5 6
```

## Applications
- **Shortest path finding** (unweighted graphs)
- **Social networking applications** (finding connections)
- **Web crawling** (search engines)
- **AI and game development** (finding the best moves)

---

This README provides an overview of BFS, its algorithm, complexity, and a sample C++ implementation. 🚀

