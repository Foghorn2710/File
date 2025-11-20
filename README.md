class DivisionByZeroException extends Exception {
 public DivisionByZeroException(String message) {
 super(message);
 }
}
public class Main {
 public static void main(String[] args) {
 try {
 int numerator = 10;
 int denominator = 0;
 // Perform division and throw exception if denominator is zero
 if (denominator == 0) {
 throw new DivisionByZeroException("Division by zero error!");
 }
 int result = numerator / denominator;
 System.out.println("Result of division: " + result);
 } catch (DivisionByZeroException e) {
 System.out.println("Caught DivisionByZeroException: " + e.getMessage());
 } catch (ArithmeticException e) {
 System.out.println("Caught ArithmeticException: " + e.getMessage());
 } finally {
 System.out.println("Finally block executed.");
 }
 }
}
