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
