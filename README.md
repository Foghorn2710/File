#include<stdio.h>
#define size 5

char q[size];
int front=-1, rear=-1,count=0;
void insert();
void delet();
void display();

void main()
{
	int ch;
	for(;;)
	{
		printf(" \n 1.Insert 2. Delete 3. Display 4.Exit\n");
		printf("\n Enter Your Choice \n");
		scanf("%d",&ch);
		switch(ch)
		{
			case 1:
				insert();
				break;
			case 2:
				delet();
				break;
			case 3:
				display();
				break;
			case 4:
				exit(0);
				break;
			default:
				printf("Invalid Choice!");
		}
	}

}

void insert()
{
	char item;
	printf("Enter the element to be inserted to the queue \n");
	scanf("%c",&item);
	if(count= = size)
		printf(" \n Queue is Overflow ! \n");
	else
	{
		if(front==-1)
		{
			front=0;
rear=0;
		}
		else
			rear=(rear+1)%size;
		q[rear]=item;
count++;
	}
}

void display()
{
	int i;
	if(count ==0)
		printf("Queue is empty \n");
	else
	{
		for(i=front;i!=rear;i=(i+1)%size)
		{
			printf("q[%d]=%c \n",i, q[i]);
		}
		printf("q[%d]=%c \n",i, q[i]);
	}
}

void delet()
{
	int del_item=0;
	
	if(count==0)
		printf("Queue Underflow!");
	else
	{
		del_item=q[front];
		printf(" \nEleement deleted from the quees is '%c' at pos=%d \n",del_item, front);
		front=(front+1)%size;
		count--;
		
	}
}

			
