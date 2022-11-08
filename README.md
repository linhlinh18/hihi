
 Copyright: None
 Author: Tran Anh
 Description: http://www.code.tavn.net
*/

#include<conio.h>
#include<stdio.h>
#include<graphics.h>
#include<math.h>

typedef struct
{
    int x;
    int y;
}Point;

Point XacDinh(Point Tam, int R, int G)
{
    Point Kq;
    Kq.x=Tam.x+R*cos(G*M_PI/180);
    Kq.y=Tam.y+R*sin(G*M_PI/180);
    return Kq;
}


void VeNgoiSao(Point Tam, int R, int gbd,int color){
    setcolor(color);
    for(int i=0;i<5;i++){
        Point d1 = XacDinh(Tam,R,gbd+i*144);
        Point d2 = XacDinh(Tam,R,gbd+(i+1)*144);
        line(d1.x,d1.y,d2.x,d2.y);
    }
}

main()
{
    initwindow(800,600);
    Point Tam;
    Tam.x=400;
    Tam.y=300;
    int R=150;
    int gbd=270;
    int color=15;

    //Sao nam canh khong quay
    VeNgoiSao(Tam,R,gbd,color);

    //Sao nam canh xoay
     int t=0;

    while (1)
    {
        t=t+10;
        VeNgoiSao(Tam,R,gbd+t,color);
        delay(400);
        VeNgoiSao(Tam,R,gbd+t,0);
    }
    //het doan sao nam canh xoay


    getch();
}
