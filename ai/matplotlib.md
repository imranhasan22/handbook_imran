Matplotlib is a low level graph plotting library in python that serves as a visualization utility.

# Pyplot
Most of the Matplotlib utilities lies under the `pyplot` submodule, and are usually imported under the `plt` alias
```
import matplotlib.pyplot as plt
```

# Ploting
`plot()` function is used to draw points in a diagram. By default it draw a line from point to point.
- Parameter 1 is an array containing the points on the x-axis.
- Parameter 2 is an array containing the points on the y-axis.
### Plotting x and y points
```
xpoints = np.array([1, 8])
ypoints = np.array([3, 10])

plt.plot(xpoints, ypoints)
plt.show()
```
### Plotting Without Line
To plot only the markers, you can use shortcut string notation parameter 'o', which means 'rings'.
```
plt.plot(xpoints, ypoints, 'o')
```
### Multiple Points
You can plot as many points as you like, just make sure you have the same number of points in both axis.
```
xpoints = np.array([1, 2, 6, 8])
ypoints = np.array([3, 8, 1, 10])
```

### Default X Points
If we do not specify the points on the x-axis, they will get the default values 0, 1, 2, 3 etc., depending on the length of the y-points.

# Markers
You can use the keyword argument marker to emphasize each point with a specified marker
```
plt.plot(xpoints, ypoints, marker = '*')
```
### Format Strings
You can also use the shortcut string notation parameter to specify the marker. This parameter is also called fmt, and is written with this syntax: `marker|line|color`
```
plt.plot(xpoints,ypoints, 'o:r')
```
[Marker | Line | Color](https://www.w3schools.com/python/matplotlib_markers.asp)

- `ms` argument is used to set the size
- `mec` argument is used to set the color of marker border
- `mfc` argument is used to set the color of marker
```
plt.plot(xpoints, ypoints, marker = 'o', ms = 20, mec = '#4CAF50', mfc = '#4CAF50')
```

# Linestyle
- `ls` argument is used to style the plotted line. `dotted` can be written as `:`, `dashed` can be written as `--`.
- `c` argument set the color of the line
- `lw` argument set the width of the line
```
plt.plot(xpoints,ypoints, ls = 'dotted', c='r',lw='10')
```

### Multiple Lines
You can plot as many lines as you like by simply adding more `plt.plot()` functions
```
plt.plot(first)
plt.plot(second)
```
You can also plot many lines by adding the points for the x- and y-axis for each line in the same plt.plot() function.
```
plt.plot(x1, y1, x2, y2)
```

# Labels & Title
### Label
`xlabel()` and `ylabel()` functions to set a label for the x- and y-axis.
```
plt.plot(x, y)
plt.xlabel("Average Pulse")
plt.ylabel("Calorie Burnage")
```
### Title
`title()` function to set a title for the plot
```
plt.title("Sports Watch Data")
```

- `fontdict` argument is used to set the font properties
- `loc` argument is used to set the position. Legal values are `left`, `right`, `center`.
```
font = {'family':'serif','color':'darkred','size':15}
plt.title("Sports Watch Data", fontdict = font, loc='left')
```

# Grid Line
`grid()` functions is use to set the grid line to the plot
```
plt.grid()
```
- `axis` argument is use to specify which grid lines to display. Legal values are `x`, `y`, `both`.
- you can also set line properties of the grid like `grid(color = 'color', linestyle = 'linestyle', linewidth = number)`
```
plt.grid(axis='x',color = 'green', linestyle = '--', linewidth = 0.5)
```

# Subplot
`subplot()` is use to draw multiple plots in one figure. It takes three arguments that describes the layout of the figure.
 - first argument represent the number of row
 - second argument represent the number of column
 - third argument represent the index of current plot
- `title()` set the title to each plot
- `suptitle()` set the title to entire figure
```
#plot 1:
x = np.array([0, 1, 2, 3])
y = np.array([3, 8, 1, 10])
plt.subplot(1, 2, 1)
plt.plot(x,y)
plt.title("SALES")

#plot 2:
x = np.array([0, 1, 2, 3])
y = np.array([10, 20, 30, 40])
plt.subplot(1, 2, 2)
plt.plot(x,y)
plt.title("INCOME")

plt.suptitle("MY SHOP")
```

# Scatter
`scatter()` is use to draw scatter plot. It plots one dot for each observation. It needs two arrays of the same length, one for the values of the x-axis, and one for values on the y-axis
```
plt.scatter(x, y)
```

### Compare Plots
```
plt.scatter(x1, y1)
plt.scatter(x2, y2)
```

- `c` argument set the color. You can even set a specific color for each dot by using an array of colors as value for the c argument
- `s` argument set the size of the dots. just like colors, make sure the array for sizes has the same length as the arrays for the x- and y-axis
- `alpha` argument is use to adjust the transparency of the dots. Just like colors, make sure the array for sizes has the same length as the arrays for the x- and y-axis.
```
# plt.scatter(x, y, color = '#88c999')
sizes = np.array([20,50,100,200,500,1000,60,90,10,300,600,800,75])
colors = np.array(["red","green","blue","yellow","pink","black","orange","purple","beige","brown","gray","cyan","magenta"])
plt.scatter(x, y, s=sizes,c=colors, alpha=0.5)
```
### ColorMap
The Matplotlib module has a number of available colormaps.

A colormap is like a list of colors, where each color has a value that ranges from 0 to 100.

Here is an example of a colormap: 
![ColorMap](https://www.w3schools.com/python/img_colorbar.png)

This colormap is called 'viridis' and as you can see it ranges from 0, which is a purple color, up to 100, which is a yellow color.
[View Available ColorMap](https://www.w3schools.com/python/matplotlib_scatter.asp)

You can specify the colormap with the keyword argument cmap with the value of the colormap, in this case 'viridis' which is one of the built-in colormaps available in Matplotlib.

In addition you have to create an array with values (from 0 to 100), one value for each point in the scatter plot:
```
colors = np.array([0, 10, 20, 30, 40, 45, 50, 55, 60, 70, 80, 90, 100])
plt.scatter(x, y, c=colors, cmap='viridis')
```
you can include the colormap in drawing by including `plt.colorbar()`
```
plt.scatter(x, y, c=colors, cmap='viridis')
plt.colorbar()
```

# Bars
`bar()` method is use to create bar graphs. The categories and their values represented by the first and second argument.
```
categories = ["APPLES", "BANANAS"]
values = [400, 350]
plt.bar(categories, values)
```
`barh()` displayed bars horizontally
- `color` argument is use to set the color
- `width` argument set the width, for horizontal bar use `height`
```
plt.bar(x, y, color = "#4CAF50", width=0.1)
```

# Histograms
A histogram is a graph showing frequency distributions. It is a graph showing the number of observations within each given interval.

`hist()` function is used to create histograms

```
x = np.random.normal(170, 10, 250)
plt.hist(x)
```

# Pie Charts
`pie()` is used to draw pie chart
```
x = np.array([35, 25, 25, 15])
plt.pie(x)
```
By default the plotting of the first wedge starts from the x-axis and moves counterclockwise

- `labels` argument is used to set label
- `startangle` argument define the starting angle in degrees. ![Angle Chart](https://www.w3schools.com/python/img_matplotlib_pie_angles.png)
- `explode` argument allow to stand out the wedges. It must be an array with one value for each wedge. Each value represents how far from the center each wedge is displayed.
- `shadow` argument set shadow to each edge
- `color` argument set color to each wedge
- `legend()` function is use to display a list of explaination for each wedge
     - `title` argument set a header to the legend
```
x = np.array([35, 25, 25, 15])
mylabels = ["Apples", "Bananas", "Cherries", "Dates"]
myexplode = [0.2, 0, 0, 0]
mycolors = ["black", "hotpink", "b", "#4CAF50"]
plt.pie(x, labels = mylabels,startangle = 90,explode=myexplode, shadow=True,colors=myColors)
plt.legend(title = "Four Fruits:")
```