# Object&Class

- You can think of *class* as an abstract thing, e.g., Person. And *object* is an actual thing, e.g., Mike is a person.
- Java usually orgnizes code in **class** and encapsulate data in **object**

The following example will show you how to use class and object:

```java
package oop.ObjectClass;

public class Application {
    public static void main(String[] args) {
        //In here we need to instantiate class-Student
        //After instantiation, we can get an object of class-Student
        Student student1 = new Student();
        Student student2 = new Student();
        //Now, student1 and student2 are objects of class-Student
        //And we can assign value in Object now
        student1.name = "Mike";
        student1.age = 21;
        System.out.println(student1.name);
        student1.study();
    }
}
/*
class Student
*/
// using class to orgnize code
public class Student {
    String name;
    int age;
    public void study(){
        System.out.println(this.name+" is learning Java");
    }
}

```

**Constructor**

- Constructor will initialize the value of the object

- By default, constuctor will generate a empty method, and this method shares same name with class.

-  When you use *new* to instantiate a class, a constuctor is required.
- Shortcut to call constructor: "alt+insert" for win "control+return" for os

```java
public class Application {
    public static void main(String[] args) {
      Student student = new Student();
    }
}

public class Student {
  //By default, constuctor will generate a empty method, and this method shares same name with class.
  public Student(){
    
  }
  //If you want to define a constuctor with parametar, you need to keep above empty method. Otherwise, it will return a error
  public Student(String name){
    this.name = "MIKE";
  }
}
```

**Memory analysis of object creation**

![image-20220407122818427](/Users/yanglimin/Library/Application Support/typora-user-images/image-20220407122818427.png)

**Summary of object&class**

- Class is an abstract thing and object is an actual thing
- Method
  - Define and call
- Reference
  - Basic 8 types, e.g., char, String, int, etc.
  - **Object** is manipulated by referencing **class**.e.g., *Student student1 = new Student()*. **Stack-->Head**, as can be seen in above screenshoot
- Class contains attributes (field)
  - default initialization 
    - number: 0, 0.0
    - char: u0000
    - boolean: false
    - reference: null
  - rule of filed definition 
    - modifier type name = value e.g., *public String name = "Mike"*
-  Objectt creation and use
  - you need to use *new* to create object, e.g., *Student student = new Student()*
  - attributes of object: *student.name*
  - method of object: *student.study()*
- Class:
  - staic attributes: E.g.,*String name*
  - dynamic behavior: method e.g., *public void study(){}*
