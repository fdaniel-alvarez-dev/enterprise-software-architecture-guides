GitHub Repository Structure
/Java-Streams-Filtering/
├── README.md          # Problem statement, solution explanation, diagram
├── src/
│   ├── Product.java   # Product class definition
│   ├── StreamExample.java  # Java 8 Streams solution
└── diagram.mmd        # Mermaid flowchart of the logic

Generating the GitHub-Ready Content
I'll create the full README.md, Java solution, and Mermaid diagram now. 🚀
Java 8 Streams - Filtering & Mapping
Problem Statement
Your task is to filter a list of products where the price is greater than $100 and return only their names using Java 8 Streams.
Example Input
List<Product> products = Arrays.asList(
    new Product("Laptop", 1200),
    new Product("Phone", 800),
    new Product("Mouse", 50),
    new Product("Keyboard", 150)
);
Expected Output
[Laptop, Phone, Keyboard]

Solution Explanation
We use Streams API to:
    1. Filter products with price > 100.
    2. Map each product to its name.
    3. Collect results into a List<String>.
Java 8 Solution
import java.util.*;
import java.util.stream.Collectors;

class Product {
    String name;
    double price;

    Product(String name, double price) {
        this.name = name;
        this.price = price;
    }
    public String getName() { return name; }
    public double getPrice() { return price; }
}

public class StreamExample {
    public static void main(String[] args) {
        List<Product> products = Arrays.asList(
            new Product("Laptop", 1200),
            new Product("Phone", 800),
            new Product("Mouse", 50),
            new Product("Keyboard", 150)
        );

        List<String> filteredProducts = products.stream()
            .filter(p -> p.getPrice() > 100) // Step 1: Filter
            .map(Product::getName)           // Step 2: Map to Name
            .collect(Collectors.toList());   // Step 3: Collect

        System.out.println(filteredProducts);
    }
}
