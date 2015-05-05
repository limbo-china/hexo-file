title: "leetcode_136 单次出现数（异或）"
date: 2015-05-05 23:54:07
tags:
categories: Leetcode
photos: 
---

数组中除一个数出现1次外其余均出现2次，异或求解
<!--more-->
{% codeblock %}
int singleNumber(int* nums, int numsSize) {
    if(numsSize==1)
        return nums[0];
    int result = nums[0];
    for(int i=1;i<numsSize;i++)
        result = result ^ nums[i];
    return result;
}
{% endcodeblock %}