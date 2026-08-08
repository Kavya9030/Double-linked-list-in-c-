# Double-linked-list-in-c-
A Doubly Linked List is a data structure where each node contains data, a pointer to the next node, and a pointer to the previous node. This program allows users to insert, display, and delete elements from the list.


CODE:-
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node *prev;
    struct Node *next;
};

struct Node *head = NULL;

void insert(int data) {
    struct Node *newNode = malloc(sizeof(struct Node));

    newNode->data = data;
    newNode->prev = NULL;
    newNode->next = NULL;

    if (head == NULL) {
        head = newNode;
    } else {
        struct Node *temp = head;

        while (temp->next != NULL)
            temp = temp->next;

        temp->next = newNode;
        newNode->prev = temp;
    }

    printf("Element inserted successfully.\n");
}

void displayForward() {
    struct Node *temp = head;

    printf("Forward: ");
    while (temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->next;
    }
    printf("\n");
}

void displayReverse() {
    struct Node *temp = head;

    if (temp == NULL) {
        printf("List is empty.\n");
        return;
    }

    while (temp->next != NULL)
        temp = temp->next;

    printf("Reverse: ");
    while (temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->prev;
    }
    printf("\n");
}

void deleteNode(int data) {
    struct Node *temp = head;

    while (temp != NULL && temp->data != data)
        temp = temp->next;

    if (temp == NULL) {
        printf("Element not found.\n");
        return;
    }

    if (temp->prev != NULL)
        temp->prev->next = temp->next;
    else
        head = temp->next;

    if (temp->next != NULL)
        temp->next->prev = temp->prev;

    free(temp);
    printf("Element deleted successfully.\n");
}

int main() {
    int choice, value;

    do {
        printf("\n--- Doubly Linked List ---\n");
        printf("1. Insert\n");
        printf("2. Display Forward\n");
        printf("3. Display Reverse\n");
        printf("4. Delete\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                printf("Enter value: ");
                scanf("%d", &value);
                insert(value);
                break;

            case 2:
                displayForward();
                break;

            case 3:
                displayReverse();
                break;

            case 4:
                printf("Enter value to delete: ");
                scanf("%d", &value);
                deleteNode(value);
                break;

            case 5:
                printf("Exiting...\n");
                break;

            default:
                printf("Invalid choice!\n");
        }
    } while (choice != 5);

    return 0;
}


SAMPLE INPUT :-
Enter your choice: 1
Enter value: 10

Enter your choice: 1
Enter value: 20

Enter your choice: 1
Enter value: 30

SAMPLE OUTPUT:-
Element inserted successfully.
Element inserted successfully.
Element inserted successfully.

Forward: 10 20 30



FEATURES :-
*Create a doubly linked list.
*Insert elements.
*Display elements in forward order.
*Display elements in reverse order.
*Delete an element.
