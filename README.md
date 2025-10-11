#include<stdio.h>
#include<conio.h>

char Mainstr[100],Pat[100],Replace[100],ans[100];
int i,j,c,m,k;

void read()
{
	printf("\nEnter a string \n");
	gets(Mainstr);
	printf("\nEnter a search string \n");
	flushall();
	gets(Pat);
	printf("\nEnter a replace string \n");
	flushall();
	gets(Replace);
}

void find_replace()
{
	i = m = c = j = 0;
	while ( Mainstr[c] != '\0')
	{
		if ( Mainstr[m] == Pat[i] ) // ...... matching
		{
			i++;
			m++;
			if ( Pat[i] == '\0') //.....found occ
			{
				//.... copy replace string in ans string .....
			for(k=0; Replace[k] != '\0';k++,j++) {
				ans[j] = Replace[k];}
			i=0;
			c=m;
			}
		}
		else //... mismatch
		{
			ans[j] = Mainstr[c];
			j++;
			c++;
			m = c;
			i=0;
		}
	}
	ans[j] = '\0';
	printf("\nThe resultant string is\n%s" ,ans);
}
void main()
{
	clrscr();
	read();
	find_replace();
	getch();
}
