![]()
```java
import java.util.*;

public class Solution {
    public int numDistinct (String S, String T) {
        int l1=S.length();
        int l2=T.length();
        //dp[x][y]表示S前y个字符的子串中等于T前x个字符的子串的子序列个数
        int[][] dp=new int[l2+1][l1+1];
        //额外设置一行一列表示空串，并且S的任何子串构成空串的可能组合都是1
        for(int i=0;i<=l1;i++){
            dp[0][i]=1;
        }
        for(int i=1;i<=l2;i++){
            for(int j=1;j<=l1;j++){
                //如果字符相同，组合数为以下两者之和
                //1.使用这个字符，组合数即两者各忽视该字符-dp[i-1][j-1]
                //2.删除这个字符，组合数即母串忽视该字符-dp[i][j-1]
                if(S.charAt(j-1)==T.charAt(i-1)){
                    dp[i][j]=dp[i-1][j-1]+dp[i][j-1];
                }
                //如果字符不同，相当于这个字符不起作用-dp[i][j-1]
                else{
                    dp[i][j]=dp[i][j-1];
                }
            }
        }
        return dp[l2][l1];
    }
}
```
