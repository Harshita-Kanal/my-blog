---
title: Linked List 101-Move the first element of a linked list to the end
og_image: start-blog-gatsby-twitter.png
---
In this problem, given a linked list move the first element of the linked list to the end of the linked list.
```cpp
Example input:
1 -> 2 -> 2 -> 3

Example output:
2 -> 2 -> 3 -> 1
```

### What are linked lists ?
Linked List is a data structure. It is a linear data structure where the elements of the linked list are stored in non-consecutive
memory locations, each node in the linked list contains a data item and pointer to the next node in the linked list.

### Representation of linked lists
In our program we have represented a linked list using a `struct` construct in C++.
```cpp
struct node {
    int data;
    struct node* next;
};
```
Here, `data` represents the data value in the node and the `next` pointer represents the pointer to the next node in the list.

### Solution Approach
In this solution approach we maintain two pointers. The `first` pointer and the `last` pointer. Both of them initially contain reference to the head. The next element after the head is made the new head by moving the head reference to the next of current head. The `next` of the `last` points to the previous head and it's `next` stores 
`null`.

## Implementation of the approach
Here we have implemented the above approach in `C++`

```cpp
#include <bits/stdc++.h>
using namespace std;

//node representation
struct node {
    int data;
    struct node* next;

};

//pointer declaration
struct node* head;
struct node* tail = new node;
struct node* temp = new node;
struct node* curr;
struct node* pre;

//this is a function to print the data items in the linked list
void print_data(struct node* head){
 temp = head;
 while(temp != NULL){
    cout << temp -> data << " ";
    temp = temp -> next;
 }
}

//the move to end function which implements the algorithm.
void move_to_end(struct node** head_pointer){

if(*head_pointer == NULL){ //this means our list is empty, we return
    return;
}

struct node* first = *head_pointer;
struct node* last = *head_pointer;

//go to the last node of the list and
//store the address of the last node
while(last -> next != NULL){
    last = last -> next;
}
//we store the address of the second node here, this is the new head.
*head_pointer = first -> next;
//the previous head has the next set as NULL
first -> next = NULL;
//the previous head now becomes the tail
last -> next = first;
}

int main(){
int n, num, key;
cout << "Enter the number of elements" <<endl;
cin >> n ;

//accepting list from user
cout << "Enter the elements: " <<endl;
do {
 cin >> num;
 if(head == NULL){
    head = new node;
    head -> data = num;
    head -> next = NULL;
    tail = head;
 }
 else{
    //create and initialize a new node
    struct node *new_node = new node;
    new_node -> data = num;
    new_node -> next = NULL;
    tail -> next = new_node;
    tail = new_node;
 }
 n = n - 1;
}while(n > 0);
cout << "List before moving" <<endl;
print_data(head);
//pass the reference of head
move_to_end(&head);
cout <<"\nList after moving" <<endl;
print_data(head);
}

```

### A small example to understand the solution

Consider the linked list:
```cpp
head           tail
1 -> 3 -> 2 -> 3
```
Initially the `head_pointer` pointer would be storing the address of the `head` or the first element of the linked list. <br/>
The `first` and `last` pointers are also initialized.

```cpp
    head      tail
1 -> 3 -> 2 -> 3
```
The `head_pointer` then points to the next element after the `head`. We make the next of `head` as our new head now.

```cpp
    head      tail
1 -> 3 -> 2 -> 3
```
Now `tail` is moved to the first element and it's next stores `null`. The structure of the list now becomes as follows

```cpp
head           tail
3 -> 2 -> 3 -> 1
```
This is the required output.
<br/>

__Time complexity__: The time complexity of this approach is given by O(N), where, N is the number of nodes in the linked list. As we traverse all the N nodes in one pass.
