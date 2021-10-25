# C-001--
求最小公倍数算法：

最小公倍数=两整数的乘积÷最大公约数

求最大公约数算法：

(1)辗转相除法

有两整数a和b：

① a%b得余数c

② 若c=0，则b即为两数的最大公约数

③ 若c≠0，则a=b，b=c，再回去执行①

例如求27和15的最大公约数过程为：

27÷15 余1215÷12余312÷3余0因此，3即为最大公约数

 代码如下：

复制代码
1#include<stdio.h>
 2 int main()   /*  辗转相除法求最大公约数 */ 
 3 { 
 4    int m, n, a, b, t, c;
 5    printf("Input two integer numbers:\n");
 6    scanf("%d%d", &a, &b);
 7    m=a;   n=b;
 8    while(b!=0)  /* 余数不为0，继续相除，直到余数为0 */ 
 9    {
　　　　　　 c=a%b; a=b;  b=c;//注意值的赋值情况
　　　　}
10    printf("The largest common divisor:%d\n", a);//注意，最后一次除数的值被b赋给了a
11    printf("The least common multiple:%d\n", m*n/a);
12 }
//不能想当然的写成：while（c!=0）
{
　　　　c=a%b;
　　　　a=b;
　　　　b=c;
}
复制代码
可以简写成：

1 int gcd(int a,int b)
2 {
3    return b==0?a:gcd(b,a%b);
4 }
⑵ 相减法

有两整数a和b：

① 若a>b，则a=a-b

② 若a<b，则b=b-a

③ 若a=b，则a（或b）即为两数的最大公约数

④ 若a≠b，则再回去执行①

例如求27和15的最大公约数过程为：

27－15＝12( 15>12 ) 15－12＝3( 12>3 )

12－3＝9( 9>3 ) 9－3＝6( 6>3 )

6－3＝3( 3==3 )

因此，3即为最大公约数

代码如下：

复制代码
1 #include<stdio.h>
 2 int main ( )  /* 相减法求最大公约数 */
 3 {  
 4    int m, n, a, b, c;
 5    printf("Input two integer numbers:\n");
 6    scanf ("%d,%d", &a, &b);m=a; n=b; 
 7      /* a, b不相等，大数减小数，直到相等为止。*/ 
 8    while ( a!=b) 
 9          if (a>b)  a=a-b;     
10          else  b=b-a;
11    printf("The largest common divisor:%d\n", a);
12    printf("The least common multiple:%d\n", m*n/a);
13 }
复制代码
⑶穷举法

有两整数a和b：

① i=1

② 若a，b能同时被i整除，则t＝i

③ i++

④ 若 i <= a(或b)，则再回去执行②

⑤ 若 i > a(或b)，则t即为最大公约数，结束

改进：

① i= a(或b)

② 若a，b能同时被i整除，则i即为最大公约数，

结束

③ i--，再回去执行②

有两整数a和b：

① i=1

② 若a，b能同时被i整除，则t＝i

③ i++

④ 若 i <= a(或b)，则再回去执行②

⑤ 若 i > a(或b)，则t即为最大公约数，结束

改进：

① i= a(或b)

② 若a，b能同时被i整除，则i即为最大公约数，

结束

③ i--，再回去执行②


1 #include<stdio.h>
 2 int main ()  /* 穷举法求最大公约数 */
 3 {  
 4    int  m, n, a, b, i, t;
 5    printf("Input two integer numbers:\n");
 6    scanf ("%d,%d", &a, &b);m=a;  n=b; 
 7    for (i=1; i<= a; i++)  
 8        if ( a%i == 0 && b%i ==0 )    t=i;
 9    printf("The largest common divisor:%d\n", t);
10    printf("The least common multiple:%d\n", m*n/t);
11 } 
12 /*  改进后的
13    for (t= a; t>0; t-- )    
14        if ( a%t == 0 && b%t ==0 )    break; 
15 */


1 //穷举法求最小公倍数
 2      for (i= a; ; i++ )
 3          if ( i % a == 0 && i % b ==0 )     break;
 4      printf("The least common multiple:%d\n", i )
 5  
 6 //多个数的最大公约数和最小公倍数
 7      for (i= a; i>0; i-- )
 8          if (a%i==0&&b%i==0&&c%i==0)     break;
 9      printf("The largest common divisor:%d\n", i);
10      for (i= a; ; i++ )
11          if (i%a==0&&i%b==0&&i% c==0)    break;
12      printf("The least common multiple:%d\n", i)；
