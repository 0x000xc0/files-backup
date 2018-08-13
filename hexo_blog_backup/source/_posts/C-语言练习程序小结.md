---
title: C 语言练习程序小结
date: 2018-08-01 19:23:38
tags: C
---
# 小结一 某点与圆
> - 需要用多个数学函数求值时，类型最好用 double。
- 非整型求绝对值用 fabs() 函数，而不是 abs()。
- 二次方用 pow() 函数，而不是习惯性用 `^2`。

例：四个圆塔高10米，半径1米，圆心在四个象限绝对值为（2，2），判断任意点坐标所在处高度？

解：某一点到圆心的距离大于圆的半径。
在圆外即满足 (2-|y|)^2 + (2-|x|)^2 > 1 。

程序：
```C
#include<stdio.h>
#include<math.h>
int main()
{
    double x,y;
    double r;
    printf("Enter site x,y value:\n");
    printf("x=?\n");
    scanf("%lf",&x);printf("x value:%lf\n",x);
    printf("y=?\n");
    scanf("%lf",&y);printf("y value:%lf\n",y);
    r=pow((2-fabs(y)),2)+pow((2-fabs(x)),2);
    r=sqrt(r);
    printf("\nr=%lf\n",r);
    if(pow((2-fabs(y)),2)+pow((2-fabs(x)),2)>1) //即 r>1
    {
        printf("\nHeight:0 M\n");
    }
    else
    {
        printf("\nHeight:10 M\n");
    }
    return 0;
}
```

程序运行结果：
![意点坐标所在处高度](图1.PNG)

# 小结二 求根
> - 迭代法求平方根。公式为 `x2=(x1+a/x1)/2` ，x1 初值取任意值 (1)。
- 牛顿迭代法求方程的根。公式为 `x2=x1-f(x1)/f'(x1)` ，x1 初值取某数附近。
- 二分法求方程的根。公式为取区间中点 `i=(a+b)/2` ，判断 `f(a)*f(i)<0` 是区间改为 `[a,i]`，否则区间就在 `[i,b]` 。

## 1 迭代法求平方根
例：求 x=a^(1/2) ？

解：求平方根的迭代公式为 `x2=(x1+a/x1)/2`,x2 下标为 n+1，x1 下标为 n。
利用迭代公式，使两次值的差的绝对值小于 1e-5，注意初值可以取任意值，本例取 1。

程序：
```C
#include<stdio.h>
#include<math.h>
int main()
{
    double a,x1,x2,temp,num1,num2;
    x1=1;//x1取一个初值。
    scanf("%lf",&a);
    do
    {
        x2=0.5*(x1+a/x1);//迭代公式。
        temp=x1;//保存求出的x1值。
        x1=x2;//准备下一次循环x1的值。

        num1=temp-x2;
        num2=fabs(num1);
    }while(num2>=10e-5);//满足一直循环。
    printf("%lf is root1=%lf,root2=%lf\n",a,temp);
    return 0;
}
```

程序运行结果：
![迭代法求平方根](图2.PNG)

## 2 牛顿迭代法求方程的根
例：2x^3 - 4x^2 +3x - 6 = 0，求 1.5 附近的根？

解：公式为 `x2=x1-f(x1)/f'(x1)`，x2 下标为 n+1，x1 下标为 n。
利用迭代公式，使两次值的差的绝对值小于 1e-5，注意初值取 1.5。

程序：
```C
#include<stdio.h>
#include<math.h>
int main()
{
    double x1,x2,temp,num;
    x1=1.5;
    do
    {
        x2=x1-(2*pow(x1,3)-4*pow(x1,2)+3*x1-6)/(6*pow(x1,2)-8*x1+3);
        temp=x1;
        x1=x2;
        num=fabs(temp-x2);
    }while(num>1e-5);
    printf("2x^3 - 4x^2 +3x - 6 = 0 root at 1.5\n\nroot1=%lf\nroot2=%lf\nroot=%5.2lf\n",temp,x2,x2);
    return 0;
}
```

程序运行结果：
![牛顿迭代法求方程的根](图3.PNG)

## 3 二分法求方程的根
例：求 2x^3 - 4x^2 + 3x - 6 = 0 在（-10，10）之间的根？

解：取区间中点 `i=(a+b)/2`，如果 `f(a)*f(i) 小于 0，则区间就变为在 [a,i]，否则区间就在 [i,b]，将新的区间表示为 [a,b]`

程序：
```C
#include<stdio.h>
#include<math.h>
int main()
{
    double a=-10,b=10,i,s;
    do
    {
        i=(a+b)/2;
        s=(2*pow(a,3)-4*pow(a,2)+3*a-6)*(2*pow(i,3)-4*pow(i,2)+3*i-6);
        if(s<0)
        {
            b=i;
        }
        else
        {
            a=i;
        }
    }while(b-a>1e-5);
    printf("2x^3 - 4x^2 + 3x - 6 = 0 at(-10,10)\nroot1=%lf,root2=%lf\nroot=%5.2lf\n",a,b,b);
    return 0;
}
```

程序运行结果：
![二分法求方程的根](图4.PNG)