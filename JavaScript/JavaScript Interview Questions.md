1. What is an Immediately Invoked Function in JavaScript?
2. **Strict Mode**:
	1. Duplicate arguments are not allowed by developers.
	2. In strict mode, you won't be able to use the JavaScript keyword as a parameter or function name.
	3. The 'use strict' keyword is used to define strict mode at the start of the script. Strict mode is supported by all browsers.
	4. Engineers will not be allowed to create global variables in 'Strict Mode.
3. **Higher Order Function:** Functions that operate on other functions, either by taking them as arguments or by returning them, are called higher-order functions.
	Example:
		
		1. function higherOrder(fn) { 
			fn(); 
		} 
		higherOrder(function() { console.log("Hello world") });

		2. function higherOrder2() { 
			return function() { 
				return "Do something"; 
			} 
		} 
		var x = higherOrder2(); x() // Returns "Do something"
		
4. Self-invocation function: Without being requested, a self-invoking expression is automatically invoked (initiated). If a function expression is followed by (), it will execute automatically. *A function declaration cannot be invoked by itself*.
5. Call() vs apply() vs bind()
6. **Currying is an advanced technique to transform a function of arguments n, to n functions of one or fewer arguments.**
   Example:
   ```JS
   function add (a) { 
	   return function(b){ 
		   return a + b; 
		   } 
		} 
		
	add(3)(4)
	```
7. Global, local/function, Block Scope
8. **Closure**: Function bundled with variables of lexical scope.
9. **Making a variable *private* using closure:**
```JS
   function randomFunc(){ 
	   var obj1 = {name:"Vivian", age:45}; 
	   
	   return function(){ 
		   console.log(obj1.name + " is "+ "awesome"); // Has access to obj1 even when the randomFunc function is executed 
		} 
	
	} 
	
	var initialiseClosure = randomFunc(); // Returns a function 
	initialiseClosure();
```
10. What are object prototypes: - **A prototype is a blueprint of an object. The prototype** allows us to use properties and methods on an object even if the properties and methods do not exist on the current object.
    Example: Inbuilt functions on array and other data structures.
11. Implementation of Memoization using closure:
```javascript
function memoizedAddTo256(){ 
	var cache = {}; 
	return function(num){ 
		if(num in cache){ 
			console.log("cached value"); 
			return cache[num] 
		} else{ 
			cache[num] = num + 256; 
			return cache[num]; 
		} 
	} 
} 

var memoizedFunc = memoizedAddTo256(); 
memoizedFunc(20); // Normal 
return memoizedFunc(20); // Cached return   
```
12. DOM(Data Object Model) vs BOM(Browser Object Model)
13. Function Expression VS function statement
14. **Arrow function**: By general definition, **this** keyword always refers to the object that is calling the function. In the arrow functions, there is no binding of **this** keyword. This keyword inside an arrow function does not refer to the object calling it. It rather inherits its value from the parent scope which is the window object in this case.
15. Prototype Design pattern
16. Scope difference of var, const, let:

		|keyword          |const|let|var|
		|-----------------|-----|---|---|
		|global scope     |no   |no |yes|
		|function scope   |yes  |yes|yes|
		|block scope      |yes  |yes|no |
		|can be reassigned|no   |yes|yes|
 
17. Rest Parameter VS Spread operator
18. The spread operator is commonly used to make deep copies of JS objects. When we have nested arrays or nested data in an object, the spread operator makes a deep copy of top-level data and a shallow copy of the nested data.
19. Promises and its state: Pending, Fulfilled, Rejected, Settled.
20. Classes in JS: 
	-  Unlike functions, classes are not hoisted. A class cannot be used before it is declared.
	- A class can inherit properties and methods from other classes by using the extend keyword.
	- All the syntaxes inside the class must follow the strict mode(‘use strict’) of javascript. An error will be thrown if the strict mode rules are not followed.
21. Generator function
22. Weakset in JS:
	- Weakset contains only objects and no other type.
	- An object inside the weakset is referenced weakly. This means, that if the object inside the weakset does not have a reference, it will be garbage collected.
	- Unlike Set, WeakSet only has three methods, **add()** , **delete()** and **has()**.
23. WeakMap in JS:
    - The keys and values in weakmap should always be an object.
	- If there are no references to the object, the object will be garbage collected.
24. Prototypal vs Classical Inheritance
25. Temporal Dead Zone
26. **Types of desgin patterns:**
    - **Creational Design Pattern:** The object generation mechanism is addressed by the JavaScript Creational Design Pattern. They aim to make items that are appropriate for a certain scenario.
	- **Structural Design Pattern:** The JavaScript Structural Design Pattern explains how the classes and objects we've generated so far can be combined to construct bigger frameworks. This pattern makes it easier to create relationships between items by defining a straightforward way to do so.
	- **Behavioral Design Pattern:** This design pattern highlights typical patterns of communication between objects in JavaScript. As a result, the communication may be carried out with greater freedom.
27. Is JavaScript a pass-by-reference or pass-by-value language?
28. Difference between Async/Await and Generators usage to achieve the same functionality.
29. Primitive data types in JS: Boolean, Undefined, NULL, Number, String
30. Deferred Script in JS: The processing of HTML code while the page loads are disabled by nature till the script hasn't halted. Your page will be affected if your network is a bit slow, or if the script is very hefty. When you use Deferred, the script waits for the HTML parser to finish before executing it. This reduces the time it takes for web pages to load, allowing them to appear more quickly.
31. 
