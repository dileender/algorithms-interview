# Linked list

+ [Reverse Linked List](#reverse-linked-list)
+ [Intersection of Two Linked Lists](#intersection-of-two-linked-lists)
+ [Middle of the Linked List](#middle-of-the-linked-list)
+ [Remove Nth Node From End of List](#remove-nth-node-from-end-of-list)

## Reverse Linked List

https://leetcode.com/problems/reverse-linked-list/

```cpp
ListNode* reverseList(ListNode* head) {
ListNode *current = head, *previous = NULL, *next;
    
		while(current != NULL)
		{
			next = current->next;
			current->next = previous;
			previous = current;
			current = next;
		}
		
		return previous;
	}
}
```

## Intersection of Two Linked Lists

https://leetcode.com/problems/intersection-of-two-linked-lists/

```cpp
ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        ListNode *a = headA, *b = headB;
         while (a != NULL && b != NULL) {
            a = a->next;
            b = b->next;
        }
        if (a == NULL) {
            while (b != NULL) {
                headB = headB->next;
                b = b->next;
            }
        }
        if (b == NULL) {
            while (a != NULL) {
                headA = headA->next;
                a = a->next;
            }
        }
        while (headA != headB) {
            headA = headA->next;
            headB = headB->next;
        }
        return headA;
        }
```

## Middle of the Linked List

https://leetcode.com/problems/middle-of-the-linked-list/

```cpp
 ListNode* middleNode(ListNode* head) {
        if (head == NULL || head->next == NULL)
            return NULL;
        ListNode *slow = head, *fast = head;
        while (fast != NULL && fast->next != NULL) {
            slow = slow->next;
            fast = fast->next->next;
        }
        return slow;  
    }
```

## Remove Nth Node From End of List

https://leetcode.com/problems/remove-nth-node-from-end-of-list/

```cpp
ListNode* removeNthFromEnd(ListNode* head, int n) {
        if (head == NULL || n == 0)
            return head;
    ListNode *s = new ListNode(0);
    s->next = head;
    ListNode *first = s;
    ListNode *second = s;
    for (int i = 1; i <= n + 1; i++) {
        first = first->next;
    }
    while (first != NULL) {
        first = first->next;
        second = second->next;
    }
    second->next = second->next->next;
    return head;
    }
```
