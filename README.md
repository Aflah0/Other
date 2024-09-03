include<stdio.h>
#include<string.h>
char key[100][100],head[100] [100],dig[100][100 ],op[100][100],id[100][100];
int i=0,j=0,k=0,l=0,a=0,b=0,c=0,d=0,m=0,n=0;
%}
 
KW "int"|"while"|"if"|"else"|"for"|"char"|"float"|"case"|"switch"
HF "#include<".*">"
OP "+"|"-"|"*"|"/"|"="
DIG [0-9]*[0-9]*"."[0-9]+
ID [a-zA-Z][a-zA-Z0-9]*
 
%%
{KW} {strcpy(key[i],yytext);i++;}
{HF} {strcpy(head[j],yytext);j++;}
{DIG} {strcpy(dig[k],yytext);k++;}
{OP} {strcpy(op[m],yytext);m++;}
{ID} {strcpy(id[n],yytext);n++;}
. {}
%%
 
main()
{
yyin=fopen("input.c","r+");
yylex();
printf("\nKeywords:");
for(a=0;a<i;a++){
       printf("\n\t%s",key[a]);
}
printf("\nHeaderfiles:");
for(b=0;b<j;b++){
       printf("\n\t%s",head[b]);
}
printf("\nDigits:");
for(c=0;c<k;c++){
       printf("\n\t%s",dig[c]);
}
printf("\nOperators:");
for(d=0;d<m;d++){
       printf("\n\t%s",op[d]);
}
printf("\nIdentifiers:");
for(d=0;d<n;d++){
       printf("\n\t%s", id[d]);
}
}
 
int yywrap() {
       //printf("Errors\n");
       return 1;
}
