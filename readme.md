# Mock Test 1
## Q 1 
  Given a non-negative integer x, return the square root of x rounded down to the nearest integer. The returned integer should be non-negative as well. You must not use any built-in exponent function or operator. 

 Example 1:
Input: x = 4 Output: 2 Explanation: The square root of 4 is 2, so we return 2.
Example 2:

Input: x = 8 Output: 2 Explanation: The square root of 8 is 2.82842..., and since we round it down to the nearest integer, 2 is returned.
Constraints:

0 <= x <= 231 - 1
```js
var mySqrt = function(x) {
    let left = 1;
    let right = x;
    if(x < 2) return x;
    while(left < right) {
        const mid = Math.floor((left + right) / 2)
        if(mid*mid === x) return mid
        else if(mid*mid >x) right = mid
        else left = mid+1
    }
    return left - 1
};
```
#
## Q2 
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.


Example 1:

Input: l1 = [2,4,3], l2 = [5,6,4] Output: [7,0,8]
Explanation: 342 + 465 = 807.

Example 2:

Input: l1 = [0], l2 = [0] Output: [0]

Example 3:

Input: l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9] Output: [8,9,9,9,0,0,0,1]

 ```js
 var addTwoNumbers = function (l1, l2) {
    let head = null;
    let temp = null;
    let carry = 0;
   
    while (l1 !== null || l2 !== null) {
        let sum = carry;
        if (l1 != null) {
            sum += l1.val;
            l1 = l1.next;
        }
        if (l2 != null) {
            sum += l2.val;
            l2 = l2.next;
        }
        let node = new ListNode(Math.floor(sum) % 10);
        carry = Math.floor(sum / 10);
        if (temp == null) {
            temp = head = node;
        }
        else {
            temp.next = node;
            temp = temp.next;
        }
    }
    if (carry > 0) {
        temp.next = new ListNode(carry);
    }
    return head;
};

class ListNode {
    constructor(val) {
        this.val = val;
        this.next = null;
    }
}
let head1 = new ListNode(2);
head1.next = new ListNode(4);
head1.next.next = new ListNode(3);

let head2 = new ListNode(5);
head2.next = new ListNode(6);
head2.next.next = new ListNode(4);

let result = addTwoNumbers(head1, head2);
let s = "";
while (result !== null) {
    s += result.val + " ";
    result = result.next;
}
console.log(s);
```
