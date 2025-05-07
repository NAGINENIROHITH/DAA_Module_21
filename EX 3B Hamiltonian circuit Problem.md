# EX 3B Hamiltonian Circuit Problem
## DATE:
## AIM:
To write a python program to check whether Hamiltonian path exits in the given graph.

## Algorithm
1. Initialization of DP Table:

The DP table dp[i][mask] stores whether it’s possible to visit vertex i with a subset of vertices represented by mask.

2. Check All Subsets:

For each subset of vertices, attempt to add a vertex j to the path if it is connected to another vertex k that is already in the subset.

3. Backtracking with Bitmasking:

The algorithm explores all possible vertex orderings using dynamic programming, checking whether it's possible to reach each vertex with the current subset.

4. Final Check:

The algorithm checks if any vertex i has been visited with the subset of all vertices. If so, it indicates that a Hamiltonian path exists.

5. Result:

If such a path exists, print YES. Otherwise, print NO.
## Program:
```
/*
Program to implement to check whether Hamiltonian path exits in the given graph.
Developed by: NAGINENI ROHITH
Register Number:  212222040105
*/
```
```
def Hamiltonian_path(adj, N):
    dp = [[False for i in range(1 << N)]
                 for j in range(N)]
    for i in range(N):
        dp[i][1 << i] = True
    for i in range(1 << N):
        for j in range(N):
 
            if ((i & (1 << j)) != 0):
 
                for k in range(N):
                    if ((i & (1 << k)) != 0 and
                             adj[k][j] == 1 and
                                     j != k and
                          dp[k][i ^ (1 << j)]):
                        dp[j][i] = True
                        break
    for i in range(N):
        if (dp[i][(1 << N) - 1]):
            return True
    return False
adj = [ [ 0, 1, 1, 1, 0 ] ,
        [ 1, 0, 1, 0, 1 ],
        [ 1, 1, 0, 1, 1 ],
        [ 1, 0, 1, 0, 0 ] ]
 
N = len(adj)
 
if (Hamiltonian_path(adj, N)):
    print("YES")
else:
    print("NO")
```
## Output:
![image](https://github.com/user-attachments/assets/68aabc7f-c079-4b8b-91a3-6c7ff6c9afda)

## Result:
The Hamiltonian path program executed successfully, and it determined whether a Hamiltonian path exists in the given graph.
