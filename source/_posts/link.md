title: "Link"
date: 2015-04-06 01:12:22
tags: Link
categories: Data Structure
---
求链表的交集和并集:
<!--more-->
{% codeblock %}#include "stdafx.h"
#include "stdio.h"
#include "stdlib.h"



struct Node;
typedef struct Node *pointer;
typedef pointer List;
typedef pointer Position;

struct Node
{
	int Element;
	Position Next;
};



List CreatList();	//创建一个链表头；					
Position FindElementPre(int ele, List L); //寻找所给元素的前驱结点；
void DeleteElement(int ele);//删除所给元素结点；
void DeletePosition(Position P);//删除所给位置所在结点；
void PrintList(List L);//打印链表元素；
void DeleteList(List L);//删除链表；
void Insert(int ele, List L, Position &Tail);//向链表尾插入元素；
void Intersection(List L, List M);//求两个升序链表元素集合的交集；
void MergeList(List L, List M);//求两个升序链表元素集合的并集；


List CreatList()
{
	List L;
	L = (List)malloc(sizeof(struct Node));
	L->Next = NULL;
	return L;
}
void PrintList(List L)
{
	Position Cell;
	if (L->Next == NULL)
		printf("there are no elements in the list!\n");
	else
	{
		Cell = L->Next;
		while (Cell->Next != NULL)
			printf("%d ", Cell->Element), Cell = Cell->Next;
		if (Cell->Next == NULL)
			printf("%d\n", Cell->Element);
	}

}
void DeleteList(List L)
{
	Position P,Temp;
	P = L->Next;
	L->Next = NULL;
	while (P != NULL)
	{
		Temp = P->Next;
		free(P);
		P = Temp;
	}
}
void Insert(int ele, List L, Position &Tail)
{

	Position TempNode;
	TempNode = (Position)malloc(sizeof(struct Node));
	if (TempNode == NULL)
		printf("error!");
	TempNode->Element = ele;
	if (L->Next == NULL)
	{
		Tail->Element = ele;
		L->Next = Tail;
		Tail->Next = NULL;
	}
	else
	{
		Tail->Next = TempNode;
		Tail = Tail->Next;
		Tail->Next = NULL;
	}
}
Position FindElementPre(int ele, List L)
{
	Position Cell;
	Cell = L;
	while (Cell->Next != NULL&&Cell->Next->Element != ele)
		Cell = Cell->Next;
	return Cell;
}
void DeleteElement(int ele,List L)
{
	Position Temp;
	Position Cell = FindElementPre(ele,L);
	Temp = Cell->Next;
	Cell->Next = Temp->Next;
	free(Temp);
}
void DeletePositionBeh(Position P)
{
	Position Temp;
	Temp = P->Next;
	P->Next = Temp->Next;
	free(Temp);
}
void Intersection(List L, List M)
{
	Position LCell = L->Next;
	Position MCell = M->Next;
	List RES = CreatList();
	Position RESTail=(Position)malloc(sizeof(struct Node));
	while (LCell != NULL&&MCell != NULL)
	{
		
			if (LCell->Element > MCell->Element)
				MCell = MCell->Next;
			else if (LCell->Element == MCell->Element)
			{
				Insert(LCell->Element, RES, RESTail);
				LCell = LCell->Next;
			}
			else
				LCell = LCell->Next;
		
	}
	PrintList(RES);
	DeleteList(RES);
}
void MergeList(List L, List M)
{
	Position LCell = L->Next;
	Position MCell = M->Next;
	List RES = CreatList();
	Position RESTail = (Position)malloc(sizeof(struct Node));
	while (LCell != NULL&&MCell != NULL)
	{
		
		if (LCell->Element > MCell->Element)
		{
			Insert(MCell->Element, RES, RESTail);
			MCell = MCell->Next;
		}
		else if (LCell->Element == MCell->Element)
		{
			MCell = MCell->Next;
		}
		else
		{
			Insert(LCell->Element, RES, RESTail);
			LCell = LCell->Next;
		}
	}
	while (LCell != NULL)
	{
		Insert(LCell->Element, RES, RESTail);
		LCell = LCell->Next;
	}
	while (MCell != NULL)
	{
		Insert(MCell->Element, RES, RESTail);
		MCell = MCell->Next;
	}
	PrintList(RES);
	DeleteList(RES);
}

int main(int argc, char *argv[]) {
	List A, B,RES; int x;
	A = CreatList();
	B= CreatList();
	Position ATail = (Position)malloc(sizeof(struct Node));;
	Position BTail = (Position)malloc(sizeof(struct Node));;
	while (scanf("%d", &x) != EOF)
	{
		Insert(x, A, ATail);
	}
	while (scanf("%d", &x) != EOF)
	{
		Insert(x, B, BTail);
	}
	Intersection(A, B);
	MergeList(A, B);
	return 0;
}{% endcodeblock %}