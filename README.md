# Last-hope


pg 1
..







-_________________<<<<___________
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

a)



b)

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
first = temp;
}

}

void insert_atlast()

{

if(first==NULL)

{

create();

first = temp;

last = first;

}

else

{

create();

last->next = temp;

last = temp;

}

}

void display()

{

temp1=first;

if(temp1 == NULL)

{

printf("List empty to display \n");

return;

}

printf("\n Linked list elements from begining : \n");

printf("USN\t NAME\t BRANCH\t SEMESTER\t PH.NUM\n");

while (temp1!= NULL)

{

printf("%s\t %s\t %s\t %d\t\t %ld\n", temp1->usn, temp1->name,temp1->branch,temp1-

>sem,temp1->phno);

temp1 = temp1->next;

}

printf(" No of students = %d ", count);

}

void delete_end()

{

struct node *temp;

temp=first;

if(first==NULL)

/* List is Empty */

{

printf("List is Empty\n");

return;

}

if(temp->next==NULL)

/* If only there is one node in the List */

{
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

printf("%s %s %s %d %ld\n", temp->usn, temp->name,temp->branch, temp->sem, temp-

>phno );

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

temp = temp1 = NULL;

printf("-----------------MENU----------------------\n");

printf("\n 1 Create a SLL of n Employees");

printf("\n 2 - Display from beginning");

printf("\n 3 - Insert at end");

printf("\n 4 - delete at end");

printf("\n 5 - Insert at beg");

printf("\n 6 - delete at beg");

printf("\n 7 - exit\n");

printf("-------------------------------------------\n");

while (1)

{

printf("\n Enter choice : ");

scanf("%d", &ch);

switch (ch)

{

case 1: printf("\n Enter no of students : ");

scanf("%d", &n);

for(i=0;i<n;i++)

insert_atfirst();

break;

case 2: display();

break;

case 3: insert_atlast();

break;

case 4: delete_end();

break;

case 5: insert_atfirst();

break;

case 6: delete_front();

break;

case 7: exit(0);

default:printf("Wrong Choice\n");

}

}

}


 

_______________>><<>____________

pg 8

#include<string.h>
int count=0;
struct node
{
struct node *prev;
int ssn,phno;
float sal;
char name[20],dept[10],desg[20];
struct node *next;
}*h,*temp,*temp1,*temp2,*temp4;
void create()
{
int ssn,phno;
float sal;
char name[20],dept[10],desg[20];
 temp =(struct node *)malloc(sizeof(struct node));
 temp->prev = NULL;
 temp->next = NULL;
 printf("\n Enter ssn,name,department, designation, salary and phno of employee : ");
 scanf("%d %s %s %s %f %d", &ssn, name,dept,desg,&sal, &phno);
 temp->ssn = ssn;
 strcpy(temp->name,name);
 strcpy(temp->dept,dept);
 strcpy(temp->desg,desg);
 temp->sal = sal;
 temp->phno = phno;
 count++;
}
void insertbeg()
{
if (h == NULL)
 {
create();
 h = temp;
 temp1 = h;
 }
else
 {
 create();
 temp->next = h;
 h->prev = temp;
 h = temp;
 }
}
void insertend()
{
if(h==NULL)
 {
 create();
 h = temp;
 temp1 = h;
 }
else
 {
 create();
 temp1->next = temp;
 temp->prev = temp1;
 temp1 = temp;
 }
}
void displaybeg()
{
 temp2 =h;
if(temp2 == NULL)
 {
 printf("List empty to display \n");
 return;
 }
 printf("\n Linked list elements from begining : \n");
while (temp2!= NULL)
 {
 printf("%d %s %s %s %f %d\n", temp2->ssn, temp2->name,temp2->dept,
 temp2->desg,temp2->sal, temp2->phno );
 temp2 = temp2->next; 
}
 printf(" No of employees = %d ", count);
}
int deleteend()
{
struct node *temp;
 temp=h;
if(temp->next==NULL)
 {
 free(temp);
 h=NULL;
 return 0;
 }
else
 {
 temp2=temp1->prev;
 temp2->next=NULL;
 printf("%d %s %s %s %f %d\n", temp1->ssn, temp1->name,temp1->dept,
 temp1->desg,temp1->sal, temp1->phno );
 free(temp1);
 }
 count--;
return 0;
}
int deletebeg()
{
struct node *temp;
 temp=h;
if(temp->next==NULL)
 {
 free(temp);
 h=NULL;
 }
else
 {
 h=h->next;
 printf("%d %s %s %s %f %d", temp->ssn, temp->name,temp->dept,
 temp->desg,temp->sal, temp->phno );
 free(temp);
 }
 count--;
return 0; 
}
void main()
{
int ch,n,i;
 h=NULL;
 temp = temp1 = NULL;
 printf("-----------------MENU--------------------\n");
 printf("\n 1 - create a DLL of n emp");
 printf("\n 2 - Display from beginning");
 printf("\n 3 - Insert at end");
 printf("\n 4 - delete at end");
 printf("\n 5 - Insert at beg");
 printf("\n 6 - delete at beg");
 printf("\n 7 - exit\n");
 printf("------------------------------------------\n");
while (1)
 {
 printf("\n Enter choice : ");
 scanf("%d", &ch);
 switch (ch)
 {
 case 1:
 printf("\n Enter no of employees : ");
 scanf("%d", &n);
 for(i=0;i<n;i++)
 insertend();
 break;
 case 2:
 displaybeg();
 break;
 case 3:
 insertend();
 break;
 case 4:
 deleteend();
 break;
 case 5:
 insertbeg();
 break;
 case 6:
 deletebeg();
 break;
 case 7:
 exit(0);
 default: 
printf("wrong choice\n");
 }
 }
}

----______________<>><_______________

pg 9 

#include<stdio.h>

#include<math.h>

#include<stdlib.h>

struct node

{

int cf, px, py, pz;

int flag;

struct node *link;

};

typedef struct node NODE;

NODE* getnode()

{

NODE *x;

x = (NODE*)malloc(sizeof(NODE));

if(x == NULL)

{

printf("Insufficient memory\n");


exit(0);

}
return x;

}

void display(NODE *head)

{

NODE *temp;

if(head->link == head)

{

printf("Polynomial does not exist\n");

return;

}

temp = head->link;

printf("\n");

while(temp != head)

{

printf("%d x^%d y^%d z^%d",temp->cf,temp->px,temp->py,temp->pz);

if(temp->link != head)

printf(" + ");

temp = temp->link;

}

printf("\n");

}

NODE* insert_rear(int cf,int x,int y,int z,NODE *head)

{

NODE *temp, *cur;

temp = getnode();

temp->cf = cf;

temp->px = x;

temp->py = y;

temp->pz = z;

cur = head->link;

while(cur->link != head)

cur = cur->link;

cur->link = temp;

temp->link = head;

return head;

}

NODE* read_poly(NODE *head)

{

int px, py, pz, cf, ch;

printf("\nEnter coeff: ");

scanf("%d",&cf);

printf("\nEnter x, y, z powers(0-indiacate NO term): ");

scanf("%d%d%d", &px, &py, &pz);

head = insert_rear(cf,px,py,pz,head);

printf("\nIf you wish to continue press 1 otherwise 0: ");

scanf("%d", &ch);

while(ch != 0)

{
 printf("\nEnter coeff: ");

scanf("%d",&cf);

printf("\nEnter x, y, z powers(0-indiacate NO term): ");

scanf("%d%d%d",&px, &py, &pz);

head = insert_rear(cf,px,py,pz,head);

printf("\nIf you wish to continue press 1 otherwise 0: ");

scanf("%d", &ch);

}

return head;

}

NODE* add_poly(NODE *h1,NODE *h2,NODE *h3)

{

NODE *p1, *p2;

int cf;

p1 = h1->link;

while(p1 != h1)

{

p2=h2->link;

while(p2 != h2)

{

if(p1->px == p2->px && p1->py == p2->py && p1->pz == p2->pz)

break;

p2 = p2->link;

}

if(p2 != h2)

{

cf = p1->cf + p2->cf;

p2->flag = 1;

if(cf != 0)

h3 = insert_rear(cf,p1->px,p1->py,p1->pz,h3);

}

else

h3 = insert_rear(p1->cf,p1->px,p1->py,p1->pz,h3);

p1 = p1->link;

}

p2 = h2->link;

while(p2 != h2)

{

if(p2->flag == 0)

h3 = insert_rear(p2->cf,p2->px,p2->py,p2->pz,h3);

p2 = p2->link;

}

return h3;

}

void evaluate(NODE *head)

{

NODE *h1=head->link;

int x, y, z;
float result = 0.0;

printf("\nEnter x, y, z, terms to evaluate:\n");

scanf("%d%d%d", &x, &y, &z);

while(h1 != head)

{

result = result + (h1->cf * pow(x,h1->px) * pow(y,h1->py) * pow(z,h1->pz));

h1 = h1->link;

}

printf("\nPolynomial result is: %f", result);

}

void main()

{

NODE *h1, *h2, *h3, *eval;

int ch;

while(1)

{

eval = getnode();

h1 = getnode();

h2 = getnode();

h3 = getnode();

eval->link = eval;

h1->link = h1;

h2->link = h2;

h3->link = h3;

printf("\n\n1.Evaluate polynomial\n2.Add two polynomials\n3.Exit\n");

printf("Enter your choice: ");

scanf("%d", &ch);

switch(ch)

{

case 1: printf("\nEnter polynomial to evaluate:\n");

eval = read_poly(eval);

display(eval);

evaluate(eval);

free(eval);

break;

case 2: printf("\nEnter the first polynomial: ");

h1 = read_poly(h1);

printf("Flag = %d\n",h1->flag);

printf("\nEnter the second polynomial: ");

h2 = read_poly(h2);

h3 = add_poly(h1,h2,h3);

printf("\nFirst polynomial is: ");

display(h1);

printf("\nSecond polynomial is: ");

display(h2);

printf("\nThe sum of 2 polynomials is: ");

display(h3);

free(h1);
free(h2); 

free(h3);

break;

case 3: exit(0);

break;

default:printf("

\nInvalid entry");

}

}

}

____________<<<<<<_________<<<<__


pg 10


#include <stdio.h>

#include <stdlib.h>

struct BST

{

int data;

struct BST *left;

struct BST *right;

};

typedef struct BST NODE;

NODE* createtree(NODE *root, int data)

{

if (root == NULL)

{

NODE *temp;

temp = (NODE*) malloc (sizeof(NODE));

temp->data = data;

temp->left = temp->right = NULL;

return temp;

}

if (data < (root->data))

root->left = createtree(root->left, data);

else if (data > root->data)

root -> right = createtree(root->right, data);

return root;

}

void inorder(NODE *root)

{

if(root != NULL)

{

inorder(root->left);

printf("%d\t", root->data);

inorder(root->right);
}

void preorder(NODE *root)

{

if(root != NULL)

{

printf("%d\t", root->data);

preorder(root->left);

preorder(root->right);

}

}

void postorder(NODE *root)

{

if(root != NULL)

{

postorder(root->left);

postorder(root->right);

printf("%d\t", root->data);

}

}

NODE *search(NODE *root, int data)

{

if(root == NULL)

printf("\nElement not found");

else if(data < root->data)

root->left = search(root->left, data);

else if(data > root->data)

root->right = search(root->right, data);

else

printf("\nElement found is: %d", root->data);

return root;

}

void main()

{

int data, ch, i, n;

NODE *root = NULL;

while (1)

{

printf("\n1.Creation of Binary Search Tree");

printf("\n2.Inorder\n3.Preorder\n4.Postorder\n5.Search\n6.Exit");

printf("\nEnter your choice: ");

scanf("%d", &ch);

switch (ch)

{

case 1: printf("\nEnter N value: " );

scanf("%d", &n);

printf("\nEnter the values to create BST like(6,9,5,2,8,15,24,14,7,8,5,2)\n");

for(i=0; i<n; i++)


{

scanf("%d", &data);

root = createtree(root, data);

}

break;

case 2: printf("\nInorder Traversal: \n");

inorder(root);

break;

case 3: printf("\nPreorder Traversal: \n");

preorder(root);

break;

case 4: printf("\nPostorder Traversal: \n");

postorder(root);

break;

case 5: printf("\nEnter the element to Search: ");

scanf("%d", &data);

root=search(root, data);

break;

case 6: exit(0);

default: printf("\nWrong Option");

break;

}

}

}










