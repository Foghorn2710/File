// Abstract methods to be implemented by subclasses
 public abstract double calculateArea();
 public abstract double calculatePerimeter();
}
class Circle extends Shape {
 private double radius;
 // Constructor for Circle
 public Circle(double radius) {
 this.radius = radius;
 }
 @Override
 public double calculateArea() {
 return Math.PI * radius * radius;
 }
 @Override
 public double calculatePerimeter() {
 return 2 * Math.PI * radius;
 }
}
class Triangle extends Shape {
 private double side1;
 private double side2;
 private double side3;
 // Constructor for Triangle
 public Triangle(double side1, double side2, double side3) {
 this.side2 = side2;
 this.side3 = side3;
 }
 @Override
 public double calculateArea() {
 // Using Heron's formula to calculate area of a triangle
 double s = (side1 + side2 + side3) / 2;
 return Math.sqrt(s * (s - side1) * (s - side2) * (s - side3));
 }
 @Override
 public double calculatePerimeter() {
 return side1 + side2 + side3;
 }
}
public class Main {
 public static void main(String[] args) {
 // Creating instances of Circle and Triangle
 Circle circle = new Circle(5);
 Triangle triangle = new Triangle(3, 4, 5);
 // Calculating and displaying area and perimeter for Circle
 System.out.println("Circle - Area: " + circle.calculateArea());
 System.out.println("Circle - Perimeter: " + circle.calculatePerimeter());
 // Calculating and displaying area and perimeter for Triangle
 System.out.println("Triangle - Area: " + triangle.calculateArea());
 System.out.println("Triangle - Perimeter: " + triangle.calculatePerimeter());}}
