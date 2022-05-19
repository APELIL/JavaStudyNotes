# Deadlock

> Deadlock in Java means a thread is waiting for an object lock that is accuquired by another thread, and second thread is waiting for a object lock that accuquired by the first thread.

*For example, two boys are playing, boy 1 has a car, boy 2 has a pistol, they both want to play with each other's toys, but they don't want to put down their own toys, which creates a deadlock.*

CODE:

```java
package Thread;

public class DeadLock {
    public static void main(String[] args) {
        play boy1 = new play("Mike", 0);
        play boy2 = new play("James", 1);
        boy1.start();
        boy2.start();
    }
}

//1.Toy 1
class Toy1{}
//2.Toy 2
class Toy2{}

//play
class play extends Thread {
    //simulate only one resource is available by using static
    static Toy1 t1 = new Toy1();
    static Toy2 t2 = new Toy2();

    int choice;
    String name;

    public play(String name, int choice) {
        this.name = name;
        this.choice = choice;
    }

    @Override
    public void run() {
//        super.run();
        try {
            PlayTogether();
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }

    public void PlayTogether() throws InterruptedException {
        if (choice == 0) {
            synchronized (t1) { //lock t1
                System.out.println(this.name + " play toy1");
                Thread.sleep(1000);
                synchronized (t2) { // boy 1 want to get lock t2
                    System.out.println(this.name + " want to play toy2");
                }
            }
        } else {
            synchronized (t2) { //lock t2
                System.out.println(this.name + " play toy2");
                Thread.sleep(1000);
                Thread.sleep(2000);
                synchronized (t1) { // boy 2 want to get lock t1
                    System.out.println(this.name + " want to play toy1");
                }
            }
        }
    }
}
//output -> the programme will stuck there
/*
Mike play toy1
James play toy2
*/
```

**Solution** - *Ensure that a thread does not hold two locks at the same time*

```JAVA
   public void PlayTogether() throws InterruptedException {
        if (choice == 0) {
            synchronized (t1) { //lock t1
                System.out.println(this.name + " play toy1");
                Thread.sleep(1000);
            }
            synchronized (t2) { // boy 1 want to get lock t2
                System.out.println(this.name + " want to play toy2");
            }
        } else {
            synchronized (t2) { //lock t2
                System.out.println(this.name + " play toy2");
                Thread.sleep(2000);
            }
            synchronized (t1) { // boy 2 want to get lock t1
                System.out.println(this.name + " want to play toy1");
            }
        }
    }
```

