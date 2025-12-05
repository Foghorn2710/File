1a)
#include<stdio.h> // printf()
#include<stdlib.h> // exit()
#include<sys/types.h> // pid_t
#include<sys/wait.h> // wait()
#include<unistd.h> // fork
int main(int argc, char **argv)
{
pid_t pid;
pid = fork();
if(pid==0)
{
printf("It is the child process and pid is %d\n",getpid());
int i=0;
for(i=0;i<8;i++)
{
printf("%d\n",i);
}
exit(0);
}
else if(pid > 0)
{
printf("It is the parent process and pid is %d\n",getpid());
int status;
wait(&status);
printf("Child is repeated\n");
}
else
{
printf("Error in forking..\n");
exit(EXIT_FAILURE);
}
return 0;
}



2a&b
#include<stdio.h> 
int main()
{
 int n,bt[20],wt[20],tat[20],avwt=0,avtat=0,i,j;
 printf("Enter total number of processes(maximum 20): ");
 scanf("%d",&n); 
 printf("\nEnter Process Burst Time:\n");
 for(i=0;i<n;i++)
 {
 printf("P[%d]: ",i+1);
 scanf("%d",&bt[i]);
 } 
 wt[0]=0;
 for(i=1;i<n;i++)
 {
 wt[i]=0;
 for(j=0;j<i;j++)
 wt[i]+=bt[j];
 }
 printf("\nProcess\t\tBurst Time\tWaiting Time\tTurnaround Time");
 //calculating turnaround time
 for(i=0;i<n;i++)
 {
 tat[i]=bt[i]+wt[i];
 avwt+=wt[i];
 avtat+=tat[i];
 printf("\nP[%d]\t\t%d\t\t%d\t\t%d",i+1,bt[i],wt[i],tat[i]);
 } 
 avwt/=i;
 avtat/=i;
 printf("\n\nAverage Waiting Time:%d",avwt);
 printf("\nAverage Turnaround Time:%d",avtat);
 return 0;
}


#include<stdio.h>
int main()
{ 
 int bt[20],p[20],wt[20],tat[20],i,j,n,total=0,pos,temp;
 float avg_wt,avg_tat;
 printf("Enter number of process: ");
 scanf("%d",&n);
 printf("\nEnter Burst Time:\n");
 for(i=0;i<n;i++)
 { 
 printf("p%d: ",i+1);
 scanf("%d",&bt[i]);
 p[i]=i+1; 
 } 
 for(i=0;i<n;i++)
 { pos=i;
 for(j=i+1;j<n;j++)
 { if(bt[j]<bt[pos])
 pos=j;
 }
 temp=bt[i];
 bt[i]=bt[pos];
 bt[pos]=temp;
 temp=p[i];
 p[i]=p[pos];
 p[pos]=temp;
 } 
 wt[0]=0;
 for(i=1;i<n;i++)
 { wt[i]=0;
 for(j=0;j<i;j++)
 wt[i]+=bt[j];
 total+=wt[i];
 
 }
 avg_wt=(float)total/n; 
 total=0;
 printf("\nProcess\t Burst Time \tWaiting Time\tTurnaround Time");
 for(i=0;i<n;i++)
 { tat[i]=bt[i]+wt[i]; 
 total+=tat[i];
 printf("\np%d\t\t %d\t\t %d\t\t\t%d",p[i],bt[i],wt[i],tat[i]);
 } 
 avg_tat=(float)total/n; 
 printf("\n\nAverage Waiting Time=%f",avg_wt);
 printf("\nAverage Turnaround Time=%f\n",avg_tat);
 return 0;
}

3)#include<stdio.h>
void main()
{
int buffer[10], bufsize, in, out, produce, consume, choice=0;
in = 0;
out = 0;
bufsize = 10;
while(choice !=3)
{
printf("\n 1. Produce \t 2. Consume \t3. Exit");
printf("\n Enter your choice: ");
scanf("%d", &choice);
switch(choice) {
case 1: if((in+1)%bufsize==out)
printf("\n Buffer is Full");
else
{
printf("\nEnter the value: ");
scanf("%d", &produce);
buffer[in] = produce;
in = (in+1)%bufsize;
}
break;
case 2: if(in == out)
printf("\nBuffer is Empty");
else
{
consume = buffer[out];
printf("\nThe consumed value is %d", consume);
out = (out+1)%bufsize;
}
break;
} } }

4)/*Writer Process*/
#include <stdio.h>
#include <fcntl.h>
#include <sys/stat.h>
#include <sys/types.h>
#include <unistd.h>
int main()
{
int fd;
char buf[1024];
/* create the FIFO (named pipe) */
char * myfifo = "/tmp/myfifo";
mkfifo(myfifo, 0666);
printf("Run Reader process to read the FIFO File\n");
fd = open(myfifo, O_WRONLY);
write(fd,"Hi", sizeof("Hi"));
/* write "Hi" to the FIFO */
close(fd);
unlink(myfifo); /* remove the FIFO */
return 0;
}
/* Reader Process*/
#include <fcntl.h>
#include <sys/stat.h>
#include <sys/types.h>
#include <unistd.h>
#include <stdio.h>
#define MAX_BUF 1024
int main()
{
int fd;
/* A temp FIFO file is not created in reader */
char *myfifo = "/tmp/myfifo";
char buf[MAX_BUF];
/* open, read, and display the message from the FIFO */
fd = open(myfifo, O_RDONLY);
read(fd, buf, MAX_BUF);
printf("Writer: %s\n", buf);
close(fd);
return 0;
}

5) #include <stdio.h>
#include <stdlib.h>
int main()
{
 int Max[10][10], need[10][10], alloc[10][10], avail[10], completed[10], safeSequence[10];
 int p, r, i, j, process, count;
 count = 0;
 printf("Enter the no of processes : ");
 scanf("%d", &p);
 for(i = 0; i< p; i++)
 completed[i] = 0;
 printf("\n\nEnter the no of resources : ");
 scanf("%d", &r);
 printf("\n\nEnter the Max Matrix for each process : ");
 for(i = 0; i < p; i++)
 {
 printf("\nFor process %d : ", i + 1);
 for(j = 0; j < r; j++)
 scanf("%d", &Max[i][j]);
 }
 printf("\n\nEnter the allocation for each process : ");
 for(i = 0; i < p; i++)
 {
 printf("\nFor process %d : ",i + 1);
 for(j = 0; j < r; j++)
 scanf("%d", &alloc[i][j]);
 }
 printf("\n\nEnter the Available Resources : ");
 for(i = 0; i < r; i++)
 scanf("%d", &avail[i]);
 for(i = 0; i < p; i++)
 for(j = 0; j < r; j++)
 need[i][j] = Max[i][j] - alloc[i][j];
 do
 {
 printf("\n Max matrix:\tAllocation matrix:\n");
 for(i = 0; i < p; i++)
 {
 for( j = 0; j < r; j++)
 printf("%d ", Max[i][j]);
 printf("\t\t");
for( j = 0; j < r; j++)
 printf("%d ", alloc[i][j]);
 printf("\n");
 }
 process = -1;
 for(i = 0; i < p; i++)
 {
 if(completed[i] == 0)//if not completed
 {
 process = i ;
 for(j = 0; j < r; j++)
 {
 if(avail[j] < need[i][j])
 {
 process = -1;
 break;
 }
 }
 }
 if(process != -1)
 break;
 }
 if(process != -1)
 {
 printf("\nProcess %d runs to completion!", process + 1);
 safeSequence[count] = process + 1;
 count++;
 for(j = 0; j < r; j++)
 {
 avail[j] += alloc[process][j];
 alloc[process][j] = 0;
 Max[process][j] = 0;
 completed[process] = 1;
 }
 }
 }
 while(count != p && process != -1);
 if(count == p)
 {
 printf("\nThe system is in a safe state!!\n");
 printf("Safe Sequence : < ");
 for( i = 0; i < p; i++)
 printf("%d ", safeSequence[i]);
 printf(">\n");
 }
 else
 printf("\nThe system is in an unsafe state!!");
}
