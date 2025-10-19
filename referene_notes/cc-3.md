2025-04-21T08:44
## Contents
1. Objects hide their data behind abstractions and expose functions that operate on that data . Data structures expose their data and have no meaning meaningful functions. 
```
# data structure
class Point:
	def __init__(self):
		self.x: float
		self.y: float

# Object intertace
class Point(ABC):
	@abstractmethod
	def get_x():
		pass
	@abstractmethod
	def get_y():
		pass
	@abstractmethod
	def setCartesian(x: float, y: float):
		pass
```
2. Procedure code make it easy to add functions; but hard to add objects because all the functions must change. In contrast, OO codes make it easy to add class; but hard to add functions because all the classes must change.
3. The Law of Demeter: a method f of a class C should only calls the method of these:
	1. C
	2. An object created by f
	3. An object passed as an argument of f
	4. An object held in a instance variable of C
	5. For example, this code seems violates the law (if the functions are not accessor functions): `dir = ctxt.getOptions().getScratchDir().getAbsolutePath()`
	6. Data transfer objects are objects of classes with public variables and no functions.
## Reference

Clean code
