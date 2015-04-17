title: "C free函数细节"
date: 2015-04-10 01:45:46
tags: Free
categories: C
photos: 
---
{% codeblock %}
void DeleteList(List L)
{
	Position P, Temp;
	P = L->Next;
	L->Next = NULL;
	while (P != NULL)
	{
		Temp = P->Next;
		free(P);
		P = Temp;
	}
}
{% endcodeblock %}
<!--more-->
比较两段代码，2次调用DeleteList删除链表，第2次对已存在的合法链表进行删除链表操作时，在Free函数处出现错误。在其后加入`p=NULL`操作即可。即释放指针空间后应置其为NULL。
{% codeblock %}
void DeleteList(List L)
{
	Position P, Temp;
	P = L->Next;
	L->Next = NULL;
	while (P != NULL)
	{
		Temp = P->Next;
		free(P);
		P = NULL;
		P = Temp;
	}
}
{% endcodeblock %}