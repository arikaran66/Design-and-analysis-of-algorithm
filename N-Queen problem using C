[24bcsl03@mepcolinux ex8]$cat nqueen.c
#include <stdio.h>
#define MAX_SIZE 10
int board[MAX_SIZE][MAX_SIZE];
int N;
int solutionCount = 0; 
void printSolution() {
    printf("\nSolution %d:\n", ++solutionCount);
    for (int i = 0; i < N; i++) {
        for (int j = 0; j < N; j++)
            printf("%c ", board[i][j] ? 'Q' : '.'); // Using Q and . for clarity
        printf("\n");
    }
}
int isSafe(int row, int col) {
    int i, j;
    for (i = 0; i < col; i++)
        if (board[row][i])
            return 0;
    for (i = row, j = col; i >= 0 && j >= 0; i--, j--)
        if (board[i][j])
            return 0;
    for (i = row, j = col; j >= 0 && i < N; i++, j--)
        if (board[i][j])
            return 0;
    return 1;
}
void solveNQ(int col) {
    if (col >= N) {
        printSolution();
        return;
    }
    for (int i = 0; i < N; i++) {
        if (isSafe(i, col)) {
            board[i][col] = 1;
            solveNQ(col + 1);
            board[i][col] = 0;
        }
    }
}
int main() {
    printf("Enter the size of the chessboard (up to %d): ", MAX_SIZE);
    if (scanf("%d", &N) != 1 || N > MAX_SIZE) {
        printf("Invalid input.\n");
        return 0;
    }
    solveNQ(0);
    if (solutionCount == 0) {
        printf("No solution exists for N = %d\n", N);
    } else {
        printf("\nTotal solution sets found: %d\n", solutionCount);
    }
    return 0;
}
