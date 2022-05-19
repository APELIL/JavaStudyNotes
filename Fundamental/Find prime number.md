# Find prime number

#### What is prime number? Divisible only by 1 and itself

```java
package loopPrac;

public class primeNumber {
    //Question ： find out the prime number between 101-105
    public static void main(String[] args) {
        outer: for (int i = 101; i<150; i++){
            for (int j = 2; j<i/2;j++){//half of the number
                if(i%j==0){// find out the number that can divide i
                    continue outer;
                }
            }
            System.out.print(i+"\t");
        }
    }
}

```

