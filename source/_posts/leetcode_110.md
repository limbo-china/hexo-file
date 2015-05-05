title: "leetcode_110 判断AVL树"
date: 2015-05-02 20:49:47
tags:
categories: Leetcode
photos: 
---
{% codeblock %}
struct TreeNode
{
    struct TreeNode *left;
    struct TreeNode *right;
    int key;
};
{% endcodeblock %}
<!--more-->
{% codeblock %}
//这里先判断是否为二叉搜索树，其次判断是否为平衡的
bool IsAVL(TreeNode *root,int depth)
{
    if (isBST(root)&&isBalance(root,&depth))
    return true;
    return false;
}

//判断是否为二叉搜索树
bool isBST(TreeNode *root)
{
    if(root == NULL)return true;
    if (!isBST(root->left))return false;
    if (!isBST(root->right))return false;
    TreeNode *cur = root->left;
    if (cur != NULL)
    {
        while(cur->right!=NULL)cur = cur->right;
        if(root->key < cur->key)return false;
    }
    TreeNode *cur = root->right;
    if (cur != NULL)
    {
        while(cur->left!=NULL)cur = cur->left;
        if(root->key > cur->key)return false;
    }
    return true;
}

//判断是否平衡
bool isBalance(TreeNode *root,int *depth)
{
    if (root == NULL)
    {
        *depth = 0;
        return true;
    }
    int depthl,depthr;
    if(!isBalance(root->left,&depthl))return false;
    if(!isBalance(root->right,&depthr))return false;
    int diff = depthl - depthr;
    if(diff > 1 || diff < -1)return false;
    *depth = 1+(depthl>depthr?depthl:depthr);
    return true;
}
{% endcodeblock %}