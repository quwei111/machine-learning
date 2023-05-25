# Hashmap/ Hashset

## 基础
- 哈希碰撞：拉链法和线性探测法

## defaultdict
- defaultdict means that if a key is not found in the dictionary, then instead of a KeyError being thrown, a new entry is create

- dict and defaultdict
```python
somedict = {}
print(somedict[3]) # KeyError

someddict = defaultdict(int)
print(someddict[3]) # print int(), thus 0

d = defaultdict(list)
print(d[2])  # []

d = collections.defaultdict(set)
print(d[3])

# 带权重的图
graph = collections.defaultdict(dict)
```


- 排序
```python
# 根据values
sorted(footballers_goals.items(), key=lambda x:x[1])
```

- 增/改
```python

```