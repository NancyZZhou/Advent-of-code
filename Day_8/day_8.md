```python
with open('input.txt') as f:
    data = f.read().replace('\n', '')
```


```python
n_col = 99
n_row = int(len(data) / n_col)
```


```python
list_input = np.array([int(i) for i in data])
matrix = list_input.reshape(n_row, n_col)
```


```python
# Part 1

n_visible = 0
for i in range(1, n_row-1):
    for j in range(1, n_col-1):
        if matrix[i, j] > max(matrix[i, 0:j]) or matrix[i, j] > max(matrix[i, j+1:]) or matrix[i, j] > max(matrix[0:i, j]) or matrix[i, j] > max(matrix[i+1:, j]):
            n_visible = n_visible + 1

n_edge = n_col * 2 + (n_row - 2) * 2
n_vis_total = n_visible + n_edge
print(n_vis_total)
```


```python
# Part 2

scores = []

for i in range(1, n_row-1):
    for j in range(1, n_col-1):
        left = [k for k in range(0, j) if matrix[i, k] >= matrix[i, j]]
        right = [k for k in range(j+1, n_col) if matrix[i, k] >= matrix[i, j]]
        up = [k for k in range(0, i) if matrix[k, j] >= matrix[i, j]]
        down = [k for k in range(i+1, n_row) if matrix[k, j] >= matrix[i, j]]

        if len(left) > 0:
            score_left = j - left[-1]
        else:
            score_left = j
        
        if len(right) > 0:
            score_right = right[0] - j
        else:
            score_right = n_col - j - 1
        
        if len(up) > 0:
            score_up = i - up[-1]
        else:
            score_up = i
        
        if len(down) > 0:
            score_down = down[0] - i
        else:
            score_down = n_row - i - 1
        
        scores.append(score_left*score_right*score_up*score_down)

print(max(scores))
```
