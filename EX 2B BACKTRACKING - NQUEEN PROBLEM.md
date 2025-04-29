# EX 2B BACKTRACKING - NQUEEN PROBLEM
## DATE: 08.03.2025
## AIM:
To solve the N-Queen problem using backtracking, which places N queens on an N*N chessboard such that no two queens threaten each other.

## Algorithm  

1. Take an integer input `N` representing the size of the chessboard and number of queens.  
2. Define `printSolution(board)` to print the current configuration of the chessboard.  
3. Define `isSafe(board, row, col)` to check if placing a queen at `(row, col)` is safe.  
4. In `isSafe`, check the current row to the left for any queen.  
5. Check the upper-left diagonal for any queen.  
6. Check the lower-left diagonal for any queen.  
7. If no queens threaten the position, return `True`; otherwise, return `False`.  
8. Define `solveNQUtil(board, col)` to place queens recursively column by column.  
9. If all columns are processed (`col >= N`), return `True` (solution found).  
10. Try placing a queen in each row of the current column and check if it is safe.  
11. If placing the queen is safe, mark it and recursively try placing the rest.  
12. If recursion fails, backtrack by removing the queen (`board[i][col] = 0`).  
13. If no safe position is found in the current column, return `False`.  
14. Define `solveNQ()` to initialize an `N x N` board with all zeros.  
15. Call `solveNQUtil(board, 0)` to start solving from the first column.  
16. If a solution exists, print the board; otherwise, print "Solution does not exist".  

## Program:
```
/*
Program to implement N-Queen problem using backtracking.
Developed by: AKSHAYAA M
Register Number: 212222230009
*/
```
```python
global N
N = int(input())
 
def printSolution(board):
    for i in range(N):
        for j in range(N):
            print(board[i][j], end = " ")
        print()
 
def isSafe(board, row, col):
 
    # Check this row on left side
    for i in range(col):
        if board[row][i] == 1:
            return False
 
    # Check upper diagonal on left side
    for i, j in zip(range(row, -1, -1),
                    range(col, -1, -1)):
        if board[i][j] == 1:
            return False
 
    # Check lower diagonal on left side
    for i, j in zip(range(row, N, 1),
                    range(col, -1, -1)):
        if board[i][j] == 1:
            return False
 
    return True
 
def solveNQUtil(board, col):
      if col>=N:
          return True
      for i in range(N):
          if isSafe(board, i, col):
              board[i][col]=1
              if solveNQUtil(board, col+1):
                  return True
              board[i][col]=0
      return False
      
def solveNQ():
    board = [ [0, 0, 0, 0],
              [0, 0, 0, 0],
              [0, 0, 0, 0],
              [0, 0, 0, 0]]
              
    if solveNQUtil(board, 0) == False:
        print ("Solution does not exist")
        return False
 
    printSolution(board)
    return True
 
# Driver Code
solveNQ()
```
## Output:

![image](https://github.com/user-attachments/assets/4900525f-0b5e-4edc-a207-988c626194d1)

## Result:
The N-Queens program executed successfully, and a valid board configuration was generated.
