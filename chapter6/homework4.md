## 代码
```cpp{.line-numbers}
int binsearch_before(int x, int[] A, int n)
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

## 解答
约定中的
```cpp{.line-numbers}
//@assert lower <= mid && mid < upper;
```
会告警。因为加法可能溢出为负数。如lower=2^30-1,upper=2^30+1时，mid=(lower+upper)/2 = (-2^31)/2 = -2^30，不满足约定

