- SOLID principle
	- S - Single Responsibility Principle
	- O - Open for extension, closed for modification
	- L - Liskov Principle
	- I - Interface Segregation
	- D - Dependency Inversion
- **Why do we need them** (Advantages):
	- Avoid duplication of code
	- Easy to maintain
	- Easy to understand
	- Flexible software
	- Reduce complexity

- **The S**: Class should have only one reason to change or a single responsibility
  ```Java
  class Invoice {
	private Marker marker
	private int qty;

	public Invoice(Marker marker, int qty){
		this.marker = marker;
		this.qty = qty;
	}

	public int calculateTotal() {
		int price = ((marker.price) * this.qty);
		return price;
	}

	public void printInvoice(){
		//print the invoice
	}

	public void saveToDB(){
		//save the data to DB
	}
}
```
❌ This class violates the single responsibility principle as there can be multiple reason to modify this class. For example: Printing invoice logic needs to changed, or tax calculation logic needs to be changed.

✅ This can be corrected by breaking the class and giving each a single responsibilty.
```Java
class Invoice {
	private Marker marker
	private int qty;

	public Invoice(Marker marker, int qty){
		this.marker = marker;
		this.qty = qty;
	}

	public int calculateTotal() {
		int price = ((marker.price) * this.qty);
		return price;
	}
}

class InvoiceDao {

	public InvoiceDao(Invoice invoice){
		this.invoice = invoice;
	}

	public void saveToDB(){
		//save the data to DB
	}
}

class InvoicePrinter {

	public InvoicePrinter(Invoice invoice){
		this.invoice = invoice;
	}

	public void printInvoice(){
		//print the invoice
	}
}
```

- **The O** 🚀: Open for extension, closed for modification
  ```Java
  class InvoiceDao {

	public InvoiceDao(Invoice invoice){
		this.invoice = invoice;
	}

	public void saveToDB(){
		//save the data to DB
	}

	public void saveToFile(){
		//save the data to file
	}
}
```
❌ Above implementation will cause an already live code to change if we add ```saveToFile()``` or any other saving function is introduced.

✅ To make this implementation correct, we implement the interface or saving method and extend it whenever required.
```Java
interface InvoiceDao {
	public void save(Invoice invoice);
}

class DatabaseInvoiceDao implements InvoiceDao {
	public void saveToDB(){
		//save the data to DB
	}
}

class FileInvoiceDao implements InvoiceDao {
	public void saveToFile(){
		//save the data to file
	}
}
```

- **The L** 🚀: If class B is a subtype of class A, then we should be able to replace object A with B without breaking the behaviour of the program. In simple words, the subclass should extend the capability if the parent class and not narrow it down.

  ```Java
  interface Bike {
	void turnOnEngine();
	void accelerate();
}

class Motorcycle implements Bike {
	boolean isEngineOn;
	int speed;

	public void turnOnEngine(){
		isEngineOn = true;
	}

	public void accelerate(){
		speed *= 10;
	}
}

class Bicycle implements Bike {
	public void turnOnEngine(){
		throw new AssertionError("Engine not present");
	}

	public void accelerate(){
		speed *= 2;
	}
}
```
❌ This violates the Liskov principle as when Bike(parent class) class is replaced by Bicycle(subtype/ child class), the code will error when ```turnOnEngine()``` function is called.

✅ To avoid this keep only generic methods in parent class. For ex, here there can be a ```Vehicle``` class which has ```accelerate``` function and the remaining function can be moved to ``Bike
class which extends the ```Vehicle``` class.

- **The I** 🚀: Interface should be such that client should not implement unnecessary functions they do not need
  ```Java
  interface RestaurantEmployee {
	void washDishes();
	void serveToCustomers();
	void cookFood();
}

class waiter implements RestaurantEmployee {
	
	public void washDishes(){
		//not a waiter's job
	}

	public void serveToCustomers(){
		//waiter's job
		System.out.println("Serving the customer");
	}

	public void cookFood(){
		//not a waiter's job
	}
}
```
❌ This implementation is again wrong as it is not a waiter's job to
```cookFood()``` and ```washDishes()```.

✅ Correct Implementation:
```Java
interface WaiterInterface {
	void serveToCustomers();
	void takeOrder();
}

class Waiter implements WaiterInterface {
	
	public void serveToCustomers(){
		//waiter's job
		System.out.println("Serving the customer");
	}

	public void takeOrder(){
		//waiter's job
		System.out.println("Taking order");
	}
}

interface ChefInterface {
	void cookFood();
	void decideMenu();
}

class Chef implements ChefInterface {
	
	public void cookFood(){
		//chef's job
		System.out.println("Cooking food");
	}

	public void decideMenu(){
		//waiter's job
		System.out.println("Deciding Menu");
	}
}
```

- **The D** 🚀: Class should depend on interface rather than concrete class.
  ```Java
  class MacBook {
	private final WiredKeyboard keyboard;
	private final WiredMouse mouse;

	public MacBook(){
		keyboard = new WiredKeyboard(); //Concrete class assignment
		mouse = new WiredMouse();
	}
}
```
❌ Tightly couple with concrete class.

✅ Can be corrected by using a constructor and interface over a concrete class.
```Java
class MacBook {
	private final Keyboard keyboard;
	private final Mouse mouse;

	public MacBook(Keyboard keyboard, Mouse mouse){
		this.keyboard = keyboard; //Interface assignment
		this.mouse = mouse;
	}
}
```

