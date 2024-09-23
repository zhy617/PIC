## 代码
```cpp{.line-numbers}
int binsearch_final(int x, int[] A, int n)
//@requires 0 <= n && n <= \length(A);
//@requires is_sorted(A, 0, n);
/*@ensures (-1 == \result && !is_in(x, A, 0, n))
|| ((0 <= \result && \result < n) && A[\result] == x && !is_in(x,A,0,\result));
@*/
{ 
    int lower = 0;
    int upper = n;
    while (lower < upper - 1)
    //@loop_invariant 0 <= lower && lower <= upper && upper <= n;
    //@loop_invariant (lower == 0 || A[lower] < x);
    //@loop_invariant (upper == n || A[upper] >= x);
    { 
        int mid = lower + (upper-lower)/2;
        //@assert lower <= mid && mid < upper;
        
        if (A[mid] < x) lower = mid;
        else /*@assert(A[mid] >= x);@*/
        upper = mid;
        // printint(lower);printint(upper);
    }
    if(lower < n && A[lower] == x){
        return lower;
        //@assert lower == 0;
    }
    if(lower + 1 < n && A[lower+1]==x)return lower+1;
    return -1;
}
```

## 证明循环不变量
循环不变量
```cpp{.line-numbers}
    //@loop_invariant 0 <= lower && lower <= upper && upper <= n;
    //@loop_invariant (lower == 0 || A[lower] < x);
    //@loop_invariant (upper == n || A[upper] >= x);
```

### 初始情况
初始情况下，lower=0,upper=n，自然满足循环不变量

### 循环时
假设某一循环时满足循环不变量，考虑对于下一个循环的影响。
- A[mid] < x：那么只有lower改变，下一个循环前的A[lower']=A[mid]< x，满足循环不变量2，又因为lower<=mid<=upper，自然满足循环不变量1
- A[mid] >= x:那么只有upper改变，下一个循环前的A[upper']=A[mid]>= x,满足循环不变量3，又因为lower<=mid<=upper，自然满足循环不变量1

## 证明后置条件
```cpp{.line-numbers}
/*@ensures (-1 == \result && !is_in(x, A, 0, n))
|| ((0 <= \result && \result < n) && A[\result] == x && !is_in(x,A,0,\result));
@*/
```
因为满足前置条件和循环不变量，所以可得
- lower==0 || A[lower]<x
- upper==n || A[upper]>=x
- lower < upper-1
所以考虑以下几种情况
- lower==0时，那么只可能是A[lower],A[lower+1]几种，判断是否越界即可
- A[lower]<x时，那么只可能是A[lower+1]，判断一下是否越界即可。
即我们实现的是找到包含小于x的最右边的数，然后判断下一位是否是x即可。

综上，当x存在时总能找到最左边的x，x不存在时返回-1，所以满足后置条件。