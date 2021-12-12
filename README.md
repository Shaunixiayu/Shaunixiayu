/*给定一个顺序存储的线性表，请设计一个算法查找该线性表中最长的连续递增子序列。例如，(1,9,2,5,7,3,4,6,8,0)中最长的递增子序列为(3,4,6,8)。

输入格式:
输入第1行给出正整数n（≤10 
5
 ）；第2行给出n个整数，其间以空格分隔。*/
 

#include<stdio.h>
#include<stdlib.h>
typedef int Position;
typedef struct LNode *PtrToNode;
typedef int ElmentType;
#define MAXSIZE 100001
struct LNode
{
	ElmentType Data[MAXSIZE];
	Position Last;
};
typedef PtrToNode List;
List ReadInput()
{
	int N,i;
	List L;
	L=(List)malloc(sizeof(struct LNode));
	L->Last=-1;
	scanf("%d",&N);
	L->Last=N-1;
	for(i=0;i<=L->Last;i++)
	{
		scanf("%d",&L->Data[i]);
	}
	return L;
}
void PrintList( List L )
{
	int i=0;
	printf("%d",L->Data[i]);
	for(i=1;i<=L->Last;i++)
	{
		printf(" %d",L->Data[i]);
	}

}
void find(List L)
{
	int i;
	int Maxlen=0,len=0;
	int head=0,Tmphead=0,Tmptail=0,tail=0;
	while(Tmptail<L->Last)
	{
		while(L->Data[Tmptail]<L->Data[Tmptail+1])
		{
			Tmptail++;
		}
		len=Tmptail-Tmphead+1;
		{
			if(len>Maxlen)
			{
				Maxlen=len;
				head=Tmphead;
				tail=Tmptail;
			}
			else
			{
				Tmphead=Tmptail+1;
				Tmptail=Tmphead;
			}
		}
	}
	printf("%d",L->Data[head]);
	for(i=head+1;i<=tail;i++)
	{
		printf(" %d",L->Data[i]);
	}

}

int main()
{
	List L;
	int i;
	L=ReadInput();
	find(L);
	system("pause");
	return 0;
}
