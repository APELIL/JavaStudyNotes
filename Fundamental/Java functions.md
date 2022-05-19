# Java method

#### Static and non-static methods

**Static** 

```java
//method
public static int test1(int a, int b){
  return a+b;
}
//main
public static void main(String[] args){
  //you can call method like this way:
  int a = 3;
  int b = 4;
  int result = test1(a,b);
}
```

**Non-static**

```java
package oop.method;

public class Demo01 {
    public static void main(String[] args) {
        int a = 1;
        int b = 2;
      // call non-static method
        Demo01 sum = new Demo01();
        int result = sum.sumStatic(a,b);
        System.out.println(result);
    }
//    // static method
//    public static int sum(int x, int y){
//        return x+y;
//    }
    // non-static method
    public int sumStatic(int x, int y){
        return x+y;
    }
}
```

**Difference between static and non-static**

*Static: Load with class, so you do not need to new a class (initialization)*

*Non-static: It needs to be initialized before we call non-static method*

```java
//1. b() method can be called in a() method
public static void a(){
  b();
}
public static void b(){}
//2. b() method can not be called in a() method 
public static void a(){
  b();
}
public void b(){}
```



#### Example 1 using of basic method:

```java
public class Demo01 {
    public static void main(String[] args) {
        int sum = add(1,2);// call function;'1' and '2' are actual parameter
        System.out.println(sum);
    }
    public static int add(int a, int b){
      /*
      ‘public static’: modifier, to tell the compiler how to call the method 
      'int':type of return value
      'add(formal parameter: int a, int b)':function name - CamelCase rule
      
      */
        return a+b;
    }
}
```

#### Example 2 using commond pass value

```java
package method;

public class Demo02 {
    public static void main(String[] args) {
        for (int i = 0; i < args.length; i++) {
            System.out.println(args[i]);

        }
    }
}
/*
(base) 192-168-1-104:src yanglimin$ cd method
(base) 192-168-1-104:method yanglimin$ javac Demo02.java
(base) 192-168-1-104:method yanglimin$ cd ../
(base) 192-168-1-104:src yanglimin$ java method.Demo02
(base) 192-168-1-104:src yanglimin$ java method.Demo02 LILAPE STUDIO

LILAPE
STUDIO

*/
```

#### Example 3 Variable arguments

When number of parameter is not sure, we can use variable arguments

You need to notice: the variable arguments should at the end of method parameter defenition. Here is an example

```java
public void test(int a, int...b){//acceptable
}
public void test(int...b, int a){//unacceptable
}
```

 Here is an example of using variable arguments:

```java
package method;

public class Demo03 {
    public static void main(String[] args) {
        Demo03 demo03 = new Demo03();
        demo03.test(1,3,4,5);// you can pass different number of parameter by using 'int...a' in your method
    }
    public void test(int...a){
        for (int i = 0; i < a.length; i++) {
            System.out.println(a[i]/2);
        }

    }
}

```

