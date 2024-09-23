# 练习1

[![pFvK0yT.png](https://s21.ax1x.com/2024/04/14/pFvK0yT.png)](https://imgse.com/i/pFvK0yT)
只经过一次左旋后，树变成如图所示。可以发现，实际上y的深度并没有改变，反而z的深度降低了。
所以那么假如(z,b)树高为h,(x,y)为h，那么z的左子树树高为h+2,右子树树高为h，不平衡。
[![pFvuOLF.png](https://s21.ax1x.com/2024/04/14/pFvuOLF.png)](https://imgse.com/i/pFvuOLF)

# 练习4
## cir 1
[![pFvMVXT.png](https://s21.ax1x.com/2024/04/14/pFvMVXT.png)](https://imgse.com/i/pFvMVXT)
如图，当前 $T = x$ ，同时 $h(y) = h((z,x)) + 1 = h((x,b)) + 1$，这时只需要对x执行一次右旋即可。如下图
[![pFvMenU.png](https://s21.ax1x.com/2024/04/14/pFvMenU.png)](https://imgse.com/i/pFvMenU)
所以平衡了。

## cir 2
[![pFvMKAJ.png](https://s21.ax1x.com/2024/04/14/pFvMKAJ.png)](https://imgse.com/i/pFvMKAJ)
如图，当前 $T = x$，且$h((a,z)) \leq h(y) $。
那么有 $h = h(y) = h((x,b)) +1$。又因为avl树的性质，所以有

$$h((z,y)) = h \\
  h((y,x)) = h || h-1 \\
  h((a,x)) = h || h-1 \\
  h((x,b)) = h-1$$
经过一次双旋转后有
[![pFvM8c6.png](https://s21.ax1x.com/2024/04/14/pFvM8c6.png)](https://imgse.com/i/pFvM8c6)
所以平衡了。