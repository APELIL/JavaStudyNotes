### Java value conversion

From low to high:

Byte, short, char-> int -> long -> float -> double



Cast: from high level to low one, e.g., 

```java
int i = 128
  byte b = (byte)i 
  //output b = -128 memory overflow
```

 Notes:

1. boolean value is unconversionable 
2. cast may lead to memory overflow, e.g., 

``` java
int money = 10_0000_0000; // JDK new feature: numbers can be separted by "_"
int year = 20;
int total = money*year; // memory overflow 
//solution:
long total = money*((long)year);
```



### Java variable

While define a vairable:

1. type
2. name 
3. value

``` java
String temp = "Java"
```

**Local variable**

1. Declaring and initializing values

**Instance variable**

1. Declaring in the class

2. If there is no initilizing values, it will return defualt value (**boolean**:false, **basic types**: 0, **other type**: null)

3. **Example for using instance variable**

   ``` java
   public class Demo05 {
       String i1;
       int i2;
       public static void main(String[] args) {
           Demo05 instanceVariable = new Demo05();
           System.out.println(instanceVariable.i1);//out null
       }
   }
   ```

   

**Class variable (e.g., static)**

1. Can be used in another function 

**Constant**

``` java
pulic class Demo{
static final pi = 3.14
final static pi = 3.14
public static void main(String[] args){
  System.output.println(pi)
}
} 
// No order requirement 
// They are identical 
```

#### Variable specification

1. Class variable: monthSalary (hump principle)

2. Local variable: start with lower case and hump principle

3. Constant: upper case and underscore e.g., MAX_VALUE

4. Class name: start with upper case e.g., Demo01

   ``` java
   public class Demo01{
     
   }
   ```

   

5. Function name: start with lower case and hump principle e.g., run(), runMain()