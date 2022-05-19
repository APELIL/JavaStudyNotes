## Scanner,while&do while, switch, break&continue

1. The difference between next() and nextLine()

   ```java
   /*
   nextLine()
   **/
   public class next_nl {
       public static void main(String[] args) {
           Scanner scanner = new Scanner(System.in);
         //  String in = scanner.nextLine();
        		String in = scanner.next();
           System.out.println("you entered:"+in);
           scanner.close();
       }
   }
   // output of nextLine():
   //hello lil
   //you entered:hello lil
   
   //output of next(): - while encountering space after a character, it will igonre the following things
   //hello lil
   //you entered:hello
   ```

   

2. Switch

   ```java
   import java.util.Scanner;
   
   public class switchDemo01 {
       public static void main(String[] args) {
           String name = "lilape";
           Scanner scanner = new Scanner(System.in);
           String in = scanner.nextLine();
           switch (in) {
               case "lilape":
                   System.out.println("LILAPE");
                   break;
           }
       }
   
   }
   
   ```

   

3. Case penetration phenomenon  (you should add break in the end of case)

   ```java
   switch (o) {
               case "+":
                   result = a + b;
                   break;
   }
   ```

   

4. Switch support not only char but also string type(convert string to hashcode)

4. the difference between while() and do while()
   1. while(), do judgement before execute 
   2. do while(), execute before do judgement, and do while() ensure the programm can be executed at least once 
   
4. The difference between break and continue
   
    ```java
    package loop;
    
    public class break_continue {
        public static void main(String[] args) {
            int i = 0;
            while (i<100){
                i++;
                if(i%10==0) {
                    System.out.println();
    //                break;//end the while loop
                    continue;//jump out if statement
                }
                System.out.print(i+"\t");
            }
        }
    }
    // output of break:
    1	2	3	4	5	6	7	8	9	
    // output of continue 
    1	2	3	4	5	6	7	8	9...
    ....
    91	92	93	94	95	96	97	98	99	
    ```
   
   