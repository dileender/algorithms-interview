+ [Implement Stack using Queues](#implement-stack-using-queues)
+ [Implement Queue using Stacks](#implement-queue-using-stacks)
+ [Desigh Linked list](#design-linked-list)

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

## Design Linked List

https://leetcode.com/problems/design-linked-list/

```cpp
class Node{
public:
    Node* next;
    int val;
    Node(int v) : val(v){next = nullptr;}
    };
    Node* head = nullptr;
    Node* tail = nullptr;
    int len = 0;
class MyLinkedList {
public:
    /** Initialize your data structure here. */
    MyLinkedList() {
        
    }
    
    /** Get the value of the index-th node in the linked list. If the index is invalid, return -1. */
    int get(int index) {
        if(index < 0){
            return -1;
        } else if(index < len){
            auto tmp = head;
            for(int i = 0;i<index;i++){
                tmp = tmp->next;
            }
            return tmp->val;
        } else {
            return -1;
        } 
    }
    
    /** Add a node of value val before the first element of the linked list. After the insertion, the new node will be the first node of the linked list. */
    void addAtHead(int val) {
        if(head == nullptr){
            head = tail = new Node(val);
        } else {
            auto t = new Node(val);
            t->next = head;
            head = t;
        }
        len++;
    }
    
    /** Append a node of value val to the last element of the linked list. */
    void addAtTail(int val) {
         if(tail == nullptr){
            head = tail = new Node(val);
        } else {
            auto t = new Node(val);
            tail->next = t;
            tail = tail->next;
        }
        len++;
    }
    
    /** Add a node of value val before the index-th node in the linked list. If index equals to the length of linked list, the node will be appended to the end of linked list. If index is greater than the length, the node will not be inserted. */
    void addAtIndex(int index, int val) {
        if(index < 0){
            addAtHead(val);
        } else if(len == index){
            addAtTail(val);
        } else if(index == 0) {
            addAtHead(val);
        } else if(index>len){
            return;
        } else {
            auto tmp = head;
            for(int i = 1;i<index;i++){
                tmp = tmp->next;
            }
            auto t = new Node(val);
            t->next = tmp->next;
            tmp->next = t;
            len++;
        }
    }
    
    /** Delete the index-th node in the linked list, if the index is valid. */
    void deleteAtIndex(int index) {
       if(index>=len){
            return;
        } else if(index<0){
            return;
        }
        if(index==0){
            auto tmp = head->next;
            delete head;
            head = tmp;
        }  else {
            auto tmp = head;
            for(int i = 1;i<index;i++){
                tmp = tmp->next;
            }
            auto t = tmp->next;
            tmp->next = t->next;
            delete t;
            if(index == len -1){
                tail = tmp;
            }
        }
        len--;
        if(len == 0){
            tail = nullptr;
        } 
    }
```
