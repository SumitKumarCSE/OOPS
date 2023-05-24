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

`Encapsulation`: It is defined as wrapping up of data and information under a single unit. In object-oriented programming, encapsulation is defined as binding together the data and the functions that manipulate them. Class is an example of encapsulation in computer science in that it consists of data and methods that have been bundled into a single unit.
```javascript
#include <iostream>
usingnamespacestd;
class Student{ 
  // private data members 
  private: stringstudentName; 
  int studentRollno; 
  int studentAge; 
  // get method for student name to access 
  // private variable studentName 
  public: 
    stringgetStudentName() {
      returnstudentName; 
    } 
  // set method for student name to set 
  // the value in private variable studentName 
  void setStudentName(stringstudentName) { 
    this-> studentName = studentName; 
  } 
  // get method for student rollno to access 
  // private variable studentRollno 
  int getStudentRollno() { 
    returnstudentRollno; 
  } 
  // set method for student rollno to set 
  // the value in private variable studentRollno 
  void setStudentRollno(intstudentRollno) { 
    this-> studentRollno = studentRollno; 
  } 
  // get method for student age to access 
  // private variable studentAge 
  int getStudentAge() { 
    returnstudentAge; 
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
