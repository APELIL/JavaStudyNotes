# Print the triangle (practice)

You need to print a triangle like this:

```java
```



You can think like this way:

1. print a blank triangle 1

![image-20220327143229004](/Users/yanglimin/Library/Application Support/typora-user-images/image-20220327143229004.png)

```java
package loopPrac;

public class printTriangle {
    public static void main(String[] args) {
        for (int i = 0; i < 5; i++) {
            for (int j = 5; j > i; j--) {
                System.out.print("-");
            }
            for (int j = 0; j <= i; j++) {
                System.out.print("*");
            }
            for (int j = 0; j < i; j++) {
                System.out.print("*");
            }
            System.out.println();
            
        }
    }
}

```

