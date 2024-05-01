# tic-tac-toe-game
#include <stdio.h>

char cell1 = ' ';
char cell2 = ' ';
char cell3 = ' ';
char cell4 = ' ';
char cell5 = ' ';
char cell6 = ' ';
char cell7 = ' ';
char cell8 = ' ';
char cell9 = ' ';

void print_board() {
    printf("\n");
    printf(" %c | %c | %c\n", cell1, cell2, cell3);
    printf("---+---+---\n");
    printf(" %c | %c | %c\n", cell4, cell5, cell6);
    printf("---+---+---\n");
    printf(" %c | %c | %c\n", cell7, cell8, cell9);
    printf("\n");
}

int check_winner() {
    // Check rows
    if((cell1 == cell2 && cell2 == cell3 && cell1 != ' ') ||
       (cell4 == cell5 && cell5 == cell6 && cell4 != ' ') ||
       (cell7 == cell8 && cell8 == cell9 && cell7 != ' ')) {
        return 1;
    }
    
    // Check columns
    if((cell1 == cell4 && cell4 == cell7 && cell1 != ' ') ||
       (cell2 == cell5 && cell5 == cell8 && cell2 != ' ') ||
       (cell3 == cell6 && cell6 == cell9 && cell3 != ' ')) {
        return 1;
    }
    
    // Check diagonals
    if((cell1 == cell5 && cell5 == cell9 && cell1 != ' ') ||
       (cell3 == cell5 && cell5 == cell7 && cell3 != ' ')) {
        return 1;
    }
    
    return 0;
}

int main(void) {
    int i, position;
    
    for (i = 0; i < 9; i++) {
        if (i % 2 == 0) {
            printf("Player X, it's your turn.\n");
        } else {
            printf("Player O, it's your turn.\n");
        }
        
        printf("Enter position (1-9): ");
        scanf("%d", &position);
        
        if (position < 1 || position > 9) {
            printf("Invalid position. Enter a number between 1 and 9.\n");
            i--;
            continue;
        }
        
        if (position == 1 && cell1 == ' ') {
            cell1 = (i % 2 == 0) ? 'X' : 'O';
        } else if (position == 2 && cell2 == ' ') {
            cell2 = (i % 2 == 0) ? 'X' : 'O';
        } else if (position == 3 && cell3 == ' ') {
            cell3 = (i % 2 == 0) ? 'X' : 'O';
        } else if (position == 4 && cell4 == ' ') {
            cell4 = (i % 2 == 0) ? 'X' : 'O';
        } else if (position == 5 && cell5 == ' ') {
            cell5 = (i % 2 == 0) ? 'X' : 'O';
        } else if (position == 6 && cell6 == ' ') {
            cell6 = (i % 2 == 0) ? 'X' : 'O';
        } else if (position == 7 && cell7 == ' ') {
            cell7 = (i % 2 == 0) ? 'X' : 'O';
        } else if (position == 8 && cell8 == ' ') {
            cell8 = (i % 2 == 0) ? 'X' : 'O';
        } else if (position == 9 && cell9 == ' ') {
            cell9 = (i % 2 == 0) ? 'X' : 'O';
        } else {
            printf("Position already taken. Try again.\n");
            i--;
            continue;
        }
        
        print_board();
        
        if (check_winner()) {
            if (i % 2 == 0) {
                printf("Player X wins!\n");
            } else {
                printf("Player O wins!\n");
            }
            return 0;
        }
    }

    printf("It's a draw!\n");

    return 0;
}
