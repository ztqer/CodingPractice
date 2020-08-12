![]()
```java
import java.util.*;

/*
 * public class ListNode {
 *   int val;
 *   ListNode next = null;
 * }
 */

public class Solution {
    public ListNode rotateRight (ListNode head, int k) {
        //特殊情况
        if(k==0||head==null){
            return head;
        }
        int count=0;
        Stack<ListNode> stack=new Stack<>();
        ListNode node=head;
        stack.push(head);
        count++;
        while(node.next!=null){
            node=node.next;
            stack.push(node);
            count++;
        }
        //无法进入for循环，node还指向尾节点，故单独return
        if(count==k){
            return head;
        }
        //k超过链表长度相当于转动k%count次
        if(count<k){
            k%=count;
        }
        //从栈中反向取出节点拼接到头上
        ListNode next=head;
        for(int i=1;i<=k;i++){
            node=stack.pop();
            node.next=next;
            next=node;
        }
        ListNode result=node;
        //将新尾节点指向null
        node=stack.pop();
        node.next=null;
        return result;
    }
}
```
