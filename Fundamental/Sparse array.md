# Sparse array

1. To save memory 

![WechatIMG282](/Users/yanglimin/iCloud Drive (Archive)/Documents/JAVA/notebook/Image for blogger/Sparse array/WechatIMG282.jpeg)

The following code illustate how program transfer an original 2D array to a sparse array, and conver sparse array to original array by sparse array we generated as well

```java
package Array;

import com.sun.xml.internal.ws.api.model.wsdl.WSDLOutput;

import java.lang.reflect.Array;
import java.util.Arrays;

public class SparseArray {
    public static void main(String[] args) {
        int[][] checkerboard = new int[11][11];
        checkerboard[1][2]=1;
        checkerboard[10][10]=2;
        System.out.println("Original checkerboard");
        Print2DArray(checkerboard);
        //get amount of value that is not 0
        int sum = 0;
        for (int i = 0; i < checkerboard.length; i++) {
            for (int j = 0; j < checkerboard.length; j++) {
                if (checkerboard[i][j]!=0){
                    sum+=1;
                }
            }
        }
        System.out.println("the number of none 0 element:"+sum);
        // create a sparse array
        int[][] SpaseArray = new int[sum+1][3];
        SpaseArray[0][0] = checkerboard.length;
        SpaseArray[0][1] = checkerboard.length;
        SpaseArray[0][2] = sum;
//        System.out.println(Arrays.toString(SpaseArray));
        int count = 0;
        for (int i = 0; i < checkerboard.length; i++) {
            for (int j = 0; j < checkerboard[i].length; j++) {
                if (checkerboard[i][j]!=0){
                    count++;
                    SpaseArray[count][0] = i;
                    SpaseArray[count][1] = j;
                    SpaseArray[count][2] = checkerboard[i][j];
                }
            }
        }
        System.out.println("Sparse Array");
        Print2DArray(SpaseArray);
        System.out.println("===================================");
        System.out.println("From Sparse Array to original Array");
        int[][] array = new int[SpaseArray[0][0]][SpaseArray[0][1]];
        for (int i = 1; i < SpaseArray.length; i++) {
            array[SpaseArray[i][0]][SpaseArray[i][1]] = SpaseArray[i][2];
        }
        
        Print2DArray(array);
    }
    //function Print2DArray
    public static void Print2DArray(int[][] array){
        for (int[] ints : array) {
            for (int anInt : ints) {
                System.out.print(anInt+"\t");
            }
            System.out.println();
        }
    }
}

```

