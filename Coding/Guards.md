When you verify that values are all OK in a function before you do anything.

> Boundary checks, assertions, etc.

```python
def calcChecksum(i, seed):
	# guards
	if i is None or i == '':
		return 0
		
	if seed > 256:
		return 0
	
	
	# rest of code...
```