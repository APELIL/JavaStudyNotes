# Multithreading-Runnable interface

1. extends V.S. Runnable

   ![image-20220427235840680](/Users/yanglimin/Library/Application Support/typora-user-images/image-20220427235840680.png)

2. Example of using runnable

   ```java
   package Thread;
   
   public class TestRunnable implements Runnable{
       @Override
       public void run() {
           for (int i = 0; i < 200; i++) {
               System.out.println("run+"+i);
           }
       }
   
       public static void main(String[] args) {
   
           //create object of runnable interface implementation class
           TestRunnable testRunnable = new TestRunnable();
           //create threading object to turn on the multithreading
           Thread thread = new Thread(testRunnable);
           thread.start();
           for (int i = 0; i < 200; i++) {
               System.out.println("main+"+i);
           }
   
       }
   }
   ```

   