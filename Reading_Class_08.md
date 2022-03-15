# Reading: Class 08

> [Back to the main](./README.md)

---

## List Comprehension

    x = [ y**2 for y in list1 ] 

return a list, it will square all values in list1 and store the new list in x 

    [ print( x ) for x in range(5) ] 
    
we can make a loop without using its return values 

    [[[ print(x, y, z) for x in range(5) ] for y in range(10) ] for z in range(15) ]  
    
we can make nested loops using this property 

    colors = [ “red”, “black”, “yellow”, “green”, “pink” ]

    shortColors  = [ (color.upper()) for color in colors if len(color) < 5]
	
we use it as a filter to return specific values from a list based on a condition 
 
it will filter the short colors and return [“RED”, “PINK” ]

we can write it in several lines :

    shortColors  = [    color.upper()
 			            for color in colors 
 			            if len(color) < 5 	]

---

## Dictionary Comprehension

    scores = { str(score): score**2 for score in [10,20,30,40] }

scores will be :
{ “10”: 100, “20”: 400, “30”: 900, “40”: 1600 }


---

## Decorators 
 
    from decorators import *

- @debug : display a simulation debugging of the function when we call it

        class TimeWaster:
            @debug
            def __init__(self, max_num):
                self.max_num = max_num

- @timer : tells us how much time the function took to be executed when we call it 

        @timer
        def waste_time():
            for _ in range(num_times):
                sum([i**2 for i in range(self.max_num)])

- @do_twice : it will call the function twice when we call it  

        @do_twice
        def greet():
            print(“hello”)        

- @count_calls : it keeps counting how many times we called this function and display the count each time we call it 

        @count_calls
        def say_whee():
            print("Whee!")

- @repeat : call the function many times upon calling it 

        @repeat(num_times=4)
        def greet(name):
            print(f"Hello {name}")

- @set_unit : set a virtual unit to a mathematical function 

        import math
        @set_unit("cm^3")
        def volume(radius, height):
            return math.pi * radius**2 * height
        print(volume.unit)
        prints : cm^3

    we can do the same with python annotations (sued for type hints)

        import math
        def volume(radius, height) -> "cm^3":
            return math.pi * radius**2 * height


- Nesting decorators : we can use multiple decorators for the same function 

        @do_twice
        @debug
        def greet():
            print(“Hello")

---
