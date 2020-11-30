#include<fstream.h>
#include<iomanip.h>
#include<conio.h>
#include<stdlib.h>
#include<stdio.h>
#include<graphics.h>
#include<string.h>
#include<dos.h>
void clear()
{
	cleardevice();
	clrscr();
	cleardevice();
}
int length(int val)
{
	int len=0;
	while(val/10>0)
	{
		val/=10;
		len++;
	}
	return len;
}
class player
{
	char name1[20];
	char name2[20];
	char winner[20];
	int pid;
	public:
	void setid(int i)
	{
		pid=i+1;
	}
	void nameinput()
	{
		cout<<"\n\n\n\n\t\t\t\tRecord ID: "<<pid;
		cout<<"\n\t\t\t\tPlayer 1: ";
		gets(name1);
		cout<<"\n\t\t\t\tPlayer 2: ";
		gets(name2);
	}
	void setwin(char win[20])
	{
		if(strcmpi(win,"Player 1")==0)
			strcpy(winner,name1);
		else if(strcmpi(win,"Player 2")==0)
			strcpy(winner,name2);
		else
			strcpy(winner,win);
	}
	void show(int rmax,int p1l,int p2l,int wl)
	{
		int idl=length(pid);
		idl/=2;
		int n1l=strlen(name1)/2;
		int n2l=strlen(name2)/2;
		int winl=strlen(winner)/2;
		cout<<"||"<<setw(rmax+idl+2)<<pid<<setw(rmax-idl+3)<<"||"<<setw(p1l+n1l+1)<<name1<<setw(p1l-n1l+3)<<"||"<<setw(p2l+n2l+1)<<name2<<setw(p2l-n2l+3)<<"||"<<setw(wl+winl+1)<<winner<<setw(wl-winl+3)<<"||";
	}
	void r1()
	{
		cout<<name1;
	}
	void r2()
	{
		cout<<name2;
	}
	void win()
	{
		cout<<winner;
	}
	char * rn1()
	{
		return name1;
	}
	char * rn2()
	{
		return name2;
	}
	char * rwin()
	{
		return winner;
	}
	void modn1(char edit[20])
	{
		strcpy(name1,edit);
	}
	void modn2(char edit[20])
	{
		strcpy(name2,edit);
	}
	void modn3(char edit[20])
	{
		strcpy(winner,edit);
	}
	int rid()
	{
		return pid;
	}
}p;
void start()
{
	int gd=DETECT,gm;
	char ent;
	initgraph(&gd,&gd,"c:\\TURBOC3\\BGI");
	clear();
	cout<<"\n\t\t\tGAME INTRODUCTION!!";
	cout<<"\n\n\t\t\t\t\t\tPress Enter to Continue...";
	line(175,10,360,10);
	line(360,10,360,40);
	line(360,40,175,40);
	line(175,40,175,10);
	ent=getch();
	while(ent!='\r')
		ent=getch();
	cout<<"\n\n\t1.Aim of the Game is to Checkmate your Opponent by moving your pieces.";
	ent=getch();
	while(ent!='\r')
		ent=getch();
	cout<<"\n\n\t2.Checkmate is a situation where the opponent can not move any piece";
	cout<<"\n\t  to save his King.";
	ent=getch();
	while(ent!='\r')
		ent=getch();
	cout<<"\n\n\t3.In a situation where King is under the direct attack of any piece but";
	cout<<"\n\t  can be saved, the King is in danger & the situation is called Check.";
	ent=getch();
	while(ent!='\r')
		ent=getch();
	cout<<"\n\n\t4.A red box will represent the selected piece.";
	ent=getch();
	while(ent!='\r')
		ent=getch();
	cout<<"\n\n\t5.Use arrow keys to reach the piece which you want to move.";
	ent=getch();
	while(ent!='\r')
		ent=getch();
	cout<<"\n\n\t6.Press Spacebar to select this piece.";
	ent=getch();
	while(ent!='\r')
		ent=getch();
	cout<<"\n\n\t7.Blue boxes show the possible places where the selected piece can go.";
	ent=getch();
	while(ent!='\r')
		ent=getch();
	cout<<"\n\n\t8.To reach to a Blue Box, use the arrow keys and press Enter to place";
	cout<<"\n\t  the piece at the desired location.";
	ent=getch();
	while(ent!='\r')
		ent=getch();
	cout<<"\n\n\t9.If any of the two players wants to quit the game, just press '/'";
	ent=getch();
	while(ent!='\r')
		ent=getch();
	cout<<"\n\n\t10.The game will not be saved and the other player will automatically";
	cout<<"\n\t   win the game.";
	ent=getch();
	while(ent!='\r')
		ent=getch();
	cout<<"\n\n\t11.No player will be allowed to undo any move, so play carefully!";
	ent=getch();
	while(ent!='\r')
		ent=getch();
}
void rook(int color,int x,int y)
{
	setcolor(0);
	line(x-15,y+16,x+15,y+16);
	line(x-15,y+16,x-15,y+11);
	line(x+15,y+16,x+15,y+11);
	line(x+15,y+11,x-15,y+11);
	line(x-15,y+11,x-8,y+6);
	line(x+15,y+11,x+8,y+6);
	line(x-8,y+6,x+8,y+6);
	line(x+8,y+6,x+8,y-7);
	line(x-8,y+6,x-8,y-7);
	line(x-8,y-7,x+8,y-7);
	line(x-8,y-7,x-15,y-12);
	line(x+8,y-7,x+15,y-12);
	line(x+15,y-12,x+15,y-16);
	line(x-15,y-12,x-15,y-16);
	line(x-15,y-16,x-8,y-16);
	line(x-8,y-16,x-8,y-14);
	line(x-8,y-14,x-3.5,y-14);
	line(x-3.5,y-14,x-3.5,y-16);
	line(x-3.5,y-16,x+3.5,y-16);
	line(x+3.5,y-16,x+3.5,y-14);
	line(x+3.5,y-14,x+8,y-14);
	line(x+8,y-14,x+8,y-16);
	line(x+8,y-16,x+15,y-16);
	setfillstyle(SOLID_FILL,color);
	floodfill(x,y+13,0);
	floodfill(x,y+10,0);
	floodfill(x,y+4,0);
	floodfill(x,y-9,0);
}
void pawn(int color,int x,int y)
{
	setcolor(0);
	line(x-12,y+16,x+12,y+16);
	arc(x,y+16,0,80,12);
	arc(x,y+16,100,180,12);
	arc(x,y-2,310,0,7);
	arc(x,y-2,0,75,7);
	arc(x,y-2,105,240,7);
	arc(x,y-12,300,0,4);
	arc(x,y-12,0,240,4);
	setfillstyle(SOLID_FILL,color);
	floodfill(x,y,0);
}
void knight(int color,int x,int y)
{
	setcolor(0);
	line(x-6.5,y+16,x+11.5,y+16);
	arc(x-0.5,y+14,120,185,6);
	arc(x-6.5,y+4,300,5,6);
	line(x-0.5,y+2,x-6.5,y+6);
	arc(x-7.5,y+5,150,330,1);
	line(x-7.5,y+3,x-10.5,y+5);
	arc(x-9.5,y+3,120,240,3);
	line(x-10.5,y+1,x-6.5,y-6);
	line(x-10.5,y+3,x-9.5,y+2);
	line(x-6.5,y-6,x-6.5,y-9);
	line(x-6.5,y-9,x-3.5,y-11);
	line(x-6.5,y-11,x-1.5,y-11);
	arc(x+1.5,y-12,90,200,4);
	line(x+1.5,y-15,x+1.5,y-12);
	line(x-2.5,y-14,x-4.5,y-16);
	line(x-4.5,y-16,x-6.5,y-8);
	arc(x+1.5,y-4,0,90,8);
	arc(x-2.5,y+5,337,40,15);
	line(x+11.5,y+12,x+11.5,y+16);
	circle(x-4.5,y-5,1);
	setfillstyle(SOLID_FILL,color);
	floodfill(x+2.5,y+2,0);
	floodfill(x-6.5,y+4,0);
	floodfill(x-11.5,y+3,0);
	floodfill(x-3.5,y-13,0);
	setfillstyle(SOLID_FILL,15-color);
	floodfill(x-4.5,y-5,0);
}
void king(int color,int x,int y)
{
	setcolor(0);
	arc(x,y-9,240,300,25);
	arc(x,y+61,75,105,50);
	arc(x,y+56,75,105,50);
	arc(x,y+51,75,105,50);
	line(x+12,y+11,x+12,y+2);
	line(x-13,y+12,x-13,y+2);
	line(x,y,x,y-4);
	line(x+12,y+2,x+16,y-2);
	line(x-13,y+2,x-16,y-2);
	line(x,y-4,x-7,y-9);
	line(x,y-4,x+8,y-10);
	arc(x+12,y-6,330,0,5);
	arc(x+12,y-6,0,125,5);
	arc(x-12,y-6,30,220,5);
	arc(x,y-4,30,140,5);
	line(x-1,y-10,x-1,y-12);
	line(x-1,y-12,x-3,y-12);
	line(x-3,y-12,x-3,y-14);
	line(x-3,y-14,x-1,y-14);
	line(x-1,y-14,x-1,y-16);
	line(x-1,y-16,x+1,y-16);
	line(x+1,y-16,x+1,y-14);
	line(x+1,y-14,x+3,y-14);
	line(x+3,y-14,x+3,y-12);
	line(x+3,y-12,x+1,y-12);
	line(x+1,y-12,x+1,y-10);
	setfillstyle(SOLID_FILL,color);
	floodfill(x,y+14,0);
	floodfill(x,y+8,0);
	floodfill(x,y+4,0);
	floodfill(x+5,y-4,0);
	floodfill(x-5,y-4,0);
	floodfill(x,y-6,0);
	floodfill(x,y-13,0);
}
void queen(int color,int x,int y)
{
	setcolor(0);
	arc(x,y-24,250,290,40);
	arc(x,y+49,70,107,40);
	line(x+13,y+13,x+13,y+11);
	line(x-13,y+13,x-13,y+11);
	line(x-10,y+9,x-10,y+6);
	line(x+10,y+9,x+10,y+6);
	line(x-10,y+6,x+10,y+6);
	line(x-10,y+6,x-14,y+2);
	line(x+10,y+6,x+14,y+2);
	arc(x,y+40,70,108,40);
	line(x+14,y+2,x+15,y-8);
	line(x+15,y-8,x+9,y+1);
	line(x+9,y+1,x+8,y-10);
	line(x+8,y-10,x+3,y);
	line(x+3,y,x,y-12);
	line(x,y-12,x-3,y);
	line(x-3,y,x-8,y-10);
	line(x-8,y-10,x-9,y+1);
	line(x-9,y+1,x-15,y-8);
	line(x-15,y-8,x-14,y+2);
	circle(x-16,y-10,2);
	circle(x-9,y-12,2);
	circle(x,y-14,2);
	circle(x+9,y-12,2);
	circle(x+16,y-10,2);
	setfillstyle(SOLID_FILL,color);
	floodfill(x,y+12,0);
	floodfill(x,y+8,0);
	floodfill(x,y+4,0);
	floodfill(x,y-9,0);
	floodfill(x-6,y-2,0);
	floodfill(x-13,y-2,0);
	floodfill(x+6,y-2,0);
	floodfill(x+13,y-2,0);
	floodfill(x-16,y-10,0);
	floodfill(x-9,y-12,0);
	floodfill(x,y-14,0);
	floodfill(x+9,y-12,0);
	floodfill(x+16,y-10,0);
}
void bishop(int color,int x,int y)
{
	setcolor(0);
	circle(x,y-13,3);
	line(x,y-10,x-4,y-6);
	line(x,y-10,x+4,y-6);
	arc(x-1,y-1,120,250,5);
	arc(x+1,y-1,300,60,5);
	line(x+2,y+5,x-2,y+5);
	line(x+2,y+5,x+4,y+7);
	line(x-2,y+5,x-4,y+7);
	line(x+4,y+7,x-4,y+7);
	line(x+4,y+7,x+5,y+9);
	line(x-4,y+7,x-5,y+9);
	line(x-5,y+9,x+5,y+9);
	arc(x-5,y+7,230,345,5);
	arc(x-10,y+16,50,165,5);
	arc(x+5,y+7,195,310,5);
	arc(x+10,y+16,10,120,5);
	line(x-15,y+16,x-13,y+16);
	line(x+13,y+16,x+15,y+16);
	arc(x+3,y+11,195,310,3);
	arc(x+9,y+16,10,120,3);
	line(x+7,y+14,x+5,y+14);
	arc(x-3,y+11,230,345,3);
	arc(x-9,y+16,50,165,3);
	line(x-7,y+14,x-5,y+14);
	line(x-2.5,y-2,x+3.5,y-2);
	line(x,y-5,x,y+1);
	setfillstyle(SOLID_FILL,color);
	floodfill(x,y-13,0);
	floodfill(x,y-9,0);
	floodfill(x,y+4,0);
	floodfill(x,y+6,0);
	floodfill(x,y+8,0);
	floodfill(x,y+10,0);
	floodfill(x+8,y+12,0);
	floodfill(x-8,y+12,0);
}
void display(int a[8][8])
{
	for(int i=0;i<8;i++)
	{
		for(int j=0;j<8;j++)
		{
			if(a[i][j]==82)
				rook(7,123+(56*i),43+(56*j));
			else if(a[i][j]==72)
				knight(7,123+(56*i),43+(56*j));
			else if(a[i][j]==66)
				bishop(7,123+(56*i),43+(56*j));
			else if(a[i][j]==81)
				queen(7,123+(56*i),43+(56*j));
			else if(a[i][j]==75)
				king(7,123+(56*i),43+(56*j));
			else if(a[i][j]==80)
				pawn(7,123+(56*i),43+(56*j));
			else if(a[i][j]==114)
				rook(8,123+(56*i),43+(56*j));
			else if(a[i][j]==104)
				knight(8,123+(56*i),43+(56*j));
			else if(a[i][j]==98)
				bishop(8,123+(56*i),43+(56*j));
			else if(a[i][j]==113)
				queen(8,123+(56*i),43+(56*j));
			else if(a[i][j]==107)
				king(8,123+(56*i),43+(56*j));
			else if(a[i][j]==112)
				pawn(8,123+(56*i),43+(56*j));
		}
	}
}
void check(int a[8][8],int turn,int &cno)
{
	for(int x=0;x<8;x++)
	{
		for(int y=0;y<8;y++)
		{
			if(turn%2==0 && a[x][y]==75)
			{
				if(x>0 && y>0 && a[x-1][y-1]==112)
					cno++;
				if(x<7 && y>0 && a[x+1][y-1]==112)
					cno++;
				if(x>0 && y>1 && a[x-1][y-2]==104)
					cno++;
				if(x>0 && y<6 && a[x-1][y+2]==104)
					cno++;
				if(x<7 && y<6 && a[x+1][y+2]==104)
					cno++;
				if(x<7 && y>1 && a[x+1][y-2]==104)
					cno++;
				if(x>1 && y>0 && a[x-2][y-1]==104)
					cno++;
				if(x>1 && y<7 && a[x-2][y+1]==104)
					cno++;
				if(x<6 && y>0 && a[x+2][y-1]==104)
					cno++;
				if(x<6 && y<7 && a[x+2][y+1]==104)
					cno++;
				if(x>0 && y>0 && a[x-1][y-1]==107)
					cno++;
				if(x>0 && y<7 && a[x-1][y+1]==107)
					cno++;
				if(x<7 && y<7 && a[x+1][y+1]==107)
					cno++;
				if(x<7 && y>0 && a[x+1][y-1]==107)
					cno++;
				if(x>0 && a[x-1][y]==107)
					cno++;
				if(y<7 && a[x][y+1]==107)
					cno++;
				if(y>0 && a[x][y-1]==107)
					cno++;
				if(x<7 && a[x+1][y]==107)
					cno++;
				if(x!=0)
				{
					for(int i=x-1;i>=0;i--)
					{
						if(a[i][y]!=0 || i==7)
							break;
					}
					if(a[i][y]==114 || a[i][y]==113)
						cno++;
				}
				if(x!=7)
				{
					for(int i=x+1;i<8;i++)
					{
						if(a[i][y]!=0 || i==7)
							break;
					}
					if(a[i][y]==114 || a[i][y]==113)
						cno++;
				}
				if(y!=0)
				{
					for(int i=y-1;i>=0;i--)
					{
						if(a[x][i]!=0 || i==7)
							break;
					}
					if(a[x][i]==114 || a[x][i]==113)
						cno++;
				}
				if(y!=7)
				{
					for(int i=y+1;i<8;i++)
					{
						if(a[x][i]!=0 || i==7)
							break;
					}
					if(a[x][i]==114 || a[x][i]==113)
						cno++;
				}
				if(x!=0 && y!=0)
				{
					for(int i=x-1,j=y-1;i>=0,j>=0;i--,j--)
					{
						if(a[i][j]!=0 || i==0 || j==0)
							break;
					}
					if(a[i][j]==98 || a[i][j]==113)
						cno++;
				}
				if(x!=7 && y!=7)
				{
					for(int i=x+1,j=y+1;i<8,j<8;i++,j++)
					{
						if(a[i][j]!=0 || i==7 || j==7)
							break;
					}
					if(a[i][j]==98 || a[i][j]==113)
						cno++;
				}
				if(x!=7 && y!=0)
				{
					for(int i=y-1,j=x+1;i>=0,j<8;i--,j++)
					{
						if(a[j][i]!=0 || i==0 || j==7)
							break;
					}
					if(a[j][i]==98 || a[j][i]==113)
						cno++;

				}
				if(x!=0 && y!=7)
				{
					for(int i=y+1,j=x-1;i<8,j>=0;i++,j--)
					{
						if(a[j][i]!=0 || i==7 || j==0)
							break;
					}
					if(a[j][i]==98 || a[j][i]==113)
						cno++;
				}
			}
			if(turn%2==1 && a[x][y]==107)
			{
				if(x>0 && y>0 && a[x-1][y-1]==80)
					cno++;
				if(x<7 && y>0 && a[x+1][y-1]==80)
					cno++;
				if(x>0 && y>1 && a[x-1][y-2]==72)
					cno++;
				if(x>0 && y<6 && a[x-1][y+2]==72)
					cno++;
				if(x<7 && y<6 && a[x+1][y+2]==72)
					cno++;
				if(x<7 && y>1 && a[x+1][y-2]==72)
					cno++;
				if(x>1 && y>0 && a[x-2][y-1]==72)
					cno++;
				if(x>1 && y<7 && a[x-2][y+1]==72)
					cno++;
				if(x<6 && y>0 && a[x+2][y-1]==72)
					cno++;
				if(x<6 && y<7 && a[x+2][y+1]==72)
					cno++;
				if(x>0 && y>0 && a[x-1][y-1]==75)
					cno++;
				if(x>0 && y<7 && a[x-1][y+1]==75)
					cno++;
				if(x<7 && y<7 && a[x+1][y+1]==75)
					cno++;
				if(x<7 && y>0 && a[x+1][y-1]==75)
					cno++;
				if(x>0 && a[x-1][y]==75)
					cno++;
				if(y<7 && a[x][y+1]==75)
					cno++;
				if(y>0 && a[x][y-1]==75)
					cno++;
				if(x<7 && a[x+1][y]==75)
					cno++;
				if(x!=0)
				{
					for(int i=x-1;i>=0;i--)
					{
						if(a[i][y]!=0 || i==7)
							break;
					}
					if(a[i][y]==82 || a[i][y]==81)
						cno++;
				}
				if(x!=7)
				{
					for(int i=x+1;i<8;i++)
					{
						if(a[i][y]!=0 || i==7)
							break;
					}
					if(a[i][y]==82 || a[i][y]==81)
						cno++;
				}
				if(y!=0)
				{
					for(int i=y-1;i>=0;i--)
					{
						if(a[x][i]!=0 || i==7)
							break;
					}
					if(a[x][i]==82 || a[x][i]==81)
						cno++;
				}
				if(y!=7)
				{
					for(int i=y+1;i<8;i++)
					{
						if(a[x][i]!=0 || i==7)
							break;
					}
					if(a[x][i]==82 || a[x][i]==81)
						cno++;
				}
				if(x!=0 && y!=0)
				{
					for(int i=x-1,j=y-1;i>=0,j>=0;i--,j--)
					{
						if(a[i][j]!=0 || i==0 || j==0)
							break;
					}
					if(a[i][j]==66 || a[i][j]==81)
						cno++;
				}
				if(x!=7 && y!=7)
				{
					for(int i=x+1,j=y+1;i<8,j<8;i++,j++)
					{
						if(a[i][j]!=0 || i==7 || j==7)
							break;
					}
					if(a[i][j]==66 || a[i][j]==81)
						cno++;
				}
				if(x!=7 && y!=0)
				{
					for(int i=y-1,j=x+1;i>=0,j<8;i--,j++)
					{
						if(a[j][i]!=0 || i==0 || j==7)
							break;
					}
					if(a[j][i]==66 || a[j][i]==81)
						cno++;

				}
				if(x!=0 && y!=7)
				{
					for(int i=y+1,j=x-1;i<8,j>=0;i++,j--)
					{
						if(a[j][i]!=0 || i==7 || j==0)
							break;
					}
					if(a[j][i]==66 || a[j][i]==81)
						cno++;
				}
			}
		}
	}
}
int checkbox(int x,int y,int dx,int dy,int a[8][8],int turn,int count)
{
	int ccount,num;
	int temp=a[x][y];
	a[x][y]=a[dx][dy];
	a[dx][dy]=temp;
	num=a[x][y];
	a[x][y]=0;
	check(a,turn,count);
	if(count>0)
		ccount=1;
	else
		ccount=0;
	a[x][y]=num;
	temp=a[x][y];
	a[x][y]=a[dx][dy];
	a[dx][dy]=temp;
	return ccount;
}
void box(int x,int y,int f,int b)
{
	setcolor(0);
	if(x>8 || y>8)
		setcolor(3);
	line(95+(56*x),15+(56*y),151+(56*x),15+(56*y));
	line(151+(56*x),15+(56*y),151+(56*x),71+(56*y));
	line(151+(56*x),71+(56*y),95+(56*x),71+(56*y));
	line(95+(56*x),71+(56*y),95+(56*x),15+(56*y));
	setfillstyle(SOLID_FILL,f);
	floodfill(96+(56*x),16+(56*y),0);
	setcolor(b);
	line(151+(56*x),15+(56*y),151+(56*x),71+(56*y));
	line(151+(56*x),71+(56*y),95+(56*x),71+(56*y));
	line(95+(56*x),71+(56*y),95+(56*x),15+(56*y));
	line(95+(56*x),15+(56*y),151+(56*x),15+(56*y));
}
int bbox(int x,int y,int a[8][8],int turn,int count,int show=0)
{
	int p=0,checkno=0,c=0;
	if(a[x][y]==80)
	{
		if(x>0 && y>0 && a[x-1][y-1]>97 && a[x-1][y-1]<115)
		{
			p=checkbox(x,y,x-1,y-1,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x-1,y-1,9,1);
				c++;
			}
		}
		if(x<7 && y>0 && a[x+1][y-1]>97 && a[x+1][y-1]<115)
		{
			p=checkbox(x,y,x+1,y-1,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x+1,y-1,9,1);
				c++;
			}
		}
		if(y==6)
		{
			if(a[x][5]==0 && a[x][4]==0)
			{
				p=checkbox(x,y,x,5,a,turn,checkno);
				if(p==0)
				{
					if(show==0)
						box(x,5,9,1);
					c++;
				}
				p=checkbox(x,y,x,4,a,turn,checkno);
				if(p==0)
				{
					if(show==0)
						box(x,4,9,1);
					c++;
				}
			}
			else if(a[x][4]!=0 && a[x][5]==0)
			{
				p=checkbox(x,y,x,5,a,turn,checkno);
				if(p==0)
				{
					if(show==0)
						box(x,5,9,1);
					c++;
				}
			}
		}
		if(y>0 && a[x][y-1]==0)
		{
			p=checkbox(x,y,x,y-1,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x,y-1,9,1);
				c++;
			}
		}
	}
	else if(a[x][y]==112)
	{
		if(x>0 && y>0 && a[x-1][y-1]>65 && a[x-1][y-1]<83)
		{
			p=checkbox(x,y,x-1,y-1,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x-1,y-1,9,1);
				c++;
			}
		}
		if(x<7 && y<7 && a[x+1][y-1]>65 && a[x+1][y-1]<83)
		{
			p=checkbox(x,y,x+1,y-1,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x+1,y-1,9,1);
				c++;
			}
		}
		if(y==6)
		{
			if(a[x][5]==0 && a[x][4]==0)
			{
				p=checkbox(x,y,x,5,a,turn,checkno);
				if(p==0)
				{
					if(show==0)
						box(x,5,9,1);
					c++;
				}
				p=checkbox(x,y,x,4,a,turn,checkno);
				if(p==0)
				{
					if(show==0)
						box(x,4,9,1);
					c++;
				}
			}
			else if(a[x][4]!=0 && a[x][5]==0)
			{
				p=checkbox(x,y,x,5,a,turn,checkno);
				if(p==0)
				{
					if(show==0)
						box(x,5,9,1);
					c++;
				}
			}
		}
		if(y>0 && a[x][y-1]==0)
		{
			p=checkbox(x,y,x,y-1,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x,y-1,9,1);
				c++;
			}
		}
	}
	else if(a[x][y]==82)
	{
		if(x!=0)
		{
			for(int i=x-1;i>=0;i--)
			{
				if(a[i][y]!=0)
				{
					if(a[i][y]>65 && a[i][y]<83)
						break;
					else if(a[i][y]>97 && a[i][y]<115)
					{
						p=checkbox(x,y,i,y,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(i,y,9,1);
							c++;
							break;
						}
					}
				}
				else
				{
					p=checkbox(x,y,i,y,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(i,y,9,1);
						c++;
					}
				}
			}
		}
		if(x!=7)
		{
			for(int i=x+1;i<8;i++)
			{
				if(a[i][y]!=0)
				{
					if(a[i][y]>65 && a[i][y]<83)
						break;
					else if(a[i][y]>97 && a[i][y]<115)
					{
						p=checkbox(x,y,i,y,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(i,y,9,1);
							c++;
							break;
						}
					}
				}
				else
				{
					p=checkbox(x,y,i,y,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(i,y,9,1);
						c++;
					}
				}
			}
		}
		if(y!=0)
		{
			for(int i=y-1;i>=0;i--)
			{
				if(a[x][i]!=0)
				{
					if(a[x][i]>65 && a[x][i]<83)
						break;
					else if(a[x][i]>97 && a[x][i]<115)
					{
						p=checkbox(x,y,x,i,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(x,i,9,1);
							c++;
							break;
						}
					}
				}
				else
				{
					p=checkbox(x,y,x,i,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(x,i,9,1);
						c++;
					}
				}
			}
		}
		if(y!=7)
		{
			for(int i=y+1;i<8;i++)
			{
				if(a[x][i]!=0)
				{
					if(a[x][i]>65 && a[x][i]<83)
						break;
					else if(a[x][i]>97 && a[x][i]<115)
					{
						p=checkbox(x,y,x,i,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(x,i,9,1);
							c++;
							break;
						}
					}
				}
				else
				{
					p=checkbox(x,y,x,i,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(x,i,9,1);
						c++;
					}
				}
			}
		}
	}
	else if(a[x][y]==114)
	{
		if(x!=0)
		{
			for(int i=x-1;i>=0;i--)
			{
				if(a[i][y]!=0)
				{
					if(a[i][y]>97 && a[i][y]<115)
						break;
					else if(a[i][y]>65 && a[i][y]<83)
					{
						p=checkbox(x,y,i,y,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(i,y,9,1);
							c++;
							break;
						}
					}
				}
				else
				{
					p=checkbox(x,y,i,y,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(i,y,9,1);
						c++;
					}
				}
			}
		}
		if(x!=7)
		{
			for(int i=x+1;i<8;i++)
			{
				if(a[i][y]!=0)
				{
					if(a[i][y]>97 && a[i][y]<115)
						break;
					else if(a[i][y]>65 && a[i][y]<83)
					{
						p=checkbox(x,y,i,y,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(i,y,9,1);
							c++;
							break;
						}
					}
				}
				else
				{
					p=checkbox(x,y,i,y,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(i,y,9,1);
						c++;
					}
				}
			}
		}
		if(y!=0)
		{
			for(int i=y-1;i>=0;i--)
			{
				if(a[x][i]!=0)
				{
					if(a[x][i]>97 && a[x][i]<115)
						break;
					else if(a[x][i]>65 && a[x][i]<83)
					{
						p=checkbox(x,y,x,i,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(x,i,9,1);
							c++;
							break;
						}
					}
				}
				else
				{
					p=checkbox(x,y,x,i,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(x,i,9,1);
						c++;
					}
				}
			}
		}
		if(y!=7)
		{
			for(int i=y+1;i<8;i++)
			{
				if(a[x][i]!=0)
				{
					if(a[x][i]>97 && a[x][i]<115)
						break;
					else if(a[x][i]>65 && a[x][i]<83)
					{
						p=checkbox(x,y,x,i,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(x,i,9,1);
							c++;
							break;
						}
					}
				}
				else
				{
					p=checkbox(x,y,x,i,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(x,i,9,1);
						c++;
					}
				}
			}
		}
	}
	else if(a[x][y]==66)
	{
		if(x!=0 && y!=0)
		{
			for(int i=x-1,j=y-1;i>=0,j>=0;i--,j--)
			{
				if(j<0 || i<0)
					break;
				if(a[i][j]!=0)
				{
					if(a[i][j]>65 && a[i][j]<83)
						break;
					else if(a[i][j]>97 && a[i][j]<115)
					{
						p=checkbox(x,y,i,j,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(i,j,9,1);
							c++;
						}
						break;
					}
				}
				else
				{
					p=checkbox(x,y,i,j,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(i,j,9,1);
						c++;
					}
				}
			}
		}
		if(x!=7 && y!=7)
		{
			for(int i=x+1,j=y+1;i<8,j<8;i++,j++)
			{
				if(j==8 || i==8)
					break;
				if(a[i][j]!=0)
				{
					if(a[i][j]>65 && a[i][j]<83)
						break;
					else if(a[i][j]>97 && a[i][j]<115)
					{
						p=checkbox(x,y,i,j,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(i,j,9,1);
							c++;
							break;
						}
					}
				}
				else
				{
					p=checkbox(x,y,i,j,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(i,j,9,1);
						c++;
					}
				}
			}
		}
		if(x!=7 && y!=0)
		{
			for(int i=y-1,j=x+1;i>=0,j<8;i--,j++)
			{
				if(j==8 || i<0)
					break;
				if(a[j][i]!=0)
				{
					if(a[j][i]>65 && a[j][i]<83)
						break;
					else if(a[j][i]>97 && a[j][i]<115)
					{
						p=checkbox(x,y,j,i,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(j,i,9,1);
							c++;
							break;
						}
					}
				}
				else
				{
					p=checkbox(x,y,j,i,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(j,i,9,1);
						c++;
					}
				}
			}
		}
		if(x!=0 && y!=7)
		{
			for(int i=y+1,j=x-1;i<8,j>=0;i++,j--)
			{
				if(i==8 || j<0)
					break;
				if(a[j][i]!=0)
				{
					if(a[j][i]>65 && a[j][i]<83)
						break;
					else if(a[j][i]>97 && a[j][i]<115)
					{
						p=checkbox(x,y,j,i,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(j,i,9,1);
							c++;
							break;
						}
					}
				}
				else
				{
					p=checkbox(x,y,j,i,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(j,i,9,1);
						c++;
					}
				}
			}
		}
	}
	else if(a[x][y]==98)
	{
		if(x!=0 && y!=0)
		{
			for(int i=x-1,j=y-1;i>=0,j>=0;i--,j--)
			{
				if(j<0 || i<0)
					break;
				if(a[i][j]!=0)
				{
					if(a[i][j]>97 && a[i][j]<115)
						break;
					else if(a[i][j]>65 && a[i][j]<83)
					{
						p=checkbox(x,y,i,j,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(i,j,9,1);
							c++;
						}
						break;
					}
				}
				else
				{
					p=checkbox(x,y,i,j,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(i,j,9,1);
						c++;
					}
				}
			}
		}
		if(x!=7 && y!=7)
		{
			for(int i=x+1,j=y+1;i<8,j<8;i++,j++)
			{
				if(j==8 || i==8)
					break;
				if(a[i][j]!=0)
				{
					if(a[i][j]>97 && a[i][j]<115)
						break;
					else if(a[i][j]>65 && a[i][j]<83)
					{
						p=checkbox(x,y,i,j,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(i,j,9,1);
							c++;
							break;
						}
					}
				}
				else
				{
					p=checkbox(x,y,i,j,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(i,j,9,1);
						c++;
					}
				}
			}
		}
		if(x!=7 && y!=0)
		{
			for(int i=y-1,j=x+1;i>=0,j<8;i--,j++)
			{
				if(j==8 || i<0)
					break;
				if(a[j][i]!=0)
				{
					if(a[j][i]>97 && a[j][i]<115)
						break;
					else if(a[j][i]>65 && a[j][i]<83)
					{
						p=checkbox(x,y,j,i,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(j,i,9,1);
							c++;
							break;
						}
					}
				}
				else
				{
					p=checkbox(x,y,j,i,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(j,i,9,1);
						c++;
					}
				}
			}
		}
		if(x!=0 && y!=7)
		{
			for(int i=y+1,j=x-1;i<8,j>=0;i++,j--)
			{
				if(i==8 || j<0)
					break;
				if(a[j][i]!=0)
				{
					if(a[j][i]>97 && a[j][i]<115)
						break;
					else if(a[j][i]>65 && a[j][i]<83)
					{
						p=checkbox(x,y,j,i,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(j,i,9,1);
							c++;
							break;
						}
					}
				}
				else
				{
					p=checkbox(x,y,j,i,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(j,i,9,1);
						c++;
					}
				}
			}
		}
	}
	else if(a[x][y]==81)
	{
		if(x!=0)
		{
			for(int i=x-1;i>=0;i--)
			{
				if(a[i][y]!=0)
				{
					if(a[i][y]>65 && a[i][y]<83)
						break;
					else if(a[i][y]>97 && a[i][y]<115)
					{
						p=checkbox(x,y,i,y,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(i,y,9,1);
							c++;
						}
						break;
					}
				}
				else
				{
					p=checkbox(x,y,i,y,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(i,y,9,1);
						c++;
					}
				}
			}
		}
		if(x!=7)
		{
			for(int i=x+1;i<8;i++)
			{
				if(a[i][y]!=0)
				{
					if(a[i][y]>65 && a[i][y]<83)
						break;
					else if(a[i][y]>97 && a[i][y]<115)
					{
						p=checkbox(x,y,i,y,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(i,y,9,1);
							c++;
							break;
						}
						break;
					}
				}
				else
				{
					p=checkbox(x,y,i,y,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(i,y,9,1);
						c++;
					}
				}
			}
		}
		if(y!=0)
		{
			for(int i=y-1;i>=0;i--)
			{
				if(a[x][i]!=0)
				{
					if(a[x][i]>65 && a[x][i]<83)
						break;
					else if(a[x][i]>97 && a[x][i]<115)
					{
						p=checkbox(x,y,x,i,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(x,i,9,1);
							c++;
							break;
						}
						break;
					}
				}
				else
				{
					p=checkbox(x,y,x,i,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(x,i,9,1);
						c++;
					}
				}
			}
		}
		if(y!=7)
		{
			for(int i=y+1;i<8;i++)
			{
				if(a[x][i]!=0)
				{
					if(a[x][i]>65 && a[x][i]<83)
						break;
					else if(a[x][i]>97 && a[x][i]<115)
					{
						p=checkbox(x,y,x,i,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(x,i,9,1);
							c++;
							break;
						}
						break;
					}
				}
				else
				{
					p=checkbox(x,y,x,i,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(x,i,9,1);
						c++;
					}
				}
			}
		}
		if(x!=0 && y!=0)
		{
			for(int i=x-1,j=y-1;i>=0,j>=0;i--,j--)
			{
				if(j<0 || i<0)
					break;
				if(a[i][j]!=0)
				{
					if(a[i][j]>65 && a[i][j]<83)
						break;
					else if(a[i][j]>97 && a[i][j]<115)
					{
						p=checkbox(x,y,i,j,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(i,j,9,1);
							c++;
						}
						break;
					}
				}
				else
				{
					p=checkbox(x,y,i,j,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(i,j,9,1);
						c++;
					}
				}
			}
		}
		if(x!=7 && y!=7)
		{
			for(int i=x+1,j=y+1;i<8,j<8;i++,j++)
			{
				if(j==8 || i==8)
					break;
				if(a[i][j]!=0)
				{
					if(a[i][j]>65 && a[i][j]<83)
						break;
					else if(a[i][j]>97 && a[i][j]<115)
					{
						p=checkbox(x,y,i,j,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(i,j,9,1);
							c++;
							break;
						}
						break;
					}
				}
				else
				{
					p=checkbox(x,y,i,j,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(i,j,9,1);
						c++;
					}
				}
			}
		}
		if(x!=7 && y!=0)
		{
			for(int i=y-1,j=x+1;i>=0,j<8;i--,j++)
			{
				if(j==8 || i<0)
					break;
				if(a[j][i]!=0)
				{
					if(a[j][i]>65 && a[j][i]<83)
						break;
					else if(a[j][i]>97 && a[j][i]<115)
					{
						p=checkbox(x,y,j,i,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(j,i,9,1);
							c++;
							break;
						}
						break;
					}
				}
				else
				{
					p=checkbox(x,y,j,i,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(j,i,9,1);
						c++;
					}
				}
			}
		}
		if(x!=0 && y!=7)
		{
			for(int i=y+1,j=x-1;i<8,j>=0;i++,j--)
			{
				if(i==8 || j<0)
					break;
				if(a[j][i]!=0)
				{
					if(a[j][i]>65 && a[j][i]<83)
						break;
					else if(a[j][i]>97 && a[j][i]<115)
					{
						p=checkbox(x,y,j,i,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(j,i,9,1);
							c++;
							break;
						}
						break;
					}
				}
				else
				{
					p=checkbox(x,y,j,i,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(j,i,9,1);
						c++;
					}
				}
			}
		}
	}
	else if(a[x][y]==113)
	{
		if(x!=0)
		{
			for(int i=x-1;i>=0;i--)
			{
				if(a[i][y]!=0)
				{
					if(a[i][y]>97 && a[i][y]<115)
						break;
					else if(a[i][y]>65 && a[i][y]<83)
					{
						p=checkbox(x,y,i,y,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(i,y,9,1);
							c++;
						}
						break;
					}
				}
				else
				{
					p=checkbox(x,y,i,y,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(i,y,9,1);
						c++;
					}
				}
			}
		}
		if(x!=7)
		{
			for(int i=x+1;i<8;i++)
			{
				if(a[i][y]!=0)
				{
					if(a[i][y]>97 && a[i][y]<115)
						break;
					else if(a[i][y]>65 && a[i][y]<83)
					{
						p=checkbox(x,y,i,y,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(i,y,9,1);
							c++;
							break;
						}
						break;
					}
				}
				else
				{
					p=checkbox(x,y,i,y,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(i,y,9,1);
						c++;
					}
				}
			}
		}
		if(y!=0)
		{
			for(int i=y-1;i>=0;i--)
			{
				if(a[x][i]!=0)
				{
					if(a[x][i]>97 && a[x][i]<115)
						break;
					else if(a[x][i]>65 && a[x][i]<83)
					{
						p=checkbox(x,y,x,i,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(x,i,9,1);
							c++;
							break;
						}
						break;
					}
				}
				else
				{
					p=checkbox(x,y,x,i,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(x,i,9,1);
						c++;
					}
				}
			}
		}
		if(y!=7)
		{
			for(int i=y+1;i<8;i++)
			{
				if(a[x][i]!=0)
				{
					if(a[x][i]>97 && a[x][i]<115)
						break;
					else if(a[x][i]>65 && a[x][i]<83)
					{
						p=checkbox(x,y,x,i,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(x,i,9,1);
							c++;
							break;
						}
						break;
					}
				}
				else
				{
					p=checkbox(x,y,x,i,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(x,i,9,1);
						c++;
					}
				}
			}
		}
		if(x!=0 && y!=0)
		{
			for(int i=x-1,j=y-1;i>=0,j>=0;i--,j--)
			{
				if(j<0 || i<0)
					break;
				if(a[i][j]!=0)
				{
					if(a[i][j]>97 && a[i][j]<115)
						break;
					else if(a[i][j]>65 && a[i][j]<83)
					{
						p=checkbox(x,y,i,j,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(i,j,9,1);
							c++;
						}
						break;
					}
				}
				else
				{
					p=checkbox(x,y,i,j,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(i,j,9,1);
						c++;
					}
				}
			}
		}
		if(x!=7 && y!=7)
		{
			for(int i=x+1,j=y+1;i<8,j<8;i++,j++)
			{
				if(j==8 || i==8)
					break;
				if(a[i][j]!=0)
				{
					if(a[i][j]>97 && a[i][j]<115)
						break;
					else if(a[i][j]>65 && a[i][j]<83)
					{
						p=checkbox(x,y,i,j,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(i,j,9,1);
							c++;
							break;
						}
						break;
					}
				}
				else
				{
					p=checkbox(x,y,i,j,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(i,j,9,1);
						c++;
					}
				}
			}
		}
		if(x!=7 && y!=0)
		{
			for(int i=y-1,j=x+1;i>=0,j<8;i--,j++)
			{
				if(j==8 || i<0)
					break;
				if(a[j][i]!=0)
				{
					if(a[j][i]>97 && a[j][i]<115)
						break;
					else if(a[j][i]>65 && a[j][i]<83)
					{
						p=checkbox(x,y,j,i,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(j,i,9,1);
							c++;
							break;
						}
						break;
					}
				}
				else
				{
					p=checkbox(x,y,j,i,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(j,i,9,1);
						c++;
					}
				}
			}
		}
		if(x!=0 && y!=7)
		{
			for(int i=y+1,j=x-1;i<8,j>=0;i++,j--)
			{
				if(i==8 || j<0)
					break;
				if(a[j][i]!=0)
				{
					if(a[j][i]>97 && a[j][i]<115)
						break;
					else if(a[j][i]>65 && a[j][i]<83)
					{
						p=checkbox(x,y,j,i,a,turn,checkno);
						if(p==0)
						{
							if(show==0)
								box(j,i,9,1);
							c++;
							break;
						}
						break;
					}
				}
				else
				{
					p=checkbox(x,y,j,i,a,turn,checkno);
					if(p==0)
					{
						if(show==0)
							box(j,i,9,1);
						c++;
					}
				}
			}
		}
	}
	else if(a[x][y]==72)
	{
		if(x>0 && y>1 && (a[x-1][y-2]<65 || a[x-1][y-2]>83))
		{
			p=checkbox(x,y,x-1,y-2,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x-1,y-2,9,1);
				c++;
			}
		}
		if(x>0 && y<6 && (a[x-1][y+2]<65 || a[x-1][y+2]>83))
		{
			p=checkbox(x,y,x-1,y+2,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x-1,y+2,9,1);
				c++;
			}
		}
		if(x<7 && y<6 && (a[x+1][y+2]<65 || a[x+1][y+2]>83))
		{
			p=checkbox(x,y,x+1,y+2,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x+1,y+2,9,1);
				c++;
			}
		}
		if(x<7 && y>1 && (a[x+1][y-2]<65 || a[x+1][y-2]>83))
		{
			p=checkbox(x,y,x+1,y-2,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x+1,y-2,9,1);
				c++;
			}
		}
		if(x>1 && y>0 && (a[x-2][y-1]<65 || a[x-2][y-1]>83))
		{
			p=checkbox(x,y,x-2,y-1,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x-2,y-1,9,1);
				c++;
			}
		}
		if(x>1 && y<7 && (a[x-2][y+1]<65 || a[x-2][y+1]>83))
		{
			p=checkbox(x,y,x-2,y+1,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x-2,y+1,9,1);
				c++;
			}
		}
		if(x<6 && y>0 && (a[x+2][y-1]<65 || a[x+2][y-1]>83))
		{
			p=checkbox(x,y,x+2,y-1,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x+2,y-1,9,1);
				c++;
			}
		}
		if(x<6 && y<7 && (a[x+2][y+1]<65 || a[x+2][y+1]>83))
		{
			p=checkbox(x,y,x+2,y+1,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x+2,y+1,9,1);
				c++;
			}
		}
	}
	else if(a[x][y]==104)
	{
		if(x>0 && y>1 && (a[x-1][y-2]<97 || a[x-1][y-2]>115))
		{
			p=checkbox(x,y,x-1,y-2,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x-1,y-2,9,1);
				c++;
			}
		}
		if(x>0 && y<6 && (a[x-1][y+2]<97 || a[x-1][y+2]>115))
		{
			p=checkbox(x,y,x-1,y+2,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x-1,y+2,9,1);
				c++;
			}
		}
		if(x<7 && y<6 && (a[x+1][y+2]<97 || a[x+1][y+2]>115))
		{
			p=checkbox(x,y,x+1,y+2,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x+1,y+2,9,1);
				c++;
			}
		}
		if(x<7 && y>1 && (a[x+1][y-2]<97 || a[x+1][y-2]>115))
		{
			p=checkbox(x,y,x+1,y-2,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x+1,y-2,9,1);
				c++;
			}
		}
		if(x>1 && y>0 && (a[x-2][y-1]<97 || a[x-2][y-1]>115))
		{
			p=checkbox(x,y,x-2,y-1,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x-2,y-1,9,1);
				c++;
			}
		}
		if(x>1 && y<7 && (a[x-2][y+1]<97 || a[x-2][y+1]>115))
		{
			p=checkbox(x,y,x-2,y+1,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x-2,y+1,9,1);
				c++;
			}
		}
		if(x<6 && y>0 && (a[x+2][y-1]<97 || a[x+2][y-1]>115))
		{
			p=checkbox(x,y,x+2,y-1,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x+2,y-1,9,1);
				c++;
			}
		}
		if(x<6 && y<7 && (a[x+2][y+1]<97 || a[x+2][y+1]>115))
		{
			p=checkbox(x,y,x+2,y+1,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x+2,y+1,9,1);
				c++;
			}
		}
	}
	else if(a[x][y]==75)
	{
		if(x>0 && (a[x-1][y]<65 || a[x-1][y]>83))
		{
			p=checkbox(x,y,x-1,y,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x-1,y,9,1);
				c++;
			}
		}
		if(x<7 && (a[x+1][y]<65 || a[x+1][y]>83))
		{
			p=checkbox(x,y,x+1,y,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x+1,y,9,1);
				c++;
			}
		}
		if(y>0 && (a[x][y-1]<65 || a[x][y-1]>83))
		{
			p=checkbox(x,y,x,y-1,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x,y-1,9,1);
				c++;
			}
		}
		if(y<7 && (a[x][y+1]<65 || a[x][y+1]>83))
		{
			p=checkbox(x,y,x,y+1,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x,y+1,9,1);
				c++;
			}
		}
		if(x>0  && y>0 && (a[x-1][y-1]<65 || a[x-1][y-1]>83))
		{
			p=checkbox(x,y,x-1,y-1,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x-1,y-1,9,1);
				c++;
			}
		}
		if(x<7  && y<7 && (a[x+1][y+1]<65 || a[x+1][y+1]>83))
		{
			p=checkbox(x,y,x+1,y+1,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x+1,y+1,9,1);
				c++;
			}
		}
		if(x>0  && y<7 && (a[x-1][y+1]<65 || a[x-1][y+1]>83))
		{
			p=checkbox(x,y,x-1,y+1,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x-1,y+1,9,1);
				c++;
			}
		}
		if(x<7  && y>0 && (a[x+1][y-1]<65 || a[x+1][y-1]>83))
		{
			p=checkbox(x,y,x+1,y-1,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x+1,y-1,9,1);
				c++;
			}
		}
		if(x==4 && y==7 && a[5][7]==0 && a[6][7]==0 && count==0)
		{
			p=checkbox(4,7,6,7,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(6,7,9,1);
				c++;
			}
		}
	}
	else if(a[x][y]==107)
	{
		if(x>0 && (a[x-1][y]<97 || a[x-1][y]>115))
		{
			p=checkbox(x,y,x-1,y,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x-1,y,9,1);
				c++;
			}
		}
		if(x<7 && (a[x+1][y]<97 || a[x+1][y]>115))
		{
			p=checkbox(x,y,x+1,y,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x+1,y,9,1);
				c++;
			}
		}
		if(y>0 && (a[x][y-1]<97 || a[x][y-1]>115))
		{
			p=checkbox(x,y,x,y-1,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x,y-1,9,1);
				c++;
			}
		}
		if(y<7 && (a[x][y+1]<97 || a[x][y+1]>115))
		{
			p=checkbox(x,y,x,y+1,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x,y+1,9,1);
				c++;
			}
		}
		if(x>0  && y>0 && (a[x-1][y-1]<97 || a[x-1][y-1]>115))
		{
			p=checkbox(x,y,x-1,y-1,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x-1,y-1,9,1);
				c++;
			}
		}
		if(x<7  && y<7 && (a[x+1][y+1]<97 || a[x+1][y+1]>115))
		{
			p=checkbox(x,y,x+1,y+1,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x+1,y+1,9,1);
				c++;
			}
		}
		if(x>0  && y<7 && (a[x-1][y+1]<97 || a[x-1][y+1]>115))
		{
			p=checkbox(x,y,x-1,y+1,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x-1,y+1,9,1);
				c++;
			}
		}
		if(x<7  && y>0 && (a[x+1][y-1]<97 || a[x+1][y-1]>115))
		{
			p=checkbox(x,y,x+1,y-1,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(x+1,y-1,9,1);
				c++;
			}
		}
		if(x==3 && y==7 && a[2][7]==0 && a[1][7]==0 && count==0)
		{
			p=checkbox(3,7,1,7,a,turn,checkno);
			if(p==0)
			{
				if(show==0)
					box(1,7,9,1);
				c++;
			}
		}
	}
	return c;
}
void dsbox(int x,int y)
{
	setcolor(0);
	line(95+(56*x),15+(56*y),151+(56*x),15+(56*y));
	line(151+(56*x),15+(56*y),151+(56*x),71+(56*y));
	line(151+(56*x),71+(56*y),95+(56*x),71+(56*y));
	line(95+(56*x),71+(56*y),95+(56*x),15+(56*y));
	int p=x+y;
	if(p%2==1)
	{
		setfillstyle(SOLID_FILL,BROWN);
		floodfill(96+(56*x),16+(56*y),0);
	}
	else if(p%2==0)
	{
		setfillstyle(SOLID_FILL,WHITE);
		floodfill(96+(56*x),16+(56*y),0);
	}
}
void dbbox()
{
	for(int i=0;i<8;i++)
	{
		for(int j=0;j<8;j++)
		{
			dsbox(i,j);
		}
	}
}
void board()
{
	setfillstyle(SOLID_FILL,CYAN);
	floodfill(0,0,WHITE);
	for(int i=95,j=15;i<=543,j<=463;i+=56,j+=56)
	{
		line(i,15,i,463);
		line(95,j,543,j);
	}
	for(int k=0;k<8;k++)
	{
		for(int l=0;l<8;l++)
		{
			int p=k+l;
			if(p%2==1)
			{
				setfillstyle(SOLID_FILL,BROWN);
				floodfill((123+(k*56)),(43+(l*56)),WHITE);
			}
			else if(p%2==0)
			{
				setfillstyle(SOLID_FILL,WHITE);
				floodfill((123+(k*56)),(43+(l*56)),WHITE);
			}
		}
	}
	for(int x=0;x<8;x++)
		for(int y=0;y<8;y++)
			dsbox(x,y);
	setcolor(0);
	for(i=95,j=15;i<=543,j<=463;i+=56,j+=56)
	{
		line(i,15,i,463);
		line(95,j,543,j);
	}
	line(94,14,544,14);
	line(544,14,544,464);
	line(544,464,94,464);
	line(94,464,94,14);
	setfillstyle(SOLID_FILL,CYAN);
	floodfill(0,0,0);
}
void main()
{
	cout<<"\n\n\n\n\n\n\t\t\t    Welcome to CHESS!!!!!!!";
	cout<<"\n\n\n\n\t\t\t    Computer Science Project \n";
	cout<<"\n\n\n\n\n\n\n\n\n\n\t\t\t\t\t\tCreated by: ";
	cout<<"\n\n\t\t\t\t\t\tAbhishek Dutta";

	delay(3500);
	clrscr();
	int choice;
	do
	{
	cout<<"\n\n\n\t\tWhat would you like to enter as?";
	cout<<"\n\n1) Administrator";
	cout<<"\n2) Player";
	cout<<"\n3) Exit";
	cout<<"\n\n\nEnter the corresponding number: ";
	cin>>choice;
	if(choice==1)
	{
		clrscr();
		cout<<"\n\n\n\n\n\n\n\n\n\n\n\t\tEnter administrator Password: ";
		char pass[30];
		for(int i=0;i<30;i++)
		{
			pass[i]=getch();
			if(pass[i]=='\r')
			{       pass[i]='\0';
				break;
			}
			else if(pass[i]=='\b' && i>0)
			{
				clrscr();
				cout<<"\n\n\n\n\n\n\n\n\n\n\n\t\tEnter Administrator Password: ";
				for(int j=0;j<i-1;j++)
					cout<<"*";
				i-=2;
			}
			else
				cout<<"*";
		}
		if(strcmp(pass,"Project")==0)
		{
			clrscr();
			int num;
			cout<<"\n\t\t\t\tWhat would you like to do?";
			cout<<"\n\n\t\t1) Add a Record";
			cout<<"\n\t\t2) Modify an Existing Record";
			cout<<"\n\t\t3) Search for a Record";
			cout<<"\n\t\t4) Delete a Record";
			cout<<"\n\t\t5) Display Records";
			cout<<"\n\n\t\tEnter the corresponding number: ";
			cin>>num;
			if(num==1)
			{
				clrscr();
				ofstream f;
				ifstream k;
				char ch='y';
				do
				{
					char winner[20];
					int d,all=0;
					while(all!=1)
					{
						clrscr();
						int c=0;
						cout<<"\nEnter Player ID(0 to exit): ";
						cin>>d;
						if(d==0)
							break;
						k.open("Chess.dat",ios::binary);
						while(k.read((char *)&p,sizeof(p)))
						{
							if(p.rid()==d)
								c=1;
						}
						if(c!=0)
						{
							cout<<"\n\nPlayer ID already exists. Kindly Enter a New ID!";
							delay(1000);
						}
						else if(c==0 && d>=1000)
						{
							cout<<"\n\nPlease Enter an Id till 999!";
							delay(1000);
						}
						else if(c==0 && d<1000)
							all=1;
						k.close();
					}
					if(d==0)
						break;
					f.open("Chess.dat",ios::binary|ios::app);
					clrscr();
					p.setid(d-1);
					cout<<"\n";
					p.nameinput();
					cout<<"\n\t\t\t\tWinner: ";
					gets(winner);
					while(strcmp(winner,p.rn1())!=0 && strcmp(winner,p.rn2())!=0 && strcmpi(winner,"Draw")!=0)
					{
						cout<<"\n\nEnter a valid Winner name: ";
						gets(winner);
					}
					p.setwin(winner);
					f.write((char *)&p,sizeof(p));
					cout<<"\n\nRecord Added!\nDo you want to continue?[y/n]: ";
					cin>>ch;
					f.close();
				}while(ch=='y' || ch=='Y');
			}
			if(num==2)
			{
				clrscr();
				ifstream f;
				char ch1;
				do
				{
					char ch2='n';
					int a;
					do
					{
						clrscr();
						int c=0;
						cout<<"\n\t\t\tEnter Player ID(0 to exit): ";
						cin>>a;
						if(a==0)
							break;
						f.open("Chess.dat",ios::binary);
						while(f.read((char *)&p,sizeof(p)))
						{
							if(p.rid()==a)
							{
								cout<<"\n\n\tPlayer 1: ";
								p.r1();
								cout<<"\n\tPlayer 2: ";
								p.r2();
								cout<<"\n\tWinner: ";
								p.win();
								c=1;
								break;
							}
						}
						if(c==0)
						{
							cout<<"\n\n\tRecord not found, kindly recheck the Player ID!!";
							delay(1000);
						}
						else
						{
							cout<<"\n\n\tIs this the record you want to modify?[y/n]: ";
							cin>>ch2;
						}
						f.close();
					}while(ch2=='n' || ch2=='N');
					if(a==0)
						break;
					fstream k("Chess.dat",ios::binary|ios::in|ios::out);
					while(k.read((char *)&p,sizeof(p)))
					{
						if(p.rid()==a)
							break;
					}
					char ch3;
					do
					{
						int ans;
						k.seekg(k.tellg()-sizeof(p),ios::beg);
						cout<<"\n\n\t1) Player 1";
						cout<<"\n\t2) Player 2";
						cout<<"\n\t3) Winner";
						cout<<"\n\n\tEnter the number corresponding to whatever you want to modify: ";
						cin>>ans;
						if(ans>3)
						{
							while(ans>3)
							{
								cout<<"\n\tPlease enter a valid number: ";
								cin>>ans;
							}
						}
						if(ans==1)
						{
							char n1[20];
							cout<<"\n\tEnter new Player Name: ";
							gets(n1);
							if(strcmp(n1,p.rwin())!=0 && strcmp(p.rn2(),p.rwin())!=0 && strcmpi(p.rwin(),"Draw")!=0)
								p.modn3(n1);
							p.modn1(n1);
							k.write((char *)&p,sizeof(p));
						}
						else if(ans==2)
						{
							char n2[20];
							cout<<"\n\tEnter new Player Name: ";
							gets(n2);
							if(strcmp(n2,p.rwin())!=0 && strcmp(p.rn1(),p.rwin())!=0 && strcmpi(p.rwin(),"Draw")!=0)
								p.modn3(n2);
							p.modn2(n2);
							k.write((char *)&p,sizeof(p));
						}
						else if(ans==3)
						{
							char n3[20];
							cout<<"\n\tEnter new Winner: ";
							gets(n3);
							while(strcmp(n3,p.rn1())!=0 && strcmp(n3,p.rn2())!=0 && strcmpi(n3,"Draw")!=0)
							{
								cout<<"\n\nEnter a valid Winner name: ";
								gets(n3);
							}
							p.modn3(n3);
							k.write((char *)&p,sizeof(p));
						}
						cout<<"\n\tDo you want to Modify any thing else in this record?[y/n]: ";
						cin>>ch3;
					}while(ch3=='y' || ch3=='Y');
					cout<<"\n\n\nRecord updated!\nDo you want to continue?[y/n]: ";
					cin>>ch1;
					k.close();
				}while(ch1=='y' || ch1=='Y');
			}
			if(num==3)
			{
				clrscr();
				ifstream f;
				int a;
				char ch='y';
				do
				{
					clrscr();
					int c=0;
					cout<<"\n\t\t\tEnter Player ID(0 to exit): ";
					cin>>a;
					if(a==0)
						break;
					f.open("Chess.dat",ios::binary);
					while(f.read((char *)&p,sizeof(p)))
					{
						if(p.rid()==a)
						{
							cout<<"\n\n\tPlayer 1: ";
							p.r1();
							cout<<"\n\tPlayer 2: ";
							p.r2();
							cout<<"\n\tWinner: ";
							p.win();
							c=1;
						}
					}
					if(c==0)
					{
						cout<<"\n\n\tRecord not found, kindly recheck the Player ID!!";
						delay(750);
					}
					else
					{
						cout<<"\n\n\tDo you want to continue?[y/n]: ";
						cin>>ch;
					}
					f.close();
				}while(ch=='y' || ch=='Y');
			}
			if(num==4)
			{
				clrscr();
				fstream f;
				char ch1;
				do
				{
					char ch2='n';
					int a;
					do
					{
						clrscr();
						int c=0;
						cout<<"\n\t\t\tEnter Player ID(0 to exit): ";
						cin>>a;
						if(a==0)
							break;
						f.open("Chess.dat",ios::binary|ios::in|ios::out);
						while(f.read((char *)&p,sizeof(p)))
						{
							if(p.rid()==a)
							{
								cout<<"\n\n\tPlayer 1: ";
								p.r1();
								cout<<"\n\tPlayer 2: ";
								p.r2();
								cout<<"\n\tWinner: ";
								p.win();
								c=1;
							}
						}
						if(c==0)
						{
							cout<<"\n\n\tRecord not found, kindly recheck the Player ID!!";
							delay(750);
						}
						else
						{
							cout<<"\n\n\tIs this the record you want to modify?[y/n]: ";
							cin>>ch2;
						}
						f.close();
					}while(ch2=='n' || ch2=='N');
					if(a==0)
						break;
					ofstream k1("Temp.dat",ios::binary);
					ifstream k2("Chess.dat",ios::binary);
					while(k2.read((char *)&p,sizeof(p)))
					{
						if(p.rid()!=a)
							k1.write((char *)&p,sizeof(p));
					}
					k1.close();
					k2.close();
					remove("Chess.dat");
					rename("Temp.dat","Chess.dat");
					cout<<"\n\n\nRecord deleted!\nDo you want to continue?[y/n]: ";
					cin>>ch1;
				}while(ch1=='y' || ch1=='Y');
			}
			if(num==5)
			{
				clrscr();
				ifstream k("Chess.dat",ios::binary);
				int rmax=2,p1l=8,p2l=8,wl=6;
				while(k.read((char *)&p,sizeof(p)))
				{
					int rcount=length(p.rid());
					if(rcount>rmax)
						rmax=rcount;
					if(strlen(p.rn1())>p1l)
						p1l=strlen(p.rn1());
					if(strlen(p.rn2())>p2l)
						p2l=strlen(p.rn2());
					if(strlen(p.rwin())>wl)
						wl=strlen(p.rwin());
				}
				k.close();
				rmax=rmax/2;
				p1l=p1l/2;
				p2l=p2l/2;
				wl=wl/2;
				int w=2*(rmax+p1l+p2l+wl)+19;
				cout<<"\n\n";
				for(int o=1;o<=w;o++)
					cout<<"-";
				cout<<"\n||"<<setw(rmax+2)<<"ID"<<setw(rmax+3)<<"||"<<setw(p1l+5)<<"Player 1"<<setw(p1l-1)<<"||"<<setw(p2l+5)<<"Player 2"<<setw(p2l-1)<<"||"<<setw(wl+4)<<"Winner"<<setw(wl)<<"||";
				cout<<"\n";
				for(o=1;o<=w;o++)
					cout<<"-";
				cout<<"\n";
				for(o=1;o<=w;o++)
					cout<<"-";
				cout<<"\n";
				ifstream f("Chess.dat",ios::binary);
				while(f.read((char *)&p,sizeof(p)))
				{
					p.show(rmax,p1l,p2l,wl);
					cout<<"\n";
					for(int o=1;o<=w;o++)
						cout<<"-";
					cout<<"\n";
				}
				f.close();
				getch();
			}
		}
		else
		{
			cout<<"\n\n\t\t\tWrong Password";
			delay(500);
		}
		clrscr();
	}
	if(choice==2)
	{
	start();
	char move;
	ofstream f("Chess.dat",ios::binary|ios::app);
	ifstream k("Chess.dat",ios::binary);
	int per=0,d;
	while(per!=1)
	{
		srand(time(NULL));
		d=(rand()%1000)+1;
		int c=0;
		while(k.read((char *)&p,sizeof(p)))
		{
			if(p.rid()==d)
				c=1;
		}
		if(c==0)
			per=1;
	}
	clear();
	p.setid(d);
	p.nameinput();
	char dest;
	int pieces[8][8];
	for(int x=0;x<8;x++)
	{
		for(int y=0;y<8;y++)
		{
			pieces[x][y]=0;
		}
	}
	pieces[0][0]=82;
	pieces[1][0]=72;
	pieces[2][0]=66;
	pieces[3][0]=75;
	pieces[4][0]=81;
	pieces[5][0]=66;
	pieces[6][0]=72;
	pieces[7][0]=82;
	pieces[0][7]=114;
	pieces[1][7]=104;
	pieces[2][7]=98;
	pieces[3][7]=107;
	pieces[4][7]=113;
	pieces[5][7]=98;
	pieces[6][7]=104;
	pieces[7][7]=114;
	for(int pp=0;pp<8;pp++)
	{
		pieces[pp][1]=80;
		pieces[pp][6]=112;
	}
	int chmate,wmcount=0,bmcount=0,wcount=0,bcount=0;
	int gd=DETECT,gm;
	initgraph(&gd,&gm,"C:\\TURBOC3\\BGI");
	clear();
	for(int i=0;;i++)
	{
		board();
		for(x=0;x<8;x++)
		{
			for(int y=0;y<=x;y++)
			{
				int temp=pieces[x][y];
				pieces[x][y]=pieces[7-x][7-y];
				pieces[7-x][7-y]=temp;
			}
		}
		int d=7/2,y;
		for(x=0,y=0;x<=d,y<=d;x++,y++)
		{
			int temp=pieces[x][y];
			pieces[x][y]=pieces[7-x][7-y];
			pieces[7-x][7-y]=temp;
		}
		display(pieces);
		chmate=0;
		int wpcount=0,bpcount=0;
		for(int m=0;m<8;m++)
		{
			for(int n=0;n<8;n++)
			{
				int count=0;
				if(i%2==0 && pieces[m][n]>65 && pieces[m][n]<83)
				{
					wpcount++;
					count=bbox(m,n,pieces,i,wmcount,1);
					chmate=chmate+count;
				}
				if(i%2==1 && pieces[m][n]>97 && pieces[m][n]<115)
				{
					bpcount++;
					count=bbox(m,n,pieces,i,bmcount,1);
					chmate=chmate+count;
				}
			}
		}
		if(chmate==0)
			break;
		int cnum=0;
		check(pieces,i,cnum);
		if(cnum>0)
		outtextxy(300,4,"CHECK!!!");
		box(7,7,12,4);
		int bx=7,by=7;
		int app=0;
		while(app!=1)
		{
			int px=bx,py=by,count;
			if(move=='/')
				break;
			else if(move=='K' && bx>0)
				bx--;
			else if(move=='P' && by<7)
				by++;
			else if(move=='H' && by>0)
				by--;
			else if(move=='M' && bx<7)
				bx++;
			if(px!=bx || py!=by)
				dsbox(px,py);
			dbbox();
			box(bx,by,12,4);
			if(i%2==0 && pieces[bx][by]>65 && pieces[bx][by]<83)
			{
				count=0;
				count=bbox(bx,by,pieces,i,wmcount);
			}
			else if(i%2==1 && pieces[bx][by]>97 && pieces[bx][by]<115)
			{
				count=0;
				count=bbox(bx,by,pieces,i,bmcount);
			}
			if(move==' ')
			{
				if(i%2==0 && pieces[bx][by]!=0 && pieces[bx][by]>=66 && pieces[bx][by]<83 && count!=0)
					app=1;
				if(i%2==1 && pieces[bx][by]!=0 && pieces[bx][by]>=98 && pieces[bx][by]<115 && count!=0)
					app=1;
			}
			if(app!=1)
				move=getch();
		}
		if(move=='/')
			break;
		else if(move==' ')
		{
			move='no';
			box(bx,by,10,2);
			int ox=bx,oy=by,color;
			int dir;
			dest=getch();
			dir=dest;
			int per=0;
			while(per!=1)
			{
				int px=bx,py=by,count;
				if(dest=='/')
					break;
				else if(dir==75 && bx>0)
					bx--;
				else if(dir==80 && by<7)
					by++;
				else if(dir==72 && by>0)
					by--;
				else if(dir==77 && bx<7)
					bx++;
				if(px!=bx || py!=by)
					dsbox(px,py);
				if(i%2==0)
					count=bbox(ox,oy,pieces,i,wmcount);
				if(i%2==1)
					count=bbox(ox,oy,pieces,i,bmcount);
				count++;
				color=getpixel(96+(56*bx),16+(56*by));
				if(dest=='\r' && color==9)
					per=1;
				box(bx,by,10,2);
				if(per!=1)
				{
					dest=getch();
					dir=dest;
				}
			}
			if(dest=='/')
				break;
			else if(dest=='\r')
			{
				dbbox();
				int castling=0;
				if(ox==4 && oy==7 && bx==6 && by==7 && pieces[ox][oy]==75 && pieces[7][7]==82 && i%2==0)
				{
					int castle=pieces[7][7];
					pieces[7][7]=pieces[5][7];
					pieces[5][7]=castle;
					pieces[0][0]=0;
					castling=1;
				}
				else if(ox==3 && oy==7 && bx==1 && by==7 && pieces[ox][oy]==107 && pieces[0][7]==114 && i%2==1)
				{
					int castle=pieces[0][7];
					pieces[0][7]=pieces[2][7];
					pieces[2][7]=castle;
					pieces[0][7]=0;
					castling=1;
				}
				int temp=pieces[ox][oy];
				pieces[ox][oy]=pieces[bx][by];
				pieces[bx][by]=temp;
				pieces[ox][oy]=0;
				setcolor(BLUE);
				line(95+(56*ox),15+(56*oy),151+(56*ox),15+(56*oy));
				line(151+(56*ox),15+(56*oy),151+(56*ox),71+(56*oy));
				line(151+(56*ox),71+(56*oy),95+(56*ox),71+(56*oy));
				line(95+(56*ox),71+(56*oy),95+(56*ox),15+(56*oy));
				int m=ox+oy;
				if(m%2==1)
				{
					setfillstyle(SOLID_FILL,BROWN);
					floodfill(123+(56*ox),43+(56*oy),BLUE);
				}
				else if(m%2==0)
				{
					setfillstyle(SOLID_FILL,WHITE);
					floodfill(123+(56*ox),43+(56*oy),BLUE);
				}
				setcolor(0);
				line(95+(56*ox),15+(56*oy),151+(56*ox),15+(56*oy));
				line(151+(56*ox),15+(56*oy),151+(56*ox),71+(56*oy));
				line(151+(56*ox),71+(56*oy),95+(56*ox),71+(56*oy));
				line(95+(56*ox),71+(56*oy),95+(56*ox),15+(56*oy));
				setcolor(BLUE);
				line(95+(56*bx),15+(56*by),151+(56*bx),15+(56*by));
				line(151+(56*bx),15+(56*by),151+(56*bx),71+(56*by));
				line(151+(56*bx),71+(56*by),95+(56*bx),71+(56*by));
				line(95+(56*bx),71+(56*by),95+(56*bx),15+(56*by));
				int n=bx+by;
				if(n%2==1)
				{
					setfillstyle(SOLID_FILL,BROWN);
					floodfill(123+(56*bx),43+(56*by),BLUE);
				}
				else if(n%2==0)
				{
					setfillstyle(SOLID_FILL,WHITE);
					floodfill(123+(56*bx),43+(56*by),BLUE);
				}
				setcolor(0);
				line(95+(56*bx),15+(56*by),151+(56*bx),15+(56*by));
				line(151+(56*bx),15+(56*by),151+(56*bx),71+(56*by));
				line(151+(56*bx),71+(56*by),95+(56*bx),71+(56*by));
				line(95+(56*bx),71+(56*by),95+(56*bx),15+(56*by));
				char convert;
				int q,r,k,b,all=0;
				if(i%2==0)
				{
					q=81;
					r=82;
					k=72;
					b=66;
				}
				else
				{
					q=113;
					r=114;
					k=104;
					b=98;
				}
				for(int u=0;u<8;u++)
				{
					if(pieces[u][0]==80 || pieces[u][0]==112)
					{
						outtextxy(150,4,"Convert your Pawn into(Q/B/K/R): ");
						while(all!=1)
						{
							convert=getch();
							if(convert=='q')
							{
								pieces[u][0]=q;
								all=1;
							}
							else if(convert=='r')
							{
								pieces[u][0]=r;
								all=1;
							}
							else if(convert=='b')
							{
								pieces[u][0]=b;
								all=1;
							}
							else if(convert=='k')
							{
								pieces[u][0]=k;
								all=1;
							}
						}
					}
				}
				if(castling==1)
				{
					int a1,a2,a3,a4,b1,b2,b3,b4,c1,c2,c3,c4,col;
					if(i%2==0)
					{
						a1=487;
						a2=407;
						a3=543;
						a4=463;
						b1=375;
						b2=407;
						b3=431;
						b4=463;
						c1=515;
						c2=435;
						c3=403;
						c4=435;
						col=15;
					}
					else
					{
						a1=95;
						a2=407;
						a3=151;
						a4=463;
						b1=207;
						b2=407;
						b3=263;
						b4=463;
						c1=123;
						c2=435;
						c3=235;
						c4=435;
						col=6;
					}
					setcolor(BLUE);
					line(a1,a2,a3,a2);
					line(a3,a2,a3,a4);
					line(a3,a4,a1,a4);
					line(a1,a4,a1,a2);
					setfillstyle(SOLID_FILL,col);
					floodfill(c1,c2,BLUE);
					setcolor(0);
					line(a1,a2,a3,a2);
					line(a3,a2,a3,a4);
					line(a3,a4,a1,a4);
					line(a1,a4,a1,a2);
					setcolor(BLUE);
					line(b1,b2,b3,b2);
					line(b3,b2,b3,b4);
					line(b3,b4,b1,b4);
					line(b1,b4,b1,b2);
					setfillstyle(SOLID_FILL,col);
					floodfill(c3,c4,BLUE);
					setcolor(0);
					line(b1,b2,b3,b2);
					line(b3,b2,b3,b4);
					line(b3,b4,b1,b4);
					line(b1,b4,b1,b2);
				}
				if(i%2==0 && wpcount==1)
					wcount++;
				else if(i%2==1 && bpcount==1)
					bcount++;
			}
			if(i%2==0 && ((ox==4 && oy==7) || (ox==7 && oy==7)))
			       wmcount++;
			else if(i%2==1 && ((ox==3 && oy==7) || (ox==0 && oy==7)))
				bmcount++;
			display(pieces);
			delay(1000);
		}
		if(wcount==50 || bcount==50)
			break;
	}
	if(wcount==50 || bcount==50)
	{
		clear();
		cout<<"\n\n\n\n\n\n\n\n\n\n\n\n\t\t\tCONGRATUATIONS to both Players..."<<"\n\t\t\t\t\tThe Match is a draw!!!!";
		p.setwin("Draw");
	}
	if(chmate==0 && i%2==0)
	{
		clear();
		cout<<"\n\n\n\n\n\n\n\n\n\n\n\n\t\t\tIts a CHECKMATE...BLACK WINS!"<<"\n\t\t\t\t\tCONGRATUATIONS to ";
		p.r2();
		cout<<" on winning!!!!";
		p.setwin("Player 2");
	}
	else if(chmate==0 && i%2==1)
	{
		clear();
		cout<<"\n\n\n\n\n\n\n\n\n\n\n\n\t\t\tIts a CHECKMATE...WHITE WINS!"<<"\n\t\t\t\t\tCONGRATUATIONS to ";
		p.r1();
		cout<<" on winning!!!!";
		p.setwin("Player 1");
	}
	else if((move=='/' || dest=='/') && i%2==0)
	{
		clear();
		cout<<"\n\n\n\n\n\n\n\n\n\n\n\n\t\t\tBLACK WINS..."<<"\n\t\t\t\t\tCONGRATUATIONS to ";
		p.r2();
		cout<<" on winning!!!!";
		p.setwin("Player 2");
	}
	else if((move=='/' || dest=='/') && i%2==1)
	{
		clear();
		cout<<"\n\n\n\n\n\n\n\n\n\n\n\n\t\t\tWHITE WINS..."<<"\n\t\t\t\t\tCONGRATUATIONS to ";
		p.r1();
		cout<<" on winning!!!!";
		p.setwin("Player 1");
	}
	f.write((char *)&p,sizeof(p));
	f.close();
	k.close();
	delay(2000);
	closegraph();
	}
	if(choice==3)
		exit(0);
	}while(choice!=3);
}

