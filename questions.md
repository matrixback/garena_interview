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
