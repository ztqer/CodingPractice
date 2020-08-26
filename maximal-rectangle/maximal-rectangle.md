![](https://github.com/ztqer/CodingPractice/blob/master/maximal-rectangle/maximal-rectangle1.png)
```java
import java.util.*;

public class Solution {
    public int maximalRectangle(char[][] matrix){
        if (matrix==null || matrix.length==0 || matrix[0].length==0)
            return 0;
        int m=matrix.length, n=matrix[0].length;
        int max=0;
        int[] h=new int[n+1];
        //额外添加一个空列，使n-1列的直方图能在循环中被检查
        h[n]=0;
        for(int i=0;i<m;i++){
            //转化成直方图的形式
            for(int j=0;j<=n-1;j++){
                if (matrix[i][j]=='1'){
                    h[j]++;
                }
                else{
                    h[j]=0;
                }
            }
            //当递增时，向栈中添加
            //当出现下降时，出栈直到找出比此列更低的列
            //计算出面积并比较更新最大面积
            Stack<Integer> stack=new Stack<Integer>();
            stack.push(-1);
            for(int j=0;j<=n;j++){
                while(stack.peek()!=-1 && h[j]<h[stack.peek()]){
                    int top=stack.pop();
                    max = Math.max(max,(j-1-stack.peek())*h[top]);
                }
                stack.push(j);
            }
        }
        return max;
    }
}
```
![](https://github.com/ztqer/CodingPractice/blob/master/maximal-rectangle/maximal-rectangle1.png)
