---
layout: post
title:  "C语言之三"
categories: Other
tags: C语言
author: Liu
description: 
---
# 2019年07月22日

## 回顾

main()函数中的return的作用：使用return0表示代码正常执行，操作系统可以识别该返回值，并且理解该返回值，让程序正常执行。如果返回的是其他值，则程序停止执行。
00stdio.h  标准输入输出流。示例代码：

        #include <stdio.h>
        /*
        在这里引入了关于标准输入输出流，默认有三个文件
        stdin
        stdout
        stderr
        */
        int main(int argc, char const *argv[])
        {
            //printf("hello world \n");
            fprintf(stdout,"hello world \n");
            
            //scanf("%d",&a);
            int a;
            fscanf(stdin,"%d",&a);
            if (a>0)
            {
                printf("输入的值是多少呢？是  %d\n",a);
            }else
            {
                fprintf(stderr,"数字能小鱼 0 \n");
                return 1;
            };
            printf("输入的值是：%d\n",a);
            return 0;
        }

printf对比fprintf，scanf对比fscanf，多一个输入输出的参数，设置输入输出的位置。  
重定向：在代码执行时候，命令 `./a.out 0>>a0.txt 1>>a1.txt 2>>a2.txt` 将输入流（“0>>”）重定向为a0.txt，输出流（“1>>”）重定向为a1.txt，错误流（“2>>”）重定向为a2.txt。`cat a1.txt` 打开并查看a1.txt的内容。示例代码：

        #include <stdio.h>
        int main(int argc, char const *argv[])
        {
            printf("输入第一个值a： \n");
            int a;
            scanf("%d",&a);
            printf("输入第二个值b： \n");
            int b;
            scanf("%d",&b);
            printf("a+b=%d\n",a+b);
            printf("然后，来计算除法了\n");
            
            int i,j ;
            printf("请输入被除数：\n");
            scanf("%d",&i);
            printf("请输入除数：\n");
            scanf("%d",&j);
            if (0!=j)
            {
                printf("%d÷%d=%d\n",i,j,i/j);
            }else
            {
                printf("除数不能为0\n");
                fprintf(stderr,"报错信息，除数不能为零！\n");
                return 1;
            }
        return 0;
        }

00使用管道，将上一个程序执行的结果输出到下一个程序使用。  
`./input.out | ./avg.out` 得到输入所有数字的平均值。

2019年07月22日09:37:18
