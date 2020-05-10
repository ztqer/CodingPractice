![](https://github.com/ztqer/CodingPractice/blob/master/minimum-depth-of-binary-tree/minimum-depth-of-binary-tree.png)
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
    public int run(TreeNode root) {
        if(root==null){
            return 0;
        }
        ArrayList<TreeNode> layer=new ArrayList<>();
        layer.add(root);
        return FindMinDepth(layer,1);
    }
    
    //按层遍历，找到叶子节点即结束，返回深度
    public int FindMinDepth(ArrayList<TreeNode> layer,int count){
        ArrayList<TreeNode> nextLayer=new ArrayList<>();
        for(TreeNode node:layer){
            if(node.left==null&&node.right==null){
                return count;
            }
            if(node.left!=null){
                nextLayer.add(node.left);
            }
            if(node.right!=null){
                nextLayer.add(node.right);
            }
        }
        return FindMinDepth(nextLayer,count+1);
    }
}
```
