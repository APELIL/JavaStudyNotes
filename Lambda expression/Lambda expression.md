# Lambda expression

1. Why lambda?

   1. Avoid defining too many anonymous inner class
   2. Simplify the code, keep the core part of code

2. Premise of lambda

   1. Requires a functional interface

   2. ```java
      //if you want to use lambda like this way, only one line code is acceptable
      like = () -> System.out.println("I like lambda expression - lambda expression2");
      ```

3. The following code illustrates the simplified process from outer class to lambda

```java
package com.lilrich.lambda;

import java.sql.SQLOutput;

public class TestLambda {
    //2. static inner class
    static class Like2 implements ILike{
        @Override
        public void lambda() {
            System.out.println("I like lambda expression - static inner class");
        }
    }
    public static void main(String[] args) {
        ILike like = new Like1();
        //1. outer class
        like.lambda();
        //2. static inner class
        like = new Like2();
        like.lambda();
        //3. local inner class -> put class in the main() method
        class Like3 implements ILike{
            @Override
            public void lambda() {
                System.out.println("I like lambda expression - local inner class");
            }
        }
        like = new Like3();
        like.lambda();

        //4. anonymous inner class
        like = new ILike() {
            @Override
            public void lambda() {
                System.out.println("I like lambda expression - anonymous inner class");
            }
        };
        like.lambda();

        //5. lambda expression1
        like = ()->{
            System.out.println("I like lambda expression - lambda expression1");
            System.out.println("I love lambda");
        };
      	like.lambda();
        //6. lambda expression2 remove curly braces
        like = () -> System.out.println("I like lambda expression - lambda expression2");
        like.lambda();
    }
}

//Functional interface -> only one abstract method
interface ILike{
    void lambda();
}

//1.outer class
class Like1 implements ILike{
    @Override
    public void lambda() {
        System.out.println("I like lambda expression - outer class");
    }
}
```

