Similar to a [[Sets|set]], but now there's a non-specific key associated with a value.
> AKA: associative array, (hash) map, hash table

- Values can be non-unique, but keys must be unique
	- Different addresses, same package basically

```python
# initialize
bands = {'thom':'Radiohead', 'john':'The Beatles', 'Sebastien':'DFA1979'}

print(bands['Sebastien']) # DFA1979

# these return view objects, which update with the dict
bands.keys() # returns list of keys
bands.values() # return list of values
bands.items () # return keys + values

```