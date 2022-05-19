# Static proxy - marry example

1. How to implement static proxy？

   1. The proxy object and real object need to implement same interface
   2. Proxy object need to proxy real role (e.g., Wedding company help you to prepare wedding)

2. Benefit of static proxy:

   1. Proxy object can do many operations that real object cannot
   2. Real object can focus on its own task

3. Example of wedding company

   ```java
   package staticProxy;
   
   public class TestStaticProxy {
       public static void main(String[] args) {
           Customer customer = new Customer();
           WeddingCompany weddingCompany = new WeddingCompany(customer);
           weddingCompany.HappyMarry();
       }
   }
   
   //interface
   interface Marry{
       void HappyMarry();
   }
   //Customer: you
   class Customer implements Marry{
       @Override
       public void HappyMarry() {
           System.out.println("You're getting married");
       }
   }
   
   //Proxy: Wedding company
   class WeddingCompany implements Marry{
       //Proxy target
       private Marry target;
       //Constructor
       public WeddingCompany(Marry target) {
           this.target = target;
       }
   
       @Override
       public void HappyMarry() {
           beforeMarry();
           this.target.HappyMarry();
       }
   
       private void beforeMarry() {
           System.out.println("Wedding company is planning the wedding for you");
       }
   }
   
   ```

   