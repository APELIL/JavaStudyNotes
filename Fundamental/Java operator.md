### Java operator

1. #### arithmetic operators: +, -, *, /, %(surplus), ++, --

   * **some tricky things between a++ and ++a:** 

   ``` java
   public class Demo01 {
       public static void main(String[] args) {
           int a = 3;
           int b = a++;//a = a + 1
           int c = ++a;
           System.out.println(a); // a = 5 due to added twice
           System.out.println(b);// b = 3
           System.out.println(c);// c = 5
       }
   }
   ```

   ​	**a++ means assign first, add later**

   ​	**++a means add first, then assign** 

   * **exponentiation:**

   ```java
   double pow = Math.pow(3,2) // 2^3 2 to power of 3
   ```

2. #### logical operator

   1. and &&
   2. or||
   3. Negate !(a||b)

   * **shortcut cirtcuits operation**: when first boolean is false, program will not process next boolean operation, e.g., 

   ``` java
   int s1 = 5;
   boolean boo = (s1<4)&&(s1++<=5);
   System.out.println("short circuit"+boo);
   System.out.println("s1 value"+s1); // s1 = 5 due to s1 is false, it wont process s1++
   
   // ********
   boolean boo1 = (s1>=5) && (s1++<=5);
   System.out.println("s1 value"+s1); // s1 = 6 due to s1 is true, it will process s1++
   ```

3. #### bit operation

   &, |, ^, ~, >>, <<, >>>

   * **What is the advantage of bit operation?** - more efficiency, the computer only need to shift to left or right, e.g., 

   ``` java
   /*<< *2
   >> /2
   0000 0000 0
   0000 0001 1
   0000 0010 2
   0000 0011 3
   0000 0100 4
   0000 1000 8
   0001 0000 16
   2<<3 indicates shift left 3 bit from 2 (0000 0010 2)
   2<<3 is identical with 2 to power of 3
   */
   ```

   

> Interview question about bit operation:
>
> What is the most efficient way to calculate 2*8 =16?
>
> Answer: using bit operation 2<<3

4. #### another assignment operator 

   +=, -=, *=, /= 

   a += b, a = a + b 

> Interview question about System.out.println()
>
> **When String + some thing, it will automatically convert the later item to String type, so that is the reason why ""+a+b = 1024.**
>
> ``` java
> public class Demo03 {
>     public static void main(String[] args) {
>         int a = 10;
>         int b = 20;
>         // What is the diff between System.out.println(""+a+b) and System.out.println(a+b+"") ? 
>         System.out.println(""+a+b);// out: 1020
>         System.out.println(a+b+"");// out: 30
>     }
> }
> ```

5. #### ternary operator x ? a : b

   x ? a : b 

   if x is true, return a, otherwise return b

   For example:

   ``` java
   public class Demo04 {
       public static void main(String[] args) {
       // ternary operator
       int score = 77;
       String type =  score < 50 ? "fail" : "pass";
           System.out.println(type); // out: pass
       }
   }
   ```

   



