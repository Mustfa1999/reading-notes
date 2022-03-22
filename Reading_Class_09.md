# Reading: Class 09

> [Back to the main](./README.md)

---

## Magic methods:

Magic methods: they are a special set of available methods we can define in a class so that we can specify a the behavior of the class whenever we use a specific operator, all these functions are automatically defined by default in any class with no special behavior but we can overwrite them to change that, all of them has double underscore (dander) before and after their names

---

## Object Initialization

- __init__ function:

    the constructor is the most common magic method, it will be run automatically once we create an instance of that class, and it will only affect its instance

        class MyClass:
            def __init__(self)
                print(“New object has been created !”)
        obj = MyClass()

---

## Object Representation

- __str__ function:

    this function specifies the returned string value when we try to print the object itself, we can call it by passing the object to the (str) function

        class MyClass: 
            def __init__(self, name)
                self.name = name
            def __str__(self)
                print(f“This object named {self.name}”)
        obj = MyClass(“Jack”)
        print(str(obj))
        prints : This object named Jack

- __repr__ function:

    this function specifies the represented string value when of the object, we can call it by passing the object to the (repr) function

        class MyClass: 
            def __init__(self, name, age)
                self.name = name
                self.age= age
            def __repr__(self)
                print(f“Name: {self.name}, Age: {self.age}”)
        obj = MyClass(“Jack”, 25)
        print(repr(obj))
        prints : Name: Jack, Age:25

---

## Iteration

- __len__ function:

    this function used to add a custom counting property to the class, we can call it by passing the object to the (len) function

    class MyClass: 
        def __init__(self, name)
            self.name = name
            self.scores = [52, 41, 70, 14]
        def __len__(self)
            return len(self.scores)
    obj = MyClass(“Jack”)
    print(len(obj))
    prints : 4

- __getitem__ function:

    this function used to make the instance of the class iterable so we can use indexing on it or loop through it, we can call it by passing the object to the (getitem) function

        class MyClass: 
            def __init__(self, name)
                self.name = name
                self.scores = [52, 41, 70, 14]
            def __getitem__(self, pos)
                return self.scores[pos]
        obj = MyClass(“Jack”)
        for x in onj: 
            print(x, end=”, ”) 		 prints : 52, 41, 70, 14
        print( x[2] ) 				 prints : 70

- __reversed__ function:

    this function used to reverse the order of the iterable object (the class has to have the getitem method), we can call it by passing the object to the (reversed) function

        class MyClass: 
            def __init__(self, name)
                self.name = name
                self.scores = [52, 41, 70, 14]
            def __getitem__(self, pos)
                return self.scores[pos]
            def __reversed__(self)
                return self[::-1]
        obj = MyClass(“Jack”)
        print(reversed(obj))
        prints : [14, 70, 41, 52] 

---

## Operator Overloading for Comparing

we use them to able the comparison between objects of this class, we can use any of the six signs, every method of those has to have a parameter called (other) besides the (self) parameter, we pass the second instance as an argument for the (other) parameter
( == ) equal (eq)
( != ) not equal (nq)
( < ) less than (lt)
( <= ) less than or equal (le)
( > ) greater than (gt)
( >= ) greater than or equal (ge)

```
class MyClass: 
    # The init
 	def __init__(self, name, balance)
 		self.name = name
 		self.balance = balance
    
    # The equality (==, !=)
 	def __eq__(self, other)
 		return self.balance == other.balance
	def __nq__(self, other)
 		return self.balance != other.balance
    
    # The less/greater than or equal (<, <=, >, >=)
	def __lt__(self, other)
 		return self.balance < other.balance
 	def __le__(self, other)
 		return self.balance <= other.balance
	def __gt__(self, other)
 		return self.balance > other.balance
 	def __ge__(self, other)
 		return self.balance >= other.balance

    # The logical and/or/xor (&, |, ^)
	def __and__(self, other)
 		return self.balance and other.balance
	def __or__(self, other)
 		return self.balance or other.balance
 	def __xor__(self, other)
 		return self.balance xor other.balance

# Test 
obj1 = MyClass(“Jack”, 50)
obj2 = MyClass(“Ted”, 30)

print(obj1 == obj2) 	# prints: False
print(obj1 >= obj2) 	# prints: True
print(obj1 < obj2) 		# prints: False
```

---

## Operator Overloading for Arithmetic operations
we use them to able using the any arithmetic operator between two objects, like if we use the ( + ) operator between two instances of the class (MyClass), the function (__add__) will be called 

```
class MyClass:
    # The init
 	def __init__(self, par1, par2)
 		self.x = par1
 		self.y = par2

    #The add/subtract (+, -)
 	def __add__(self, other):
 		return MyClass( self.x + other.x,  self.y + other.y )
	def __sub__(self, other):
 		return MyClass( self.x - other.x,  self.y - other.y )

    # The multiply / true division / floor division (*, /, //)
 	def __mul__(self, other):
 		return MyClass( self.x * other.x,  self.y * other.y )
	def __truediv__(self, other):
 		return MyClass( self.x / other.x,  self.y / other.y ) 
	def __floordiv__(self, other):
 		return MyClass( self.x // other.x,  self.y // other.y )

    # The modulo/power (%, **)
 	def __mod__(self, other):
 		return MyClass( self.x % other.x,  self.y % other.y )
	def __pow__(self, other):
 		return MyClass( self.x ** other.x,  self.y ** other.y ) 

# Test 
first = MyClass(5, 7)  	 the instance (first) has x=5, y=7
second = MyClass(3, 9)     the instance (second) has x=3, y=9
result = first + second

print(result.x)    # it prints 8 which is (5+7)
print(result.y)    # it prints 12 which is (3+9)

# (first+second) is translated into (first.__add__(second))
```

---

## Callable Python Objects: __call__
we use it to make the object callable by itself 

    class MyClass: 
        def __init__(self, name)
            self.name = name
        def __call__(self)
            print(f“my name is {self.name}”)
    obj = MyClass(“Jack”)
    obj()

print: my name is Jack

---

## Context Manager Support and the With Statement: __enter__, __exit__

we use it so the object will have a custom behavior when we use it with the (with) statement, the (enter) method will be called once we enter the (with) block, and the (exit) method will be called once we exit its block

    class MyClass: 
        def __init__(self, name)
            self.name = name
        def __enter__(self)
            print(“entering the with …”)
        def __exit__(self)
            print(“exiting the with”)
    
    obj = MyClass(“Jack”)
    
    with obj as x:
        print(“hello”)

**that will print:**

    entering the with …
    hello
    exiting the with
