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
    int upper = n - 1;
    while (lower < upper)
    //@loop_invariant 0 <= lower && upper <= n - 1;
    //@loop_invariant (lower == 0 || A[lower - 1] < x);
    //@loop_invariant (upper == n - 1 || A[upper + 1] > x);
    { 
        int mid = lower + (upper-lower)/2;
        //@assert lower <= mid && mid < upper;
        if (A[mid] == x) return mid;
        else if (A[mid] < x) lower = mid+1;
        else /*@assert(A[mid] > x);@*/
        upper = mid - 1;
    }
    return -1;
}
```

## 證明上面代碼中的三個循環不變量：
```cpp{.line-numbers}
//@loop_invariant 0 <= lower && upper <= n - 1;         --1
//@loop_invariant (lower == 0 || A[lower - 1] < x);     --2
//@loop_invariant (upper == n - 1 || A[upper + 1] > x); --3
```
### 證明：
1.在初始情況下，有lower=0 和 upper = n-1，而且函數有前置條件：0<=n&&n<=\length(A)，所以循環不變量都成立。
2.假設在某次進入循环前，3個循環不變量都成立，即有：
- 0<=lower && upper<= n-1
- lower==0 || A[lower-1]<x
- upper==n-1 || A[upper+1]>x
- lower < upper

分三種情況跳轉
- A[mid]==x：跳出循環，不改變，即循環不變量成立
- A[mid]< x：则lower=mid+1
    - 因爲lower <= mid < upper ，則滿足循環不變量1
    - 因爲A[lower-1]=A[mid] < x，所以滿足循環不變量2
    - upper不改變，所以滿足循環不變量3
- A[mid]>x:則upper=mid-1
    - 因爲lower<=mid<upper，所以滿足循環不變量1
    - 因爲lower不變，所以滿足循環不變量2
    - 因爲A[upper+1]=A[mid]>x，所以滿足循環不變量3


## 證明循環會終止：
每次循環后，upper-lower必然減少，而且有下界1，故必然終止。