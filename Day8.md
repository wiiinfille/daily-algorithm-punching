#### 题目
多级双向链表中，除了指向下一个节点和前一个节点指针之外，它还有一个子链表指针，可能指向单独的双向链表。这些子列表也可能会有一个或多个自己的子项，依此类推，生成多级数据结构，如下面的示例所示。

给你位于列表第一级的头节点，请你扁平化列表，使所有结点出现在单级双链表中。

#### 题解

#### 代码
```javascript
var flatten = function (head) {

    if(!head || !head.next) return head
    let res = head
    while (head) {
        if(head.child){
            let nextHead = head.next
            let childHead = flatten(head.child)
            head.child = null

            head.next = childHead
            childHead.pre = head

            let childEnd = childHead
            while (childEnd && childEnd.next){
                childEnd = childEnd.next
            }
            childEnd.next = nextHead
            nextHead.pre = childEnd
            break
        }
        head = head.next
    }

    return res
};
```
