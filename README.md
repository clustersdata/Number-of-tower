# Number-of-tower

Number of tower

Problem Description

在讲述DP算法的时候，一个经典的例子就是数塔问题，它是这样描述的：


有如下所示的数塔，要求从顶层走到底层，若每一步只能走到相邻的结点，则经过的结点的数字之和最大是多少？


已经告诉你了，这是个DP的题目，你能AC吗?


Input

输入数据首先包括一个整数C,表示测试实例的个数，每个测试实例的第一行是一个整数N(1 <= N <= 100)，表示数塔的高度，接下来用N行数字表示数塔，其中第i行有个i个整数，且所有的整数均在区间[0,99]内。

Output

对于每个测试实例，输出可能得到的最大和，每个实例的输出占一行。

Sample Input

1 5 7 3 8 8 1 0 2 7 4 4 4 5 2 6 5

Sample Output

30


代码：#include<stdio.h>

#include<string.h>

#define MAX 101

int arr[MAX][MAX][2];

void res()

{

    int n;  int i,j;
    
    memset(arr,0,MAX*MAX*sizeof(int));
    
    scanf("%d",&n);
    
    for(i=0;i<n;i++)    //输入数塔
    
        for(j=0;j<=i;j++) {   scanf("%d",&arr[i][j][0]);    arr[i][j][1]=arr[i][j][0];  }
        
    for(i=n-2;i>=0;i--)
    
    {
    
        for(j=0;j<=i;j++)
        
        {
        
            if(arr[i+1][j][1]>arr[i+1][j+1][1])    arr[i][j][1]+=arr[i+1][j][1];
            
            else                            arr[i][j][1]+=arr[i+1][j+1][1];
            
        }
        
    }
    
    printf("%d\n",arr[0][0][1]);
    
}

int main()

{

    int num;
    
    scanf("%d",&num);
    
    while(num--)  {  res();   }
    
    return 0;
    
}

