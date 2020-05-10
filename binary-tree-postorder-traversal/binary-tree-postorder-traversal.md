```java
/**
 * Definition for binary tree
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
import java.util.*;

public class Solution {
    public ArrayList<Integer> postorderTraversal(TreeNode root) {
        ArrayList<Integer> list=new ArrayList<>();
        if(root==null){
            return list;
        }
        Stack<TreeNode> stack=new Stack<>();
        stack.push(root);
        TreeNode node=null;
        TreeNode last=null;
        while(!stack.isEmpty()){
            //查看根节点不取出
            node=stack.peek();
            //1.到达叶子结点 2.孩子都已经被取出 则取出
            if((node.left==null&&node.right==null)||
               (last!=null&&(node.right==last||node.left==last))){
                stack.pop();
                list.add(node.val);
                last=node;
            }
            else{
                if(node.right!=null){
                    stack.push(node.right);
                }
                if(node.left!=null){
                    stack.push(node.left);
                }
            }
        }
        return list;
    }
}
```
