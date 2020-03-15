![](https://github.com/ztqer/CodingPractice/blob/master/construct-binary-tree-from-preorder-and-inorder-traversal/construct-binary-tree-from-preorder-and-inorder-traversal.png)
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
//前序->根,中序找到根->左右子树,前序根据子树大小->左右子树
public class Solution {
    public TreeNode buildTree(int[] preorder, int[] inorder) {
        if(preorder.length==0){
            return null;
        }
        TreeNode root=new TreeNode(preorder[0]);
        setChildren(preorder, inorder, root);
        return root;
    }
    private void setChildren(int[] preorder, int[] inorder, TreeNode root){
        int length=preorder.length;
        if(length==1){
            return;
        }
        int inRoot=0;
        for(int i=1;i<=length;i++){
            if(inorder[i-1]==preorder[0]){
                inRoot=i;
            }
        }
        int[] preLeft=new int[inRoot-1];
        int[] preRight=new int[length-inRoot];
        int[] inLeft=new int[inRoot-1];
        int[] inRight=new int[length-inRoot];
        for(int i=1;i<=inRoot-1;i++){
            preLeft[i-1]=preorder[i];
            inLeft[i-1]=inorder[i-1];
        }
        for(int i=inRoot+1;i<=length;i++){
            preRight[i-inRoot-1]=preorder[i-1];
            inRight[i-inRoot-1]=inorder[i-1];
        }
        if(inRoot-1>=1){
            TreeNode left=new TreeNode(preLeft[0]);
            root.left=left;
            setChildren(preLeft,inLeft,left);
        }
        if(length-inRoot>=1){
            TreeNode right=new TreeNode(preRight[0]);
            root.right=right;
            setChildren(preRight,inRight,right);
        }
    }
}
```
