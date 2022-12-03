```python
import pandas as pd
import string
import numpy as np
```


```python
with open('input.txt', 'r') as f:
    data = f.read().split('\n')

# Part 1

item_both = pd.DataFrame({'rucksack':
    [set(rucksack[0:int(len(rucksack)/2)]).intersection(set(rucksack[int(len(rucksack)/2):])).pop() for rucksack in data]
    }
    )

letter_value = list(range(1, 53))
letters = dict(zip(list(string.ascii_letters), letter_value))

item_both['value'] = item_both['rucksack'].map(letters)
print(sum(item_both['value']))
```


```python
# Part 2
group_elements = 3
data_group = np.array_split(np.array(data), len(data)/group_elements)

group_badge = pd.DataFrame({'badge': [set(group[0]).intersection(set(group[1])).intersection(set(group[2])).pop() for group in data_group]})
group_badge['value'] = group_badge['badge'].map(letters)
print(group_badge['value'].sum())
```
