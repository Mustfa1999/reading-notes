# Reading: Class 11

> [Back to the main](./README.md)

---

    import numpy as np

define a numpy array:

    list1 = [ 10, 4, 6 ]
    a = np.array( list1 )  

we can pass the pre-defined array 

    b = np.array( [ 5, 4, 2 ] ) 
    
we can write it manually 

    a / b 

it will divide each element of (a) over the corresponding one in the (b) and return ( [ 2, 1, 3 ] )

	a * b 

product 

	a + b  
    
summation

	s – b 
    
subtraction 

	a.dot(b) 
    
dot product

	list2 = array([ 0,  9, 18, 27, 36, 45, 54])
    res = list2 > 20 

it will return Boolean results for the condition applied on each element : array([False, False, False,  True,  True,  True,  True])

    list2[res] 
    
that will apply the Boolean sequence on the list to show only what had satisfied the condition : array([27, 36, 45, 54])

---

if we have an array: A 

    A = np.array( [0,1,2,3,4,5], [10,11,12,13,14,15], [20,21, … )
```
0	1	2	3	4	5
10	11	12	13	14	15
20	21	22	23	24	25
30	31	32	33	34	35
40	41	42	43	44	45
50	51	52	53	54	55
```

	A[2]
    
get the third row

	A[ : , 2 ] 
    
get the third column

	A[0, 3:5] 
    
get me the corresponding of row 0 and columns from 3 to 4 
array([3, 4])

	A[4: , 4:] 
    
rows from 4 to the end, and columns from 4 to the end
array([[44, 45], [54, 55])

	A[:, 2] 
    
all the rows and column 2
array([2, 12, 22, 32, 42, 52])

	A[ 2::2 , ::2 ] 
    
row (2), to the end of it, with step of (2), and all columns, to the end of them, with step of (2)
array([20, 22, 24], [40, 42, 44])

	A[2][3] 
    
get the element at row 2 and colum3
23

	A[[ 1, 2, 2, 3 ]] 
    
this will get some specific rows (duplicates are allowed)

```
10	11	12	13	14	15
20	21	22	23	24	25
20	21	22	23	24	25
30	31	32	33	34	35
```

---

if we have :

    a = np.array( [ 1, 2, 3, 4 ] ) 

then:

	np.sin( a* np.pi ) : returns the sin of all the items in (a)
	np.sum(a) : return the sum of all the values in the array
	np.sqrt(a) : taking square root of every element in the array
	np.exp(a) : calculating exponential (e^)
	np.log(a) : calculating log
	np.std(a) : taking the standard deviation
	np.around( a ) : it will approximate the items of (a)
	np.around( a, decimals=3 ) : it approximate the items of (a) with 3 digits after decimal point
	np.floor( a ) : returns the floor
	np.ceil( a ) : returns the ceil 
	np.arcsin( a* np.pi/180 ) : returns the inverse sin
	np.degrees( a* np.pi ) : returns
	np.zeros(3) : it will make a vector of 3 items filled with zeros
	np.zeros(3, 4) : it will make a 3x4 array filled with zeros
	np.ones(3, 4) : it will make a 3x4 array filled with ones
	np.linespace(1, 5, 20) : create a sequence from 1 to 5 with 20 samples in between
	np.random.choice( [ “False”, “True” ] , size=1000 ) : it will make a list which each element of it has random choice between (true) and (false)
	np.random.randint( 0, 100 , size=1000 ) : it will make a list which each element of it has random choice between 0 and 100
	np.random.rand(4, 6) : create an array (4x6) of random numbers
	np.random.seed(444) : it will raise the randomness to 444 times the original

	np.arange( 1, 10, 3 ) : it will make a list of integers starts from 1 and ends with 10 with a step of 3 between them (it doesn’t necessary reach the last number 10 and it won’t reach it if it was at the last step) and the data type of the result will be (numpy.ndarray object), it will print [ 1 4 7 ]

	np.arange( -3, 10, 3 ) : it will print [ -3 0 3 6 9 ]
	np.arange( 10, 1, -2 ) : it will print [ 10  8  6  4  2 ]
	np.arange( 0, 10 ) : it will print numbers from 0 to 9
	np.arange( 10 ) : it will print numbers from 0 to 9

---

	myArray = np.arrange(12).reshape(3, 4) 
    
it will reshape the array to be as 3 rows and 4 columns
array( [ [0, 1, 2,     3]
 	   [4, 5,  6,    7]
 	   [8, 9, 10, 11] )

	myArray.size() : returns the size 12
	myArray.shape() : returns the shape (3, 4)
	myArray.ndim() : returns number of dimensions 2
	myArray.itemsize() : returns the item size in bytes 4
	myArray.sum(axis=0) : it will add the elements of each column together, so it will turn the array to a vector 
	myArray.sum(axis=1) : it will add the elements of each row together, so it will turn the array to a vector
	myArray.mean(axis=0) : it will calculate the mean of each column
	
	myArray.max() : maximum of each column
	myArray.argmax()  : return the index of maximum value
	myArray.min() : minimum of each column
	maArry.argmin()  : return the index of minimum value
	myArray.average() : the average 
	myArray.median() : the median
	myArray.std() : the standard deviation 
	myArray.var() : the variance 
	myArray.cumsum() : cumulative summation (add each item with the next one and get the result of each adding)

	myArray = ( [1, 2], [3, 4], dtype=complex ) : it will change the data type to be complex --> array( [ 1+0.j , 2+0.j ], [ 3+0.j , 4+0.j ] )

	myArray.reshape(24) : it reshape it as a vector of 9 elements
	myArray.shape() : it will give (2,4,3)

	myArray = np.arrange(24).reshape(2, 4, 3) : it will reshape the array to be as 2 lists, each one has 3 columns and 4 rows
```
array(
[[[ 0,  1,  2],
[ 3,  4,  5], 
[ 6,  7,  8],
[ 9, 10, 11]],

[[12, 13, 14],
[15, 16, 17],
[18, 19, 20], 
[21, 22, 23]]] 	)
```

------------------------------------------------------------
if score =
``` 
      py-score    django-score      js-score
10      88.0            86.0   	        71.0
11      79.0            81.0      	    95.0
12      81.0            78.0  	        88.0
13      80.0            88.0            79.0
14      68.0            74.0     	    91.0
15      61.0            70.0     	    91.0
16      84.0            81.0      	    80.0
```
then: 

	np.average(score, axis=1, weights=[0.4, 0.3, 0.3]) 
	
it will calculate the average of each row and give the first column-element (py-score) a weight of (0.4) out of (1) in the calculation, and give (0.3) for (django-score) and (js-score) , it will return: array([82.3, 84.4, 82.2, 82.1, 76.7, 72.7, 81.9])

	score_copy = score.copy() 
	
this will make a copy of the data so we can apply changes on it without affecting the original data (score)

---

## Polynomials

### Define one:

	p = np.poly1d([4, 3, -2, 10])    	

4X^3+3X^2-2X+10

	print(p) 
	
it will print the polynomial in this shape:
```
 	     3       2
 	4 x + 3 x - 2 x + 10
```

### Evaluate at a point:
p(3) : evaluate (p) at (3)

	np.polyval([4, 3, -2, 10] , 3) 
	
evaluate (p) at (3)

- Adding polynomials:

		p1, p2 = np.poly1d([1, 7]),  np.poly1d([4, 0, 1])
		sum = np.polyadd(p1, p2)  

- Subtracting polynomials:

		sub = np.polysub(p1, p2)  

- Multiplying polynomials:

		mul = np.polyaddmul(p1, p2) 

- Dividing polynomials:

		div = np.polydiv(p1, p2) 

- Derivate polynomials:

		der = np.polyder(p)
	
	get the derivative 
	
		der(4) 
	
	evaluate the derivative (der) at (4)

		der2 = np.polyder(p, 2)
		
	get the second derivative

- Integrate polynomials:

		integral = np.polyint(p)
		print(integral(4)-integral(2)) 
		
	it will evaluate the integral from 2 to 4 

		integral2 = np.polyint(p, 2)
		
	get the double integral

	


	





