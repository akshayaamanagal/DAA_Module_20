# EX 2A BACKTRACKING - RAT IN MAZE PROBLEM
## DATE: 04.03.2025
## AIM:
To implement the Rat in a Maze problem using backtracking and find all possible paths from the start to the destination in a given maze.

## Algorithm  
1. Define `printSolution(sol)` to display the solution matrix.  
2. Define `isSafe(maze, x, y)` to check if position `(x, y)` is within bounds and accessible (`1`).  
3. Define `solveMaze(maze)` to initialize a solution matrix and call the recursive utility function.  
4. If the utility function returns `False`, print "Solution doesn't exist" and return `False`.  
5. If a solution exists, print the solution matrix and return `True`.  
6. Define `solveMazeUtil(maze, x, y, sol)` to solve the maze recursively.  
7. If `(x, y)` is the destination `(N-1, N-1)`, mark it in the solution and return `True`.  
8. If `(x, y)` is safe, mark it as part of the solution path.  
9. Recursively attempt to move right (`x+1, y`); if successful, return `True`.  
10. If right move fails, try moving down (`x, y+1`); if successful, return `True`.  
11. If neither move leads to a solution, backtrack by unmarking `(x, y)` and return `False`.  
12. Define the maze as a 4x4 grid with 1s (paths) and 0s (walls).  
13. Call `solveMaze(maze)` to find and print the path from the top-left to bottom-right corner.  


## Program:
```
/*
Program to implement Rat in a Maze.
Developed by: AKSHAYAA M
Register Number: 212222230009
*/
```
```python
N = 4
def printSolution( sol ):
     for i in sol:
        for j in i:
            print(str(j) + " ", end ="")
        print("")
 

def isSafe( maze, x, y ):
     
    if x >= 0 and x < N and y >= 0 and y < N and maze[x][y] == 1:
        return True
     
    return False
 

def solveMaze( maze ):
     
    # Creating a 4 * 4 2-D list
    sol = [ [ 0 for j in range(4) ] for i in range(4) ]
     
    if solveMazeUtil(maze, 0, 0, sol) == False:
        print("Solution doesn't exist");
        return False
     
    printSolution(sol)
    return True
     

def solveMazeUtil(maze, x, y, sol):
    if x==N-1 and y==N-1:
        sol[x][y]=1
        return True
    if isSafe(maze,x,y)==True:
        sol[x][y] = 1
        if solveMazeUtil(maze,x+1,y,sol) == True:
            return True
        if solveMazeUtil(maze,x,y+1,sol)== True:
            return True
        sol[x][y] = 0
        return False


# Driver program to test above function
if __name__ == "__main__":
    # Initialising the maze
    maze = [ [1, 0, 0, 0],
             [1, 1, 0, 1],
             [0, 1, 0, 0],
             [1, 1, 1, 1] ]
              
    solveMaze(maze)
```

## Output:

![image](https://github.com/user-attachments/assets/f301e983-c455-4eb6-92a4-5c8c91c361d9)


## Result:
The Rat in a Maze program executed successfully, and a valid path from the start to the destination was found and display.
