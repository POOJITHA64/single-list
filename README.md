# single-list
#include<stdio.h>
#include<stdlib.h>
struct node
{
    int data;
    struct node*next;
}*newnode,*temp;
struct node*head=NULL;
struct node*tail=NULL;
void create()
{
    int value;
    int ch;
    do
    {
        newnode=(struct node*)malloc(sizeof(struct node));
        printf("enter the value\n");
        scanf("%d",&value);
        newnode->data=value;
        newnode->next=NULL;
        if(head==NULL)
        {
            head=newnode;
            tail=newnode;
        }
        else
        {
            tail->next=newnode;
            tail=newnode;
        }
        printf("1-continue,0-exit\n");
        fflush(stdin);
        scanf("%d",&ch);
    }
    while(ch==1);
}
void display()
{
    temp=head;
    while(temp!=NULL)
    {
    printf("%d\t",temp->data);
    temp=temp->next;
    }
}
void insert_beg()
{
    int value;
    newnode=(struct node*)malloc(sizeof(struct node));
    printf("enter the value\n");
    scanf("%d",&value);
    newnode->data=value;
    newnode->next=head;
    head=newnode;
}
void insert_end()
{
    int value;
    newnode=(struct node*)malloc(sizeof(struct node));
    printf("enter the value");
    scanf("%d",&value);
    newnode->data=value;
    newnode->next=NULL;
    tail=newnode;
}
void insert_pos()
{
    int value,i,pos;
    newnode=(struct node*)malloc(sizeof(struct node));
    printf("enter teh value");
    scanf("%d",&value);
    printf("enter the position");
    scanf("%d",&pos);
    for(i=0;i<pos-1;i++)
    {
        temp=temp->next;
    }
    newnode=value;
    newnode->next=temp->next;
    temp->next=newnode;
}
void delete_beg()
{
    head=temp;
    temp=temp->next;
    temp->next=NULL;
}
void delete_end()
{
    head=temp;
    while(temp->next!=NULL)
    {
        temp=temp->next;
        tail=temp;
    }
}
void delete_pos()
{
    int value,i,pos;
    newnode=(struct node*)malloc(sizeof(struct node));
    printf("enter the value");
    scanf("%d",&value);
    printf("enter the position");
    scanf("%d",&pos);
    for(i=0;i<pos-1;i++)
    {
        temp=temp->next;
    }
    temp->next=temp->next->next;
}
void count()
{
    int count=0;
    temp=head;
    while(temp!=NULL)
    {
        count++;
        temp=temp->next;
    }
}
void reverse()
{
    struct node *prevnode,*currentnode,*nextnode;
    prevnode=0;
    currentnode=nextnode=head;
    while(nextnode!=0)
    {
        nextnode=nextnode->next;
        currentnode->next=prevnode;
        prevnode=currentnode;
        currentnode=nextnode;
    }
    head=prevnode;
}
void main()
{
        int choice=0;
        while(1)
        {
            printf("Operations on Single linked list are:\n");
            printf("1.Create()\n");
            printf("2.Display()\n");
            printf("3.Insert_beg()\n");
            printf("4.Insert_end()\n");
            printf("5.Insert_pos()\n");
            printf("6.Delete_beg()\n");
            printf("7.Delete_end()\n");
            printf("8.Delete_pos()\n");
            printf("9.To count the number of elements in a Created Single Linked List:\n");
            printf("10.To reverse the elements of a Created single linked list:\n");
            printf("Others:Exit()\n");
            printf("Enter your choice:\n");
            scanf("%d",&choice);
            switch(choice)
            {
                case 1:
                        create();
                        break;
                case 2:
                        display();
                        break;
                case 3:
                        insert_beg();
                        break;
                case 4:
                        insert_end();
                        break;
                case 5:
                        insert_pos();
                        break;
                case 6:
                        delete_beg();
                        break;
                case 7:
                        delete_end();
                        break;
                case 8:
                        delete_pos();
                        break;
                case 9:
                        count();
                        break;
                case 10:
                        reverse();
                        break;
                default:
                        break;
            }
        }
}


