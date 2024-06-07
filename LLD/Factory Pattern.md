- Factory Pattern diagram:  ![](Factory%20Pattern.png)

- Code:
```Java
  //Shape class
public interface Shape {
	void draw();
}

public class Circle implements Shape {
	void draw(){
		//draws circle
		System.out.println("circle");
	}
}

public class Rectangle implements Shape {
	void draw(){
		//draws rectangle
		System.out.println("rectangle");
	}
}

public class Triangle implements Shape {
	void draw(){
		//draws triangle
		System.out.println("triangle");
	}
}
```

```Java
//Factory class
public class ShapeFactory {
	Shape getShape(String inputShape){
		switch(inputShape){
			case "Circle": return new Circle();
			case "Rectangle": return new Rectangle();
			case "Triangle": return new Triangle();
			default: return null;
		}
	}
}
```

```Java
//Main method
public class void main(){
	ShapeFactory shapeFactoryObj = new ShapeFactory();
	Shape shapeObj = shapeFactoryObj.getShape("Circle");
	shapeObj.draw();
}
```