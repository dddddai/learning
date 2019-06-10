class Solution(object):
    def insertIntoBST(self, root, val):
        """
        :type root: TreeNode
        :type val: int
        :rtype: TreeNode
        """
        if root is None:
            return TreeNode(val)
        
        cur=root
        while 1:
            if val<cur.val:
                if cur.left:
                    cur=cur.left
                    continue
                cur.left=TreeNode(val)
                break
            else:
                if cur.right:
                    cur=cur.right
                    continue
                cur.right=TreeNode(val)
                break
                
        return root
        
        
        
        
        
class Solution {
    public TreeNode insertIntoBST(TreeNode root, int val) {
        if(root==null){
            return new TreeNode(val);
        }
        TreeNode cur=root;
        while(true){
            if(val<cur.val){
                if(cur.left==null){
                    cur.left=new TreeNode(val);
                    break;
                }else{
                    cur=cur.left;
                }
            }else{
                if(cur.right==null){
                    cur.right=new TreeNode(val);
                    break;
                }else{
                    cur=cur.right;
                }
            }
        }
        return root;
    }
}        
       
