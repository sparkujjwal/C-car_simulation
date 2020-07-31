# C-car_simulation
#include<graphics.h><br/>
#include<conio.h><br>
#include<dos.h><br>
class car<br>
{<br/>
protected:
	int x,y;
	int outline;
	int fillcolor;
public:
	void set(int sx,int sy,int so,int sf)
	{
	x=sx;y=sy;outline=so;fillcolor=sf;
	}
	void draw()
	{
	setcolor(outline);
	setfillstyle(SOLID_FILL,fillcolor);
	}
};
/*class rub:public car
{
public:
	void set(int s,int e)
	{
	car::set(s,e,0,0);
	}
	void erase()
	{
	car::draw();
	int box[]={0,0,
		   x+120,y-260,
		   x+120,y,
		   0,480};
	fillpoly(4,box);
	}
};*/
class road:public car
{
public:
	void set(int rx,int ry)
	{
	car::set(rx,ry,15,8);
	}
	void draw()
	{
	car::draw();
	setlinestyle(0,SOLID_LINE,THICK_WIDTH);
	line(x-640,y,x+640,y);
	}
};
class rect:public car
{
public:
	void set(int s,int d)
	{
	car::set(s,d,4,8);
	}
	void draw()
	{
	car::draw();
	int shape[]={x-120,y-40,
		     x-120,y-180,
		     x-120,y-260,
		     x+60,y-260,
		     x+120,y-180,
		     x+120,y-40};
	fillpoly(6,shape);
	}
};
class tyre1:public car
{
public:
	void set(int c,int s)
	{
	car::set(c,s,5,10);
	}
	void draw()
	{
	car::draw();
	circle(x-60,y-40,40);
	floodfill(x-60,y-40,5);
	}
};
class tyre2:public car
{
public:
	void set(int d,int l)
	{
	car::set(d,l,5,10);
	}
	void draw()
	{
	car::draw();
	circle(x+60,y-40,40);
	floodfill(x+60,y-40,5);
	}
};
class boundary:public car
{
public:
	void set(int a,int v)
	{
	car::set(a,v,4,0);
	}
	void draw()
	{
	car::draw();
	line(x-120,y-180,x+120,y-180);
	}
};
class pol:public car
{
public:
	void set(int d,int h)
	{
	car::set(d,h,15,15);
	}
	void draw()
	{
	car::draw();
	int nam[]={x-50,y,
		   x-50,y-200,
		   x+50,y-200,
		   x+50,y};
	fillpoly(4,nam);
	}
};
class unite:public car
{
private:
	road r;
	rect re;
	tyre1 o;
	tyre2 oo;
	boundary bound;
     //	rub del;
public:
	void set(int x,int y)
	{
	r.set(x,y);
	re.set(x,y);
	o.set(x,y);
	oo.set(x,y);
	bound.set(x,y);
       //	del.set(x,y);
	}
	void draw()
	{
       //	del.erase();
	r.draw();
	re.draw();
	o.draw();
	oo.draw();
	bound.draw();
	}
};
int main()
{
int driver,mode;
driver=DETECT;
initgraph(&driver,&mode,"\\turboc3\\bgi");
char ch[]="########  CAR GAME  ########";
moveto(70,100);
settextstyle(BOLD_FONT,HORIZ_DIR,1);
setcolor(4);
outtext(ch);
char s[]="ujjwal production";
moveto(190,200);
outtext(s);
char hj[]="PRESS ENTER";
moveto(220,300);
outtext(hj);
getch();
cleardevice();
char v[]="GAME OVER";
pol p;
unite obj;
int n;
char q[]=" BE CAREFUL";
for(n=100;n<=640;n++)
{
if(n==300)
{
moveto(200,50);
outtext(q);
delay(2000);
}
p.set(500,380);
p.draw();
if(n>=320)
{
break;
}
obj.set(n,380);
obj.draw();
sound(300);delay(20);nosound();
sound(250);nosound();
getch();
getch();
getch();
cleardevice();
}
for(int h=1;h<20;h++)
{
sound(456);delay(20);nosound();
sound(749);delay(20);nosound();
}
cleardevice();
moveto(170,200);
outtext("you bombard it");
delay(1500);
cleardevice();
moveto(200,300);
settextstyle(DEFAULT_FONT,HORIZ_DIR,2);
outtext(v);
delay(2000);
getch();
closegraph();
return 0;
}


