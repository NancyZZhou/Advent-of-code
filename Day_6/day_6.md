```python
with open('input.txt') as f:
    data = f.read()
```


```python
# Part 1

no_packet = 4
for i in range(len(data)-no_packet):
    if len(set(data[i:i+no_packet])) == no_packet:
        print(i+no_packet)
        break
```


```python
# Part 2

no_message = 14
for i in range(len(data)-no_message):
    if len(set(data[i:i+no_message])) == no_message:
        print(i+no_message)
        break
```
