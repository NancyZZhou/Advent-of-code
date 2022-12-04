```python
with open('input.txt', 'r') as f:
    data = f.read().split('\n')
```


```python
import re

# Part 1
n_fully_contain = 0

for i in range(0, len(data)):
    pair = re.split(',|-', data[i])
    if set(range(int(pair[0]), int(pair[1])+1)).issubset(range(int(pair[2]), int(pair[3])+1)) or set(range(int(pair[2]), int(pair[3])+1)).issubset(range(int(pair[0]), int(pair[1])+1)):
        n_fully_contain = n_fully_contain + 1
print(n_fully_contain)
```


```python
# Part 2
n_overlap = 0

for i in range(0, len(data)):
    pair = re.split(',|-', data[i])
    if set(range(int(pair[0]), int(pair[1])+1)).intersection(range(int(pair[2]), int(pair[3])+1)):
        n_overlap = n_overlap + 1
print(n_overlap)
```
