# Tic-Tac-Toe-Game
 I  have successfully completed task 1 of  C developer internship under Inter Crowd  Task 1: BirthdayListProgram.    IDE used - Visual studio code .I would like to thank Intern Crowd te group.
#include <stdio.h>

// Function to draw the Tic-Tac-Toe board
void drawBoard(char board[3][3]) {
    printf("-------------\n");
    for (int i = 0; i < 3; i++) {
        printf("| %c | %c | %c |\n", board[i][0], board[i][1], board[i][2]);
        printf("-------------\n");
    }
}

// Function to check if the game has been won
int checkWin(char board[3][3], char symbol) {
    // Check rows
    for (int i = 0; i < 3; i++) {
        if (board[i][0] == symbol && board[i][1] == symbol && board[i][2] == symbol)
            return 1;
    }

    // Check columns
    for (int i = 0; i < 3; i++) {
        if (board[0][i] == symbol && board[1][i] == symbol && board[2][i] == symbol)
            return 1;
    }

    // Check diagonals
    if (board[0][0] == symbol && board[1][1] == symbol && board[2][2] == symbol)
        return 1;

    if (board[0][2] == symbol && board[1][1] == symbol && board[2][0] == symbol)
        return 1;

    return 0;
}

int main() {
    char board[3][3] = { { ' ', ' ', ' ' }, { ' ', ' ', ' ' }, { ' ', ' ', ' ' } };
    int row, col;
    char currentPlayer = 'X';
    int moves = 0;

    printf("Tic-Tac-Toe Game\n");
    printf("Player 1: X | Player 2: O\n");
    printf("-------------\n");
    printf("| 1 | 2 | 3 |\n");
    printf("-------------\n");
    printf("| 4 | 5 | 6 |\n");
    printf("-------------\n");
    printf("| 7 | 8 | 9 |\n");
    printf("-------------\n");

    while (1) {
        printf("Player %c's turn. Enter the position (1-9): ", currentPlayer);
        scanf("%d", &moves);
        row = (moves - 1) / 3;
        col = (moves - 1) % 3;

        if (board[row][col] == ' ') {
            board[row][col] = currentPlayer;
            drawBoard(board);

            if (checkWin(board, currentPlayer)) {
                printf("Player %c wins!\n", currentPlayer);
                break;
            }

            moves++;
            if (moves > 9) {
                printf("It's a draw!\n");
                break;
            }

            currentPlayer = (currentPlayer == 'X') ? 'O' : 'X';
        } else {
            printf("Invalid move. Try again.\n");
        }
    }

    return 0;
}
