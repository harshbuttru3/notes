- C++ was developed by **Bjarne Stroustrup** at  Bell labs (1980s).
- It is an extension of **C** with **Object-Oriented programming (OOP)** features.
- It's multi-paradigm (procedural + object-oriented).

#### Why C++?
- Powerful performance like C.
- Supports large, modular programs using OOP.





##  **Advantages of OOP**

- **Reusability**: Use existing code.
    
- **Scalability**: Easy to extend.
    
- **Security**: Data hiding.
    
- **Modularity**: Programs are divided into objects.
    

✅ _Exam Tip_: _"OOP increases reusability, scalability, security, and modularity."_

##  **Object-Oriented Technology**

- Focuses on **objects** rather than procedures.
    
- Objects are **real-world entities** (Car, Student, etc.) with **data + methods**.
    
- **OOP** Concepts:
    
    - **Class**: Blueprint of objects.
        
    - **Object**: Instance of a class.
        
    - **Inheritance**: Child class inherits from parent class.
        
    - **Polymorphism**: Same name, different behavior.
        
    - **Encapsulation**: Binding data + methods.
        
    - **Abstraction**: Hiding internal details.

### Encapsulation : 
- It refers to **bundling of data (attributes) and methods (functions) that operates on the data into a single unit (class)**. 
- It also involves **restricting direct access to some of an object's components**, which helps prevent unintended interference and misuse.

***Key Aspects of Encapsulation :***
1.  **Data Hiding** - Making fields (variables) private and providing access via public methods (getters and setters) . 
2.  **Controlled Access :** prevents external code from directly modifying internal data, ensuring validation and security.
3. **Modularity :** Keeps related data and behavior together, improving code Organisation and reusability.

```cpp
#include <iostream>
#include <string>
using namespace std;

class BankAccount {
private:  // Hidden access
	string owner;
	double balance;
public: //controlled access
	BankAccount(string owner, double balance): owner(owner),balance(balance) {}

	void deposit(double amount){
		if (amount > 0) balance += amount;
}
	void withdraw(double amount){
		if (amoutn > 0 && amount <= balance) balance -= amount;
}
	double getBalance(){return balance;}
		string getOwner(){return owner;}
};

int main(){
	BankAccount acc("Alice", 1000);
	acc.deposit(500);
	acc.withdraw(200);
	cout << "Balance: $" << acc.getBalance() << endl;
	return 0;
}
```

### Inheritance : 
It is a fundamental OOP concept that allows a **new class (derived/child class)** to **inherit properties and behaviors (methods and fields)** from an **existing class (base/parent class)**.

***Key Points:*** 
1. **Reusability :** Avoid rewriting the same code by inheriting from a base class.
2. **Extensibility** : Child classes can add new features or modify inherited ones.
3. **Hierarchical Relationship :** Represents an "is-a" relationship (eg, `Car` is a `vehicle`)

#### Types of Inheritance in c++


| Type                     | Description                                         |
| ------------------------ | --------------------------------------------------- |
| Single Inheritance       | A class inherits from **One** base class            |
| Multiple Inheritance     | A class inherits from **Multiple** base class       |
| Multilevel Inheritance   | A derived class acts as a base for another class.   |
| Hierarchical Inheritance | Multiple class inherit from **one** base class      |
| Hybrid Inheritance       | Combination of multiple and multilevel inheritance. |
***Example of Single Inheritance***
```cpp
#include <iostream>
using namespace std;

// Base class (Parent)
class Vehicle {
public:
    string brand = "Toyota";
    void honk() {
        cout << "Beep! Beep!" << endl;
    }
};

// Derived class (Child)
class Car : public Vehicle {  // 'public' inheritance
public:
    string model = "Corolla";
};

int main() {
    Car myCar;
    cout << "Brand: " << myCar.brand << endl;  // Inherited from Vehicle
    cout << "Model: " << myCar.model << endl;  // Own property
    myCar.honk();  // Inherited method
    return 0;
}
```


***Example of multiple inheritance***
```cpp
#include <iostream>
using namespace std;

//base class 1
class Engine {
public : 
	void start() { cout << "Engine started!" << endl;}
};
//base class 2
class MusicSystem {
public:
	void play() { cout << "Music playing" << endl;}
};

//Derived class (inherits from both)
class Car : public Engine, public MusicSystem {};

int main() {
	Car mycar;
	mycar.start(); // From Engine
	mycar.play();  // from MusicSystem
	return 0;
}
```

***Multilevel Inheritance***
```cpp
#include <iostream>
using namespace std;

//base class
class Animal {
public:
	void eat() {cout << "Eating..." << endl;}
};
//derived class
class Mammal : public Animal {
public:
	void breate(){ cout << "Breathing..." << endl;}
};

// Derived from Mammal
class Dog : public Mammal {
public:
	void bark() { cout << "Barking..." << endl;}
};
```

***Hierarchical Inheritance***
```cpp
#include <iostream>
using namespace std;

//Base class
class Vehicle {
public:
	void start() { cout << "Vehicle started!" << endl;}
};

//Derived class 1
class Car : public Vehicle {
public:
	void drive() { cout << "car is moving." << endl;}
};

//Derived class 2
class Bike : public Vehicle {
public: 
	void ride() { cout << "bike is running." << endl;}
	};
```

***Hybrid Inheritance***
```cpp
#include <iostream>
using namespace std;

//base class
class Person {
public:
	string name;
	Person(string n) : name(n){}
	void display() {cout << "Name: " << name << endl;}
};

//Derived 1
class Student : public Person {
public:
	int rollNo;
	Student(string n, int r) : Person(n), rollNo(r) {}
};

//Derived 2
class Employee : public Person {
public:
	int empId;
	Employee(string n, int id) : Person(n), empId(id) {}
};

// Derived from both student and Employee
class TeachingAsistant : public Student, public Employee {
public:
	TeachingAssistant(string n, int r, int id) : Student(n,r), Employee(n, id) {}
};

int main() {
TeachingAssistant ta("Alice", 101, 1001);

	//ta.diaplay(); ❌Error (ambiguous, which display() to call?)

	//Solution : Use scope resolution
	ta.Student::display(); //calls Person's display() via Student
	cout << "Roll NO: " << ta.rollNo << endl;
	coutn << "Employee ID: " << ta.empId << endl;
return 0;
}
```
```handdrawn-ink
{
	"versionAtEmbed": "0.3.4",
	"filepath": "Ink/Drawing/2025.4.28 - 2.12am.drawing",
	"width": 974,
	"aspectRatio": 1.7904411764705883
}
```



### Polymorphism : 
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

#### 2. Runtime Polymorphism (Dynamic)
resolved during runtime using:

- ***Function overrinding (with `virtual` functions)
```cpp
#include <iostream>
using namespace std;

class Animal {
public:
	virtual void sound() {  // 'virtual' enables overriding
		cout << "Animal makes sound\n";
	}
};

class Dog : public Animal {
public: 
	void sound() override {
		cout << "Dog barks: Woof!\n";
	}
};

class Cat : public Animal {
public:
	void sound() override {
		cout << "Cat meows: Meow!\n";	
	}
};

int main() {
Animal* a1 = new Dog();
Animal* a2 = new Cat();

a1->sound();
a2->sound();

delete a1, a2;
return 0
}
```

***Key Points:***
- `virtual` keyword allows runtime binding.
- Without `virtual`, the base class method runs (early binding).
- `override` (c++11) ensures correct overriding.
##### **a)  `a1->sound()` vs `a1.sound()`**

- **`->`** is used for **pointer access** (shortcut for `(*a1).sound()`).
    
- **`.`** is used for **direct object access**.
##### **b) `new Dog()` - Dynamic Memory Allocation**

- `new Dog()` creates a `Dog` object **on the heap** (not automatic cleanup).
    
- Returns a **pointer** to that object (`Animal*`).




### Abstraction : 
it focuses on **hiding complex implementation details** while exposing only the **essential features** to users.

> "Show what an object does, not how it does it."

1. ***Abstract Class***
```cpp
#include <iostream>
using namespace std;

//Abstract class (cannot be instantiated)
class Shape {
public:
	//pure virtual function (makes shape abstract)
	virtual float area() = 0;

	void printArea() {
	cout << "Area: " << area() << endl; // Uses abstract method
	}
};

//Concrete class (implements the abstraction)
class Circle : public Shape {
	float radius;
public:
	Circle(float r) : radius(r) {}

	//Must implement area() (otherwise circle becomes abstract too)
	float area() override {
		return 3.14 * radius * radius;
	}
};
int main() {
	//shape s; // ❌ Error - can't instantiate abstract class
	Circle c(5);
	c.printArea(); // Output: Area: 78.5
	return 0;
}
```

2. ***Interface (Pure Abstract Class)***
```cpp
class Drawable {
public:
	virtual void draw() =0; //pure virtual function
	virtual ~Drawable() {} //virtual destructor
};

class Circle : public Drawable {
public: 
	void draw() override {
		cout << "Drawing a circle" << endl;
	}
};

int main(){
	Drawable* d = new circle();
	d->draw();
	delete d; 
	return 0;
}
```

#### **Why Use Abstraction?**

1. **Simplifies Complex Systems**
    
    - Users interact with high-level interfaces without worrying about internal details.
        
2. **Reduces Complexity**
    
    - Changes to implementation don't affect code using the abstraction.
        
3. **Enforces Structure**
    
    - Derived classes must implement all abstract methods.
        
4. **Supports Polymorphism**
    
    - Enables runtime binding through base class pointers/references.