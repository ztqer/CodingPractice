![]()
```java
import java.util.*;

/*
 * public class TreeNode {
 *   int val = 0;
 *   TreeNode left = null;
 *   TreeNode right = null;
 * }
 */
/*
 * public class ListNode {
 *   int val;
 *   ListNode next = null;
 * }
 */

public class Solution {
    /**
     * 
     * @param head ListNode类 
     * @return TreeNode类
     */
    public TreeNode sortedListToBST (ListNode head) {
        return buildTree(head,null);
    }
    
    public static TreeNode buildTree(ListNode head,ListNode tail)
    {
        //特殊情况
        if(head==tail){
            return null;
        }
        //通过快慢指针找到链表中间节点
        ListNode fast=head;
        ListNode slow=head;
        while(fast!=tail&&fast.next!=tail){
            fast=fast.next.next;
            slow=slow.next;
        }
        //创建根节点并分割两个子链表递归
        TreeNode root=new TreeNode(slow.val);
        root.left=buildTree(head,slow);
        root.right=buildTree(slow.next,tail);
        return root;
    }
}
```
