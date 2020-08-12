```java
import java.util.*;

public class Solution {
    public int candy (int[] ratings) {
        int[] candynum=new int[ratings.length];
        for(int i=0;i<=ratings.length-1;i++){
            candynum[i]=1;
        }
        //从左到右，保证右侧得分高的人糖果多
        for(int i=0;i<=ratings.length-1;i++){
            if(i+1<=ratings.length-1){
                if(ratings[i+1]>ratings[i]&&candynum[i+1]<=candynum[i]){
                    candynum[i+1]=candynum[i]+1;
                }
                if(ratings[i+1]<ratings[i]&&candynum[i+1]>=candynum[i]){
                    candynum[i]=candynum[i+1]+1;
                }
            }
        }
        //从右到左，保证左边得分高的人糖果多
        for(int i=ratings.length-1;i>=0;i--){
            if(i-1>=0){
                if(ratings[i-1]>ratings[i]&&candynum[i-1]<=candynum[i]){
                    candynum[i-1]=candynum[i]+1;
                }
                if(ratings[i-1]<ratings[i]&&candynum[i-1]>=candynum[i]){
                    candynum[i]=candynum[i-1]+1;
                }
            }
        }
        int result=0;
        for(int i=0;i<=ratings.length-1;i++){
            result+=candynum[i];
        }
        return result;
    }
}
```
