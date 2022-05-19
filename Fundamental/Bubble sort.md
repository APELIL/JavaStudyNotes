# Bubble sort

```java
package Array;

import java.util.Arrays;

public class BubbleSort {
    public static void main(String[] args) {
        int[] nums = {1,3,4,2,5};
        int[] result = BubbleSort(nums);
        System.out.println(Arrays.toString(result));
    }
    public static int[] BubbleSort(int[] array){
        int temp;
        for (int i = 0; i < array.length-1; i++) {
            for (int j = 0; j < array.length-1-i; j++) {
                if (array[j]<array[j+1]){
                    temp = array[j+1];
                    array[j+1] = array[j];
                    array[j] =temp;
                }
            }

        }
        return array;
    }
}

```

