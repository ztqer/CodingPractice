![]()
```java
import java.util.*;
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode mergeKLists(ArrayList<ListNode> lists) {
        if(lists==null||lists.size()==0){
            return null;
        }
        //定义头节点值做比较的优先级队列
        PriorityQueue<ListNode> queue=new PriorityQueue<ListNode>(lists.size(), new Comparator<ListNode>() {
            @Override
            public int compare(ListNode n1, ListNode n2) {
                if(n1.val==n2.val) {
                    return 0;
                }
                return n1.val>n2.val?1:-1;
            }
        });
        //每次从队列取出最小的点添加到新链表，同时把这个点除去自身的子链表放回队列
        for(ListNode node:lists){
            if(node!=null){
                queue.add(node);
            }
        }
        //预置一个头节点，把真正头节点的操作能放进循环里
        ListNode head=new ListNode(0);
        ListNode now=head;
        while(!queue.isEmpty()){
            now.next=queue.poll();
            now=now.next;
            if(now.next!=null){
                queue.add(now.next);
            }
        }
        return head.next;
    }
}
```
