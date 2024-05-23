## OOP's
**Object-Oriented Programming (OOP)** in C++ along with corresponding code examples to illustrate each concept.

### 1. Classes and Objects

A class is a blueprint for creating objects (a particular data structure), and an object is an instance of a class.

```cpp
#include <iostream>
using namespace std;

class Car {
public:
    string brand;
    string model;
    int year;

    void displayInfo() {
        cout << "Brand: " << brand << ", Model: " << model << ", Year: " << year << endl;
    }
};

int main() {
    Car car1;
    car1.brand = "Toyota";
    car1.model = "Camry";
    car1.year = 2021;

    car1.displayInfo();
    return 0;
}
```

### 2. Encapsulation

Encapsulation is the bundling of data with the methods that operate on that data. It restricts direct access to some of an object's components.

```cpp
#include <iostream>
using namespace std;

class Employee {
private:
    int salary;

public:
    void setSalary(int s) {
        salary = s;
    }

    int getSalary() {
        return salary;
    }
};

int main() {
    Employee emp;
    emp.setSalary(50000);
    cout << "Employee Salary: " << emp.getSalary() << endl;
    return 0;
}
```

### 3. Inheritance

Inheritance is a mechanism where a new class is derived from an existing class. The new class inherits attributes and behaviors of the existing class.

```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    void eat() {
        cout << "Eating..." << endl;
    }
};

class Dog : public Animal {
public:
    void bark() {
        cout << "Barking..." << endl;
    }
};

int main() {
    Dog dog1;
    dog1.eat();
    dog1.bark();
    return 0;
}
```

### 4. Polymorphism

Polymorphism means the ability to take many forms. It allows methods to do different things based on the object it is acting upon.

#### Compile-time Polymorphism (Function Overloading)

```cpp
#include <iostream>
using namespace std;

class Print {
public:
    void display(int i) {
        cout << "Integer: " << i << endl;
    }

    void display(double f) {
        cout << "Float: " << f << endl;
    }

    void display(string s) {
        cout << "String: " << s << endl;
    }
};

int main() {
    Print p;
    p.display(5);
    p.display(5.99);
    p.display("Hello");
    return 0;
}
```

#### Runtime Polymorphism (Method Overriding)

```cpp
#include <iostream>
using namespace std;

class Base {
public:
    virtual void show() {
        cout << "Base class" << endl;
    }
};

class Derived : public Base {
public:
    void show() override {
        cout << "Derived class" << endl;
    }
};

int main() {
    Base* b;
    Derived d;
    b = &d;

    b->show();
    return 0;
}
```

### 5. Abstraction

Abstraction means hiding the complex implementation details and showing only the essential features of the object.

```cpp
#include <iostream>
using namespace std;

class AbstractEmployee {
    virtual void askForPromotion() = 0; // Pure virtual function
};

class Employee : public AbstractEmployee {
private:
    string name;
    int age;

public:
    Employee(string empName, int empAge) : name(empName), age(empAge) {}

    void askForPromotion() override {
        if (age > 30)
            cout << name << ", you got promoted!" << endl;
        else
            cout << name << ", sorry, no promotion for you." << endl;
    }
};

int main() {
    Employee emp1("John", 35);
    Employee emp2("Jane", 25);

    emp1.askForPromotion();
    emp2.askForPromotion();

    return 0;
}
```

### 6. Constructors and Destructors

Constructors are special member functions of a class that are executed whenever new objects of that class are created. Destructors are used to destroy the objects created by constructors.

```cpp
#include <iostream>
using namespace std;

class Person {
public:
    Person() {
        cout << "Constructor called!" << endl;
    }

    ~Person() {
        cout << "Destructor called!" << endl;
    }
};

int main() {
    Person p1;
    return 0;
}
```

### 7. Operator Overloading

Operator overloading allows C++ operators to have user-defined meanings on user-defined types (classes).

```cpp
#include <iostream>
using namespace std;

class Complex {
private:
    float real;
    float imag;

public:
    Complex() : real(0), imag(0) {}

    Complex operator + (const Complex& obj) {
        Complex temp;
        temp.real = real + obj.real;
        temp.imag = imag + obj.imag;
        return temp;
    }

    void display() {
        cout << "Real: " << real << " Imaginary: " << imag << endl;
    }
};

int main() {
    Complex c1, c2, result;
    c1 = Complex();
    c2 = Complex();
    
    result = c1 + c2;

    result.display();
    return 0;
}
```

### 8. Friend Functions

Friend functions are those functions that are not a member of a class but have access to its private and protected members.

```cpp
#include <iostream>
using namespace std;

class Box {
private:
    double width;

public:
    friend void printWidth(Box b);
    void setWidth(double w) {
        width = w;
    }
};

void printWidth(Box b) {
    cout << "Width of box: " << b.width << endl;
}

int main() {
    Box b;
    b.setWidth(10.0);
    printWidth(b);
    return 0;
}
```

These examples cover the essential OOP concepts in C++. Each code snippet demonstrates how the concept is applied in practice.