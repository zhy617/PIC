## 代码
```cpp{.line-numbers}
int binsearch_final(int x, int[] A, int n)
//@requires 0 <= n && n <= \length(A);
//@requires is_sorted(A, 0, n);
/*@ensures (-1 == \result && !is_in(x, A, 0, n))
|| ((0 <= \result && \result < n) && A[\result] == x);
@*/
{ 
    int lower = 0;
    int upper = n;
    while (lower < upper)
    //@loop_invariant 0 <= lower && lower <= upper && upper <= n;
    //@loop_invariant (lower == 0 || A[lower-1] < x);
    //@loop_invariant (upper == n || A[upper] > x);
    //@loop_invariant (is_in(x,A,0,n) == is_in(x,A,lower,upper));
    { 
        int mid = lower + (upper-lower)/2;
        //@assert lower <= mid && mid < upper;
        if (A[mid] == x) return mid;
        else if (A[mid] < x) lower = mid+1;
        else /*@assert(A[mid] > x);@*/
        upper = mid;
    }
    return -1;
}
```

## 证明新的循环不变量
```cpp{.line-numbers}
//@loop_invariant (is_in(x,A,0,n) == is_in(x,A,lower,upper));
```
### 初始
在初始情况下，有lower=0 和upper=n，所以is_in的输入都一致，那么结果肯定一致
### 循环中
假设某次进入循环前，满足循环不变量，那么分三种情况跳转
- A[mid]==x：则跳出循环，之后不会再进入循环，循环不变量成立
- A[mid] < x:则lower = mid+1。因为A数组有序，而且A[mid]< x，则代表[lower,mid] 中没有x，那么只可能是[mid+1,upper)中有，则循环不变量满足
- A[mid] > x:则代表[mid,upper)中没有x，那么只可能是在[lower,mid)中有x，所以循环不变量满足。

## 验证循环不变量隐含后置条件
经过手动测试多组数据，并未发现后置条件报错。测试数据如下
- x=3,n=5,A[]={1,2,3,4,5}
- x=3,n=5,A[]={3,3,3,3,3}
- x=3,n=0