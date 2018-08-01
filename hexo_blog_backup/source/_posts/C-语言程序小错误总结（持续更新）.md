---
title: C 语言程序小错误总结（持续更新）
date: 2018-08-01 19:23:38
tags: Tips
---
# 小结一
> - 需要用多个数学函数求值时，类型最好用 double。
- 非整型求绝对值用 fabs() 函数，而不是 abs()。
- 二次方用 pow() 函数，而不是习惯性用 `^2`。

程序示例：
四个圆塔高10米，半径1米，圆心在四个象限绝对值为（2，2），判断任意点坐标所在处高度？
解：在圆外即满足 (2-|y|)^2 + (2-|x|)^2 > 1 。

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