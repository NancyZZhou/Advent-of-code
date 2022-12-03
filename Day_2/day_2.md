```python
import pandas as pd

data = pd.read_csv('input.txt', header=None, delim_whitespace=True, names=['opponent', 'me'])

data['score_game_1'] = data.apply(lambda x: game_1(x['opponent'], x['me']), axis=1)
print(sum(data['score_game_1']))

data['score_game_2'] = data.apply(lambda x: game_2(x['opponent'], x['me']), axis=1)
print(sum(data['score_game_2']))
```


```python
def game_1(a, b):
    if a == 'A':
        if b == 'X':
            return 1 + 3
        elif b == 'Y':
            return 2 + 6
        else:
            return 3 + 0
    elif a == 'B':
        if b == 'Y':
            return 2 + 3
        elif b == 'Z':
            return 3 + 6
        else:
            return 1 + 0
    else:
        if b == 'Z':
            return 3 + 3
        elif b == 'X':
            return 1 + 6
        else:
            return 2 + 0
```


```python
def game_2(a, b):
    if a == 'A':
        if b == 'X':
            return 3 + 0
        elif b == 'Y':
            return 1 + 3
        else:
            return 2 + 6
    elif a == 'B':
        if b == 'Y':
            return 2 + 3
        elif b == 'Z':
            return 3 + 6
        else:
            return 1 + 0
    else:
        if b == 'Z':
            return 1 + 6
        elif b == 'X':
            return 2 + 0
        else:
            return 3 + 3
```


```python

```
