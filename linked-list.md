# Linked list

+ [Reverse Linked List](#reverse-linked-list)
+ [Intersection of Two Linked Lists](#intersection-of-two-linked-lists)

## Reverse Linked List

https://leetcode.com/problems/reverse-linked-list/

```cpp
ListNode* reverseList(ListNode* head) {
ListNode *current = head, *previous = NULL, *next;
    
		while(current!= NULL)
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
        ListNode *a=headA, *b=headB;
         while (a!=NULL&&b!=NULL) {
            a=a->next;
            b=b->next;
        }
        if (a==NULL) {
            while (b!=NULL) {
                headB=headB->next;
                b=b->next;
            }
        }
        if (b==NULL) {
            while (a!=NULL) {
                headA=headA->next;
                a=a->next;
            }
        }
        while (headA!=headB) {
            headA=headA->next;
            headB=headB->next;
        }
        return headA;
        }
```
