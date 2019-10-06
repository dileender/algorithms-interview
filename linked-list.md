# Linked list

+ [Reverse Linked List](#reverse-linked-list)

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
