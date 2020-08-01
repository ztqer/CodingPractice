![](https://github.com/ztqer/CodingPractice/blob/master/最小的K个数/最小的K个数.png)
```java
import java.util.*;

public class Solution {
    public ArrayList<Integer> GetLeastNumbers_Solution(int [] input, int k) {
        ArrayList<Integer> result=new ArrayList<>();
        if(input==null||input.length==0||k==0||k>input.length){
            return result;
        }
        for(int i=input.length;i>=input.length-k+1;i--){
            adjustHeap(input,i);
            result.add(input[i-1]);
        }
        return result;
    }
    
    //原地调整小顶堆，将排好的放在最后
    //坐标n的父节点为（n-1）/2（自动舍小数部分），左子节点为2n+1
    public static void adjustHeap(int[] array,int length){
        //从右向左，从下到上，检查所有非叶子节点
        for(int i=(length-1)/2;i>=0;i--){
            if((i+1)*2<=length-1 && array[(i+1)*2]<array[i]){
                swap(array,i,(i+1)*2);
            }
            if(i*2+1<=length-1 && array[i*2+1]<array[i]){
                swap(array,i,i*2+1);
            }
        } 
        swap(array,0,length-1);
    }
    
    //交换元素
    public static void swap(int[] array,int a,int b){
        int tmp=array[a];
        array[a]=array[b];
        array[b]=tmp;
    }
}
```
