# Ex.No:2  
# Ex.Name: Topological Sorting (using vector and algorithm STLs)  

## Date:16/10/25

## Aim:  
To Write A C++ Program for Topological Sorting (using vector and algorithm STLs)  
<img width="162" height="133" alt="image" src="https://github.com/user-attachments/assets/2c688db9-6cdf-4311-aed5-922d00398eb9" />

## Algorithm
1. Start the program.
2. Define a `pair` struct with:
   - two integers: `a` and `b`
   - a constructor `pair(int a, int b)`
   - a `print(std::ostream&)` method that outputs `(a, b)`
3. Overload `operator<<` for `pair` so `std::cout << p` prints `(a, b)` by calling `print`.
4. Define a comparator `topological_pair_comparator` with:
   - `bool operator()(const pair& p, const pair& q) const`
   - Return `true` **only if** `p.a < q.a` **and** `p.b < q.b`  
     (i.e., `p` strictly dominates `q` on both coordinates).
5. Create a global `std::vector<pair>` named `pairs` and initialize it with:
   - `(1,1), (1,2), (2,1), (3,1), (1,3), (2,2), (4,0), (5,5)`
6. In `main()`:
   - Call `std::sort(pairs.begin(), pairs.end(), tpc)` to reorder the vector using the dominance comparator.
     - For any two elements `p` and `q`:
       - If `p.a < q.a` **and** `p.b < q.b`, then `p` is placed before `q`.
       - If neither dominates the other (e.g., `(2,1)` vs `(1,2)`), the comparator returns `false` both ways; their relative order is not strictly defined.
7. Iterate over the (re)ordered vector and print each pair with `std::cout << p << " "`.
8. Print a newline and stop the program.

## Program:
```cpp
#include <iostream>
#include <vector>
#include <algorithm>

struct pair 
{
	int a, b;
	pair(int a, int b) : a(a), b(b) {}
	
	std::ostream &print(std::ostream &out) const 
	{
		return (out << "(" << a << ", " << b << ")");
	}
};

std::ostream &operator<<(std::ostream &out, const pair &p) 
{ 
    return p.print(out); 
    
}

struct topological_pair_comparator 
{
	bool operator()(const pair &p, const pair &q) const 
	{ 
	    return p.a<q.a && p.b<q.b; 
	    
	}
} tpc;

std::vector<pair> pairs = 
{
    pair(1,1),
    pair(1,2),
    pair(2,1),
    pair(3,1),
    pair(1,3),
    pair(2,2),
    pair(4,0),
    pair(5,5)

//write code here
};

int main() {
	std::sort(pairs.begin(), pairs.end(), tpc);
	for(const pair &p : pairs) std::cout << p << " ";
	std::cout << std::endl;
	return 0;
}
```

 ## Output:
<img width="1228" height="307" alt="image" src="https://github.com/user-attachments/assets/9eb8527e-c9cd-4567-9ab8-699fe01dcd01" />

## Result:
```
Input:	
0 0

Output:
(1, 1) (1, 2) (2, 1) (3, 1) (1, 3) (2, 2) (4, 0) (5, 5)
```
