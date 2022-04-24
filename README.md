# Compilers-lab-manual-NIT-Manipur
## A collection of Compilers and System Design lab programs in NIT Manipur. You may find it useful.
## Q1. Write a program to print tokens for input string using the pattern given as : 

Pattern Token 
identifier ID 
number NUM 
if IF 
else ELSE 
then THEN 
while WHILE 
< RELOP 
> RELOP 
( BRACKET 
) BRACKET
### CODE:

%{  
#include<stdio.h>  
#include<string.h>  
ID, NUM, IF, THEN, ELSE, WHILE,  RELOP, BRACKET;  
%}  
letter [A-Z,a-z]  
 Page:2  digit [0-9]  
id {letter}({letter}{digit})*  
%%  
{id} {printf("ID"); return(ID);}  {numb} {printf("NUM");return(NUM);}  if {printf("IF");}  
else {printf("ELSE");}  
then {printf("THEN");}  
while {printf("RELOP");}  
"&gt;" {printf("RELOP");}  
"(" {printf("BRACKET");}  
")" {printf("BRACKET");}  
%%  
int main(void) 
{  
yylex();  
return 0;  
}  
int yywrap()  
{  
}  

##  To write a lex program to count the number of line,  space and words.  
### LEX CODE:  
%{  
#include<stdio.h>  
int lc=0,sc=0,wc=0;  
%}  
%%  
"" sc++;  
\n lc++;  
"EXIT" return 0;  
[a-z A-Z 0-9][a-z A-Z 0-9]* wc++;  
%%  
int yywrap(void)  
{  
return 1;  
}  
int main()  
{  
printf("Enter a string -\n");  
yylex();  
printf("sc:%d,lc:%d,wc:%d\n",sc,lc,wc);  
return 0;  
}
