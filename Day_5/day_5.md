```python
import re
import numpy as np

with open('input.txt') as f:
    data = f.read().split('\n\n')
```


```python
stacks = data[0].split('\n')
stacks_T = [''.join(s) for s in zip(*stacks)][1:-1:4]

instructions = re.findall(r'\d+', data[1])
instruct_no = np.reshape(instructions, (int(len(instructions)/3), 3))
```


```python
# Part 1

stacks_T_stripped = [stack.strip().rstrip(stack[-1]) for stack in stacks_T]

for i in range(len(instruct_no)):
    move_no = instruct_no[i][0]
    move_from = instruct_no[i][1]
    move_to = instruct_no[i][2]

    move = stacks_T_stripped[int(move_from)-1][0:int(move_no)]
    stacks_T_stripped[int(move_to)-1] = move[::-1] + stacks_T_stripped[int(move_to)-1]
    stacks_T_stripped[int(move_from)-1] = stacks_T_stripped[int(move_from)-1].removeprefix(move)

print(''.join(stack[0] for stack in stacks_T_stripped))
```


```python
# Part 2

stacks_T_stripped = [stack.strip().rstrip(stack[-1]) for stack in stacks_T]

for i in range(len(instruct_no)):
    move_no = instruct_no[i][0]
    move_from = instruct_no[i][1]
    move_to = instruct_no[i][2]

    move = stacks_T_stripped[int(move_from)-1][0:int(move_no)]
    stacks_T_stripped[int(move_to)-1] = move + stacks_T_stripped[int(move_to)-1]
    stacks_T_stripped[int(move_from)-1] = stacks_T_stripped[int(move_from)-1].removeprefix(move)

print(''.join(stack[0] for stack in stacks_T_stripped))
```


```python

```
