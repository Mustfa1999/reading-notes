# Reading: Class 14

> [Back to the main](./README.md)

---

## Importing classes

    import matplotlib.pyplot as plt
    import pandas as pd
    import numpy as np

---

## Plotting by matplotlib

    y = [1, 2, 3, 4]

```
plt.plot(y) : if we pass only one argument (array y), it will represent the y-axis while the x-axis will be represented as [0, 1, 2, 3, 4, …] until it fill the y-points 
```
NOTE : plots won’t be displayed until we use the order plt.show() which will show the latest figure had been plotted

    plt.show()

display the figure or the plot

	x, y = [1,2,3,4], [10,20,30,40]
    plt.plot(x,y) 
    
if we pass two arguments, the first one will represent the x-axis and the second will represent the y-axis

NOTE : the length of both x and y must be equal 

	plt.plot(x, y, 'o-') : do the plot with a bigger dots
	plt.plot(x, y, '.-') : do the plot with a smaller dots
	plt.plot(x, y, '^-') : change the dots’ style to be triangles 
	plt.plot(x, y, '--') : change the line style to be dashes ( - - - - - )

	plt.plot(x, y, 'ro-') : change the colour to Red and do the bigger dots (we can add a letter to any one of them to colour it: r: Red, g: Green, b: Blue, y:Yellow, w: White, k: Black, m: purple)
	plt.plot(x, y, 'ro') : if we do the same but without the dash ( - ), it will plot the dots without a connecting line  

	plt.plot(x, y, 'cs') : change the dots to squares 

we can plot multiple functions on the same figure :

```
x1, x2, x3 = [1,2,3,4,5], [2,4,6,8,10], [10, 20, 30, 40, 50]
y1 = [2,4,6,8,10]
plt.plot(x1,y1)
plt.plot(x2,y1)
plt.plot(x3,y1)
```

we can add some labels (legends) to mark the graphs
NOTE : we have to use the command plt.legend() to show the marks

```
x1, x2, x3 = [1,2,3,4,5], [2,4,6,8,10], [10, 20, 30, 40, 50]
y1 = [2,4,6,8,10]
plt.plot(x1,y1, label= 'line 1')
plt.plot(x2,y1, label= 'line 2')
plt.plot(x3,y1, label= 'line 3')
plt.legend()
 ```

	plt.plot(x1,y1, ’-g’) : it will change the line to green solid

we can use the following styles: 

we can create a bar plot:
```
labels = ['G1', 'G2', 'G3', 'G4', 'G5']
y = [20, 35, 30, 27, 35]
plt.bar(labels, y) : create a categorical bar that has the labels on its x-axis and the numbers on the y-axis
 ```

	plt.barh(labels, y) : create a horizontal bar

we can create split categories for 

```
labels = ['G1', 'G2', 'G3', 'G4', 'G5']
y1 = [20, 35, 30, 27, 35]
y2 = [25, 32, 34, 20, 25]
plt.bar(labels, y1, color='b', label='men')
plt.bar(labels, y2, color='r', label='women', bottom=y1)
plt.legend()
``` 


we can do a pie chart which take only numbers as input values (only integers or floats) and divide the pie according to the percentage that each number represent from the total sum of all numbers (values)
NOTE : the total sum of numbers doesn’t necessarily equal 100, it can be any number and the pie will be distributed as percentages NOT values 

```
values = np.array([10,20,30,15,25])
Labels = ["G1", "G2", "G3", "G4", "G5"]
plt.pie(values, labels= Labels)
 ```

if we want to highlight one or more pieces of the pie, we pass a list of zeros for the non-highlighted pieces, and a particular number for the desired distance from the pie for the highlighted pieces, to the argument explode 


    highlighted = [0, 0, 0, 0.3, 0]
    plt.pie(values, labels = Labels, explode= highlighted)
 
we can display images from the local disk
```
import matplotlib.image as mpimg
img = mpimg.imread( r”full path\image.jpg” )
plt.imshow(img)
```

Subplots: plotting multiple plots at the same figure 
```
plt.subplot(3,2,5) : append the next plot we make to a group of plots made of 3 rows and 2 columns (6 plots or cells) and put it on the index 5
1	2
3	4
5	6

plt.title(“resistance”) : put a title for the figure
plt.xlabel(“time”) : put a label on the x-axis
plt.ylabel(“voltage”) : put a label on the y-axis
```
we have to set the subplot by the function (subplot), then add what we want like labels and colours, and finally show the whole plot:
```
x, y = [1,2,3,4], [10,20,30,40]
plt.subplot(1, 2, 1)
plt.plot(x,y)
plt.title("Line plot 1") : add a title for the subplot 1

x2, y2 = [1,2,3,4], [10,20,30,40]
plt.subplot(1, 2, 2)
plt.plot(x2,y2)
plt.title("Line plot 2") : add a title for the subplot 2

plt.suptitle("Multiple plots") : add a title for the whole plot 
plt.show()
```

we can make a main plot (axes1) then insert another one above it :
```
fig = plt.figure() : create a new figure 
x, y = [1,2,3,4], [10,20,30,40]
axes1 = fig.add_axes([0.1, 0.1, 0.8, 0.8]) : add the main plot to the figure (start at the point (0.1,0.1) as the left bottom corner, and the point (0.8,0.8) as the right top corner)
axes2 = fig.add_axes([0.2, 0.5, 0.3, 0.2]) : add the inserted plot to the figure 

axes1.plot(x, y, 'b') : plot the main axes 
axes1.set_xlabel('X_label_axes2') : add a label on the x-axis 
axes1.set_ylabel('Y_label_axes2') : add a label on the y-axis
axes1.set_title('Axes 1 Title') : add a title to the figure 
axes2.plot(y, x, 'r') : plot the inserted axes
```

if we have the following data:
```
t = np.arange(0, 2, 0.01)
s = 1 + np.sin(2 * np.pi * t)

fig, ax = plt.subplots() : create a subplot with the name of (ax)
fig, (ax1, ax2) = plt.subplots(2, 1) : create a figure with two subplots, the figure will have 2 rows and 1 column 
ax.plot(t, s) : do the actual plot (ax) with the x and y values as s and t 
fig.suptitle('A tale of 2 subplots') : label the whole figure 
ax.set(xlabel='time (s)', ylabel='voltage (mV)', title='sin waveform') : label the plot
ax.grid() : add ax to the grid
fig.savefig("test.png") : save the figure as a picture 
```

## Plotting pandas files 

if we have a pandas data frame, we can plot and display it :
```
myDataFrame.plot() : it will plot the data frame only if it has two columns (one for indexes and the other for data)
myDataFrame.show() : it will display the graph after plotting it

myDataFrame.plot().get_figure().savefig( ' My Data Frame plot.png' ) : it will create the plot and saves it as a file called (My Data Frame plot.png) in the current directory

myDataFrame.loc[ : , ['col1', 'col2'] ].plot.hist(bins=5, alpha=0.4) : it will extract the two columns from the data frame labelled by (col1) and (clo2), and visualize it as a histogram with step of (5) in the x-axis and step of (0.4) on the y-axis 
```
