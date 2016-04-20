# KMP算法那些事
### 前言
#### 众所周知，字符串匹配暴力方法时间复杂度过大。经典的看毛片算法(KMP)算法，使用预处理的手段和后缀前缀特征以及递归思想，可以大幅度优化字符串匹配时间复杂度。
### KMP算法思路
1. KMP就是每回模式串移动的不是一个单位移动，而是将前面匹配的都移动使得首部对应被匹配的字符串对应位置。也即是模式串得移动等同模式串移动块大小的位置。
2. 模式串移动块即字符串后缀与字符串前缀的最大共同部分。
3. 利用递归的思路预处理求解模式串移动块 从第一个位置开始循环 ，标记为q，当k位置的元素不等于q位置的元素，k递归为next[k-1],相等时k后移，使得next[q]=k;
4. 跟据next数组进行移动模式串，递归求解。

![KMP模式串移动块.png](http://upload-images.jianshu.io/upload_images/525165-75d86a86f97e3cba.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

###　实现代码
#### 预处理next数组
```cpp
void makeNext(const char P[],int next[])
{
    int q,k; //声明变量
    int m = strlen(P);
    next[0] = 0;
    for (q = 1,k = 0; q < m; ++q)
    {
        //while语句 递归求解
        while(k > 0 && P[q] != P[k])
            k = next[k-1];
         //相等后移
        if (P[q] == P[k])
        {
            k++;
        }
        //赋值
        next[q] = k;
    }
}
```
#### KMP核心代码
```cpp
int kmp(const char T[],const char P[],int next[])
{
    int n,m;
    int i,q;
    n = strlen(T);
    m = strlen(P);
    makeNext(P,next);
    for (i = 0,q = 0; i < n; ++i)
    {
        while(q > 0 && P[q] != T[i])
            q = next[q-1];
        if (P[q] == T[i])
        {
            q++;
        }
        if (q == m)
        {
            printf("Pattern occurs with shift:%d\n",(i-m+1));
        }
    }
}
```
### next数组详解
#### 举个例子
![kmpnext数组举例子.png](http://upload-images.jianshu.io/upload_images/525165-40661ad7f7df645f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
##### 例子图片和代码走一遍 了然于心