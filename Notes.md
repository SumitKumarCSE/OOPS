OOPS refers to the language that uses the concept of class and object in programming.
The main aim of OOP is to bind together the data and the functions that operate on them so that no other part of the code can access this data except that function. 

`Class`: It is user-defined data type, which holds its own data members and member functions, which can be accessed and used by creating an instance of that class. A 
class is a blueprint for an object.

`Object`: An Object is an identifiable entity with some characteristics and behaviour. An Object is an instance of a Class. When a class is defined, no memory is 
allocated but when it is instantiated (i.e. an object is created) memory is allocated.

Data members are the data variables and member functions are the functions used to manipulate these variables and together these data members and member functions 
define the properties and behaviour of the object in a class.
In the above example of class Car, the data member will be speed limit, mileage, etc and member functions can apply brakes, increase speed etc.

`Access Specifier`: Access Specifier in a class are used to assign access to the class members. It sets some restrictions on the class members from accessing the 
outside functions directly.

`Public`: All the class members with a public modifier can be accessed from anywhere (inside and outside the class). A public member can be accessed outside the class.

`Private`: All the class members with a private modifier can only be accessed by the member function inside the class. A private member of a class cannot be accessed 
outside the same class. A private member of a class can be accessed by the functions of the same class.

`Protected`: The access level of a protected modifier is within the class and outside through child class (or subclass). If you do not make the child class, it cannot be accesses outside the class.
By default: All class members are private if you don’t specify an access specifier.

## Encapsulation
It is defined as wrapping up of data and information under a single unit. In object-oriented programming, encapsulation is defined as binding together the data and the functions that manipulate them. Class is an example of encapsulation in computer science in that it consists of data and methods that have been bundled into a single unit.
```javascript
#include <iostream>
using namespace std;
class Student { 
  // private data members 
  private: stringstudentName; 
  int studentRollno; 
  int studentAge; 
  // get method for student name to access 
  // private variable studentName 
  public: 
    string getStudentName() {
      return studentName; 
    } 
  // set method for student name to set 
  // the value in private variable studentName 
  void setStudentName(stringstudentName) { 
    this-> studentName = studentName; 
  } 
  // get method for student rollno to access 
  // private variable studentRollno 
  int getStudentRollno() { 
    return studentRollno; 
  } 
  // set method for student rollno to set 
  // the value in private variable studentRollno 
  void setStudentRollno(intstudentRollno) { 
    this-> studentRollno = studentRollno; 
  } 
  // get method for student age to access 
  // private variable studentAge 
  int getStudentAge() { 
    return studentAge; 
  } 
  // set method for student age to set 
  // the value in private variable studentAge 
  void setStudentAge(intstudentAge) { 
    this-> studentAge = studentAge; 
  }
}; 

int main() { 
  Student obj; 
  // setting the values of the variables 
  obj.setStudentName("Avinash"); 
  obj.setStudentRollno(101); 
  obj.setStudentAge(22); 
  // printing the values of the variables 
  cout<<"Student Name : "<< obj.getStudentName()<<endl; 
  cout<<"Student Rollno : "<< obj.getStudentRollno()<<endl; 
  cout<<"Student Age : "<< obj.getStudentAge(); 
} 
Output: 
Student Name : Avinash 
Student Rollno :101 
Student Age :22
```
## Abstraction
Abstraction means providing only some of the information to the user by hiding its internal implementation details. We just need to know about the methods of the objects that we need to call and the input parameters needed to trigger a specific operation, excluding the details of implementation and type of action performed to get the result.

Real-life example: When you send an email to someone, you just click send, and you get the success message; what happens when you click send, how data is transmitted over the network to the recipient is hidden from you (because it is irrelevant to you).
```javascript
#include <iostream>
using namespace std;

class Animal {
public:
    virtual void makeSound() = 0; // Pure virtual function
};

class Dog : public Animal {
public:
    void makeSound() override {
        cout << "Woof!" << endl;
    }
};

class Cat : public Animal {
public:
    void makeSound() override {
        cout << "Meow!" << endl;
    }
};

int main() {
    Animal* dog = new Dog();
    Animal* cat = new Cat();

    dog->makeSound();  // Output: Woof!
    cat->makeSound();  // Output: Meow!

    delete dog;
    delete cat;

    return 0;
}
```
`Encapsulation is binding and abstraction is hiding.`
## Polymorphism
The word polymorphism means having many forms. In simple words, we can define polymorphism as the ability of a message to be displayed in more than one form.

A person at the same time can have different characteristic. Like a man at the same time is a father, a husband, an employee. So the same person posses different behaviour in different situations. This is called polymorphism.

`Compile-time polymorphism` is also known as static polymorphism. This type of polymorphism can be achieved through function overloading or operator overloading.

a)	`Function overloading`: When there are multiple functions in a class with the same name but different parameters, these functions are overloaded. The main advantage of function overloading is that it increases the program’s readability. Functions can be overloaded by using different numbers of arguments or by using different types of arguments. We have already discussed function overloading in detail in the previous module.

b)	`Operator Overloading`: C++ also provides options to overload operators. For example, we can make the operator (‘+’) for the string class to concatenate two strings. We know that this is the addition operator whose task is to add two operands. When placed between integer operands, a single operator, ‘+,’ adds them and concatenates them when placed between string operands.
`Operators can’t be overloaded: ( ::  .*  . ?: )`

`C++ doesn’t support overloading of destructor.`

```javascript
#include <iostream>
using namespace std;

// Function Overloading
int add(int a, int b) {
    return a + b;
}

double add(double a, double b) {
    return a + b;
}

// Operator Overloading
class Point {
private:
    int x;
    int y;
    
public:
    Point(int xCoord, int yCoord) : x(xCoord), y(yCoord) {}
    
    Point operator+(const Point& other) {
        int sumX = x + other.x;
        int sumY = y + other.y;
        return Point(sumX, sumY);
    }
    
    friend ostream& operator<<(ostream& os, const Point& point) {
        os << "Point(" << point.x << ", " << point.y << ")";
        return os;
    }
};

int main() {
    // Function Overloading example
    int sum1 = add(2, 3);
    double sum2 = add(2.5, 3.7);
    
    cout << "Sum 1: " << sum1 << endl;  // Output: 5
    cout << "Sum 2: " << sum2 << endl;  // Output: 6.2

    // Operator Overloading example
    Point p1(2, 3);
    Point p2(4, 5);
    Point p3 = p1 + p2;
    
    cout << "Point 1: " << p1 << endl;  // Output: Point(2, 3)
    cout << "Point 2: " << p2 << endl;  // Output: Point(4, 5)
    cout << "Point 3: " << p3 << endl;  // Output: Point(6, 8)

    return 0;
}
```
`Runtime polymorphism` is also known as dynamic polymorphism. Method overriding is a way to implement runtime polymorphism.

`Method overriding`: Method overriding is a feature that allows you to redefine the parent class method in the child class based on its requirement. In other words, whatever methods the parent class has by default are available in the child class. But, sometimes, a child class may not be satisfied with parent class method implementation. The child class is allowed to redefine that method based on its requirement. This process is called method overriding. Rules for method overriding: 

●The parent class method and the method of the child class must have the same name. 

●The parent class method and the method of the child class must have the same parameters. 

●It is possible through inheritance only.

```javascript
#include <iostream>
using namespace std;

// Base class
class Animal {
public:
    virtual void makeSound() {
        cout << "The animal makes a sound." << endl;
    }
};

// Derived class
class Dog : public Animal {
public:
    void makeSound() override {
        cout << "The dog barks." << endl;
    }
};

// Derived class
class Cat : public Animal {
public:
    void makeSound() override {
        cout << "The cat meows." << endl;
    }
};

int main() {
    // Creating objects of derived classes
    Dog dog;
    Cat cat;

    // Calling makeSound() function on objects
    dog.makeSound();  // Output: The dog barks.
    cat.makeSound();  // Output: The cat meows.

    // Using base class pointer to achieve polymorphism
    Animal* animal;

    // Pointing to the dog object and calling makeSound()
    animal = &dog;
    animal->makeSound();  // Output: The dog barks.

    // Pointing to the cat object and calling makeSound()
    animal = &cat;
    animal->makeSound();  // Output: The cat meows.

    return 0;
}
```

## Inheritance
The capability of a class to derive properties and characteristics from another class is called Inheritance. Inheritance is one of the most important features of Object-Oriented Programming.

Inheritance is a feature or a process in which, new classes are created from the existing classes. The new class created is called “derived class” or “child class” and the existing class is known as the “base class” or “parent class”. The derived class now is said to be inherited from the base class.

`Public mode`: If we derive a subclass from a public base class. Then, the base class’s public members will become public in the derived class, and protected class members will become protected in the derived class.

`Protected mode`: If we derive a subclass from a Protected base class. Then both public members and protected members of the base class will become protected in the derived class.

`Private mode`: If we derive a subclass from a Private base class. Then both public members and protected members of the base class will become Private in the derived class.

When we say derived class inherits the base class, it means, the derived class inherits all the properties of the base class, without changing the properties of base class and may add new features to its own. These new features in the derived class will not affect the base class. The derived class is the specialized class for the base class.

Types of Inheritances:
1. Single Inheritance
2. Multilevel Inheritance
3. Multiple Inheritance
4. Hierarichal Inheritance
5. Hybrid Inheritance

By default memory of class object is 1byte.

Member Functions: Inside and Outside class
```javascript
class Geeks
{
    public:
    string geekname;
    int id;
    // printname is not defined inside class definition
    void printname();
    // printid is defined inside class definition
    void printid()
    {
        cout <<"Geek id is: "<<id;
    }
};
// Definition of printname using scope resolution operator ::
void Geeks::printname() {
    cout <<"Geekname is: "<<geekname;
}
int main() {
    Geeks obj1;
    obj1.geekname = "xyz";
    obj1.id=15;
    // call printname()
    obj1.printname();
    // call printid()
    obj1.printid();
    return 0;
}
```
`Constructor` is a special member function automatically called when an object is created. In C++, the constructor is automatically called when an object is created. It is a special class method because it doesn’t have any return type. It has the same name as the class itself.

A constructor initializes the class data members with garbage value if we don’t put any value to it explicitly.

The constructor must be placed in the public section of the class because we want the class to be instantiated anywhere. For every object in its lifetime constructor is called only once at the time of creation.

Constructors are special class members which are called by the compiler every time when an object of that class is instantiated.

If you created a parameterized constructor and you are willing to create the object without having any parameter then it will throw a compile time error.
So, if you are having a parameterized constructor, and want to create the object without a parameter, then you must have to create a constructor without parameter first.

```javascript
class Geeks
{
    public:
    int id;
     
    //Default Constructor
    Geeks()
    {
        cout << "Default Constructor called" << endl;
        id=-1;
    }
     
    //Parameterized Constructor
    Geeks(int x)
    {
        cout <<"Parameterized Constructor called "<< endl;
        id=x;
    }
};
int main() {
     
    // obj1 will call Default Constructor
    Geeks obj1;
    cout <<"Geek id is: "<<obj1.id << endl;
     
    // obj2 will call Parameterized Constructor
    Geeks obj2(21);
    cout <<"Geek id is: " <<obj2.id << endl;
    return 0;
}
```
A Copy Constructor creates a new object, which is exact copy of the existing object. The compiler provides a default Copy Constructor to all the classes. 
```javascript
class smartphone{ 
	//Data Members(Properties) 
	String model; 
	int year_of_manufacture; 
	bool_5g_supported; 
public: 
	//default constructor 
	smartphone(){ 
		model ="unknown"; 
		year_of_manufacture =0; 
		_5g_supported =false; 
	} 
	//parameterized constructor smartphone(stringmodel_string,intmanufacture,bool_5g_){ 
	//initialising data members 
	model = model_string; 
	year_of_manufacture = manufacture; 
	_5g_supported = _5g_; 
} 
// copy constructor 
smartphone(smartphone &obj){ 
	// copies data of the obj parameter 
	model = obj.model; 
	year_of_manufacture = obj.year_of_manufacture; 
	_5g_supported = obj._5g_supported; 
} 
}; 

int main(){ 
	//creating objects of smartphone class 
	// using default constructor 
	smartphone unknown; 
	// using parameterized constructor 
	smartphoneiphone("iphone 11",2019,false); 
	// using copy constructor 
	smartphoneiphone_2(iphone); 
}
```
`Destructor`: A destructor is a special member function that works just opposite to a constructor; unlike constructors that are used for initializing an object, destructors destroy (or delete) the object. The purpose of the destructor is to free the resources that the object may have acquired during its lifetime.

The thing is to be noted here, if the object is created by using new or the constructor uses new to allocate memory that resides in the heap memory or the free store, the destructor should use delete to free the memory.

For static object allocation destructor is called automatically, but for dynamic allocated object we have to call destructor manually. By using (delete object;)

A destructor function is called automatically when: 
1. the object goes out of scope 
2. the program ends 
3. a scope (the { } parenthesis) containing local variable ends. 
4. a delete operator is called

```javascript
#include <iostream>
using namespace std;

// Base class
class Base {
public:
    Base() {
        cout << "Base constructor called." << endl;
    }

    ~Base() {
        cout << "Base destructor called." << endl;
    }
};

// Derived class
class Derived : public Base {
public:
    Derived() {
        cout << "Derived constructor called." << endl;
    }

    ~Derived() {
        cout << "Derived destructor called." << endl;
    }
};

int main() {
    Derived derived;

    return 0;
}
```
`Shallow copy`: An object is created by simply copying the data of all variables of the original object. Here, the pointer will be copied but not the memory it points to. It means that the original object and the created copy will now point to the same memory address, which is generally not preferred.

Since both objects will reference the exact memory location, then changed made by one will reflect those change in another object as well. This can lead to unpleasant side effects if the elements of values are changed via some other reference. Since we wanted to create an object replica, the shallow copy will not fulfill this purpose.

C++ compiler implicitly creates a copy constructor and assignment operator to perform shallow copy at compile time

```javascript
#include <iostream>
#include <cstring>
using namespace std;

// Class with dynamically allocated data
class MyClass {
private:
    int* data;
    int size;

public:
    // Constructor
    MyClass(int s) : size(s) {
        data = new int[size];
    }

    // Destructor
    ~MyClass() {
        delete[] data;
    }

    // Shallow copy
    MyClass(const MyClass& other) : size(other.size) {
        data = other.data;
    }

    // Deep copy
    MyClass& operator=(const MyClass& other) {
        if (this != &other) {
            size = other.size;
            data = new int[size];
            memcpy(data, other.data, size * sizeof(int));
        }
        return *this;
    }

    // Getter for data
    int* getData() const {
        return data;
    }

    // Setter for data
    void setData(int index, int value) {
        data[index] = value;
    }
};

int main() {
    // Creating object and setting data
    MyClass obj1(5);
    for (int i = 0; i < 5; i++) {
        obj1.setData(i, i + 1);
    }

    // Shallow copy
    MyClass obj2 = obj1;

    // Changing data in obj1
    obj1.setData(0, 100);

    // Displaying data in obj2 (shallow copy)
    int* data2 = obj2.getData();
    for (int i = 0; i < 5; i++) {
        cout << data2[i] << " ";  // Output: 100 2 3 4 5
    }
    cout << endl;

    // Deep copy
    MyClass obj3(5);
    obj3 = obj1;

    // Changing data in obj1
    obj1.setData(1, 200);

    // Displaying data in obj3 (deep copy)
    int* data3 = obj3.getData();
    for (int i = 0; i < 5; i++) {
        cout << data3[i] << " ";  // Output: 100 2 3 4 5
    }
    cout << endl;

    return 0;
}
```
![Alt text](https://github.com/SumitKumarCSE/OOPS/blob/main/shallowcopy.png)
`Deep copy`: An object is created by copying all the fields, and it also allocates similar memory resources with the same value to the object. To perform deep copy, we need to explicitly define the copy constructor and assign dynamic memory as well if required. Also, it is necessary to allocate memory to the other constructors variables dynamically. 

A deep copy means creating a new array and copying over the values. 

Changes to the array values referred to will not result in changes to the array data refers to.
![Alt text](https://github.com/SumitKumarCSE/OOPS/blob/main/deepcopy.png)
# Virtual Function
A virtual function is a member function in the base class that we expect to redefine in derived classes. It is declared using the virtual keyword. Virtual functions are mainly used to achieve runtime polymorphism.

A virtual function is used in the base class to ensure that the function is overridden. This especially applies to cases where a pointer of base class points to a derived class object.
```javascript
class Base{
  public:
    virtual void print() {
      cout<<"Base Function"<<endl;
    }
};

class Derived : public Base {
  public:
    void print() {
      cout<<"Dervied Function"<<endl;
    }
};

int main() {
  Derived derived1;
  
  // pointer of Base type that points to derived1
  Base* base1 = &derived1;
  
  //calls member function of Derived class
  base1->print();
  
  return 0;
)

Output:
Derived Function
```
`Pure Virutal Function`: A pure virtual function is a virtual function in C++ for which we need not write any function definition and only have to declare it. It is declared by assigning 0 in the declaration.

A pure virtual function (or abstract function) in C++ is a virtual function for which we can implement, But we must override that function in the derived class; otherwise, the derived class will also become an abstract class.

`Abstract Class`: Abstract classes can’t be instantiated, i.e., we cannot create an object of this class. However, we can derive a class from it and instantiate the object of the derived class. An Abstract class has at least one pure virtual function.

It can have normal functions and variables along with pure virtual functions. 

Constructors cannot be virtual because they need to be defined in the class.
```javascript
#include <iostream>
using namespace std;

// Abstract base class
class Shape {
public:
    // Pure virtual function
    virtual double area() const = 0;

    // Concrete member function
    void displayArea() const {
        cout << "Area: " << area() << endl;
    }
};

// Derived class
class Circle : public Shape {
private:
    double radius;

public:
    Circle(double r) : radius(r) {}

    double area() const override {
        return 3.14 * radius * radius;
    }
};

// Derived class
class Rectangle : public Shape {
private:
    double length;
    double width;

public:
    Rectangle(double l, double w) : length(l), width(w) {}

    double area() const override {
        return length * width;
    }
};

int main() {
    // Creating objects of derived classes
    Circle circle(5.0);
    Rectangle rectangle(4.0, 6.0);

    // Calling member function on objects
    circle.displayArea();     // Output: Area: 78.5
    rectangle.displayArea();  // Output: Area: 24

    // Creating pointer to the abstract base class
    Shape* shapePtr = nullptr;

    // Pointing to the Circle object and calling member function
    shapePtr = &circle;
    shapePtr->displayArea();  // Output: Area: 78.5

    // Pointing to the Rectangle object and calling member function
    shapePtr = &rectangle;
    shapePtr->displayArea();  // Output: Area: 24

    return 0;
}
```
If we do not override the pure virtual function in the derived class, then the derived class also becomes an abstract class.

`Friend Function`: If a function is defined as a friend function in C++, then the protected and private data of a class can be accessed using the function. 

A class’s friend function is defined outside that class’s scope, but it has the right to access all private and protected members of the class. Even though the prototypes for friend functions appear in the class definition, friends are not member functions. 

The function can be defined anywhere in the program like a normal C++ function. The function definition does not use either the keyword friend or scope resolution operator
```javascript
class Rectangle {
  private:
    int length;
  public:
    Rectangle() {
      length=10;
    }
  friend int printLength(Rectangle);
};

int printLength(Rectangle b) {
  Rectangle b;
  cout<<"Length of Rectangle: "<<printLength(b)<<endl;
  return 0;
}

Output:
Length of Reactangle: 20
```
Characteristics of friend function: 

● A friend function can be declared in the private or public section of the class. 

● It can be called a normal function without using the object. 

● A friend function is not in the scope of the class, of which it is a friend. 

● A friend function is not invoked using the class object as it is not in the class’s scope. 

● A friend function cannot access the private and protected data members of the class directly. It needs to make use of a class object and then access the members using the dot operator. 

● A friend function can be a global function or a member of another class.
