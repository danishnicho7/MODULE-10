# Ex.No:1  
# Ex.Name: Graph Implementation using STL (DFS of Unweighted and Undirected Graph)  

## Date:16/10/25

## Aim:  
To write a C++ program to implement a **Graph using STL** for competitive programming and perform **Depth First Search (DFS)** on an unweighted and undirected graph.  

## Algorithm:  
1. Start the program.  
2. Read the number of edges in the graph.  
3. Create an adjacency list representation of the graph using `vector<int> adj[]`.  
4. For each edge `(u, v)`:  
   - Add `v` to `adj[u]`.  
   - Add `u` to `adj[v]` (since the graph is undirected).  
5. Implement a DFS function:  
   - Mark the starting node as visited.  
   - Recursively visit all its unvisited adjacent vertices.  
6. Call the DFS function from the given starting vertex.  
7. Print the DFS traversal order.  
8. Stop the program.  

## Program:
```cpp
#include <bits/stdc++.h>
using namespace std;

void addEdge(vector<int> adj[], int u, int v)
{
    adj[u].push_back(v); //singly linked ,not bidirectional
}

void DFS(vector<int> adj[], int v, vector<bool> &vis)
{
    vis[v] = true;
    cout << v << " ";
    //for(int i=0;i<adj[v].size() ; i++)
    for (auto i : adj[v])
    {
        //if(!vis[adj[v][i]])
        if (vis[i] == false)
            DFS(adj, i, vis);
    }
}

int main()
{ 
    int n,a,b;
    cin>>n;
    vector<int> adj[n];
    vector<bool> visited(n, false);
    for(int i=0; i<n; i++)
    {
        cin>>a>>b;
        addEdge(adj, a,b);
    }
    DFS(adj, 1, visited);
}
```

## Output:
<img width="863" height="871" alt="image" src="https://github.com/user-attachments/assets/75bb7076-0e4d-427a-96d2-075ed8fe4ab7" />

## Result:
```
Input:
6
1 2
1 3
2 4
3 4
4 5

Output:
1 2 4 5 3
```
