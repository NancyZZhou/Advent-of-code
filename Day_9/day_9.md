```python
import numpy as np
```


```python
with open('input.txt') as f:
    data = f.read().split('\n')
```


```python
# Part 1

head = np.array([0, 0])
tail = np.array([0, 0])
tail_trace = []

for i in range(len(data)):
#for i in range(10):
    step = data[i].split(' ')[-1]
    for j in range(int(step)):
        if data[i].startswith('L'):
            head = head - [1, 0]
        elif data[i].startswith('R'):
            head = head + [1, 0]
        elif data[i].startswith('U'):
            head = head + [0, 1]
        else:
            head = head - [0, 1]

        if np.sqrt(np.square(head[0]-tail[0]) + np.square(head[1]-tail[1])) > 2:
            #if not head[0] == tail[0] or head[1] == tail[1]:
            if head[0] > tail [0] and head[1] > tail[1]:
                tail = tail + [1, 1]
            elif head[0] > tail [0] and head[1] < tail[1]:
                tail = tail + [1, -1]
            elif head[0] < tail [0] and head[1] > tail[1]:
                tail = tail + [-1, 1]
            else:
                tail = tail + [-1, -1]
        elif np.sqrt(np.square(head[0]-tail[0]) + np.square(head[1]-tail[1])) == 2:
            if head[0] == tail[0]:
                if head[1] > tail[1]:
                    tail = tail + [0, 1]
                elif head[1] < tail[1]:
                    tail = tail - [0, 1]
            
            if head[1] == tail[1]:
                if head[0] > tail[0]:
                    tail = tail + [1, 0]
                elif head[0] < tail[0]:
                    tail = tail - [1, 0]
        
        tail_trace.append(tuple(tail.tolist()))

print(len(set(tail_trace)))
                

```


```python
# Part 2

len_rope = 10
s = (len_rope, 2)
rope = np.zeros(s)
tail_trace = []

for i in range(len(data)):
    step = data[i].split(' ')[-1]
    for j in range(int(step)):
        if data[i].startswith('L'):
            rope[0] = rope[0] - [1, 0]
        elif data[i].startswith('R'):
            rope[0] = rope[0] + [1, 0]
        elif data[i].startswith('U'):
            rope[0] = rope[0] + [0, 1]
        else:
            rope[0] = rope[0] - [0, 1]

        for k in range(len_rope-1):
            if np.sqrt(np.square(rope[k][0]-rope[k+1][0]) + np.square(rope[k][1]-rope[k+1][1])) > 2:
                if rope[k][0] > rope[k+1][0] and rope[k][1] > rope[k+1][1]:
                    rope[k+1] = rope[k+1] + [1, 1]
                elif rope[k][0] > rope[k+1][0] and rope[k][1] < rope[k+1][1]:
                    rope[k+1] = rope[k+1] + [1, -1]
                elif rope[k][0] < rope[k+1][0] and rope[k][1] > rope[k+1][1]:
                    rope[k+1] = rope[k+1] + [-1, 1]
                else:
                    rope[k+1] = rope[k+1] + [-1, -1]
            elif np.sqrt(np.square(rope[k][0]-rope[k+1][0]) + np.square(rope[k][1]-rope[k+1][1])) == 2:
                if rope[k][0] == rope[k+1][0]:
                    if rope[k][1] > rope[k+1][1]:
                        rope[k+1] = rope[k+1] + [0, 1]
                    elif rope[k][1] < rope[k+1][1]:
                        rope[k+1] = rope[k+1] - [0, 1]
                
                if rope[k][1] == rope[k+1][1]:
                    if rope[k][0] > rope[k+1][0]:
                        rope[k+1] = rope[k+1] + [1, 0]
                    elif rope[k][0] < rope[k+1][0]:
                        rope[k+1] = rope[k+1] - [1, 0]
        
        tail_trace.append(tuple(rope[len_rope-1].tolist()))

print(len(set(tail_trace)))
                

```
