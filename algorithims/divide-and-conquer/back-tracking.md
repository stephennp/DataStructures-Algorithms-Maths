# Intro

- So, while solving a problem using recursion, we break the given problem into smaller ones. Let's say we have a problem and we divided it into three smaller problems , and . Now it may be the case that the solution to does not depend on all the three subproblems, in fact we don't even know on which one it depends.
- Let's take a situation. Suppose you are standing in front of three tunnels, one of which is having a bag of gold at its end, but you don't know which one. So you'll try all three. First go in tunnel , if that is not the one, then come out of it, and go into tunnel , and again if that is not the one, come out of it and go into tunnel . So basically in backtracking we attempt solving a subproblem, and if we don't reach the desired solution, then undo whatever we did for solving that subproblem, and try solving another subproblem.

- Let's take a standard problem.
- N-Queens Problem: Given a chess board having cells, we need to place queens in such a way that no queen is attacked by any other queen. A queen can attack horizontally, vertically and diagonally.

- So initially we are having unattacked cells where we need to place queens. Let's place the first queen at a cell , so now the number of unattacked cells is reduced, and number of queens to be placed is . Place the next queen at some unattacked cell. This again reduces the number of unattacked cells and number of queens to be placed becomes . Continue doing this, as long as following conditions hold.
  - The number of unattacked cells is not .
  - The number of queens to be placed is not .
- If the number of queens to be placed becomes , then it's over, we found a solution. But if the number of unattacked cells become , then we need to backtrack, i.e. remove the last placed queen from its current cell, and place it at some other cell. We do this recursively.
  Complete algorithm is given below:

```javascript
is_attacked( x, y, board[][], N)
    //checking for row and column
    if any cell in xth row is 1
        return true
    if any cell in yth column is 1
        return true

    //checking for diagonals
    if any cell (p, q) having p+q = x+y is 1
        return true
    if any cell (p, q) having p-q = x-y is 1
        return true
    return false


N-Queens( board[][], N )
    if N is 0                     //All queens have been placed
        return true
    for i = 1 to N {
        for j = 1 to N {
            if is_attacked(i, j, board, N) is true
                skip it and move to next cell
            board[i][j] = 1            //Place current queen at cell (i,j)
            if N-Queens( board, N-1) is true    // Solve subproblem
                return true                   // if solution is found return true
            board[i][j] = 0            /* if solution is not found undo whatever changes
                                       were made i.e., remove  current queen from (i,j)*/
        }
    }
    return false
```

- Optimized solution

```csharp

  /* ld is an array where its indices indicate row-col+N-1
  (N-1) is for shifting the difference to store negative
  indices */
  static int[] ld = new int[30];

  /* rd is an array where its indices indicate row+col
  and used to check whether a queen can be placed on
  right diagonal or not*/
  static int[] rd = new int[30];

  /*column array where its indices indicates column and
  used to check whether a queen can be placed in that
  row or not*/
  static int[] cl = new int[30];
  static bool solveNQUtil(int[,] board, int col)
        {
            /* base case: If all queens are placed
            then return true */
            if (col >= N)
                return true;

            /* Consider this column and try placing
            this queen in all rows one by one */
            for (int i = 0; i < N; i++)
            {

                /* Check if the queen can be placed on
                board[i,col] */
                /* A check if a queen can be placed on
                board[row,col].We just need to check
                ld[row-col+n-1] and rd[row+coln] where
                ld and rd are for left and right
                diagonal respectively*/
                if ((ld[i - col + N - 1] != 1 &&
                     rd[i + col] != 1) && cl[i] != 1)
                {
                    /* Place this queen in board[i,col] */
                    board[i, col] = 1;
                    ld[i - col + N - 1] =
                    rd[i + col] = cl[i] = 1;

                    /* recur to place rest of the queens */
                    if (solveNQUtil(board, col + 1))
                        return true;

                    /* If placing queen in board[i,col]
                    doesn't lead to a solution, then
                    remove queen from board[i,col] */
                    board[i, col] = 0; // BACKTRACK
                    ld[i - col + N - 1] =
                    rd[i + col] = cl[i] = 0;
                }
            }

            /* If the queen cannot be placed in any row in
                this colum col then return false */
            return false;
        }
```

- References:
- https://www.geeksforgeeks.org/n-queen-problem-backtracking-3/
- https://www.hackerearth.com/practice/basic-programming/recursion/recursion-and-backtracking/tutorial/