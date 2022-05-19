### 	Java comments

1. Line comments: //

2. Block comments: /*  */

3. JavaDoc: 

   /**

   */

### 	Java identifier

1. All identifier should start with "A-Z", "a-z", "$" or "_"
2. Java is case sensitive, e.g., "Man" is not equal to "man"

### 	Java data type

> [*Java is a **strongly typed programming language** because every variable must be declared with a data type. A variable cannot start off life without knowing the range of values it can hold, and once it is declared, the data type of the variable cannot change*] (https://stackoverflow.com/questions/33958767/if-java-is-strongly-typed-then-why-does-this-code-compile#:~:text=Java%20is%20a%20strongly%20typed%20programming%20language%20because,the%20data%20type%20of%20the%20variable%20cannot%20change.).

### 	Java has two data type

1. Primitive type

   1. Integer: byte(1bits), short(2bits), int(4bits), long(8bits)
   2. Float: float(4bits), double(8bits)
   3. String: char(2bits)
   4. Boolean: true & false(1bit)

   ```java
   public class demo02 {
       public static void main(String[] args) {
   //         8 basic data type
   // Integer type
           int num1 = 10; // the most common one
           byte num2 = 20;
           short num3 = 30;
           long num4 = 30L;
   //        Float
           float num5 = 10.1F;
           double num6 = 2.111123123123;
   //        Character
           char x = 'A';//only one letter allowed
           String xx = "AAA";
   //        Boolean
           boolean flag = true;
       }
   }
   ```

   ### Data conversion

   1 byte = 8 bit

   1024 bit = 1KB

   1KB = 1M

   1024M = 1G

   ### It is better to use full float for comparison

   ``` java
   public class demo03 {
       public static void main(String[] args){
   //      binary 0b   octal 0 hex 0x (0~9 A~F)
           int n1 = 010;// n1 = 8
           int n2 = 0x10; //n2 = 16
   //        float limited diversity approximate
   
   //        =========================
   //        some tricky things:
           float n3 = 0.2f;
           double n4 = 2.0/10;
           System.out.println(n3==n4);//false
   //        as can be seen from above codes, we would better use same type to compare things
           float n5 = 2.0f/10;
           System.out.println(n3==n5);
   //        =========================
       }
   
   }
   ```

    ### Unicode

   ~~~ java 
           char a = 'a';
           char b = 'b';
           System.out.println((int)a); // unicode 97
           System.out.println((int)b); // unicode 98 
   ~~~

   #### The way to use unicode

   ```java
   char unicode = '\u0062'; // the way to use unicode 
   System.out.println(unicode); // b 
   ```

2. Reference type

   

 