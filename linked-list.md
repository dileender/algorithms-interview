# Linked list

+ [Reverse Linked List](#reverse-linked-list)

## Reverse Linked List

https://leetcode.com/problems/reverse-linked-list/

```cpp
ListNode* reverseList(ListNode* head) {
ListNode *current = head, *previos = NULL, *next;
    
		while(current!= NULL)
		{
			next = current->next;
			current->next = previos;
			previos = current;
			current = next;
		}
		
		return previos;
	}
}
```
