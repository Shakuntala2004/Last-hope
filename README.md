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
