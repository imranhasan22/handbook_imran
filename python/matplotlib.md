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
```
plt.scatter(x, y, color = '#88c999')
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