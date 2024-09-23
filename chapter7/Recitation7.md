# Checkpoint1
|O(1)|O(log(log(n)))|O(logn)|O(log^2(n))|O(n)|O(nlog(n))|O(n^2)|O(2^n)|O(n!)|
|----|--------------|-------|-----------|----|----------|------|------|-----|
|O(1),O(4)|O(log(log(n)))|O(log(n))|O(log^2(n))|O(n),O(4n+3)|O(nlog(n))|O(n^2  ),O(n^2+20000n+3)|O(2^n)|O(n!)|

# Checkpoint2
## 证明
要证 

$$n^3+300n \in O(n^3)$$

设 $f(n)= n^3+300n,g(n)=n^3,c=301$，求解 $f(n_0) \leq c\times g(n_0)$，可得$n_0 = 1$，所以存在 $c=301,n_0=1$，使得 $\forall n \geq n_0$，有 $f(n) \leq cg(n)$，证毕

# Checkpoint3
## 证明
$$\begin{align}
&\because f(n) \in O(g(n)) \\
&\therefore \exist c\in R^+,n_0\in Z^+ ,\text{s.t.} \forall n\geq n_0,f(n) \leq cg(n) \\
&\because k \gneq 0\\
&\therefore \exist c\in R^+,n_0\in Z^+ ,\text{s.t.} \forall n\geq n_0,kf(n) \leq ckg(n) \\
&\therefore kf(n) \in O(kg(n)) \\
&\because kg(n)\in O(g(n))\\
&\therefore kf(n)\in O(g(n))
\end{align}
$$