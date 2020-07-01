#### 题目
给定一个链表，返回链表开始入环的第一个节点。 如果链表无环，则返回 null。

为了表示给定链表中的环，我们使用整数 pos 来表示链表尾连接到链表中的位置（索引从 0 开始）。 如果 pos 是 -1，则在该链表中没有环。

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
 * @param {ListNode} head
 * @return {ListNode}
 */
var detectCycle = function(head) {
    var slowP = head, fastP = head;
    while(fastP) {
        if(fastP.next == null) return null;
        slowP = slowP.next;
        fastP = fastP.next.next;
        if (slowP == fastP) {
            fastP = head;
            while(true) {
                if(slowP == fastP){
                    return slowP;
                }
                fastP = fastP.next;
                slowP = slowP.next;
            }
        }
    }
    return null;
};
```
