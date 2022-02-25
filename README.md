# circular-stacks
#include<stdio.h>
#include<stdlib.h>
struct node
{
        int data;
        struct node*next;
}*temp,*newnode;
struct node*head=NULL;
struct node*tail=NULL;
void create()
         {
                 int value;
                 int ch;
                do{
                        newnode=(struct node*)malloc(sizeof(struct node*));
                        printf("enter the value");
                        scanf("%d",&value);
                         newnode->data=value;
                         newnode->next=NULL;
                       if((head==NULL))
                       {
                               head=newnode;
                               tail=newnode;
                               tail->next=newnode;
                       }
                       else
                       {
                               tail->next=newnode;
                               tail=newnode;
                               tail->next=head;
                       }
                       printf("enter 1-create,0-exist\n");
                       scanf("%d",&ch);
                }
                while(ch==1);
         }
void push()
{
        int value;
        newnode=(struct node*)malloc(sizeof(struct node*));
        printf("enter the value to be push");
        scanf("%d",&value);
        newnode->data=value;
        newnode->next=head;
        head=newnode;
        tail->next=head;
}
void pop()
{
        temp=head;
        printf("enter the value to be pop");
        head=head->next;
        temp->next=NULL;
        tail->next=head;
}
void display()
{
        temp=head;
        printf("operations on stacks is:");
        {
                while(temp==NULL)
                {
                printf("%d",temp->data);
                temp=temp->next;
                temp->next=head;
                }
        }
}
int main()
{
    int choice=0;
    printf("operations on queue is:");
    do{
        printf("enter 1-create\n");
        printf("enter 2-push\n");
        printf("enter 3-pop\n,4-display\n");
        printf("enter your choice");
       scanf("%d",&choice);
       switch(choice)
       {
           case 1:
                  create();
                  break;
           case 2:
                  push();
                  break;
           case 3:
                  pop();
                  break;
           case 4:
                  display();
                  break;
           default :
             printf("wrong choice");
             break;
       }
    }while(choice<5);
}
