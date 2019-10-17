# Linked list

+ [Reverse Linked List](#reverse-linked-list)
+ [Intersection of Two Linked Lists](#intersection-of-two-linked-lists)
+ [Middle of the Linked List](#middle-of-the-linked-list)
+ [Remove Nth Node From End of List](#remove-nth-node-from-end-of-list)
+ [Palindrome Linked List](#palindrome-linked-list)
+ [Linked List Cycle](#linked-list-cycle)
+ [Linked List Cycle II](#linked-list-cycle-ii)
+ [Merge Two Sorted Lists](#merge-two-sorted-lists)
+ [Sort List](#sort-list)
+ [Reorder List](#reorder-list)
+ [Two Sum](#two-sum)
+ [Implement Stack using Queues](#implement-stack-using-queues)
+ [Implement Queue using Stacks](#implement-queue-using-stacks)

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

## Palindrome Linked List

https://leetcode.com/problems/palindrome-linked-list/

```cpp
public:
    bool isPalindrome(ListNode* head) {
         if (head == NULL || head->next == NULL )
            return true;
        
        ListNode *head2 = middleNode(head);
        head2 = reverseList(head);
        return isEqual(head, head2);
    }
    
public:  ListNode* middleNode(ListNode* head) {
        if (head == NULL || head->next == NULL)
            return NULL;
        ListNode *slow = head, *fast = head;
        while (fast != NULL && fast->next != NULL) {
            slow = slow->next;
            fast = fast->next->next;
        }
        return slow;  
    }
    
public: ListNode* reverseList(ListNode* head) {
ListNode *current = head, *previous = NULL, *next;
                while(current != NULL){
			next = current->next;
			current->next = previous;
			previous = current;
			current = next;
		}
		return previous;
	}
    
public: bool isEqual(ListNode* head, ListNode* head2) {
        while (head != NULL && head2 != NULL) {
            if (head->val != head2->val)
                return false;
            head = head->next;
            head2 = head2->next; 
        }
      return true;
    }
```

## Linked List Cycle

https://leetcode.com/problems/linked-list-cycle/

```cpp
 bool hasCycle(ListNode *head) {
        if (head == NULL || head->next == NULL) 
        return false;
    
    ListNode *slow = head;
    ListNode *fast = head;
    while (true) {
        if (fast == NULL || fast->next == NULL) {
            return false;
        }
        slow = slow->next;
        fast = fast->next->next;
        if (slow == fast) {
            return true;
        }
    }
    }
```

## Linked List Cycle II

https://leetcode.com/problems/linked-list-cycle-ii/

```cpp
 ListNode *detectCycle(ListNode *head) {
      if (head == NULL || head->next == NULL) 
        return NULL;
    
    ListNode *slow = head;
    ListNode *fast = head;
    while (true) {
        if (fast == NULL || fast->next == NULL) {
            return NULL;
        }
        slow = slow->next;
        fast = fast->next->next;
        if (slow == fast) {
            slow = head;
            while (slow != fast) {
                slow = slow->next;
                fast = fast->next;
            }
            return slow;
        }
    }  
    }
```

## Merge Two Sorted Lists

https://leetcode.com/problems/merge-two-sorted-lists/

```cpp
   ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
         if (l1 == NULL && l2 == NULL)
             return NULL;
         if (l1 == NULL) 
             return l2;
         if (l2 == NULL) 
             return l1;

    ListNode *sortedList = new ListNode(0);
    ListNode *current = sortedList;

    while (l1 != NULL && l2 != NULL) {
        if (l1->val < l2->val) {
            current->next = l1;
            l1 = l1->next;
        } else {
            current->next = l2;
            l2 = l2->next;
        }
        current->next->next = NULL;
        current = current->next;
    }

    if (l1 != NULL) 
        current->next = l1;
    if (l2 != NULL) 
        current->next = l2;

    return sortedList->next;
        
    }
```

## Sort List

https://leetcode.com/problems/sort-list/

```cpp
 ListNode* sortList(ListNode* head) {
        if (head == NULL || head->next == NULL)
            return head;

    ListNode *slow = head, *fast = head, *previous = head;

    while (fast != NULL && fast->next != NULL) {
        previous = slow;
        slow = slow->next;
        fast = fast->next->next;
    }

    if (fast != NULL) {
        previous = slow;
        slow = slow->next;
    }
    previous->next = NULL;

    return mergeLists(sortList(head), sortList(slow));
}

public:
     ListNode* mergeLists(ListNode* l1, ListNode* l2) {
         if (l1 == NULL && l2 == NULL)
             return NULL;
         if (l1 == NULL) 
             return l2;
         if (l2 == NULL) 
             return l1;

    ListNode *head = new ListNode(0);
    ListNode *current = head;

    while (l1 != NULL && l2 != NULL) {
        if (l1->val < l2->val) {
            current->next = l1;
            l1 = l1->next;
        } else {
            current->next = l2;
            l2 = l2->next;
        }
        current->next->next = NULL;
        current = current->next;
    }

    if (l1 != NULL) 
        current->next = l1;
    if (l2 != NULL) 
        current->next = l2;

    return head->next;
        
    }
```

## Reorder List

https://leetcode.com/problems/reorder-list/

```cpp
 void reorderList(ListNode* head) {
    if (head == NULL || head->next == NULL || head->next->next == NULL) {
        return;
    }
    ListNode *slow = head, *fast = head;

    while (fast != NULL && fast->next != NULL) {
        slow = slow->next;
        fast = fast->next->next;
    }
    fast = slow;
    if (fast != NULL) {
        fast = slow->next;
        slow->next = NULL;
    }
    fast = reverseList(fast);        
    head = mergeLists(head, fast);
}
public:
    ListNode* reverseList(ListNode* head) {
    ListNode *current = head, *previous = NULL, *next;
    
		      while(current != NULL) {
			next = current->next;
			current->next = previous;
			previous = current;
			current = next;
		}
		return previous;
	}
public:
    ListNode *mergeLists(ListNode* l1, ListNode* l2) {
    ListNode *currentl1 = l1, *nextl1;
    ListNode *currentl2 = l2, *nextl2;

    while (currentl1 != NULL && currentl2 != NULL) {
        nextl1 = currentl1->next;
        nextl2 = currentl2->next;

        currentl1->next = currentl2;
        currentl2->next = nextl1;

        currentl1 = nextl1;
        currentl2 = nextl2;
    }
    return l1;
}
```

## Two Sum

https://leetcode.com/problems/two-sum/

```cpp
 vector<int> twoSum(vector<int> & nums, int target) {
    unordered_map<int, int> hash_table;
        
    for (int i = 0; i < nums.size(); ++i){
        int res = target - nums[i];
        if (hash_table.find(res) != hash_table.end())
        return vector<int> { 
            hash_table[target - nums[i]], i }; 
          hash_table.insert(pair<int, int>(nums[i], i));
         }
     return vector<int>();    
    }
```

## Implement Stack using Queues

https://leetcode.com/problems/implement-stack-using-queues/

```cpp
     int n;
    queue<int>q1;
    /** Initialize your data structure here. */
    MyStack() {
        n = 0;
    }
    
    /** Push element x onto stack. */
    void push(int x) {
        q1.push(x);
        n++;
        for (int i = 0; i< q1.size()-1; i++) {
            q1.push(q1.front());
            q1.pop();
        }
    }
    
    /** Removes the element on top of the stack and returns that element. */
    int pop() {
        n--;
        int a = q1.front();
        q1.pop();
        return a;
    }
    
    /** Get the top element. */
    int top() {
        return q1.front();
    }
    
    /** Returns whether the stack is empty. */
    bool empty() {
        return (n==0);
    }
```

## Implement Queue using Stacks

https://leetcode.com/problems/implement-queue-using-stacks/

```cpp
    stack <int> s1;
    stack <int> s2;
    /** Initialize your data structure here. */
    MyQueue() { 
        s1 = {};
        s2 = {};
    }
    
    /** Push element x to the back of queue. */
    void push(int x) {
        s1.push(x);
    }
    
    /** Removes the element from in front of queue and returns that element. */
    int pop() {
        while(!s1.empty())
        {
            s2.push(s1.top());
            s1.pop();
        }
        int ret = s2.top();
        s2.pop();
        
        while(!s2.empty())
        {
            s1.push(s2.top());
            s2.pop();    
        }
        return ret;
    }
    
    /** Get the front element. */
    int peek() {
         while(!s1.empty())
        {
            s2.push(s1.top());
            s1.pop();
        }
        int ret = s2.top();
        while(!s2.empty())
        {
            s1.push(s2.top());
            s2.pop();    
        }
        return ret;
    }
    
    /** Returns whether the queue is empty. */
    bool empty() {
        return s1.empty();
    }
```
