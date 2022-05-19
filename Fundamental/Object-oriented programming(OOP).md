# Object-oriented programming(OOP)

- What is OOP?

   - Process-oriented

   > Procedural programming is about writing procedures or methods that perform operations on the data
   >
   > Ref:https://www.w3schools.com/java/java_oop.asp

   - Object-oriented

   > Object-oriented programming is about creating objects that contain both data and methods.

   Advantage of OOP:

   > - Faster and easier to execute
   > - Provides a clear structure 
   > - Easier to maintain, modify and debug

- Object-Oriented Creation and Analysis

  ![image-20220407122954282](/Users/yanglimin/Library/Application Support/typora-user-images/image-20220407122954282.png)

- Three characteristics of object-oriented 

   - **Encapsulation attributes**

     - Encapsulate data into a box and access the data through an interface
     - Encapsulation mainly focuses on attribute, e.g., *name, age, height*
     - High cohesion, low coupling
       - **High cohesion** - internal data operation details of the class are done by class itself, and exteanl interference is not allowed 
       - **Low coupling** - Expose only a few methods for external use
       - Here is an example, a large amount of user data in a bank is managed by bank (high cohesion), and bank only provides a small number of service at ATM machine, such as deposit and withdraw (low coupling). 
     - Private attribute and get/set

   - **Why Encapsulate?**

     - Improve program security and ensure data security
     - Hide details of code 
     - Unified interface
     - Improve system maintainbility

   - ​	**Example of encapsulation**

     ```java
     // class
     public class Student {
       //using private attributes to ensure data sercurity
         private String name;
         private int age;
     
         /* get and set
          */
         //get
         public String getName(){
             return this.name;
         }
         public int getAge(){
             return this.age;
         }
         //set
         public void setName(String name){
             this.name = name;
         }
         public void setAge(int age){
             this.age = age;
         }
     }
     //main()
     public class Application {
         public static void main(String[] args) {
           Student student = new Student();
           student.setAge(3);
           student.setName("Mike");
           System.out.println(student.getAge());
           System.out.println(student.getName());
     
         }
     }
     
     ```

     

   - **Inheritance** 

     - The essence of inheritance is the abstraction of a certain batch of classes to achieve better modeling.
     - Java only support single inheritance, i.e one child only has one parent 
     - Inheritance is a relationship among classes  
     - Subclass can inherit all method of parent

     Here is an example of inheritance

     ![image-20220408001947330](/Users/yanglimin/Library/Application Support/typora-user-images/image-20220408001947330.png)

     Inheritance code example 

     ```java
     public class Application {
         public static void main(String[] args) {
             Student student = new Student();
             student.say();
             System.out.println("Child student inherit father's money $ "+ student.money);
         }
     }
     
     /* parent 
     Person -> parent
     Teacher -> child
     Student -> child*/
     public class Person {
         public int money = 10_0000_0000;
         public void say(){
             System.out.println("This methods come from parent(Person)");
         }
     }
     
     /*child Student inherit inherit Person*/
     public class Student extends Person{
     }
     
     ```

     - **object, super, method overriding**

       - **object**

       - **super V.S. this**

         - *super()* and *this()* can not call constructors at the same time 
         - If you want to call the constructor via this() or super(), this() or super() can only appear in the first line of constructor code

         *super:*

         - *super* is used to call method of parent 
         - *super* can only appear in methods or constructors of methods
         - You can not use *super* without inheritance
         - *super()* is used to call parent's constructor 

         *this:*

         - *this* is used to call the method or constuctor under the current class 
         - *this()* is used to call current constructor 

         Here is an example to show the using of *super and this*

       ```java 
       package oop.InheritanceSuper;
       
       public class Application {
           public static void main(String[] args) {
               Student student = new Student();
       //        student.test1("ApplicationName");
       //        student.test2();
           }
       }
       
       public class Student extends Person {
           private String name = "StudentName";
         	public Student(String name){}
           /*test 1 for parameter*/
           public void test1(String name){
               System.out.println(name);//ApplicationName
               System.out.println(this.name);//StudentName
               System.out.println(super.name);//PersonName
           }
           /*test 2 for method*/
           public void print(){
               System.out.println("From Student");
           }
       
           public void test2(){
               this.print();//From Student
               super.print();//From Person
           }
           /*test 3 for constructor*/
       
           public Student(){
       //        super();//to call parent constructor
               this("hello");//to call current constructor
               System.out.println("StudentConstructor");
           }
       }
       
       public class Person {
           protected String name = "PersonName";
           public void print(){
               System.out.println("From Person");
           }
           public Person(){
               System.out.println("PersonConstructor");
           }
       }
       ```

       - **method overrding**

         - Why override?

           Some methods of parent do not meet the needs of subclass

         - How to override?
           1. same method name
           2. same parameter
           3. Modifier: the range can be enlarger but not reduced (public-> protected->default->private)
           4. Throw an exception: the range can be reduced but not be enlarged e.g., ClassNotFoundException ->Exception
         - Which methods cannot be overridden?
           - private
           - final (constant)
           - static (it belongs to class/)

     

     **Example of overriding**

     ```java 
     package oop.Overriding;
     
     public class Application {
         public static void main(String[] args) {
             /*before overriding*/
             A a = new A(); // class A
             a.print();
     
             // the reference of parent class B points to child class A
             B b = new A(); // class B
             b.print();
             /*after overriding*/
             /* the output of a.print() and b.print()
             * class A
             * class A
             * */
         }
     }
     
     // parent class
     public class B {
         /*before overriding*/
     //    public static void print(){
     //        System.out.println("class B");
     //    }
     
         /*after overriding*/
         public void print(){
             System.out.println("class B");
         }
     }
     
     //child class
     public class A extends B{
         /*before overriding*/
     //    public static void print(){
     //        System.out.println("class A");
     //    }
     
         /*after overriding*/
     
         @Override
         public void print() {
             System.out.println("class A");
         }
     }
     
     ```

     

   - **Polymorphism**

     > To put it simply, polymorphism in Java allows us to perform the same action in many different ways

     		1. It is polymorphism of methods, not attributes
     		1. Polymorphism is based on inheritance
     		1. Father class can point to the subclass, but it cannot call the *unique method* of the subclass

     **Here is an example**

   ```java
   package oop.Polymorphism;
   
   public class Application {
       public static void main(String[] args) {
           Student s1 = new Student();
           //reference of father points to child
           Person s2 = new Student();
           /*
           s1 and s2 will call method of father while method of child class is empty
   
           s1.print();//run father
           s2.print();//run father
           */
   
           /* while child method is not empty
   
           s1.print();//run child
           s2.print();//run child
           */
   
           /* while overriding */
           s1.print();//run child
           s2.print();//run child
   
           /*
   
           */
           s1.study();
           ((Student) s2).study();// father can not call method that the father class does not have
           // so you need to cast the type
       }
   }
   
   package oop.Polymorphism;
   //child class
   public class Student extends Person{
   //    public void print(){
   //        System.out.println("run child");
   //    }
   
   
       @Override
       public void print() {
           System.out.println("run child");
       }
       public void study(){
           System.out.println();
       }
   }
   
   package oop.Polymorphism;
   //parent class
   public class Person {
       public void print(){
           System.out.println("run father");
       }
   }
   
   ```

   ** Conversion**

   1.  Why conversion?
      - call method easily (you doont need to *new* a new object)

   2. ***instanceof (type conversion)***: to determine whether two classes hava a parent-child relationship

   ``` java 
   public class Application {
       public static void main(String[] args) {
           /*
           relationship:
           Object -> Person -> Student
           Object -> Person -> Teacher
           Object -> String
           */
           Object object = new Student();
           System.out.println(object instanceof Object);//true
           System.out.println(object instanceof Person);//true
           System.out.println(object instanceof Teacher);//false
           System.out.println(object instanceof Student);//true
           System.out.println(object instanceof String);//false
       }
   }
   ```

   3. ***From high level to low level & low level to high level***

   ```java
   package oop.Instanceof;
   
   public class Application {
       public static void main(String[] args) {
           /* from high to low -> cast */
           Person obj1 = new Student();
   //        obj1.student(); ->invalid, you need to cast (from Person(high)->Student(low))
           Student NewObj = (Student) obj1; // or you can do like this way: ((Student)obj).student();
           NewObj.student(); // -> now it is valid
           /* from low to high */
           Student obj2 = new Student();
           // if you want to convert Student to Person:
           Person NewObj2 = obj2;
   //        NewObj2.student(); -> invalid, when converting low level to high level，it is possible to lose methods of low level
   
   
       }
   }
   
   ```

   

1. Abstract classes and interfaces
2. Inner classes and OOP combat