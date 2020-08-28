![]()
```java
import java.util.*;

public class Finder {
    public int findKth(int[] a, int n, int K) {
        //一个节点n，父节点为(n-1)/2,左子节点为2n+1,右子节点为2n+2
        //从最右侧的非叶子节点开始向前构造大顶堆
        n--;
        for(int i=(n-1)/2;i>=0;i--){
            if(((2*i+1)<=n)&&(a[i]<a[2*i+1])){
                swap(a,i,2*i+1);
            }
            if(((2*i+2)<=n)&&(a[i]<a[2*i+2])){
                swap(a,i,2*i+2);
            }
        }
        //将最大的数放在最后,递归查找剩余部分
        swap(a,0,n);
        if(K-1==0){
            return a[n];
        }
        else{
            return findKth(a,n,K-1);
        }
    }
    
    //交换元素
    public void swap(int[] array,int x,int y){
        int tmp=array[x];
        array[x]=array[y];
        array[y]=tmp;
    }
}
```
