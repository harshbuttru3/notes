
```cpp
#include <iostream>
#include <string>
using namespace std;

class Person2{
public: 
    int pension;    
    Person2(int p){
        this->pension = p;
        this->show();
    }
    void show(){
        cout << "Pension: " << pension << endl;
    };
};
class Person{
public:
    string name;
    int age; 
    Person(string name, int age, int bodycount, double s){   //constructor
        this->name = name;
        this->age = age;
        this->salary = s;
        this->bodycount = bodycount;
        this-> show();
    }
  
    Person(){
    }
    // ~Person(){
    // cout << "delete all the scoped out variables and methods\n" ; 
    // }
    void talk(){             //normal function
        // cout << "blah blah blah blah"<< endl;
        cout << salary<< endl;
        cout << bodycount << endl;
    }
     void show(){
        cout << "Name: " << name << endl;
        cout << "age: " << age << endl;
        cout << "bodycount: " << bodycount << endl;
        cout << "salary : " << salary << endl;
    }
private:
    double salary;
protected:
    int bodycount;
};

class Student : public Person, public Person2 {
public:
    int rollno;
  Student(string name, int age, int bodycount,double salary, int r, int p): Person(name, age, bodycount, salary),Person2(p){
      this->rollno = r;
    this->show();
   };
     void show  ()  {
        cout << "student overrided show()" << endl;
       cout << "roll no: " << rollno << endl;
   };

};








int main() {
    
    
Student s1("harsh", 21, 1.1, 78000, 30, 5000);
// cout << s1.bodycount << endl;


return 0;
}
```

