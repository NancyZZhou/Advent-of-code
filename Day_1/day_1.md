```python
import numpy as np

with open('input.txt', 'r') as f:
    data = f.read().replace('\n', ',').split(',,')

calories = np.array(list(sum(list(map(int, elf.split(',')))) for elf in data))

print(calories[calories.argmax()])
calories.sort()
print(sum(calories[-3:]))
```
