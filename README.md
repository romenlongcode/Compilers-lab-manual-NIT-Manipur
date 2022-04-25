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

## Q3.Write a Lex program which can recognise hex, octal, binary and decimal numbers.
### lex program:

%{  
#include<stdio.h>  
%}  
%%  
[0][b|B][0|1][0|1]* printf("this is a binary number");  [0-9][0-9]* printf("this is a decimal number");  [0][0-7][0-7]* printf("this is an octal number");  [0][x|X][0-9A-F][0-9A-F]* printf("this is a hexadecimal  number");  
%%  
int yywrap(void)  
{  
 return 1;  
}  
int main()  
{  
printf("Enter a number :\n");  
yylex();  
return 0;  
} 

## Q4 o write a Yaac program which recognizes sound  and place with definition.  
### LEX CODE:  
%{  
#include<stdio.h>  
#include<ctype.h>  
#include<stdlib.h>  
#include"y.tab.h"  
extern int yylval;  
%}  
%%  
"chik" {printf("CHIK");return(CHIK);}  
"chek" {printf("CHEK"); return(CHEK);}  
"india" {printf("INDIA"); return(INDIA);}  
%%  
int main()  
{  
yylex();  
return 0;  
}  
int yywrap()  
{  
} 
 PAGE-9  
PARSER CODE:  
%{  
#include<stdio.h>  
#include<ctype.h>  
#include<stdlib.h>  
#include"lex.yy.c"  
%}  
%token CHIK CHEK INDIA  
%%  
rhyme : sound place  
;  
sound : CHIK CHEK  
;  
place : INDIA  
;  
%%  
void yyerror(char *s)  
{  
 printf("% s is error", s);
}
