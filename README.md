# w
d
#include<stdio.h>
#include<string.h>
#include<stdlib.h>
#define N 40
char c[N];//装表达式 
float a[N/2];//装操作数 
char b[N/2];//装运算符 
int PDSZ(int x)//判断是否为数字 
{
	if(x>='0'&&x<='9')
		return 1;
	else
		return 0;
} 
int PDYSF(char y)//判断是否为运算符 
{
	if(y=='+'||y=='-'||y=='*'||y=='/')
		return 1;
	else
		return 0;
}
int JS()//计算
{
	int j=0,k=0;
	float sum;
	char *p=c;
	a[0]=atof(p);
	while(*p!='\0')
	{
		while((*p>='0'&&*p<='9')||*p=='.')
			p++;
		if(p!='\0')
		{
			b[j]=*p;
			p++;
			a[j+1]=atof(p);
			j++;
		}
	}
	c[j]='\0';
	sum=a[0];
	while(b[k]!='\0')
	{ 
		switch(b[k]) 
		{
			case '+':sum=sum+a[k+1];break;
			case '-':sum=sum-a[k+1];break;
			case '*':sum=sum*a[k+1];break;
			case '/':sum=sum/a[k+1];break;
		} 
		k++;
	}
	printf("%f",sum);
	return 0;
	
}
int YZ()//验证 
{
	int x=0,y=0,z;
	z=strlen(c)-1;
	if((c[0]>='0'&&c[0]<='9')&&(c[z]>='0'&&c[z]<='9'))
		while(c[x]!='\0')
		{
			if(PDYSF(c[x])==1&&PDYSF(c[x+1])==1)
			{
				y=1;
				break;
			}
			if(c[x]=='/'&&c[x+1]=='0')
			{
				y=1;
				break;
			}
			x++;
		}
	else
		y=1;
	if(y==0)
		return 0;
	else
	{
		printf("输入不正确,请重新输入\n");
		return 1;
	}
}
int main()
{
	while(1)
	{	
		gets(c);
		if(YZ()!=1)
			break;
	}
	JS();
	return 0;
}
