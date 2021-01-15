---
layout: post
title: Sum of two linked lists
---
I was browsing LeetCode the other day and stumbled upon a problem where you need to write a function that takes two linked lists with nodes in reverse order, eq. `1 ~> 2 ~> 3` and `4 ~> 5 ~> 6` (*each node has value `0-9`*) and outputs a linked list with the sum, eq. `5 ~> 7 ~> 9`.

After some back & forth here is the snippet accepted as an answer:

```
public class Solution {
    public ListNode AddTwoNumbers(ListNode l1, ListNode l2) {
        ListNode lhs = l1, rhs = l2, nn = cv(0), head = nn;
        int carry = 0;
        while (lhs != null || rhs != null || carry > 0) {
            int sum = carry + nv(lhs) + nv(rhs);
            carry = tens(sum);
            head = head.next = cv(sum);
            if (lhs != null) lhs = lhs.next;
            if (rhs != null) rhs = rhs.next;
        }
        return nn.next;
    }

    private int nv(ListNode n)
        => n != null ? n.val : 0;

    private ListNode cv(int n)
        => new ListNode(n % 10);

    private int tens(int n)
        => n / 10;
}
```


Let me explain a few things this snippet uses to simplify the code.

First of all, it tucked away `?:` ternary conditional operator in `nv()`, eq. *node value* helper function and **packed 3 lines into a 1-line statement**:

`int sum = carry + nv(lhs) + nv(rhs);`

Next, the snippet packed new node `.ctor` call in `cv()`, eq. *carry value* helper function combined with multi-assignment and **compressed 2 lines into a 1-line statement** as well:

`head = head.next = cv(sum);`

The rest of the code seems to be trivial, calculating the carry and moving along the specified linked lists.
