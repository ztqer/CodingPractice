![]()
```java
import java.util.*;

public class Solution {
    public int[] LRU (int[][] operators, int k) {
        LinkedHashMap<Integer,Integer> map=new LinkedHashMap<>();
        ArrayList<Integer> result=new ArrayList<>();
        for(int[] operator:operators){
            if(operator[0]==1){
                int x=operator[1];
                int y=operator[2];
                if(map.containsKey(x)){
                    map.remove(x);
                }
                else if(map.size()==k){
                    map.remove(map.keySet().toArray()[0]);
                }
                map.put(x,y);
            }
            else if(operator[0]==2){
                int x=operator[1];
                if(map.containsKey(x)){
                    int y=map.get(x);
                    result.add(y);
                    map.remove(x);
                    map.put(x,y);
                }
                else{
                    result.add(-1);
                }
            }
        }
        int[] res=new int[result.size()];
        for(int i=0;i<=result.size()-1;i++){
            res[i]=result.get(i);
        }
        return res;
    }
}
```
