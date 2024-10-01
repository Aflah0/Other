Yaccal.l
 
{
 
       #include<stdio.h>
       #include "y.tab.h"
       extern int yylval;
 
%}
 
%%
 
[0-9]+ {
               yylval=atoi(yytext);
               return NUMBER;
       }
[\t];
[\n] return 0;
 
. return yytext[0];
 
%%
 
 
int yywrap()
{
       return 1;
}
 
 
 
 
yaccal.y
 
%{
       #include<stdio.h>
       int flag = 0;
%}
 
%token NUMBER
 
%left '+''-'
%left '*''/''%'
%left '(' ')'
%right uminus
 
%%
 
       ArithmeticExpression: E
{
       printf("\nResult=%d\n",$$);
       return 0;
};
 
E:E'+'E {$$=$1+$3;}
|E'-'E {$$=$1-$3;}
|E'*'E {$$=$1*$3;}
|E'/'E {$$=$1/$3;}
|E'%'E {$$=$1%$3;}
|'-'E uminus {$$=-$2;}
|'('E')' {$$=$2;}
| NUMBER {$$=$1;}
;
 
%%    
 
void main()
{  
       printf("\nEnter any arithmetic expression: \n");
       yyparse();
}
 
void yyerror()
{  
}  