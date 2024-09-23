## 代码
```cpp{.line-numbers}
//...loop_invariant elided...
{
    lower = lower;
    upper = upper;
}
```
## 证明
- 初始时 lower = 0,upper = n 自然满足循环不变量
- 循环结束后，lower upper不变，自然也满足下个循环的不变量
循环不变量确定的时不变的关系，无法保证应该改变的关系正确改变，所以无法正确实现二分查找。原因在于循环不会终止。