#### 题目
使用栈实现队列的下列操作：

push(x) -- 将一个元素放入队列的尾部。
pop() -- 从队列首部移除元素。
peek() -- 返回队列首部的元素。
empty() -- 返回队列是否为空。
示例:

MyQueue queue = new MyQueue();

queue.push(1);
queue.push(2);
queue.peek(); // 返回 1
queue.pop(); // 返回 1
queue.empty(); // 返回 false
说明:

你只能使用标准的栈操作 -- 也就是只有 push to top, peek/pop from top, size, 和 is empty 操作是合法的。
你所使用的语言也许不支持栈。你可以使用 list 或者 deque（双端队列）来模拟一个栈，只要是标准的栈操作即可。
假设所有操作都是有效的 （例如，一个空的队列不会调用 pop 或者 peek 操作）。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/implement-queue-using-stacks
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
#### 题解
#### 代码
```javascript
/**循环队列 */
class MyQueue {
    constructor() {
        this.pushArr = [];
        this.popArr = [];
    }
    /**将一个元素放入队列的尾部 */
    push(value) {
        this.pushArr.push(value);
    }
    /**从队列首部移除元素 */
    pop() {
        if(!this.popArr.length){
            while(this.pushArr.length){
                this.popArr.push(this.pushArr.pop());
            }
        }
        return this.popArr.pop();
    }
    /**返回队列首部的元素 */
    peek() {
        if(!this.popArr.length){
            while(this.pushArr.length){
                this.popArr.push(this.pushArr.pop());
            }
        }
        return this.popArr[this.popArr.length - 1];
    }
    /**返回队列是否为空 */
    empty() {
        return !this.pushArr.length && !this.popArr.length;
    }
}


/**
 * Initialize your data structure here.
 */
var MyQueue = function() {
    this.stack1=[];
    this.stack2=[];
};

/**
 * Push element x to the back of queue. 
 * @param {number} x
 * @return {void}
 */
MyQueue.prototype.push = function(x) {
    this.stack1.push(x);
};

/**
 * Removes the element from in front of queue and returns that element.
 * @return {number}
 */
MyQueue.prototype.pop = function() {
   while(this.stack1.length!==0){
        this.stack2.push(this.stack1.pop());
   }
   var popElement=this.stack2.pop();
   while(this.stack2.length!==0){
        this.stack1.push(this.stack2.pop());
   }
   return popElement;
};

/**
 * Get the front element.
 * @return {number}
 */
MyQueue.prototype.peek = function() {
     return this.stack1[0];
};

/**
 * Returns whether the queue is empty.
 * @return {boolean}
 */
MyQueue.prototype.empty = function() {
   return !this.stack1.length;
};

/**
 * Your MyQueue object will be instantiated and called as such:
 * var obj = new MyQueue()
 * obj.push(x)
 * var param_2 = obj.pop()
 * var param_3 = obj.peek()
 * var param_4 = obj.empty()
 */

```