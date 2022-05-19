# 3 unsafe thread case & solution

### 1. Unsafely buy ticket 

```java
package ThreeUnsafeThreadCase;

public class ButTicket {

    public static void main(String[] args) {
        BuyTicket buyTicket = new BuyTicket();
        new Thread(buyTicket, "A").start();
        new Thread(buyTicket, "B").start();
        new Thread(buyTicket, "C").start();
    }
}
class BuyTicket implements Runnable{
    boolean flag = true;
    int numT = 10;
    @Override
    public void run() {
        while(flag){
            buy();
        }
    }
    private void buy(){
        if (numT<=0){
            flag = false;
            return;
        }
        try {
            Thread.sleep(100);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println(Thread.currentThread().getName()+" get ticket "+numT--);
        }
    }

// output example->A and C get same ticket 0
/*
C get ticket 1
B get ticket 0
A get ticket -1
*/
```

**Solution - synchronized**

```java
public synchronized void buy(){}
```



### Unsafe bank

```java
package ThreeUnsafeThreadCase;

import java.util.Calendar;

public class UnsafeBank {
    public static void main(String[] args) {
        Account couple = new Account("our money", 100);
        withdraw husband = new withdraw(couple,50, "Ape");
        withdraw wife = new withdraw(couple,100,"Yan");
        husband.start();
        wife.start();
    }
}
class Account{
    String name;
    int balance;
    public Account(String name, int balance){
        this.name = name;
        this.balance = balance;
    }
}
class withdraw extends Thread{
    Account account;
    int moneyToWith;
    int money;
    String name;
    public withdraw(Account account, int moneyToWith, String name){
        super(name);
        this.account = account;
        this.moneyToWith = moneyToWith;
        this.money = money;
    }
    @Override
    public void run() {
        if (account.balance - moneyToWith <0){
            System.out.println("Insufficient balance");
            return;
        }
        try {
            Thread.sleep(100);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        account.balance = account.balance - moneyToWith;
        money = money + moneyToWith;
        System.out.println(Thread.currentThread().getName()+" withdraw "+moneyToWith);
        System.out.println("Balance:"+account.balance);
        System.out.println(this.getName()+ " has "+ money);
    }
}
/*output
Ape withdraw 50
Yan withdraw 100
Balance:-50 - unreasonable*/

```

**Solution - Synchronized block** , *synchronized(Obj){}*

In this programme, synchronized is not working, since *synchronized* is for current class,which is "class withdraw{}". When we want to use synchronization, we need to know which part is changed, e.g., the balance of account has been changed, so we can use synchronized block to solove this issues. See following code.

```java
    @Override
    public void run() {
        //synchronized block
        synchronized (account){
            if (account.balance - moneyToWith <0){
                System.out.println(Thread.currentThread().getName()+" want to withdraw "+ moneyToWith+"$ but insufficient balance for the current account");
//                System.out.println("Insufficient balance");
                return;
            }
            try {
                Thread.sleep(100);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            account.balance = account.balance - moneyToWith;
            money = money + moneyToWith;
            System.out.println(Thread.currentThread().getName()+" withdraw "+moneyToWith);
            System.out.println("Balance:"+account.balance);
            System.out.println(this.getName()+ " has "+ money);
        }
    }
}
```





### 3.Unsafe list

```java
package ThreeUnsafeThreadCase;

import java.util.ArrayList;
import java.util.List;

public class UnsafeList {
    public static void main(String[] args) {
        List<String> list = new ArrayList<String>();
        for (int i = 0; i < 10000; i++) {
            new Thread(()->{
                list.add(Thread.currentThread().getName());
            }).start();
        }
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println(list.size());
    }
}
//output
/*9998*/
//expected output 10000
```

**Solution - synchronized block**

```java
new Thread(()->{
  							synchronized(list){
                list.add(Thread.currentThread().getName());}
            }).start();
```

