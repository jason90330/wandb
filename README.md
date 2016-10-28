 
#include "stdio.h"
#include<stdlib.h>
#include<ctype.h>
#include<math.h>
float fsin(float,float,float);
int main()
{
 
    char a[4], b = "sin";
    float angle, n;
   
    while (scanf("%s", a)!= EOF)
    {
        scanf("%f %f", &angle, &n);
        int i = 0;
        while (a[i] != '\0')//to小字母
        {
            a[i] = tolower(a[i]);
            i++;
        }
        while (angle > 180 || angle < -180)//角度轉換
        {
            if (angle > 180)angle -= 360;
            if (angle < -180)angle += 360;
        }
        angle = angle*3.14 / 180;
        if (!strcmp(a, "sin"))
        {
            printf("%f", n);
            //system("pause");
            float sum = fsin(angle, n, 0);
            printf("\n%f",sum);
        }
        else if (!strcmp(a, "cos"))
        {
 
        }
        else
        {
            puts("Input Error.");
 
        }
    }
    //while (getchar() != '\n');
}
 
float fsin(float angle, float n,float sum)
{
    if ((int)n == -1)
    {
        printf("\n%f", sum);
        return sum;
    }
    int pn=-1;
    int div = 1;
    for (int i = 1; i <= 2 * n + 1; i++)
        div *= i;
    if ((int)n % 2 == 0)pn = 1;
    sum += pn*pow(angle, 2 * n + 1) / div;
    //printf("\n  %f",sum);
    fsin(angle,--n,sum);
}
