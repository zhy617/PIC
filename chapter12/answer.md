- [Amortized Analysis](#amortized-analysis)
  - [a](#a)
  - [b](#b)
  - [c](#c)
- [A New Implementation of Queues](#a-new-implementation-of-queues)
  - [a](#a-1)
  - [b](#b-1)
  - [c](#c-1)
- [Strings as Keys](#strings-as-keys)
  - [a](#a-2)
  - [b](#b-2)


# Amortized Analysis
## a
最差的情况下，如上文所示，为 

$$\sum _0^{k}2^i  = 2^{k+1} = O(n)$$

所以最差的cost为 $O(N)$

## b
- 因为是bit0，最低位，所以每次increment时都会改变，所以是n次
- 因为是bit1，每两次increment改变一次，所以是 $\frac{n}{2}$次
## c
假设有k位，那么分别对每位考虑代价，那么总代价就是

$$\sum_{i = 0}^{k} \frac{n}{2^i} = n \sum_{i=0}^k \frac{1}{2^i} < 2n = O(n)$$
那么总渐进复杂度为O(n)，所以单词操作的渐进复杂度为O(1)

# A New Implementation of Queues
## a
```cpp
bool  queue_empty(queue Q){
    return stack_empty(Q->instack) && stack_empty(Q->outstack);
}
```
```cpp
void enqueue(elem e, queue Q){
    push(e, Q->instack);
}
```

```cpp
elem dequeue(queue Q)
//@requires !queue_empty(Q);
{
    if(stack_empty(Q->outstack)){
        while(!stack_empty(Q->instack)){
            push(pop(Q->instack), Q->outstack);
        }
    }
    return pop(Q->outstack);
}
```

## b
- enqueue:O(1)，只需要一个进栈操作即可。
- dequeue:O(n)，最坏情况下需要instack中n个元素，outstack为空，故需要2n+1次进栈出栈操作。


## c
- enqueue：对于每个元素，需要两次进栈操作，一次是进入instack，第二次是进入outstack。
- dequeue：对于每个元素，只需要两次出栈操作加上一次入栈操作，一次是从instack中pop，然后push进outstack，第二次是从outstack中出去。并不需要额外操作，因为只是顺序从instack转移到outstack，不会重新进栈。

# Strings as Keys

## a

$Load Factor = \frac{keys}{space} = 5$

负载因子越大，代表对空间的利用率越高，但查询效率也会偏低

## b

|0|1|2|3|4|5|
|-|-|-|-|-|-|
|1|31|961|2602|2116|2155

1 * 62 + 31 * x = ">b"
1 * 93 + 31 * (x-1) = "]a"

