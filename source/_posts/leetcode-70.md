title: "leetcode_70 爬楼梯"
date: 2015-05-05 23:43:00
tags:
categories: Leetcode
photos: 
---
斐波那契数列
Sn=Sn-1+Sn-2;
<!--more-->
{% codeblock %}
int climbStairs(int n) {
    int i,m,a,b;
    if(n==1)
     return 1;
    if(n==2)
     return 2;
     a=1;
     b=2;
     for(i=0;i<n-2;i++)
     {
         m=b;
         b+=a;
         a=m;
     }
     return b;
}
{% endcodeblock %}