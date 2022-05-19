# Array

1. How to create an array?

   ```java 
   // method 1
   //dataType[] name = value
   int[] nums;// declare an array
   // method 2
   //dataType name[] = value
   int nums[];
   ```

     1. Static initialization

        ```java 
        int[] a = {1,2,3}
        ```

   2.  Dynamic initialization

      ```java
      int[] a;
      a = new int[3];
      a[0] = 1;
      ```

      

2. How to use an array?

- *Array in for loop:*

```java
int[] nums;//1. declare an array
nums = new int[3];//2. create an array
nums[0] = 1; //3. assign a value
nums[1] = 2;
nums[2] = 3;
System.output.println(nums[0]);//4.print a value
// 1. print all of elements 
for(int i = 0; i<nums.length;i++){
  System.output.println(nums[i]);
}
// 2. calculate the sum of an array
int sum = 0
for(int i = 0; i<nums.length;i++){
  sum+=nums[i];
}
//3. fint the max element of array
int max = nums[0];
for(int i = 0; i<nums.length;i++){
  if(array[i]>max){
    max = array[i];
  }
}
```

- *Array in for each loop:*

```java
for(int num: nums){
  System.output.println(num)
}
```

- *Invert an array:*

```java
public static int[] invert(int[] array){
  int[] invert = new int[array.length];
  for (int i = 0,j = invert.length-1; i array.length;i++,j--) {
            invert[i] = array[j];
        }
        return invert;
    }
```

3. Memory analysis

   1. Java memory

      1. heap to store new object and array 

         ```java
         nums = new int[3];//2. create an array
         nums[0] = 1; //3. assign a value
         nums[1] = 2;
         nums[2] = 3;
         ```

         

      2. stack to store variable type

         ```java
         int[] nums;
         ```

4. Multidimensional Arrays