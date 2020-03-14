![]()
```
import java.util.Stack;
/*
public class ListNode {
    int val;
    ListNode next = null;

    ListNode(int val) {
        this.val = val;
    }
}*/
public class Solution {
    public ListNode FindKthToTail(ListNode head,int k) {
        if(head==null||k<=0){
            return null;
        }
        Stack<ListNode> s1=new Stack<>();
        s1.push(head);
        ListNode now=head.next;
        while(now!=null){
            s1.push(now);
            now=now.next;
        }
        for(int i=1;i<=k-1;i++){
            if(s1.isEmpty()){
                return null;
            }
            s1.pop();
        }
        if(s1.isEmpty()){
            return null;
        }
        return s1.pop();
    }
}
```
