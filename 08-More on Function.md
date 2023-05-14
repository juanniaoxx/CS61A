----
### 1. Reading(chapter 3.3) --Excptions
> 异常处理

#### 1. Expection(异常)
> 异常是直接或间接继承自`BaseException`类的的对象实例
> `assert`[断言]语句引发类`AssertionError`的异常。
> 通常来说，可以使用`rasie`语句引发`任何`类型的异常实例

```python
>>> rasie Exception('An error occured')

	Traceback (most recent call last):
		File "<stdin>" , line 1 , in <module>
	Exception: an error occured
```

> no further statements in the current block of code are executed.


#### 2.Handling exceptions(异常处理)
> try statement

```python
try:
	<try suite>
except <exception class> as <name>:
	<except suite>
```

> 例子：

```python
try :
	x = 1/0
	except ZweroDivisionError as e:
		print("hadling a" , type(e))
		x = 0
handling a <class 'ZeroDivisionError'>
>>> x
0
```


```python
def incert(x):

    """

    >>> incert_safe(2)

    Never printed if x is 0

    0.5

    >>> incert_safe(0)

    'division by zero'

    """

    result = 1 / x

    print("Never printed if x is 0")

    return result

def incert_safe(x):

    try:

        return incert(x)

    except ZeroDivisionError as e:

        return str(e)
```

///未完待续 3.3.1 异常对象

----
### 2.Lecture && guide
#### A problem :The Towers of Hanoi(汉诺塔!)
> game rules
> 1. Only one disk can be moved among the towers at any given time.(任意时刻只能移动一个盘)
> 2. Only the "top" disk can be removed.(只允许移动最顶端的盘子)
> 3. No large disk can sit over a samll disk.(不需要大盘子放在小盘子的下面【任何时刻的都不行】)

> 时间复杂度 O(2^n - 1) 递归完成

```python
def move_tower(n, start_peg, end_peg):

    """Perform moves that transfer an ordered tower of N>0 disks in the

    Towers of Hanoi puzzle from peg START_PEG to peg END_PEG, where

    1 <= START_PEG, END_PEG <= 3, and START_PEG != END_PEG. Assumes

    the disks to be moved are all smaller than those on the other pegs."""

    # >>> solve_puzzle(n) 使用这个来测试程序

    if n == 1:

        move_disk(start_peg, end_peg)

    else:

        spare_peg = 6 - start_peg - end_peg
        #假设盘子的序号分别式 1,2,3 

        move_tower(n - 1, start_peg, spare_peg)

        move_disk(start_peg, end_peg)

        move_tower(n - 1, spare_peg, end_peg)

  
  

## Extra fancy stuff for showing the moves, setting up, and solving the puzzle.

  

import time

  

PAUSE = 1.0

  

pegs = [0, [], [], []]

  

def solve_puzzle(n):

    """Show the moves to solve a Towers of Hanoi problem for a tower

    of N>0 disks."""

    set_up_puzzle(n)

    print_puzzle()

    time.sleep(PAUSE)

    move_tower(n, 1, 3)

  

def set_up_puzzle(n):

    """Set up Towers of Hanoi puzzle with N disks on peg 1, and

    other pegs empty."""

    pegs[:] = [n, [ k for k in range(n, 0, -1) ], [], []]

  

def move_disk(peg0, peg1):

    """Move disk from PEG0 and PEG1, printing the result."""

    pegs[peg1].append(pegs[peg0].pop())

    print_puzzle()

    time.sleep(PAUSE)

def print_puzzle():

    """Print current configuration of puzzle (stored in pegs)."""

    n = pegs[0]

    for k in range(n, 0, -1):

        for j in range(1, 4):

            print(" ", end="")

            if len(pegs[j]) >= k:

                c = pegs[j][k-1]

                print(" " + " " * (n - c) + "##" * c + " " * (n - c) + " ", end="")

            else:

                print(" " * (2 * n + 2), end="")

        print()

    print("=" * (6*n + 9))

    print(" " * (n+2) + "1" + " " * (2 * n + 2) + "2" + " " * (2 * n + 2) + "3")

    print()

  

# Deleting digits (spoiler alert!)
```


```python
#和算法实现有关的
def move_tower(n,start_peg,end_peg):
	if n == 1:
		move_disk(start_peg,end_peg)
	else:
		spare_peg = 6 - start_peg - end_peg
		move_tower(n - 1 , start_peg , spare_peg)
		move_disk(strat_peg,end_peg)
		move_tower(n - 1 , spare_peg,end_peg) 
def move_disk(peg0 , peg 1):
	pegs[peg1].append(pges[peg0],pop())
pegs = [0,[],[],[]]
pegs[:] = [n,[k for k in rage(n,0,-1)] , [] , []] 
#初始化汉诺塔
```

//未完成
