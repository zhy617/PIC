## 证明
要证 

$$n^3+300n \in O(n^3)$$

设 $f(n)= n^3+300n,g(n)=n^3,c=301$，求解 $f(n_0) \leq c\times g(n_0)$，可得$n_0 = 1$，所以存在 $c=301,n_0=1$，使得 $\forall n \geq n_0$，有 $f(n) \leq cg(n)$，证毕