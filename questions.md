1.
```py
sum([x for x in range(1, 100) if x % 2 == 1])
```
2. 保持元素的先后顺序

```py
lst = [1, 1, 2, 3, 4, 4, 3, 2, 5]
tmp = list(set(lst))
tmp.sort(key=lst.index)
lst = tmp
```
3.
```py
s = "abc"
reversed_s = s[::-1]
```

4. 

```py
import functools
import datetime
import time


def timeit(max_time):
    """
    计算函数执行时间的装饰器
    """
    def decorator(func):
        @functools.wraps(func)
        def wrapper(*args, **kw):
            start = datetime.datetime.now()
            res = func(*args, **kw)
            end = datetime.datetime.now()
            duration = int((end - start).total_seconds())
            print(f'"{func.__name__}" function ran for {duration}s')
            
            if duration > max_time:
                print(f'"{func.__name__}" function exceeds max_time')
                
            return res
        return wrapper
    return decorator


@timeit(max_time=1)
def func(*args, **kw):
    time.sleep(2)


func()

```
5.

```py
class InterInt:
    def __init__(self):
        self.a = 1

    def __iter__(self):
        return self

    def __next__(self):
        res = self.a
        self.a += 1
        return res


a = InterInt()
print(next(a))
print(next(a))
print(next(a))
```

6. 

```py
class CustomDict:

    def __setitem__(self, key, value):
        setattr(self, key, value)

    def __getitem__(self, key):
        if hasattr(self, key):
            return getattr(self, key)

        raise KeyError(key)


cdict = CustomDict()
cdict["a"] = 1
cdict["b"] = 2
print(cdict["a"])
print(cdict["c"])
```

7. 使用单调递增队列去做，维护一个长度为 k 的队列，添加一个元素时，和队尾元素比较
如果小于这个值，则弹出。并且弹出过期的元素。

```py
from typing import List
import collections


def find_lowest_players(k=3, map=[1, 2, 6, 2, 9, 6, 1, 8]) -> List[int]:
    """
    Find the player with lowest HP within given range.
    Using a monotonically increasing queue to solve the problem.
    Args:
        k: the players count
        map: A list of players' HPs
    Returns:
        the player with lowest HP within k
    """
    q = collections.deque()
    for i in range(k):
        while q and map[i] <= map[q[-1]]:
            q.pop()
        q.append(i)

    res = [map[q[0]]]
    for i in range(k, len(map)):
        while q and map[i] <= map[q[-1]]:
            q.pop()
        q.append(i)
        
        while q[0] <= i - k:
            q.popleft()
            
        res.append(map[q[0]])

    return res


print(find_lowest_players())
```
