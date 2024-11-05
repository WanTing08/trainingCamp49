# 203. Remove Linked List Elements
## Solution
To solve the problem we need to traverse the linked list while removing nodes that contains the target value. To simplify the edge case, like when the first node has the value we want to remove，we can use a dummy node. We create a dummy node points to the head of the list, we initialize two pointers, 'cur' points starts from the dummy node, and 'cur.next' points to the actual list node. When the 'cur.next' is not null, check if 'cur.next' is equal to the target value, if it does, bypassing the node by setting 'cur.next = cur.next.next', if it doesn't move 'cur' to the next node. After the loop, dummy.next will be the head of the modified list.

## Code
```
public Linkedlist removeElements(ListNode head, int val){
  ListNode dummy = new ListNode(0);
  dummy.next = head;
  ListNode cur = dummy;
  while(cur.next != null){
    if(cur.next.val == val) cur.next = cur.next.next;
    else cur = cur.next;
  }
  return dummy.next;
}
```

----------



