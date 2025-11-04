# Ex.No:5  
# Ex.Name: Breadth First Search (BFS) using Vectors and Queue (with double data)  

## Date:16/10/25

## Aim:  
To write a C++ program to implement **Breadth First Search (BFS)** using `vector` and `queue`, where the graph vertices are represented by **double data**.  
<img width="242" height="278" alt="image" src="https://github.com/user-attachments/assets/1572c557-bb6a-4943-8944-2cf095d4c39f" />

## Algorithm:  
1. Start the program.  
2. Read the number of vertices `V` and edges `E`.  
3. Create an adjacency list using `vector<vector<double>> adj`.  
4. For each edge `(u, v)`:  
   - Add `v` to the adjacency list of `u`.  
   - Add `u` to the adjacency list of `v` (if the graph is undirected).  
5. Maintain a `visited[]` array to mark visited vertices.  
6. Use a queue to perform BFS:  
   - Start from vertex `0`.  
   - Mark it visited and enqueue it.  
   - Dequeue a vertex, print it, and enqueue all its unvisited neighbors.  
7. Continue until the queue is empty.  
8. Stop the program.  

## Program:
```cpp
#include <bits/stdc++.h>
#define pb push_back

using namespace std;

vector<bool> v;
vector<vector<float> > g;

void edge(int a, int b)
{
	g[a].pb(b);

}

void bfs(int u)
{
	queue<float> q;

	q.push(u);
	v[u] = true;

	while (!q.empty()) {

		int f = q.front();
		q.pop();
		cout << f << " ";

		for (auto i = g[f].begin(); i != g[f].end(); i++) {
			if (!v[*i]) {
				q.push(*i);
				v[*i] = true;
			}
		}
	}
}

int main()
{
	int n, e;
	cin >> n >> e;

	v.assign(n, false);
	g.assign(n, vector<float>());

	int a, b;
	for (int i = 0; i < e; i++) {
		cin >> a >> b;
		edge(a, b);
	}

	for (int i = 0; i < n; i++) {
		if (!v[i])
			bfs(i);
	}

	return 0;
}
```

## Output:
<img width="852" height="701" alt="image" src="https://github.com/user-attachments/assets/9ce514ff-f941-4f8b-a724-dc27c207e86e" />

## Result:
```
Input:
8 9
0.0 1.1
0.0 2.2
0.0 3.3
0.0 4.4
1.1 5.5
2.2 5.5
3.3 6.6
4.4 6.6
5.5 7.7
6.6 7.7

Output:
0 1 2 3 4 5 6 7
```
