import java.util.Scanner;
public class AddMatrices {
 public static void main(String[] args) {
 if (args.length != 1) {
 System.out.println("Please provide the order of the matrix as a command-line argument.");
 return;
 }
 int N = 0;
 try {
 N = Integer.parseInt(args[0]);
 } catch (NumberFormatException e) {
 System.out.println("Please provide a valid integer for the order of the matrix.");
 return;
 }
 if (N <= 0) {
 System.out.println("Please provide a positive value for the order of the matrix.");
 return;
 }
 int[][] matrixA = new int[N][N];
 int[][] matrixB = new int[N][N];
 int[][] sumMatrix = new int[N][N];
 Scanner scanner = new Scanner(System.in);
 System.out.println("Enter the elements of the first matrix:");
 enterMatrixElements(matrixA, scanner);
 System.out.println("Enter the elements of the second matrix:");
 enterMatrixElements(matrixB, scanner);
 addMatrices(matrixA, matrixB, sumMatrix, N);
 System.out.println("The sum of the matrices is:");
 displayMatrix(sumMatrix);
 }
 public static void enterMatrixElements(int[][] matrix, Scanner scanner) {
 for (int i = 0; i < matrix.length; i++) {
 for (int j = 0; j < matrix[0].length; j++) {
 System.out.print("Enter element [" + i + "][" + j + "]: ");
 matrix[i][j] = scanner.nextInt();
 }
 }
 }
 public static void addMatrices(int[][] matrixA, int[][] matrixB, int[][] sumMatrix, int N) {
 for (int i = 0; i < N; i++) {
 for (int j = 0; j < N; j++) {
 sumMatrix[i][j] = matrixA[i][j] + matrixB[i][j];
 }
 }
 }
 public static void displayMatrix(int[][] matrix) {
 for (int[] row : matrix) {
 for (int element : row) {
 System.out.print(element + " ");
 }
 System.out.println();
 }
 }
}
