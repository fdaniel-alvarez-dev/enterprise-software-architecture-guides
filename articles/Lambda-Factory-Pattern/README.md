GitHub Repository Structure
/Lambda-Factory-Pattern/
├── README.md              # Problem statement, solution explanation, diagram
├── src/
│   ├── Shape.java         # Interface for shapes
│   ├── Circle.java        # Circle class
│   ├── Rectangle.java     # Rectangle class
│   ├── Square.java        # Square class
│   ├── ShapeFactory.java  # Java 8 Lambda-based factory
└── diagram.mmd            # Mermaid flowchart of factory process

I'll now create the full README.md, Java solution, and Mermaid diagram. 🚀
Factory Pattern Using Java 8 Lambdas
Problem Statement
Your task is to implement a Factory Pattern using Java 8 Lambdas, enabling dynamic object creation. The system should:
    1. Define a Shape interface (Circle, Rectangle, Square implementations).
    2. Implement a Lambda-based Factory for creating shapes.
    3. Return the correct shape based on the input.
Example Usage
Shape circle = ShapeFactory.getShape("circle");
circle.draw();

Expected Output
Drawing a Circle

Solution Explanation
We use Java 8 Lambdas to simplify the Factory Pattern:
    1. Create a functional interface for different shape types.
    2. Use a Map of lambdas to return the correct shape dynamically.
    3. Replace if-else or switch-case logic with clean, maintainable code.
Java 8+ Solution
import java.util.Map;
import java.util.function.Supplier;

interface Shape {
    void draw();
}

class Circle implements Shape {
    public void draw() { System.out.println("Drawing a Circle"); }
}

class Rectangle implements Shape {
    public void draw() { System.out.println("Drawing a Rectangle"); }
}

class Square implements Shape {
    public void draw() { System.out.println("Drawing a Square"); }
}

class ShapeFactory {
    private static final Map<String, Supplier<Shape>> shapeMap = Map.of(
        "circle", Circle::new,
        "rectangle", Rectangle::new,
        "square", Square::new
    );

    public static Shape getShape(String shapeType) {
        return shapeMap.getOrDefault(shapeType.toLowerCase(), () -> {
            throw new IllegalArgumentException("Unknown shape type: " + shapeType);
        }).get();
    }
}

public class FactoryPatternExample {
    public static void main(String[] args) {
        Shape shape = ShapeFactory.getShape("circle");
        shape.draw();
    }
}
