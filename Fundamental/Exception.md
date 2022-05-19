# Exception

```java
package Exception;

public class Demo01 {
    public static void main(String[] args) {
        int a = 1;
        int b = 0;

        /* Exception 1: try catch
        When using try, catch, the program can continue to run even if an exception is found */

//        try{
//            System.out.println(a/b);
//        } catch (ArithmeticException e) {
//            System.out.println("b cannot be 0");
//        }

        /* Exception 2: throw
        The program will be terminated when an exception is found
        */
        new Demo01().test(1,0);
    }
//    public void test(int a, int b){
//        if (b==0){
//            throw new ArithmeticException();
//        }
//    }
    /* Exception 3: throws
    */
    public void test(int a, int b) throws ArithmeticException{
        if (b==0){
            throw new ArithmeticException();
        }
    }
}

```

