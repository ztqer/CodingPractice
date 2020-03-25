![](https://github.com/ztqer/CodingPractice/blob/master/longest-palindromic-substring/longest-palindromic-substring.png)
```java
import java.util.ArrayList;
public class Solution {
    public String longestPalindrome(String s) {
        if(s==null){
            return s;
        }
        int length1=s.length();
        //给每个字符两边加上不存在于字符串的符号，保证必为奇数
        ArrayList<String> str=new ArrayList<>();
        str.add("!");
        for(int i=1;i<=length1;i++){
            str.add(String.valueOf(s.charAt(i-1)));
            str.add("!");
        }
        int length2=length1*2+1;
        //用一个数组存储每个字符为中心的最大回文半径
        int[] radius=new int[length2];
        //存储当前所有回文子串所能到达的最右端与该子串的中心
        int center=1;
        int right=1;
        //存储半径数组中的最大值所在位置
        int max=1;
        for(int i=2;i<length2;i++){
            //当前字符在范围内
            //1.完全包含于回文子串->找对称点
            //2.部分包含于回文子串->在对称点半径基础上往外扩展找最大半径
            //3.不在回文子串内->往外扩展找最大半径
            radius[i-1]=right>i?Math.min(radius[2*center-i-1],right-i):1;
            for(int t=radius[i-1];t<=Math.min(i-1,length2-i);t++){
                if(!str.get(i-t-1).equals(str.get(i+t-1))){
                    radius[i-1]=t-1;
                    break;
                }
                else{
                    radius[i-1]=t;
                }
            }
            //更新center，right和max
            if(radius[i-1]+i>right){
                right=radius[i-1]+i;
                center=i;
            }
            if(radius[i-1]>radius[max-1]){
                max=i;
            }
        }
        //根据max和radius[max-1]找到原来的字符串
        StringBuffer sb=new StringBuffer();
        for(int i=1;i<=2*radius[max-1]+1;i++){
            if(!str.get(max-radius[max-1]-2+i).equals("!")){
                sb.append(str.get(max-radius[max-1]-2+i));
            }
        }
        return sb.toString();
    }
}
```
