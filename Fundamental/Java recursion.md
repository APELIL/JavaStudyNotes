 # Java recursion

Why recursion?

Using short code to solve some complex problems

While using recursion, we need to pay attention:

1. Recursive header: when not to call its own method; *the program will be an infinite loop, if there is no recursive head*
2. Recursive body: when to call it own method

Here is an example of using recusion achieve factorial:

```java
package recursive;

public class factorial {
    public static void main(String[] args) {
        int result = fac(3);
        System.out.println(result);
    }
    public static int fac(int n){
        if(n==1){//recursive header
            return 1;
        }else {//recursive body
            return n*fac(n-1);
        }
    }
}
/* the procedure will process as (if input is 3):
3->3*fac(2)->3*2*fac(1)->3*2*1=6
```

