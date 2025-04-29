# EX 2D BACKTRACKING - GRAPH COLORING PROBLEM
## DATE: 15.03.2025
## AIM:
To solve the Graph Coloring Problem using backtracking, assigning colors to the vertices of a graph such that no two adjacent vertices share the same color while minimizing the number of colors used.

## Algorithm  

1. Define a class `Graph` with an initializer to set the number of vertices and an adjacency matrix.  
2. Initialize `self.graph` as a 2D list representing connections between vertices.  
3. Define `isSafe(v, colour, c)` to check if vertex `v` can be assigned color `c` without conflicting with adjacent vertices.  
4. In `isSafe`, return `False` if any adjacent vertex has the same color `c`, else return `True`.  
5. Define `graphColourUtil(m, colour, v)` as a recursive function to assign colors to vertices from 1 to `m`.  
6. If all vertices are colored (`v == self.V`), return `True` as a valid coloring is found.  
7. Try assigning each color `c` (1 to `m`) to vertex `v` and check if it is safe using `isSafe`.  
8. If safe, assign the color to `colour[v]` and recurse to the next vertex.  
9. If recursion returns `True`, propagate success; otherwise, backtrack by resetting `colour[v] = 0`.  
10. Define `graphColouring(m)` to initialize the color array and begin coloring from vertex 0.  
11. If the utility function fails to color the graph, return `False` (no solution exists).  
12. If successful, print the color assigned to each vertex and return `True`.  

## Program:
```
/*
Program to implement Graph Coloring Problem using backtracking.
Developed by: AKSHAYAA M
Register Number: 212222230009
*/
```
```python
class Graph:
    def __init__(self,vertices):
        self.V=vertices
        self.graph = [[0 for column in range(vertices)]for row in range(vertices)]
    
    def isSafe(self,v,colour,c):
        for i in range(self.V):
            if self.graph[v][i] == 1 and colour[i]==c:
                return False
        return True
        
    def graphColourUtil(self,m,colour,v):
        if v==self.V:
            return True
        for c in range(1,m+1):
            if self.isSafe(v,colour,c) == True:
                colour[v]=c
                if self.graphColourUtil(m,colour,v+1) == True:
                    return True
                colour[v]=0
    
    def graphColouring(self,m):
        colour = [0] * self.V
        if self.graphColourUtil(m,colour,0) == None:
            return False
        print("Solution exist and Following are the assigned colours:")
        for c in colour:
            print(c,end=' ')
        return True
```
## Output:

![image](https://github.com/user-attachments/assets/f8ae8a4c-365d-4e16-b7c2-e4229920ce9f)

## Result:
The Graph Coloring program executed successfully, and the colors were assigned to the vertices such that no two adjacent vertices share the same color.
