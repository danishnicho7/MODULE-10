# Ex.No:4  
# Ex.Name: Adjacency List Representation of a Graph  

## Date:16/10/25

## Aim:  
To write a C++ program to represent a **graph using adjacency list**.  
<img width="402" height="275" alt="image" src="https://github.com/user-attachments/assets/cddd561f-36fe-4646-bdcf-72b2838e951c" />

## Algorithm:  
1. Start the program.  
2. Create an adjacency list using `vector<int> adj[]`.  
3. Read the number of edges in the graph.  
4. For each edge `(u, v)`:  
   - Insert `v` into `adj[u]`.  
   - Insert `u` into `adj[v]` (if the graph is undirected).  
5. Print the adjacency list representation for all vertices.  
6. Stop the program.  

## Program:
```cpp
#include<iostream>
#include<list>
#include<iterator>
using namespace std;
void displayAdjList(list<int> adj_list[], int v)
{
   for(int i = 0; i<v; i++)
   {
      cout << i << "--->";
      list<int> :: iterator it;
      for(it = adj_list[i].begin(); it != adj_list[i].end(); ++it)
      {
         cout << *it << " ";
      }
      cout << endl;
   }
}
void add_edge(list<int> adj_list[], int u, int v)
{
   adj_list[u].push_back(v);
   adj_list[v].push_back(u);
}
int main() 
{
   
   int v = 6,a,b;
   list<int> adj_list[v];
   for(int i=0;i<6;i++)
   {
       cin>>a>>b;
       add_edge(adj_list, a, b);
   }
   displayAdjList(adj_list, v);
   return 0;
}
```

## Output:
<img width="864" height="824" alt="image" src="https://github.com/user-attachments/assets/9247161f-2442-425e-8879-5fff8fab796e" />

## Result:
```
Input:
0 4
0 3
1 2
1 4
1 5
2 3
2 5
5 3
5 4

Output:
0--->4 3
1--->2 4 5
2--->1 3
3--->0 2
4--->0 1
5--->1
```
