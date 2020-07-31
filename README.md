# C-car_simulation
#include<graphics.h><br/>
#include<conio.h><br>
#include<dos.h><br>
class car<br>
{<br/>
protected:<br>
	int x,y;<br>
	int outline;<br>
	int fillcolor;<br>
public:<br>
	void set(int sx,int sy,int so,int sf)<br>
	{<br>
	x=sx;y=sy;outline=so;fillcolor=sf;<br>
	}<br>
	void draw()<br>
	{<br>
	setcolor(outline);<br>
	setfillstyle(SOLID_FILL,fillcolor);<br>
	}<br>
};<br>
class road:public car<br>
{<br>
public:<br>
	void set(int rx,int ry)<br>
	{<br>
	car::set(rx,ry,15,8);<br>
	}<br>
	void draw()<br>
	{<br>
	car::draw();<br>
	setlinestyle(0,SOLID_LINE,THICK_WIDTH);<br>
	line(x-640,y,x+640,y);<br>
	}<br>
};<br>
class rect:public car<br>
{<br>
public:<br>
	void set(int s,int d)<br>
	{<br>
	car::set(s,d,4,8);<br>
	}<br>
	void draw()<br>
	{<br>
	car::draw();<br>
	int shape[]={x-120,y-40,<br>
		     x-120,y-180,<br>
		     x-120,y-260,<br>
		     x+60,y-260,<br>
		     x+120,y-180,<br>
		     x+120,y-40};<br>
	fillpoly(6,shape);<br>
	}<br>
};<br>
class tyre1:public car<br>
{<br>
public:<br>
	void set(int c,int s)<br>
	{<br>
	car::set(c,s,5,10);<br>
	}<br>
	void draw()<br>
	{<br>
	car::draw();<br>
	circle(x-60,y-40,40);<br>
	floodfill(x-60,y-40,5);<br>
	}<br>
};<br>
class tyre2:public car<br>
{<br>
public:<br>
	void set(int d,int l)<br>
	{<br>
	car::set(d,l,5,10);<br>
	}<br>
	void draw()<br>
	{<br>
	car::draw();<br>
	circle(x+60,y-40,40);<br>
	floodfill(x+60,y-40,5);<br>
	}<br>
};<br>
class boundary:public car<br>
{<br>
public:<br>
	void set(int a,int v)<br>
	{<br>
	car::set(a,v,4,0);<br>
	}<br>
	void draw()<br>
	{<br>
	car::draw();<br>
	line(x-120,y-180,x+120,y-180);<br>
	}<br>
};<br>
class pol:public car<br>
{<br>
public:<br>
	void set(int d,int h)<br>
	{<br>
	car::set(d,h,15,15);<br>
	}<br>
	void draw()<br>
	{<br>
	car::draw();<br>
	int nam[]={x-50,y,<br>
		   x-50,y-200,<br>
		   x+50,y-200,<br>
		   x+50,y};<br>
	fillpoly(4,nam);<br>
	}<br>
};<br>
class unite:public car<br>
{<br>
private:<br>
	road r;<br>
	rect re;<br>
	tyre1 o;<br>
	tyre2 oo;<br>
	boundary bound;<br>
     //	rub del;
public:<br>
	void set(int x,int y)<br>
	{<br>
	r.set(x,y);<br>
	re.set(x,y);<br>
	o.set(x,y);<br>
	oo.set(x,y);<br>
	bound.set(x,y);<br>
       //	del.set(x,y);
	}<br>
	void draw()<br>
	{<br>
       //	del.erase();
	r.draw();<br>
	re.draw();<br>
	o.draw();<br>
	oo.draw();<br>
	bound.draw();<br>
	}<br>
};<br>
int main()<br>
{<br>
int driver,mode;<br>
driver=DETECT;<br>
initgraph(&driver,&mode,"\\turboc3\\bgi");<br>
char ch[]="########  CAR GAME  ########";<br>
moveto(70,100);<br>
settextstyle(BOLD_FONT,HORIZ_DIR,1);<br>
setcolor(4);<br>
outtext(ch);<br>
char s[]="ujjwal production";<br>
moveto(190,200);<br>
outtext(s);<br>
char hj[]="PRESS ENTER";<br>
moveto(220,300);<br>
outtext(hj);<br>
getch();<br>
cleardevice();<br>
char v[]="GAME OVER";<br>
pol p;<br>
unite obj;<br>
int n;<br>
char q[]=" BE CAREFUL";<br>
for(n=100;n<=640;n++)<br>
{<br>
if(n==300)<br>
{
moveto(200,50);
outtext(q);
delay(2000);
}<br>
p.set(500,380);
p.draw();
if(n>=320)<br>
{
break;
}<br>
obj.set(n,380);<br>
obj.draw();<br>
sound(300);delay(20);nosound();<br>
sound(250);nosound();<br>
getch();<br>
getch();
getch();
cleardevice();
}<br>
for(int h=1;h<20;h++)<br>
{
sound(456);delay(20);nosound();
sound(749);delay(20);nosound();
}<br>
cleardevice();<br>
moveto(170,200);<br>
outtext("you bombard it");<br>
delay(1500);<br>
cleardevice();<br>
moveto(200,300);<br>
settextstyle(DEFAULT_FONT,HORIZ_DIR,2);<br>
outtext(v);<br>
delay(2000);<br>
getch();<br>
closegraph();<br>
return 0;<br>
}<br>


