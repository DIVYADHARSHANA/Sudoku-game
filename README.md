# Sudoku-game
import java.util.Scanner;

public class SudokuGame {
    static int[][] puzzle = {
        {5, 3, 0, 0, 7, 0, 0, 0, 0},
        {6, 0, 0, 1, 9, 5, 0, 0, 0},
        {0, 9, 8, 0, 0, 0, 0, 6, 0},
        {8, 0, 0, 0, 6, 0, 0, 0, 3},
        {4, 0, 0, 8, 0, 3, 0, 0, 1},
        {7, 0, 0, 0, 2, 0, 0, 0, 6},
        {0, 6, 0, 0, 0, 0, 2, 8, 0},
        {0, 0, 0, 4, 1, 9, 0, 0, 5},
        {0, 0, 0, 0, 8, 0, 0, 7, 9}
    };

    static int[][] solution = {
        {5, 3, 4, 6, 7, 8, 9, 1, 2},
        {6, 7, 2, 1, 9, 5, 3, 4, 8},
        {1, 9, 8, 3, 4, 2, 5, 6, 7},
        {8, 5, 9, 7, 6, 1, 4, 2, 3},
        {4, 2, 6, 8, 5, 3, 7, 9, 1},
        {7, 1, 3, 9, 2, 4, 8, 5, 6},
        {9, 6, 1, 5, 3, 7, 2, 8, 4},
        {2, 8, 7, 4, 1, 9, 6, 3, 5},
        {3, 4, 5, 2, 8, 6, 1, 7, 9}
    };

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int row, col, num;

        while (true) {
            printBoard();

            System.out.print("Enter row (0-8), column (0-8), and number (1-9): ");
            row = sc.nextInt();
            col = sc.nextInt();
            num = sc.nextInt();

            if (puzzle[row][col] != 0) {
                System.out.println("Cell already filled! Try a different one.");
                continue;
            }

            if (solution[row][col] == num) {
                puzzle[row][col] = num;
                System.out.println("Correct move!");
            } else {
                System.out.println("Incorrect move!");
            }

            if (isComplete()) {
                printBoard();
                System.out.println("🎉 Congratulations! You completed the puzzle!");
                break;
            }
        }

        sc.close();
    }

    static void printBoard() {
        System.out.println("\nCurrent Sudoku Board:");
        for (int i = 0; i < 9; i++) {
            if (i % 3 == 0) System.out.println("+-------+-------+-------+");
            for (int j = 0; j < 9; j++) {
                if (j % 3 == 0) System.out.print("| ");
                System.out.print(puzzle[i][j] == 0 ? ". " : puzzle[i][j] + " ");
            }
            System.out.println("|");
        }
        System.out.println("+-------+-------+-------+");
    }

    static boolean isComplete() {
        for (int i = 0; i < 9; i++)
            for (int j = 0; j < 9; j++)
                if (puzzle[i][j] == 0)
                    return false;
        return true;
    }
}
