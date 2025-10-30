class MyPoint {
 private int x;
 private int y;
 public MyPoint() {
 this(0, 0); // Default constructor setting coordinates to (0, 0)
 }
 public MyPoint(int x, int y) {
 this.x = x;
 this.y = y;
 }
 public void setXY(int x, int y) {
 this.x = x;
 this.y = y;
 }
 public int[] getXY() {
 return new int[]{x, y};
 }
 public String toString() {
 return "(" + x + ", " + y + ")";
 }
 public double distance(int x, int y) {
 int xDiff = this.x - x;
 int yDiff = this.y - y;
 return Math.sqrt(xDiff * xDiff + yDiff * yDiff);
 }
 public double distance(MyPoint another) {
 return distance(another.x, another.y);
 }
 public double distance() {
 return distance(0, 0);
 }
}
public class TestMyPoint {
 public static void main(String[] args) {
 MyPoint point1 = new MyPoint();
 MyPoint point2 = new MyPoint(3, 4);
 // Testing setXY() method
 point1.setXY(5, 6);
 // Testing getXY() method
 int[] coordinates = point1.getXY();
 System.out.println("Point 1 coordinates: (" + coordinates[0] + ", " + coordinates[1] + ")");
 // Testing toString() method
 System.out.println("Point 2: " + point2);
 // Testing distance() methods
 System.out.println("Distance between Point 1 and Point 2: " + point1.distance(point2));
 System.out.println("Distance from Point 1 to origin: " + point1.distance());}}
