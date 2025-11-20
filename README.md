class Outer {
 void display() {
 System.out.println("This is the display() method of the outer class.");
 }
 class Inner {
 void display() {
 System.out.println("This is the display() method of the inner class.");
 }
 }
}
public class Main {
 public static void main(String[] args) {
 Outer outer = new Outer();
 // Calling the display() method of the outer class
 outer.display();
 // Creating an instance of the inner class and calling its display() method
 Outer.Inner inner = outer.new Inner();
 inner.display();
 }
}
