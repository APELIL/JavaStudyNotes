# Multithreading - Race(turtle&rabbit)

```java
package Thread;

public class TestRace implements Runnable{
    private static String winner;
    @Override
    public void run() {
        for (int i = 0; i <= 100; i++) {
            boolean flag = gameOver(i);
            if (flag){
                System.out.println(flag);
                System.exit(0);
            }
            if (Thread.currentThread().getName().equals("rabbit")&&i%10==0){
                try {
                    Thread.sleep(100);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
            System.out.println(Thread.currentThread().getName()+" run "+i+" step");
        }
    }
    private boolean gameOver(int step){
        if(winner!=null){
            return true;
        }{
            if (step>=100){
            System.out.println(Thread.currentThread().getName()+" win");
            return true;
        }
        }
        return false;
    }

    public static void main(String[] args) {
        TestRace testRace = new TestRace();
        new Thread(testRace,"rabbit").start();
        new Thread(testRace,"turtle").start();

    }
}

```

