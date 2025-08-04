# For Mid Semester Examination : 
## Q1). Benefit of OOP over Procedural Programming :
1.  **Modularity :**  Code is divided into objects(classes), making it easier to manage. 
2. **Reusability :** Code can be reused using inheritance - no need to rewrite common functionalities. 
3. **Encapsulation :** Data and functions are bundled together, reducing complexity and increasing security.
4. **Abstraction :** Hides internal implementation and shows only essential features. 
5. **Inheritance :** Promotes code reuse by allowing  class to inherit properties and methods from another. 
6. **Polymorphism :** Allows The same function to behave differently based on the object(method overloading/overriding). 
7. **Maintainability :** Easier to update and debug due to modular structure.
8. **Security :** Access modifiers (private, protected, public) control data access.


Here’s a quick **comparison table** between **OOP** and **Procedural Programming**:

|Feature|Object-Oriented Programming (OOP)|Procedural Programming|
|---|---|---|
|**Structure**|Based on objects and classes|Based on functions and procedures|
|**Modularity**|High – uses encapsulated objects|Low – functions are loosely structured|
|**Code Reusability**|Supports inheritance and polymorphism|Limited reusability, requires code duplication|
|**Encapsulation**|Yes – binds data and methods together|No – data and logic are separate|
|**Abstraction**|Supported using classes and interfaces|Limited or manual abstraction|
|**Security**|Better – access modifiers restrict access|Poor – global data can be accessed easily|
|**Maintainability**|Easier – modular and organized|Harder – tightly coupled code|
|**Real-world Modeling**|Strong – maps real-world entities easily|Weak – less intuitive mapping|
|**Flexibility**|High – supports method overriding/overloading|Low – rigid function behavior|


## Q2). Difference between class and objects with syntax : 

### Class : 
- It is bluepring/template for creating objects
- Defines properties (attributes) and methods (functions). 
```cpp
class Car {
public:
	string brand;
	void start() {
		cout << "Car started";
	}
}
```

### Object : 
- It is a real-world instance of a class.
- Uses class blueprint to access data and behavior.
```cpp
Car myCar;
myCar.brand = "BMW";
myCar.start();
```
### 🧠 **Key Points to Remember:**

| Basis       | Class                          | Object                       |
| ----------- | ------------------------------ | ---------------------------- |
| Definition  | Blueprint/template             | Instance of a class          |
| Memory      | No memory allocated            | Memory allocated on creation |
| Declaration | `class ClassName { ... };`     | `ClassName objName;`         |
| Usage       | Defines behavior and structure | Performs actions using class |
| Example     | `class Car { ... };`           | `Car myCar;`                 |

## Q3). Differentiate between constructor and Destructor : 

### Constructor : 
- It is a special method **Automatically called** when a object is created.
- It is used to initialize objects.
- we can define the class properties by creating constructor funciton. and it is created by naming the function same name as of class.
```cpp
class MyClass {
public:
	MyClass() {
		cout << "Constructor called";
	}
};
```

### Destructor : 
-  A special method **automatically called** when an object is destroyed.
- Used to release resources (memory, files, etc.). 

```cpp
class MyClass {
public:
	~MyClass() {
		cout << "Destructor called";
	}
}
```

### 🧠 **Key Points to Remember:**

|Feature|Constructor|Destructor|
|---|---|---|
|Purpose|Initializes an object|Cleans up before object is destroyed|
|Name|Same as class name|Same as class name with `~` prefix|
|Parameters|Can have parameters (overloaded)|Cannot have parameters|
|Return type|No return type|No return type|
|Overloading|Can be overloaded|Cannot be overloaded|
|Call Timing|Called when object is created|Called when object goes out of scope|
|Use Case|Initialize values, open files, etc.|Close files, free memory, etc.|


## Q4). Program to find the area and perimeter of circle using constructor : 
```cpp
##include <iostream>
#define PI 3.14159
using namespace std;

class Circle {
private:
	float radius;
public:
	// Constructor to initailize radius
	Circle(float r){
	radius = r
	}
	//Function to calculate area
	float getArea(){
		return PI * radius * radius;
	}
	//Function to calculate perimeter(circumference)
	float getPerimiter () {
		return 2 * PI * radius;
	}
};

int main() {
float r;
cout << "Enter the radius of circle";
cin << r;
//creating object and passing radius to constructor
Circle c(r);

cout << "Area of Circle = " << c.getArea() << endl;
cout << "Perimiter of Circle = " << c.getPerimeter() << endl;
return 0;
}
```
```handdrawn-ink
{
	"versionAtEmbed": "0.3.4",
	"filepath": "Ink/Drawing/2025.5.17 - 0.15am.drawing",
	"width": 350,
	"aspectRatio": 1.5277588323557496
}
```
## Q5). What is reference variable ? ***VVI*** 
 A reference variable is an alias (another name) for an existing variable.
### Key Points : 
1. Shares the same memory location as the original variable.
2. declared using **&** symbol.
3. Any change to the reference affects the original variable.
4. Must be initialized at the time of declaration.
```cpp
#include <iostream>
using namespace std;
int main(){
int a = 10;
int &ref = a; //ref is reference to a

cout << "x = " << x << endl;
cout << "ref = " << ref << endl;

ref = 20;
cout << "x = " << x << endl;
cout << "ref = " << ref << endl;

return 0;
```

### Advantages : 
- Function arguments (Pass by reference)
- Avoid data copying (faster)
- To return multiple values from a function

## Q6). Differentiate between Method overloading and overriding. 

| Feature              | Method Overloading                     | Method Overriding                           |
| -------------------- | -------------------------------------- | ------------------------------------------- |
| Definition           | Same method name, different parameters | Same method name and parameters             |
| Class Scope          | Within same class                      | Across base and derived class               |
| Inheritance Required | ❌ Not required                         | ✅ Required                                  |
| Polymorphism Type    | Compile-time                           | Run-time                                    |
| Parameters           | Must be different                      | Must be same                                |
| Return Type          | Can be same or different               | Usually same (required in strict languages) |
## Q). Short Note on 
#### 1. Friend Function : 
A friend function is a special function that is **not a member** of a class but still has access to its private and protected members.

- Declared using the keyword `friend`  inside the class.
- Defined outside the class like a normal function
- Not called with an object; it takes objects as parameters.
- Used when external functions need access to class internals.
```cpp
class Box {
private:
	int length;
public: 
	Box() { length = 10;}
	friend void showLength(Box b);  //Friend function declaration
};

void showLength(Box b) {    // Friend function definition
	 cout << "Length: " << b.length << endl;
}
```

#### 2. Virtual Function : 
It is a member function in a base class that you can override in a derived class using `virtual` keyword. 
- Declared using `virtual`  in the base class.
- Enables **runtime polymorphism**.
- Ensures the **derived class's version** is called via base class Pointer.
- Must be **overridden** in derived class for custom behavior. 
```cpp
class Base {
public:
    virtual void show() {
        cout << "Base class show" << endl;
    }
};

class Derived : public Base {
public:
    void show() override {
        cout << "Derived class show" << endl;
    }
};

int main() {
    Base* ptr;
    Derived d;
    ptr = &d;
    ptr->show();  // Calls Derived's show() due to virtual function
}

```

#### 3. Inline Function : 
It is a function where the code is expanded at the point of the function call, instead of making a traditional function call.
- Declared using the `inline` keyword before the function.
- Avoids overhead of function calls (especially for small functions).
- Compiler replaces the function call with actual code.
- useful for short and frequently called functions. 
```cpp
#include <iostream>
using namespace std;

inline int square(int x) {
	return x * x;
}

int main() {
	cout << "Square of 5: " << square(5); //output 25
	return 0;
}
```

#### 4. Abstraction : 
It is the process of **hiding internal details** and showing **only the essentials features** of an object to the user. 
- Focuses on **What an object does,** not **how it does** it. 
- Reduces complexity and increases code clarity.
```cpp
class Shape{
public: 
	virtual void draw() = 0; //pure virtual function (abstract)
};
class Circle : public Shape{
public: 
	void draw() override {
		cout << "Drawing Circle" << endl;
	}
};
```
##### 📌 **Real-Life Example:**
- When driving a car, you use the steering and pedals (**what** to do), but you don’t need to know the engine's internal mechanism (**how** it works).
## Q). What is function template? using function template, write a program to find largest of three variable. 
A function template allows you to create a single function to work with different data types(int, float, char,etc) without rewriting code.

- Defined using the template keyword.
- Enables generic programming.
- compiler generates the correct version of the function at compile time.
```cpp
template <class T>
T functionName(T a, T a) {
	// function body
}
```

##### Program : Find the largest of Three variables using function template. 
```cpp
#include <iostream>
using namespace std;

//template function to find the largest of three
template <class T>
T largest(T a,T b,T c) {
	if( a>= b && a >= c)
		return a;
	else if(b >= a && b >= c)
		return b;
	else 
		return c;
}
int main(){
	cout << "Largest (int): " << largest(10, 25, 15) << endl;
	cout << "Largest (float): " << largest(5.6f, 7.2f, 6.1f) << endl;
	cout << "Largest (char): " << largest('x','a', 'm') << endl;

	return 0;
}
```

## Q). Write a c++ program to find the sum of series 1+3+5+7+9..... upto n terms : 
```cpp
#include <iostream>
using namespace std;

int main() {
	int n, sum=0;
	cout << "Enter the number of terms: ";
	cin >> n;

	 for (int i=0; i<n; i++){
		 int term = 2 * i + 1; //Generates odd numbers
		 sum += term;
	 }
	cout << "Sum of the series = " << sum << endl;

	return 0;
}
```

Or, 
we know that sum of odd numbers upto n terms is n^2
```cpp
#include <iostream>
using namespace std;

int main() { 
	int n;
	cout << "Enter the numbers of terms: ";
	cin >> n;
	cout << "Sum of the series = " << n*n << endl;

	return 0;
}
```

## Q). Write a program to find a sub-string inside a string : 

Using the built-in ***Find()*** function: 
```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
	string mainStr, subStr;

	cout << "Enter the main string: ";
	getline(cin, mainStr); //Read the entire line including spaces

	cout << "Enter the substring to search: ";
	getline(cin, subStr);

	size_t pos = mainStr.find(subStr);  // returns "string::npos" if not found.

	if(pos != string::npos) {
		cout << "Substring fount at position: " << pos << endl;
	} else {
		cout << "Substing not found! " << endl;
	}
	return 0;
}
```

Manual Substring search: 
```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
	string mainStr, subStr;
	bool found = false;

	cout << "Enter the main string: " ;
	getline(cin, mainStr);

	cout << "Enter the sub string: " ;
	getline(cin, subStr);

	int mainLen = mainStr.length();
	int subLen = subStr.length();

	for(int i=0;i<=mainLen - subLen; i++) {
		int j;
		for (j=0; j<subLen; j++){
			if(mainSt[i+j] != subStr[j]) {
				break;
			}
		}
		if ( j== subLen) {
			found = true;
			cout << "Substring found at position: " << i << endl;
			break;
		}
	}
	if(!found){
		cout << "Substring not found!" << endl;
	}
	return 0;
}
```

## Q).  Polymorphism : 
Polymorphism means **"Many forms"** , It allows object of different classes to be treated as objects of a common parent class. There are Two types: 
#### 1. Compile-Time Polymorphism (Static):
Resolved during compilation. Includes:
- ***Function Overloading***
```cpp
#include <iostream>
using namespace std;

class Math {
public:
	//same function name, different parameters
	int add(int a, int b) {
		return a+b;
	}
	double add(double a, double b) {
		return a+b;
	}
};

int main(){
	Math m;
	cout << m.add(2,3) << endl; //calls int version -> 5
	cout << m.add(2.5, 3.7) << endl: //calls double version -> 6.2
	return 0;
}
```

- ***Operator Overloading***
```cpp
#include <iostream>
using namespace std;

clas Vector {
public:
	int x,y;
	vector(int x, int y) : x(x), y(y) {}

	// Overload '+' operator
	Vector operator+(Vector v) {
		return Vector(x+v.x, y+v.y);	
	}
};
int main() {
	vector v1(1,2), v2(3,4);
	vector v3 = v1 + v2; //Uses overloaded '+'
	cout << "Result: (" << v3.x << "," << v3.y << ")"; //(4,6)
	return 0;
}
```
```cpp
#include <iostream>
using namespace std;

class Complex {
public:
	int real,imag;
	Complex(int r=0,int i =0){
		real = r;
		imag = i;
	}
	void print(){
		cout << "Complex No: "<< real << "+ " << imag + "i" ;
	}
	//Operator overloading 
	Complex operator + (Complex c){
		Complex temp;
		temp.real = real+c.real;
		temp.imag = imag+c.imag;
		return temp;
	}
	Complex operator * (Complex c){
		Complex temp;
		temp.real = real*c.real-imag*c.imag;
		temp.imag = real*c.imag - imag*c.real;
		return temp;
	}
}
int main(){
	Complex c1(4,6), c2(1,2);
	Complex c3 = c1+c2;
	c2.print();
	return 0;
}
```
