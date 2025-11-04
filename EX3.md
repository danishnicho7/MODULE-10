# Ex.No:3  
# Ex.Name: Topological Sorting using List and Stack  

## Date:16/10/25

## Aim:  
To write a C++ program to perform **Topological Sorting** for a Directed Acyclic Graph (DAG) using adjacency list and stack.  

## Algorithm:  
1. Start the program.  
2. Represent the graph using adjacency lists (`vector<int> adj[]`).  
3. Create a `visited[]` array to mark visited nodes.  
4. Implement a recursive function `topoSortUtil(v)`:  
   - Mark the current node as visited.  
   - Recursively call `topoSortUtil()` for all adjacent vertices.  
   - Push the current node into the stack after visiting all its neighbors.  
5. In `main()`, for all unvisited nodes, call `topoSortUtil()`.  
6. Pop elements from the stack to get the **Topological Ordering**.  
7. Print the ordering.  
8. Stop the program.  

## Program:
```cpp
#include <iostream>
#include <list>
#include <stack>
using namespace std;

class Graph {
	int V; 

	list<int>* adj;

	void topologicalSortUtil(int v, bool visited[], stack<int>& Stack);

public:
	Graph(int V); 

	void addEdge(int v, int w);

	void topologicalSort();
};

Graph::Graph(int V)
{
	this->V = V;
	adj = new list<int>[V];
}

void Graph::addEdge(int v, int w)
{
	adj[v].push_back(w); 
}

void Graph::topologicalSortUtil(int v, bool visited[],
								stack<int>& Stack)
{
	
	visited[v] = true;

	list<int>::iterator i;
	for (i = adj[v].begin(); i != adj[v].end(); ++i)
		if (!visited[*i])
			topologicalSortUtil(*i, visited, Stack);

	Stack.push(v);
}

void Graph::topologicalSort()
{
	
	stack <int> Stack;
	bool* visited = new bool [V];
	for(int i=0; i<V; i++)
	{
	    visited[i]=false;
	}
	for(int i=0; i<V; i++)
	{
	    if(visited[i]==false)
	    {
	        topologicalSortUtil (i, visited, Stack);
	    }
	}
	while(Stack.empty()==false)
	{
	    cout<<Stack.top()<<" ";
	    Stack.pop();
	}
}

int main()
{
    int a,b,n;
    cin>>n;
    Graph g(n);
    for(int i=0; i<6; i++)
    {
        cin>>a>>b;
        g.addEdge(a,b);
    }
    cout<<"Topological Sort of the given graph n"<<endl;
    g.topologicalSort();
	return 0;
}
```

## Output:
<img width="873" height="732" alt="image" src="https://github.com/user-attachments/assets/cc67e0f8-8fd2-4204-9626-f6fa847e120b" />

## Result:
```
Input:
6
5 2
5 0
4 0
4 1
2 3
3 1

Output:
Topological Sort of the given graph
5 4 2 3 1 0
```
