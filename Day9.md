#### 题目
给定一个单链表，其中的元素按升序排序，将其转换为高度平衡的二叉搜索树。

本题中，一个高度平衡二叉树是指一个二叉树每个节点 的左右两个子树的高度差的绝对值不超过 1。

示例:

给定的有序链表： [-10, -3, 0, 5, 9],

一个可能的答案是：[0, -3, 9, -10, null, 5], 它可以表示下面这个高度平衡二叉搜索树：
```javascript

      0
     / \
   -3   9
   /   /
 -10  5 

```
来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/convert-sorted-list-to-binary-search-tree
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
#### 题解
#### 代码
```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {ListNode} head
 * @return {TreeNode}
 */
var sortedListToBST = function(head) {
    var buildTree = function(head,tail) {
        if (head === tail){
            return null
        }
        var p1 = head,
            p2 = head;
        while(p2 !== tail){
            p2 = p2.next;
            if(p2 !== tail){
                p1 = p1.next;
                p2 = p2.next;
            }
        }
        var treeNode = new TreeNode(p1.val);
        treeNode.left = buildTree(head,p1);
        treeNode.right = buildTree(p1.next,tail);
        return treeNode;
    }
    return buildTree(head, null);
};
```
