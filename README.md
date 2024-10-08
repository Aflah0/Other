10:32
• 5G 74)
firstandfollow.c
V
#include<stdio.h>
#include<ctype.h> #include<string.h>
void followfirst(char, int, int);
void follow(char c);
void findfirst(char, int, int);
int count, n = 0;
char cale_first[10][100];
char cale_follow[10][100];
int m = 0;
char production [10][10]; char f[10], first[10];
int k; char ck; int e;
int main(int argc, char **argv)
int jm = 0;
int km = 0;
int 1, choice; char c, ch;
count = 8;
strepy(production[0], "E=TR");
strcpy(production[1], "R=+TR");
strepy(production[2], "R=#");
strepy(production[3], "T=FY");
strepy(production[4], "Y=*FY");
strepy(production[5], "Y-#");
strpy(production[6], "F=(E)");
strepy(production[7], "F=i");
int kay; char done[count];
int ptr = -1;
fork = 0; k < count; k++) i
for kay = 0; kay < 100; kay++) 1
cale_first[k][kay] = !';
int pointl = 0, point2, x;