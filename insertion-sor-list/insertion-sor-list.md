```java
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
    public ListNode insertionSortList(ListNode head) {
        if(head==null){
            return null;
        }
        ListNode newList=new ListNode(head.val);
        ListNode waiter=head.next;
        while(waiter!=null){
            ListNode tmp=waiter.next;
            newList=Sort(newList,waiter);
            waiter=tmp;
        }
        return newList;
    }
    private ListNode Sort(ListNode head,ListNode n){
        if(n.val<head.val){
            n.next=head;
            return n;
        }
        ListNode now=head;
        ListNode last=null;
        while(n.val>=now.val){
            if(now.next==null){
                now.next=n;
                n.next=null;
                return head;
            }
            if(now.next!=null){
                last=now;
                now=now.next;
            }
        }
        last.next=n;
        n.next=now;
        return head;
    }
}
```
