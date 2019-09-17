# sophomore_year_on
Study_Code
#include<iostream>
#include<cstdlib>
#include<ctime>
#define MAXSIZE 100
using namespace std;
//创建线性表
typedef struct
{
    int elem[MAXSIZE];
    int last;
}SeqList;
//O(n*n)时间复杂度.
int delete_Seq(int x,int y,SeqList* L)
{
      for(int i=0;i<MAXSIZE;i++)
    {
        if(L->elem[i]>=x&&L->elem[i]<=y)//满足条件
        {
            for(int j=i+1;j<MAXSIZE;j++)//查找不满足删除条件
            {
                if(j==MAXSIZE-1) //查到表尾
                {
                return i;
                }
                if(L->elem[j]<x||L->elem[j]>y)//交换.
                {
                    int num = L->elem[i];
                 L->elem[i]=L->elem[j];
                 L->elem[j]=num;
                 break;
                }
            }
        }
    }
}
//时间复杂度O（n）
int delete_Seq1(int x,int y,SeqList* L)
{
    int k=0;//
    int j=0;
    for(int i=0;i<L->last;i++)
    {
        if(L->elem[i]>=x&&L->elem[i]<=y)
           {
              k++;
             // L->last--;
           }
        else
            L->elem[i-k]=L->elem[i],j++;
    }
    return j;
}

int main()
{
    SeqList L;
    srand(time(NULL));
    int x;
    int y;
    int b=0;
    int s=0;

   cout<<"线性表未删除前:"<<endl;
    for(int i=0;i<MAXSIZE;i++)
    {   L.elem[i]=rand()%100;
        cout<<L.elem[i]<<'\t';
        if(!i%4&&i!=0||i==MAXSIZE-1)
            cout<<endl;
    }
    cout<<"输入需要删除的区间：";
    cin>>x>>y;
    int de_size = delete_Seq(x,y,&L);
    cout<<"线性表删除后:"<<de_size<<endl;
    for(int i=0;i<de_size;i++)
    {
        cout<<L.elem[i]<<'\t';
        if(!i%4&&i!=0)
            cout<<endl;
    }
    return 0;
}
