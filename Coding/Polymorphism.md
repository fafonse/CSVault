The fundamental property of OOP where subclasses can change their inherited functions and still have them work.

```python
class Animal():
	def __init__(self): # im too lazy to write this again
		self.hunger = 100
	def eat(self):
		self.hunger -= 1

class BigAnimal(Animal): # subclass
	def eat(self): # overriden method
		self.hunger -= 10
		
animal_list = [Animal(), BigAnimal()]

for a in animal:
	a.eat() # this works due to polymorphism
```