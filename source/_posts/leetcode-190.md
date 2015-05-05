title: "leetcode_190 反转32位二进制数"
date: 2015-05-06 00:02:13
tags:
categories: Leetcode
photos: 
---

思路:逐个取某一位，移到对应位置。
<!--more-->
{% codeblock %}
uint32_t reverseBits(uint32_t n) {
    int i;
    uint32_t temp,result=0;
    for(i = 0; i<=31; i++) 
    { 
        temp = n&(1<<i); //取某一位
        temp = temp>>i;  //左移
        temp = temp<<(31-i); //右移
        result |= temp; 
    } 
    return result; 
}
{% endcodeblock %}