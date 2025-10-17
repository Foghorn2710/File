#include<stdio.h>
#include<string.h>
#include<stdlib.h>
#include<math.h>
#define MAX 50

int stack[MAX];
char post[MAX];
int top=-1;

void pushstack(int tmp);
void calculator(char c);

void main()
{
	int i;
	printf("Insert a postfix notation :: ");
	scanf("%s",post);

	for(i=0;i<strlen(post);i++)
	{
		if(post[i]>='0' && post[i]<='9')
		{
			pushstack(i);
		}
		if(post[i]=='+' || post[i]=='-' || post[i]=='*' || post[i]=='/' || post[i]=='^')
		{
			calculator(post[i]);
		}
	}
	printf("\n\nResult :: %d",stack[top]);
}

void pushstack(int tmp)
{
	top++;
	stack[top]=(int)(post[tmp]-48);
}

void calculator(char c)
{
	int a,b,ans;
	b=stack[top];
	top--;
	a=stack[top];
	top--;


	switch(c)
	{
		case '+':
			ans=b+a;
			break;
		case '-':
			ans=b-a;
			break;
		case '*':
			ans=b*a;
			break;
		case '/':
			ans=b/a;
			break;
		case '^':
			ans=pow(b,a);
			break;
		default:
			ans=0;
	}
top++;
stack[top]=ans;
}

/* Output
Insert a postfix notation :: 22^32*+

Result :: 10
*/


b. Solving Tower of Hanoi problem with n disks 
Program
#include<stdio.h>
void towers(int, char, char, char);
void main()
{
	int num;
	clrscr();
	printf("enter the number of disks : ");
	scanf("%d", &num);
	printf("the sequence of moves involved in the ower of honai are : \n");
	towers(num, 'A','C','B');
	getch();
}

void towers(int num, char frompeg, char topeg, char auxpeg)
{
	if(num == 1)
	{
		printf("\n MOVE DISK 1 FROM PEG %c TO PEG %c", frompeg, topeg);
		return;
	}
	towers( num -1,  frompeg,  auxpeg ,topeg);
	printf("\n MOVE DISK %d FROM PEG %c TO PEG %c", num,frompeg, topeg);
	towers( num -1,  auxpeg ,topeg ,frompeg );
}


/* Output
Run 1:
enter the number of disks : 2
the sequence of moves involved in the tower of hanoi are :

 MOVE DISK 1 FROM PEG A TO PEG B
 MOVE DISK 2 FROM PEG A TO PEG C
 MOVE DISK 1 FROM PEG B TO PEG C
*/
