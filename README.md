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

