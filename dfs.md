Depth-First Search (DFS)

Overview

Uses a Stack (LIFO) (can be recursive or iterative)

Explores as deep as possible before backtracking.

Best for exploring all possible paths (e.g., maze solving, cycle detection).

Complexity

Time Complexity: O(V + E)

Space Complexity: O(V) (recursion stack or explicit stack)

DFS Algorithm

Start from a source node.

Mark it as visited and process it.

Recursively (or using a stack) visit all its unvisited neighbors.

Backtrack when no unvisited neighbors remain.

Implementation (C++)

#include <iostream>
#include <vector>
#include <stack>

using namespace std;

void dfsRecursive(vector<vector<int>>& adj, vector<bool>& visited, int node) {
    visited[node] = true;
    cout << node << " ";
    
    for (int neighbor : adj[node]) {
        if (!visited[neighbor]) {
            dfsRecursive(adj, visited, neighbor);
        }
    }
}

void dfsIterative(vector<vector<int>>& adj, int start) {
    vector<bool> visited(adj.size(), false);
    stack<int> s;
    
    s.push(start);
    while (!s.empty()) {
        int node = s.top();
        s.pop();
        
        if (!visited[node]) {
            visited[node] = true;
            cout << node << " ";
            
            for (auto it = adj[node].rbegin(); it != adj[node].rend(); ++it) {
                if (!visited[*it]) {
                    s.push(*it);
                }
            }
        }
    }
}

int main() {
    vector<vector<int>> adj = {
        {1, 2},
        {0, 3, 4},
        {0, 5, 6},
        {1},
        {1},
        {2},
        {2}
    };

    vector<bool> visited(adj.size(), false);
    cout << "Recursive DFS: ";
    dfsRecursive(adj, visited, 0);
    cout << "\nIterative DFS: ";
    dfsIterative(adj, 0);
}

Output (DFS starting from node 0):

Recursive DFS: 0 1 3 4 2 5 6
Iterative DFS: 0 1 4 3 2 6 5

Applications

Pathfinding and connectivity

Cycle detection in graphs

Topological sorting

Solving puzzles and mazes
