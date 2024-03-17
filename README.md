# Last-hope
pg-2
#include<stdio.h>

char str[50], pat[20], rep[20], res[50];
int c = 0, m = 0, i = 0, j = 0, k, flag = 0;
void stringmatch() {
  while (str[c] != '\0') {
    if (str[m] == pat[i]) {
      i++;
      m++;
      if (pat[i] == '\0') {
        flag = 1;
        for (k = 0; rep[k] != '\0'; k++, j++) {
          res[j] = rep[k];
        }
        i = 0;
        c = m;
      }
    } else {
      res[j] = str[c];
      j++;
      c++;
      m = c;
      i = 0;
    }
  }
  res[j] = '\0';
}
void main() {
  printf("Enter the main string:");
  gets(str);
  printf("\nEnter the pat string:");
  gets(pat);
  printf("\nEnter the replace string:");
  gets(rep);
  printf("\nThe string before pattern match is:\n %s", str);
  stringmatch();
  if (flag == 1)
    printf("\nThe string after pattern match and replace is: \n %s ", res);
  else
    printf("\nPattern string is not found");
}
_________________<<<<<<_

pg - 3
#include <stdio.h>
#include <stdlib.h>
int s[5],top=-1;

void push()
{
    if(top==4)
        printf("\nStack overflow!!!!");
    else
    {
        printf("\nEnter element to insert:");
        scanf("%d",&s[++top]);
    }
}

void pop()
{
    if(top==-1)
        printf("\nStack underflow!!!");
    else
        printf("\nElement popped is: %d",s[top--]);
}
void disp()
{
    int t=top;
    if(t==-1)
        printf("\nStack empty!!");
    else
        printf("\nStack elements are:\n");
    while(t>=0)
        printf("%d ",s[t--]);
}
void pali()
{
    int num[5],rev[5],i,t;
    for(i=0,t=top;t>=0;i++,t--)
        num[i]=rev[t]=s[t];
    for(i=0;i<=top;i++)
        if(num[i]!=rev[i])
        break;
    /*printf(" num     rev\n");
    for(t=0;t<=top;t++)
      printf("%4d   %4d\n",num[t],rev[t]);*///remove /* */ to display num and rev
    if(i==top+1)
        printf("\nIt is a palindrome");
    else
        printf("\nIt is not a palindrome");
}

int main()
{
    int ch;
    do
    {
        printf("\n...Stack operations.....\n");
        printf("1.PUSH\n");
        printf("2.POP\n");
        printf("3.Palindrome\n");
        printf("4.Display\n");
        printf("5.Exit\n________________\n");
        printf("Enter choice:");
        scanf("%d",&ch);
        switch(ch)
        {
            case 1:push();break;
            case 2:pop();break;
            case 3:pali();break;
            case 4:disp();break;
            case 5:exit(0);
            default:printf("\nInvalid choice");
        }
    }
    while(1);
    return 0;

}
^_______________________

pg-4

#include<stdio.h>
#include<string.h>

int F(char symbol)
{
 switch (symbol)
 {
 case '+':
 case '-':return 2;
 case '*':
 case '/':
 case '%':return 4;
 case '^':
 case '$':return 5;
 case '(':return 0;
 case '#':return -1;
 default :return 8;
 }
}

int G(char symbol)
{
 switch (symbol)
 {
 case '+':
 case '-':return 1;
 case '*':
 case '/':
 case '%':return 3;
 case '^':
 case '$':return 6;
 case '(':return 3;
 case ')':return 0;
 default :return 7;
 }
}

void infix_postfix(char infix[], char postfix[])
{
int top=-1, j=0, i;
char s[30], symbol;
s[++top] = '#';
for(i=0; i < strlen(infix); i++)
{
 symbol = infix[i];
 while (F(s[top]) > G(symbol))
 {
  postfix[j] = s[top--];
  j++;
 }
 if(F(s[top]) != G(symbol))
  s[++top] = symbol;
 else
  top--;
}
while(s[top] != '#')
 postfix[j++] = s[top--];
postfix[j] = '\0';
}

void main()
{
char infix[20], postfix[20];
printf("\nEnter a valid infix expression\n") ;
scanf ("%s", infix) ;
infix_postfix (infix, postfix);
printf("\nThe infix expression is:\n");
printf ("%s",infix);
printf("\nThe postfix expression is:\n");
printf ("%s",postfix) ;

}
______________________________

pg 5

#include <stdio.h>void tower(int n, int source, int temp, int destination) {
if (n == 0)
return;
tower(n - 1, source, destination, temp);
printf("\nMove disc %d from %c to %c", n, source, destination);
tower(n - 1, temp, source, destination);
}
void main() {
int n;
printf("\nEnter the number of discs: \n");
scanf("%d", & n);
tower(n, 'A', 'B', 'C');
printf("\n\nTotal Number of moves are: %d", (int) pow(2, n) - 1);
}
_____<<>>______________

pg 6

#include <stdio.h>
#include <stdlib.h>
#define max 5
int q[max],f=-1,r=-1;
void ins()
{
    if(f==(r+1)%max)
        printf("\nQueue overflow");
    else
    {
        if(f==-1)
            f++;
        r=(r+1)%max;
        printf("\nEnter element to be inserted:");
        scanf("%d",&q[r]);
    }
}
void del()
{
    if(r==-1)
        printf("\nQueue underflow");
    else
    {
        printf("\nElemnt deleted is:%d",q[f]);
        if(f==r)
            f=r=-1;
        else
            f=(f+1)%max;
    }
}
void disp()
{
    if(f==-1)
        printf("\nQueue empty");
    else
    {
        int i;
        printf("\nQueue elements are:\n");
        for(i=f;i!=r;i=(i+1)%max)
            printf("%d\t",q[i]);
        printf("%d",q[i]);
        printf("\nFront is at:%d\nRear is at:%d",q[f],q[r]);
    }
}
int main()
{
    printf("\nCircular Queue operations");
    printf("\n1.Insert");
    printf("\n2.Delete");
    printf("\n3.Display");
    printf("\n4.Exit");
    int ch;
    do{
        printf("\nEnter choice:");
        scanf("%d",&ch);
        switch(ch)
        {
            case 1:ins();break;
            case 2:del();break;
            case 3:disp();break;
            case 4:exit(0);
            default:printf("\nInvalid choice...!");
        }
   }while(1);
    return 0;

}
_________________________<<<>>>>>>>
pg- 7
#include<stdio.h>

#include<stdlib.h>

#include<string.h>

int count=0;

struct node

{

int sem;

long int phno;

char name[20], branch[10], usn[20];

struct node *next;

}*first=NULL,*last=NULL,*temp=NULL, *temp1;

void create()

{

int sem;

long int phno;

char name[20],branch[10],usn[20];

temp=(struct node*)malloc(sizeof(struct node));

printf("\n Enter USN, NAME, BRANCH, SEMESTER, PHNUM of student : ");

scanf("%s %s %s %d %ld", usn, name,branch, &sem,&phno);

strcpy(temp->usn,usn);

strcpy(temp->name,name);

strcpy(temp->branch,branch);

temp->sem = sem;

temp->phno = phno;

temp->next=NULL;

count++;

}

void insert_atfirst()

{

if (first == NULL)

{

create();

first = temp;

last = first;

}

else

{

create();

temp->next = first;
printf("%s %s %s %d %ld\n", temp->usn, temp->name,temp->branch, temp->sem, temp-

>phno );

free(temp);

first=NULL;

}

else

/* If more than one node in the List */

{

while(temp->next!=last)

temp=temp->next;

printf("%s %s %s %d %ld\n", last->usn, last->name,last->branch, last->sem, last->phno );

free(last);

temp->next=NULL;

last=temp;

}

count--;

}

void delete_front()

{

struct node *temp;

temp=first;

if(first==NULL)

/* List is Empty */

{

printf("List is Empty\n");

return;

}

if(temp->next==NULL) /* If only there is one node in the List */

{

printf("%s %s %s %d %ld\n", temp->usn, temp->name,temp->branch, temp->sem, temp->phno );

free(temp);

first=NULL;

}

else

/* If more than one node in the List */

{

first=temp->next;

printf("%s %s %s %d %ld", temp->usn, temp->name,temp->branch,temp->sem, temp-

>phno );

free(temp);

}

count--;

}

void main()

{

int ch,n,i;

first=NULL;
first = temp;
void display()

{

temp = first;

if(temp == NULL)

{

printf("List is Empty\n");

return;

}

printf("\n Linked list elements from begining : \n");

while (temp != NULL)

{

printf("%d %s %s %s %f %ld\n", temp->ssn, temp->name,temp->dept,temp->desg,temp-

>sal, temp->phno );

temp = temp->next;

}

printf(" No of employees = %d", count);

}

void insert_front()

{

if (first == NULL)

{

create();

first = temp;

last = first;

}

else

{

create();

temp->next = first;

first->prev = temp;

first = temp;

}

}

void delete_front()

{

struct node *cur=first;

if(first == NULL) /* If the List is Empty */

{

printf("List is Empty\n");

return;

}

if(first->next == NULL) /*If there is only one node in the List */

{

printf("%d %s %s %s %f %ld\n", first->ssn, first->name,first->dept, first->desg,first-

>sal,first->phno );

free(first);

first = NULL;

}
