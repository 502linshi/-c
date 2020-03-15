#include<stdio.h>
#include<stdlib.h>
int lastdays(int a,int b,int c){
	int days=0;
	int leap;
	int x[12]={31,28,31,30,31,30,31,31,30,31,30,31};
	for(int i=0;i<b-1;i++){
		days+=x[i];
	}
	if(a%4!=0) leap=0;
	else if(a%100!=0) leap=1;
	else if(a%400!=0) leap=0;
	else leap=1;
	if(leap&&b>=3) days=days+c+1;
	else days=days+c;
	return days; 
}
int main(){
	int start_year,start_month,start_day;
	int fin_year,fin_month,fin_day;
	int cutdays,adddays;
	int totaldays=0,yeardays=0;
	int leap;
	printf("请输入出生年月日，格式为年 月 日\n");
	scanf("%d %d %d",&start_year,&start_month,&start_day);
	printf("请输入此时年月日，格式为年 月 日\n");
	scanf("%d %d %d",&fin_year,&fin_month,&fin_day);
	adddays=lastdays(fin_year,fin_month,fin_day);
	cutdays=lastdays(start_year,start_month,start_day);
	//printf("%d\n",cutdays);
	//printf("%d\n",adddays);
	for(int i=start_year;i<fin_year;i++){
	if(i%4!=0) leap=0;
	else if(i%100!=0) leap=1;
	else if(i%400!=0) leap=0;
	else leap=1;
	if(leap) yeardays+=366;
	else yeardays+=365;
	}
