# Reading: Class 12

> [Back to the main](./README.md)

---

## Dataframe Processes

### Creating the table (Dataframe):

    data = { 'x' : [1, 2, 3],   'y': [ 2, 4, 8 ],   'z': 100 }

    pd.DataFrame(data) 
    
this will create a dataframe (indexed data in both X and Y) from the given data (it should be a dictionary were the keys represents the columns’ labels, and the values represents the data for each column) 
the Y-indexes are assigned by default to (0, 1, 2, … ) and the X-columns should be given

```
     x    y     z
0   1   2   100
1   2   4   100
2   3   8   100
```

pd.DataFrame(data, index=[100, 200, 300], columns=['z', 'y', 'x'])  :  we can change the rows labels by the (index) attribute, and change the columns labels by the (columns) attribute

```
     z    y  x
100  100  2  1
200  100  4  2
300  100  8  3
```

we can provide another form of data as a list of lists too be passed later to pd

```
data2 = np.array( [["China",1393000000,"Beijing"],
 	["united States",328200000,"Washington"],
 	["Russia",144500000,"Moscow"],
 	["Japan",126500000,"Tokyo"],
 	["India",1353000000,"New Delhi"],
 	["Germany",83020000,"Berlin"]])

df = pd.DataFrame(data2, index=['1','2','3','4','5','6'],columns=['a','b','c'])
```
```
 	a			b			c
1	China			1393000000		Beijing
2	united States	328200000		Washington
3	Russia			144500000		Moscow
4	Japan			126500000		Tokyo
5	India			1353000000		New Delhi
6	Germany		83020000		Berlin
```

```
myData = { 
 'name': ['Xavier', 'Ann', 'Jana', 'Yi', 'Robin', 'Amal', 'Nori'],
 'city': ['Mexico City', 'Toronto', 'Prague', 'Shanghai','Manchester', 'Cairo', 'Osaka'],
 'age': [41, 28, 33, 34, 38, 31, 37],
 'py-score': [88.0, 79.0, 81.0, 80.0, 68.0, 61.0, 84.0]  }  

rowLabels = [101, 102, 103, 104, 105, 106, 107]  

myArray = pd.DataFrame( data=myData, index=rowLabels ) 

```
```
	name	city	age	py-score
101	Xavier	Mexico City	41	88.0
102	Ann	Toronto	28	79.0
103	Jana	Prague	33	81.0
104	Yi	Shanghai	34	80.0
105	Robin	Manchester	38	68.0
106	Amal	Cairo	31	61.0
107	Nori	Osaka	37	84.0
```

### Extracting Data

    myArray.head(n=2) 
    
it will bring the first two rows 

```
	name	city	age	py-score
101	Xavier	Mexico City	41	88.0
102	Ann	Toronto	28	79.0
```

    myArray.tail(n=2) 
    
it will bring the last two rows

```
	name	city	age	py-score
106	Amal	Cairo	31	61.0
107	Nori	Osaka	37	84.0
```

    myArray.index 
    
it will return the indexes(rows) as a list

Int64Index([101, 102, 103, 104, 105, 106, 107], dtype='int64')

    myArray.columns 
    
it will return the columns as a list

Index(['name', 'city', 'age', 'py-score'], dtype='object')

    myArray.values() 

it will return the columns as a list

    myCities = myArray[‘city’] 
    
return the column under the label (city) 

```
101    Mexico City
102        Toronto
103         Prague
104       Shanghai
105     Manchester
106          Cairo
107          Osaka
Name: city, dtype: object
```

    myCities = myArray.city 
    
return the column under the label (city)

```
101    Mexico City
102        Toronto
103         Prague
104       Shanghai
105     Manchester
106          Cairo
107          Osaka
Name: city, dtype: object
```

    myCities[102] 
    
it will reach the corresponding cell  ‘Toronto’

    myArray[[ ‘city’, ‘age’ ]] 
    
return the specified columns

```
	city	age
101	Mexico City	41
102	Toronto	28
103	Prague	33
104	Shanghai	49
105	Manchester	38
106	Cairo	31
107	Osaka	37
```

### Extracting by (loc)

(loc) used to extract slices of the data by passing the indexes we want at first, then as an optional parameter, we pass the labels of the columns we want
the needed parameters : loc['IndexLabel', 'ColumnName']
its borders are both inclusive, the range [5, 10] means numbers from 5 to 10

•	myCities = myArray[‘city’]
myCities.loc[103] : it will return a row that has index of 103 

•	myArray.loc[ 101:105 ] : it will return rows from 101 to 105

•	myArray.loc[ :105 ] : it will return the rows from the beginning to 104

•	myArray.loc[ 104: ] : it will return the rows from 104 to the end

•	myArray.loc[ : ] : returns all rows 

•	myArray.loc[ : , ['name', 'city'] ] : it will return all rows for columns labeled under (name) and (city)

•	myArray.loc[myArray.age < 35] : return all the rows where the corresponding attribute (age) is less than 35

•	myArray.loc[myArray.city.isin([“Cairo”, “Osaka”])] : return all the rows where its corresponding attribute (city) is the list [“Cairo”, “Osaka”]

•	myArray.loc[myArray.city.isin([“Cairo”, “Osaka”]), [“city”, “age”]] : return all the rows where its corresponding attribute (city) is the list [“Cairo”, “Osaka”] for just the columns (city, age)

•	myArray.loc[myArray.index.isin(range(102, 107))] : return all the rows where its corresponding indexes is within the specified range


### Extracting by (iloc)

(iloc) is used to get the list by its index, it will return several cells by the indexes for rows and columns
its lower border is inclusive but the upper border is exclusive, the range [5, 10] means numbers from 5 to 9
•	myArray.iloc[2] : returns the third row
•	myArray[“city”].iloc[2] : returns the third cell of that column (city)
•	myArray.iloc[2:5] : returns the rows (2, 3, 4)
•	myArray.iloc[:] : returns all the rows
•	myArray.iloc[2:] : returns rows from 2 to the end
•	myArray.iloc[:5] : returns rows from the beginning to the row 4

•	myArray.iloc[ 101:105, [0, 1] ] : rows from 101 to 105 and columns (0) and (1) :
```
        name        city
101    Ann     Toronto
102   Jana      Prague
103     Yi    Shanghai
104  Robin  Manchester
105   Amal       Cairo
```

•	myArray.iloc[ 1:6:2 , 0 ] : it will return the rows 1 through 6 with a step of 2 between each two, and the column indexed by (0) :
```
101     Ann
103      Yi
105    Amal
Name: name, dtype: object
```
•	myArray.iloc[ slice(1, 6, 2), 0 ] : rows 1 through 6 with a step of 2
•	myArray.iloc[ np.s_[1:6:2], 0 ] : rows 1 through 6 with a step of 2
•	myArray.iloc[ pd.IndexSlice[1:6:2], 0 ] : rows 1 through 6 with a step of 2

	Extracting by (at & iat)
•	myArray.at[ 102, 'name' ] : it will return the cell at row labeled by (102) and the column labeled by (name) :
‘Jana’
•	myArray.iat[ 2, 0 ] : it will return the cell at row indexed by (2) and the column indexed by (0) :
‘Jana’



## Modifying the Data in the Dataframe

### Modifying a single cell

•	myArray[ 3, 2 ] = 49 : this will change the value at the cell indexed by (3, 2) to 49

### Modifying columns

•	myArray.loc[ :104, 'py-score' ] = [40, 50, 60, 70] : it will modify the cells under (py-score) that corresponding with rows from 101 to 104 to be [40, 50, 60, 70] 

•	myArray.loc[ 105: , 'py-score'] = 0 : it will modify the cells under (py-score) and rows from 105 to the end to be zeros

•	myArray.loc( : , -1 ) = np.array( [ 88.0, 79.0, 81.0, 80.0, 68.0, 61.0, 84.0 ] ) : it will modify all the rows (because we put colons ( : )  ) and the last column ( because we put -1 ) to be the entered array 

### Adding rows

•	john = pd.Series(data=[ 'John', 'Boston', 34, 79], index= myArray.columns, name=108) 

myArray = myArray.append( john )  :  this will add the vector (john) to the array (myArray) with the label (108)

### Adding columns

•	myArray[ 'js-score' ] = np.array( [ 71.0, 95.0, 88.0, 79.0, 91.0, 91.0, 80.0 ] ) : this will add a new column labelled (js-score)

•	myArray.insert( loc=3, column='django-score', 
value=np.array([86.0, 81.0, 78.0, 88.0, 74.0, 70.0, 81.0])) : it will insert a new column with at the label index (3) and shift the other columns

### Deleting rows

•	myArray.drop( labels=[108] ) : this will delete the entire row labelled under 108

### Deleting columns
•	del myArray[“django-score”] : it will delete the entire column (django-score)

•	myArray = myArray.drop(labels= ‘age’, axis=1) : it will delete the column (age) 
(axis=1) means that we want to delete a column, we can use axis=0 to drop rows


## Applying arithmetic operations 

•	myArray[py-score] + myArray[js-score] : it will add each value from (py-score) to its corresponding value from (js-score) and return a list of resultant cells
(that also works for every other operation:  - , * , ** , / )

•	myArray[py-score] / 100 : it will divide each element of the column by 100
•	myArray.py-score / 100 : it will divide each element of the column by 100


## Sorting data
•	myArray.sort_values( by='js-score', ascending=False ) : it will sort the rows descending according to the values of the column (js-score)


## Data Filtration
•	myFilter = myArray['django-score']  >=  80
it will return a vector which each element of it is “True” if it is larger or equal than (80), and “False” otherwise
```
101     True
102     True
103    False
104     True
105    False
106    False
107     True
Name: django-score, dtype: bool
```
•	myArray[myFilter] : it applys the filter on the Dataframe, and only return the rows which their elements in (myFilter) has the value ”True” :
```
          name      city            py-score    js-score 
101  Xavier  Mexico City      88.0         71.0   
102     Ann      Toronto         79.0          95.0   
104       Yi     Shanghai           80.0         79.0   
107    Nori        Osaka           84.0          80.0   
```
•	if we have a dataframe full of numbers 
arr = np.random.rand(4, 4) * 100
myArray = pd.DataFrame(arr,['a','b','c','d'],['u','v','w','x'])
```
	u		v		w		x	
a	9.748720	50.209416	91.438126	16.700044	
b	76.847081	75.085400	24.161663	25.989817	
c	30.736410	80.090946	59.642300	32.778789	
d	63.624428	56.663255	83.552941	46.308182	
```
•	myArray[ myArray > 50  ] : apply the conditional array on the original one and return only the value corresponding with (True) and replace the ones with (False) by (NaN)
```
 	u		v		w		x	
a	NaN		50.209416	91.438126	NaN	
b	76.847081	75.085400	NaN		NaN	
c	NaN		80.090946	59.642300	NaN	
d	63.624428	56.663255	83.552941	NaN	
```
•	myArray [myArray ['u'] > 50] : return the rows where values of the column ‘u’ satisfy the condition 
```
	u		v		w		x		
b	76.847081	75.085400	24.161663	25.989817	
d	63.624428	56.663255	83.552941	46.308182	
```
•	myArray [(myArray ['z']>50) | (myArray ['w']>50)] : we can cascade multiple conditions using AND ( & ) , OR ( | )


