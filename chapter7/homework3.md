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