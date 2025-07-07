#include <stdio.h>
#include <stdlib.h>

// Node structure 
typedef struct Node  
{
    int data;
    struct Node* next;
}
Node;

// Function prototypes
Node* insertAtBeginning(Node* head, int data);
Node* insertAtEnd(Node* head, int data);
Node* insertAfterValue(Node* head, int target, int data);
Node* deleteByValue(Node* head, int value);
void traverseList(Node* head);
void freeList(Node* head);

//Insert at the beginning
Node* insertAtBeginning(Node* head, int data)
{
    Node* newNode = (Node*) malloc(sizeof(Node));
    if (!newNode)
    {
        printf("memory allocation failed\n");
        return head;
    }
    newNode->data = data;
    newNode->next = head;
    return newNode;
}

//Insert at the end
Node* insertAtEnd(Node* head, int data)
{
    Node* newNode = (Node*) malloc(sizeof(Node));
    if (!newNode)
    {
       printf("memory allocation failed\n");
       return head;  
    }
    newNode->data = data;
    newNode->next = NULL;

    if (head == NULL)
        return newNode;

    Node* temp = head;
    while (temp->next != NULL)
        temp = temp->next;
        
    temp->next = newNode;
    return head;    
}

//Insert after a given value
Node* insertAfterValue(Node* head, int target, int data)
{
    Node* temp = head;
    while (temp != NULL && temp->data != target)
       temp = temp->next;

    if (temp == NULL)
    {
        printf("Value %d not found in list.\n", target);
        return head;
    }   
    
    Node* newNode = (Node*) malloc(sizeof(Node));
     if (!newNode)
      {
        printf("Memory allocation failed\n");
        return head;
      }
    newNode->data = data;
    newNode->next = temp->next;
    temp->next = newNode;
    return head;
}

//Delete a node by value
Node* deleteByValue(Node* head, int value)
{
    if (head == NULL)
    return NULL;

    Node* temp = head;
    Node* prev = NULL;

    //If head node holds the value
    if (head->data == value)
    {
        temp = head->next;
        free(head);
        return temp;
    }

    while (temp != NULL && temp->data != value)
    {
        prev = temp;
        temp = temp->next;
    }

    if (temp == NULL)
    {
        printf("value %d not found in list.\n");
        return head;
    }
    prev->next = temp->next;
    free(temp);
    return head;
}

//Display the list
void traverseList(Node* head)
{
    if (head == NULL)
    {
        printf("List is empty.\n");
        return;
    }

    Node* temp = head;
    printf("List: ");
    while (temp != NULL)
    {
        printf("%d ->", temp->data);
        temp = temp->next;
    }
    printf("NULL\n");
}

// Free all nodes
void freeList(Node* head)
{
    Node* temp;
    while (head != NULL)
    {
        temp = head;
        head = head->next;
        free(temp);
    }
}

// Test the list function
int main()
{
    Node* head = NULL;

    head = insertAtEnd(head, 10);
    head = insertAtBeginning(head, 5);
    head = insertAtEnd(head, 20);
    head = insertAfterValue(head, 10, 15);
    traverseList(head); //Expected: 5 -> 10 -> 15 -> 20 -> NULL

    head = deleteByValue(head, 10);
    traverseList(head); //Expected: 5 -> 15 -> 20 -> NULL

    head = deleteByValue(head, 100); //Not found
    traverseList(head);

    freeList(head);
    return 0;
}
