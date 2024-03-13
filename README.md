# SudokuSolver

## Synopsis
For fast solveing of Sudoku Puzzles.

## Motivation
I was motivated to do this to see more about how recursive programming can help.

## How to run
Download the project and start it up.

## Code Example
'''
 public static boolean solveSudoku(int[][] grid) {
        int[] emptyCell = findEmptyCell(grid);

        if (emptyCell == null) {
            return true; 
        }

        int row = emptyCell[0];
        int col = emptyCell[1];

        for (int num = 1; num <= 9; num++) {
            if (isValidMove(grid, row, col, num)) {
                grid[row][col] = num;

                if (solveSudoku(grid)) {
                    return true; 
                }

                grid[row][col] = 0; 
            }
        }

        return false; 
    }

    private static int[] findEmptyCell(int[][] grid) {
        for (int row = 0; row < 9; row++) {
            for (int col = 0; col < 9; col++) {
                if (grid[row][col] == 0) {
                    return new int[]{row, col};
                }
            }
        }
        return null;
    }

    private static boolean isValidMove(int[][] grid, int row, int col, int num) {
        // Check row and column
        for (int i = 0; i < 9; i++) {
            if (grid[row][i] == num || grid[i][col] == num) {
                return false;
            }
        }

        // Check subgrid
        int subgridStartRow = row - row % 3;
        int subgridStartCol = col - col % 3;
        for (int i = 0; i < 3; i++) {
            for (int j = 0; j < 3; j++) {
                if (grid[subgridStartRow + i][subgridStartCol + j] == num) {
                    return false;
                }
            }
        }

        return true;
    }
    '''
## Tests
There are two parts to my Junite test one part gives the code a Sudoku puzzle that is solvable and one that is not solvable.
