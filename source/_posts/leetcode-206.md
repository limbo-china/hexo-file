title: "leetcode_206 反转链表"
date: 2015-05-05 23:42:34
tags:
categories: Leetcode
photos: 
---
2种方法：
1\. 存入另一表
2\. 直接在表中逐个反转(迭代)(递归)
<!--more-->
--------------------------------
2\.直接在表中逐个反转(迭代):
{% codeblock %}
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */

struct ListNode* reverseList(struct ListNode* head) {
   struct ListNode* currNode;
   struct ListNode* nextNode;
   struct ListNode* prevNode;

   if(head==NULL) return NULL;

   currNode = head;
   nextNode = head->next;
   prevNode = NULL;


   while(currNode) {
       nextNode = currNode->next;
       currNode->next = prevNode;
       prevNode = currNode;
       currNode = nextNode;
   }

   return prevNode;
}
{% endcodeblock %}
