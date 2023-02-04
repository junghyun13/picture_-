# picture_-
#c
어떤 큰 도화지에 그림이 그려져 있을 때, 그 그림의 개수와, 그 그림 중 넓이가 가장 넓은 것의 넓이를 출력하는 프로그램을 작성해보자. 단, 그림이라는 것은 1로 연결된 것을 한 그림이라고 정의하자.대각선으로 연결이 된 것은 떨어진 그림이다. 그림의 넓이란 그림에 포함된 1의 개수이다. 첫째 줄에는 그림의 개수, 둘째 줄에는 그 중 가장 넓은 그림의 넓이를 출력하여라. 단, 그림이 하나도 없는 경우에는 가장 넓은 그림의 넓이는 0이다.

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int paper[100][100];
int v[100][100];
int xx[4]={-1,1,0,0};
int yy[4]={0,0,-1,1};
int a[100];
int count,max,i,picture;
int dfs(int x,int y){
	v[x][y]=1;
	int Xx;
	int Yy;
	picture++;
	for(i=0;i<4;i++){
		Xx=x+xx[i];
		Yy=y+yy[i];
		if(0<=Xx && Xx<100 && 0<=Yy && Yy<100){
			if(v[Xx][Yy]==0 && paper[Xx][Yy]==1){
				dfs(Xx,Yy);}}}
	return picture;
}


int main(){
	int n,m,i,j;
	scanf("%d %d",&n,&m);
	printf("0은 공백 1은 색칠이다! 0과 1만입력하시오.\n");
	for(i=0;i<n;i++){
		for(j=0;j<m;j++){
			scanf("%d",&paper[i][j]);}}
	for(i=0;i<n;i++){
		for(j=0;j<m;j++){
			if(v[i][j]==0 && paper[i][j]==1){ //v가 0인것은 아직 방문전 paper가 1인 것은 색칠된부분  
				picture=0;
				a[count]=dfs(i,j); //그림의 넓이=1칸당 1로 계산하니까 그냥 picture에 1로 연결된부분 숫자 세고 a에 저장  
				count++;}}
				}
	printf("그림의 개수: %d\n",count);
	for(i=0;i<count;i++){
		if(max<a[i]){
			max=a[i];}}
	printf("가장넓은 그림의 넓이: %d",max);
	return 0;
}
