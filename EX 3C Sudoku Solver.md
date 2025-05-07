# EX 3C Sudoku Solver
## DATE:
## AIM:
To write a python program to find the solution of sudoku puzzle using Backtracking.


## Algorithm
1. Find the First Empty Cell: Scan the board for an empty cell (represented by 0).

2. Try All Possible Values (1-9): For the empty cell, try placing each number from 1 to 9. For each number, check if it's valid using the isPossible() function.

3. Check for Validity: In the isPossible() function, ensure the number doesn't violate the Sudoku rules (no duplicate in the row, column, or 3x3 subgrid).

4. Recursive Backtracking: If a number is valid, place it in the cell, and recursively attempt to solve the rest of the board. If the board is filled successfully, print the solution. If not, backtrack by resetting the cell and trying the next number.

5. End Condition: If all cells are filled correctly, print the solution. If no valid solution exists (which shouldn't happen for a valid Sudoku puzzle), the algorithm will terminate after exhausting all possibilities. 

## Program:
```
/*
Program to implement to to find the solution of sudoku puzzle using Backtracking.
Developed by: NAGINENI ROHITH
Register Number:  212222040105
*/
```
```
board = [
    [0, 0, 0, 8, 0, 0, 4, 0, 3],
    [2, 0, 0, 0, 0, 4, 8, 9, 0],
    [0, 9, 0, 0, 0, 0, 0, 0, 2],
    [0, 0, 0, 0, 2, 9, 0, 1, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 7, 0, 6, 5, 0, 0, 0, 0],
    [9, 0, 0, 0, 0, 0, 0, 8, 0],
    [0, 6, 2, 7, 0, 0, 0, 0, 1],
    [4, 0, 3, 0, 0, 6, 0, 0, 0]
]

def printBoard(board):
    for i in range(0, 9):
        for j in range(0, 9):
            print(board[i][j], end=" ")
        print()

def isPossible(board, row, col, val):
    for j in range(0, 9):
        if board[row][j] == val:
            return False

    for i in range(0, 9):
        if board[i][col] == val:
            return False

    startRow = (row // 3) * 3
    startCol = (col // 3) * 3
    for i in range(0, 3):
        for j in range(0, 3):
            if board[startRow+i][startCol+j] == val:
                return False
    return True

def solve():
    for i in range(0, 9):
        for j in range(0, 9):
            if board[i][j] == 0:
                for val in range(1, 10):
                    if isPossible(board, i, j, val):
                        board[i][j] = val
                        solve()
                        board[i][j] = 0
                return
    printBoard(board)

solve()
```

## Output:
![image](https://github.com/user-attachments/assets/de5b7475-7831-4c9b-ae12-462aa14bd1e8)

## Result:
The Sudoku solver program executed successfully and found the solution for the given puzzle.
