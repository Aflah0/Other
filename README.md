 ptr += 1;
 
 
               donee[ptr] = ck;
               printf(" Follow(%c) = { ", ck);
               calc_follow[point1][point2++] = ck;
 
 
               for(i = 0 + km; i < m; i++) {
                       int lark = 0, chk = 0;
                       for(lark = 0; lark < point2; lark++)
                       {
                               if (f[i] == calc_follow[point1][lark])
                               {
                                       chk = 1;
                                       break;
                               }
                       }
                       if(chk == 0)
                       {
                               printf("%c, ", f[i]);
                               calc_follow[point1][point2++] = f[i];
                       }
               }
               printf(" }\n\n");
               km = m;
               point1++;
       }
}
 
void follow(char c)
{
       int i, j;
 
       if(production[0][0] == c) {
               f[m++] = '$';
       }
       for(i = 0; i < 10; i++)
       {
               for(j = 2;j < 10; j++)
               {
                       if(production[i][j] == c)
                       {
                               if(production[i][j+1] != '\0')
                               {
 
                                       followfirst(production[i][j+1], i, (j+2));
                               }
 
                               if(production[i][j+1]=='\0' && c!=production[i][0])
                               {
 
                                       follow(production[i][0]);
                               }
                       }
               }
       }
}
void findfirst(char c, int q1, int q2)
{
       int j;
 
       if(!(isupper(c))) {
               first[n++] = c;
       }
       for(j = 0; j < count; j++)
       {
               if(production[j][0] == c)
               {
                       if(production[j][2] == '#')
                       {
                               if(production[q1][q2] == '\0')
                                       first[n++] = '#';
                               else if(production[q1][q2] != '\0'
                                               && (q1 != 0 || q2 != 0))
                               {
 
                                       findfirst(production[q1][q2], q1, (q2+1));
                               }
                               else
                                       first[n++] = '#';
                       }
                       else if(!isupper(production[j][2]))
                       {
                               first[n++] = production[j][2];
                       }
                       else
                       {
 
                               findfirst(production[j][2], j, 3);
                       }
               }
       }
}
void followfirst(char c, int c1, int c2)
{
       int k;
 
 
       if(!(isupper(c)))
               f[m++] = c;
       else
       {
               int i = 0, j = 1;
               for(i = 0; i < count; i++)
               {
                       if(calc_first[i][0] == c)
                               break;
               }
 
while(calc_first[i][j] != '!')
               {
                       if(calc_first[i][j] != '#')
                       {
                               f[m++] = calc_first[i][j];
                       }
                       else
                       {
                               if(production[c1][c2] == '\0')
                               {
 
                                       follow(production[c1][0]);
                               }
                               else
                               {
 
                                       followfirst(production[c1][c2], c1, c2+1);
                               }
                       }
                       j++;
               }
       }
}
 