# **Torus Render Project Documentation**

---

## **1. Overview**

The Torus Render project is a Java application that demonstrates a rotating 3D torus (donut shape) rendered as ASCII art. It uses mathematical concepts like 3D transformations, perspective projection, and dynamic shading to create a smooth animation. The project is built with Maven, making it easy to manage dependencies and generate an executable JAR file.

---

## **2. Features**

- **3D ASCII Art Rendering**: Displays a rotating torus in a graphical window using ASCII characters.
- **Dynamic Lighting**: Adjusts shading based on light direction for a realistic effect.
- **Smooth Animation**: Continuously updates the torus rotation using Java Swing.
- **Maven Build**: Easy setup and generation of an executable JAR file.

---

## **3. Mathematical Concepts**

### **3.1 Torus Parametric Equation**
A torus is defined by two parameters:
- \( i \): Angle around the small circular cross-section (tube radius).
- \( j \): Angle around the central axis (donut radius).

The parametric equations for a torus are:
\[
x = (R + r \cdot \cos(i)) \cdot \cos(j)
\]
\[
y = (R + r \cdot \cos(i)) \cdot \sin(j)
\]
\[
z = r \cdot \sin(i)
\]

Where:
- \( R \): Distance from the center of the torus to the center of the tube.
- \( r \): Radius of the tube.
- \( i, j \): Angles in radians.

### **3.2 3D Rotation**
To make the torus rotate, apply rotation transformations using rotation matrices for the \( x \)-axis and \( y \)-axis:

1. **Rotation about the \( x \)-axis**:
\[
x' = x
\]
\[
y' = y \cdot \cos(A) - z \cdot \sin(A)
\]
\[
z' = y \cdot \sin(A) + z \cdot \cos(A)
\]

2. **Rotation about the \( y \)-axis**:
\[
x'' = x' \cdot \cos(B) + z' \cdot \sin(B)
\]
\[
y'' = y'
\]
\[
z'' = -x' \cdot \sin(B) + z' \cdot \cos(B)
\]

Where:
- \( A \): Rotation angle around the \( x \)-axis.
- \( B \): Rotation angle around the \( y \)-axis.

### **3.3 Perspective Projection**
The 3D points of the torus are projected onto a 2D plane for rendering on the screen using perspective projection:
\[
D = \frac{1}{z'' + k}
\]
\[
x_{\text{screen}} = x'' \cdot D
\]
\[
y_{\text{screen}} = y'' \cdot D
\]

Where:
- \( D \): Depth factor, making closer points appear larger.
- \( k \): Constant to move the torus away from the viewer to avoid division by zero.

### **3.4 Lighting and Shading**
The shading is determined based on the surface normal and a virtual light direction. The brightness \( N \) of a point is calculated as:
\[
N = 8 \cdot ((f \cdot e - c \cdot d \cdot gA) \cdot m - c \cdot d \cdot e - f \cdot gA - l \cdot d \cdot n)
\]
The brightness is mapped to ASCII characters, where brighter points correspond to characters like `@` and darker points to `.`.

---

## **4. Project Structure**

### **4.1 Maven Directory Structure**
The project follows the standard Maven directory structure:
```
project-root/
├── pom.xml                # Maven configuration file
├── src/
│   ├── main/
│   │   ├── java/          # Java source code
│   │   │   └── AsciAnimation/
│   │   │       └── TorusAnimation.java
│   │   └── resources/     # Resource files (if any)
│   └── test/
│       └── java/          # Unit tests (if any)
└── target/                # Compiled classes and packaged JAR file
```

### **4.2 Important Files**
- **`pom.xml`**: Maven configuration file to manage dependencies and plugins.
- **`TorusAnimation.java`**: The main Java class implementing the rotating torus.

---

## **5. How to Build and Run**

### **5.1 Prerequisites**
- **Java Development Kit (JDK)**: Version 8 or higher.
- **Maven**: Ensure Maven is installed and added to your system's PATH.

### **5.2 Build the Project**
1. Navigate to the project root directory:
   ```bash
   cd /path/to/torusRender
   ```
2. Use Maven to clean and package the project:
   ```bash
   mvn clean package
   ```
   This will generate an executable JAR file in the `target/` directory.

### **5.3 Run the Application**
Run the generated JAR file:
```bash
java -jar target/torusRender-1.0-SNAPSHOT.jar
```

---

## **6. Key Features and Logic**

1. **Parametric Representation**:
   - The torus is represented mathematically using two angles \( i \) and \( j \).

2. **3D Transformations**:
   - The torus points are rotated in 3D space using trigonometric transformations.

3. **Perspective Projection**:
   - The 3D points are projected onto a 2D screen with depth scaling.

4. **Lighting and Shading**:
   - Brightness is calculated based on surface normals and mapped to ASCII characters.

5. **Smooth Rendering**:
   - Java Swing's `Timer` and `repaint()` are used to create continuous animation.

---

## **7. License**
This project is licensed under the MIT License. Feel free to use, modify, and distribute it.

---

## **8. Acknowledgments**
- **GitHub Documentation**: For guidance on SSH and repository management.
- **ASCII Art Tutorials**: For inspiration on rendering techniques.
- **Java Swing Framework**: For seamless rendering and animation support.

---

