# 2021-04-25
指针学一学

程序改错。在一个3x4矩阵中找出最大数及最大数所在元素的下标。 
#include <stdio.h>
#define M 3
#define N 4
int FindMax(int (*p)[N],int m,int n, int *pRow, int *pCol) 
main()
{
    int score[M][N], i, j, maxScore, row, col;
    for ( i=0; i<M; i++ )
    {
          for ( j=0; j<N; j++ )
          {
               scanf("%d", &score[i][j]);
          }
    }
    maxScore = FindMax(*score, M, N, &row, &col);
    printf("%d %d %d\n", maxScore, row+1, col+1);
}
 
int FindMax( int (*p)[N], int m, int n, 
int *pRow, int *pCol )
{
    int  i, j, max;
    max = *(p);
    pRow = 0; 
    pCol = 0; 
    for (i=0; i<m; i++)
    {
        for (j = 0; j<n; j++)
                {
            if ( *(*(p+i)+j) > max )
                        {
                max = *(*(p+i)+j) ;
                *pRow = i;
                *pCol = j;
                        }
        }
    }
     
}

参考答案：
#include <stdio.h>
#define M 3
#define N 4
int FindMax(int (*p)[N],int m,int n, int *pRow, int *pCol);
main()
{             
    int score[M][N], i, j, maxScore, row, col;
    for ( i=0; i<M; i++ )
    {             
          for ( j=0; j<N; j++ )
          {           
               scanf("%d", &score[i][j]);
          }
    }
    maxScore = FindMax(score, M, N, &row, &col);
    printf("%d %d %d\n", maxScore, row+1, col+1);
}             
 
int FindMax( int (*p)[N], int m, int n, 
int *pRow, int *pCol )
{             
    int  i, j, max;
    max = *(*(p));
    *pRow = 0; 
    *pCol = 0; 
    for (i=0; i<m; i++)
    {             
        for (j = 0; j<n; j++)
                {             
            if ( *(*(p+i)+j) > max )
                        {             
                max = *(*(p+i)+j) ;
                *pRow = i;
                *pCol = j;
                        }
        }
    }
    return max;  
} 

