#include<stdio.h>
#include<stdlib.h>
struct node{
int data;
struct node *link;
};
/*function to create linked list of random integers*/
struct node* add_beg(struct node* head,int d)
{

    struct node *ptr=malloc(sizeof(struct node));
    ptr->data=d;
    ptr->link=NULL;
    ptr->link=head;
    head=ptr;
    return head;
};
/* Bubble sort the given linked list */
void bubbleSort(struct node *head)
{
    int swapped, i;
    struct node *ptr1;
    struct node *lptr = NULL;

    /* Checking for empty list */
    if (head == NULL)
        return;

    do
    {
        swapped = 0;
        ptr1 = head;

        while (ptr1->link != lptr)
        {
            if (ptr1->data > ptr1->link->data)
            {
                swap(ptr1, ptr1->link);
                swapped = 1;
            }
            ptr1 = ptr1->link;
        }
        lptr = ptr1;
    }
    while (swapped);
}

/* function to swap data of two nodes a and b*/
void swap(struct node *a, struct node *b)
{
    int temp = a->data;
    a->data = b->data;
    b->data = temp;
}
/* Function to print nodes in a given linked list */
void printList(struct node *head)
{
    struct node *temp = head;
    printf("\n");
    while (temp!=NULL)
    {
        printf("%d ", temp->data);
        temp = temp->link;
    }
}
int main()
{
    struct node *head=malloc(sizeof(struct node));
    head->data=rand()%1000;
    head->link= NULL;
    struct node *ptr=malloc(sizeof(struct node));
    ptr->data=rand()%1000;
    ptr->link=NULL;
    head->link=ptr;
    int i;
    for(i=1;i<99;i++)
    {
        int data=rand()%1000;
        head=add_beg(head,data);
        ptr=head;

    }
    bubbleSort(head);

    /* print list after sorting */
    printf("\n Linked list after sorting ");
    printList(head);
    return 0;
}
