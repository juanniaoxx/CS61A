> 几种常见的递归类型
> 1. 尾递归（tail recursion） 在递归的最后仅仅只有递归的操作，而没有其他操作
> 2. 线性递归（linear recursion） 在每次递归的过程中，最多只能递归一次
> 3. 树递归 (tree recursion)

----
											A Problems
Try to implement the following:
![[Pasted image 20230513130025.png]]

```python
def find_zero(lowest,highest,func):
	if lowest > highest:
		return None
	elif func(lowest) == 0:
		return lowest
	else:
		return find_zero(lowest + 1 , highest , func)
```
>What kind of recursion is this?
>tail recursion & linear recusion

> by using the fact that the function is non-decreasing(不减函数)

```python
def find_zero(lowest,highest,func):

    if lowest > highest:

        return None

    mid = (lowest + highest) // 2

    if func(mid) == 0:

        return mid

    elif func(mid) < 0:

        return find_zero(mid + 1 , highest , func)

    else:

        return find_zero(lowest , mid - 1 ,func)
```

>what kind of recursion is this?
>Tail recursion

