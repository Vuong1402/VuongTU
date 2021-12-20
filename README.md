# VuongTU
Выяснить, можно ли с поля (k, I) одним ходом ладьи, ферзя или слона (должен ввести пользователь) попасть на поле (m, n). Если нет, то выяснить, как это можно сделать за два хода (указать поле, на которое приводит первый ход).
#include <iostream>
using namespace std;
int k,l,m,n;
struct tt{
    int x,y,t;
};
tt Q[65], a[8][8];
int main()
{
    cin>>k>>l>>m>>n;
    int i,j, i_st=0,i_end=1;
    for(i=0; i<8; i++)
        for(j=0; j<8; j++)
            a[i][j].t=0;
    Q[0].x=k-1; Q[0].y=l-1; 
    while(i_st<i_end)
    {
        for(i=1; i+Q[i_st].x<8 && i+Q[i_st].y<8; i++)
            if(a[Q[i_st].x+i][Q[i_st].y+i].t==0)
            {
                a[Q[i_st].x+i][Q[i_st].y+i].t=a[Q[i_st].x][Q[i_st].y].t+1;
                a[Q[i_st].x+i][Q[i_st].y+i].x=Q[i_st].x;
                a[Q[i_st].x+i][Q[i_st].y+i].y=Q[i_st].y;
                Q[i_end].x=Q[i_st].x+i; Q[i_end++].y=Q[i_st].y+i; 
            }
        for(i=1; Q[i_st].x-i>=0 && i+Q[i_st].y<8; i++)
            if(a[Q[i_st].x-i][Q[i_st].y+i].t==0)
            {
                a[Q[i_st].x-i][Q[i_st].y+i].t=a[Q[i_st].x][Q[i_st].y].t+1;
                a[Q[i_st].x-i][Q[i_st].y+i].x=Q[i_st].x;
                a[Q[i_st].x-i][Q[i_st].y+i].y=Q[i_st].y;
                Q[i_end].x=Q[i_st].x-i; Q[i_end++].y=Q[i_st].y+i; 
            }
        for(i=1; i+Q[i_st].x<8 && Q[i_st].y-i>=0; i++)
            if(a[Q[i_st].x+i][Q[i_st].y-i].t==0)
            {
                a[Q[i_st].x+i][Q[i_st].y-i].t=a[Q[i_st].x][Q[i_st].y].t+1;
                a[Q[i_st].x+i][Q[i_st].y-i].x=Q[i_st].x;
                a[Q[i_st].x+i][Q[i_st].y-i].y=Q[i_st].y;
                Q[i_end].x=Q[i_st].x+i; Q[i_end++].y=Q[i_st].y-i; 
            }
        for(i=1; Q[i_st].x-i>=0 && Q[i_st].y-i>=0; i++)
            if(a[Q[i_st].x-i][Q[i_st].y-i].t==0)
            {
                a[Q[i_st].x-i][Q[i_st].y-i].t=a[Q[i_st].x][Q[i_st].y].t+1;
                a[Q[i_st].x-i][Q[i_st].y-i].x=Q[i_st].x;
                a[Q[i_st].x-i][Q[i_st].y-i].y=Q[i_st].y;
                Q[i_end].x=Q[i_st].x-i; Q[i_end++].y=Q[i_st].y-i; 
            }
        i_st++;
    }
    if(a[m-1][n-1].t==1)
        cout<<"1 step"<<endl;
    else
        cout<<"2 step"<<endl<<a[m-1][n-1].x+1<<" "<<a[m-1][n-1].y+1<<endl;
    return 0;
}
