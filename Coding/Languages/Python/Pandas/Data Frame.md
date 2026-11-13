Panda's representation of a table; a collection of [[Series|series]]. 

```python
data = {'Name': ["John", "Tess", "Kellen"],
		'Gender': ["Male", "Female", "Male"]}
df = pd.DataFrame(data)
```
## Accessing Elements
There are two main methods for accessing individual elements, `iloc` and `loc`. 

- `iloc` grabs an element according to it's *index*
- `loc` grabs an element based off a *conditional*

```python
df.iloc[0] # returns the entry for "John"
df.loc[df]
```