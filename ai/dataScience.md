# Statistics

The tabular and graphical approaches to summarizing raw data are useful and effective in technical reports and documents, as well as visual aids when presentations must be made to an audience. Nevertheless, numerical descriptions in the form of indices or values are often preferred for summarizing a set of data.

When we are interested in describing the entire distribution of some observations, there are two types of indices that are especially useful. These are the __measures of central tendency__ and __measures of variability__.

Measures of central tendency are numerical indices that attempt to answer the question: what is the typical value of the center, middle, representative, or the most typical of a set?

Measures of variability are numbers that attempt to answer questions like: how different from each other are the observations in the distribution? How do the observations in the distribution spread out around the typical value?

# Measures of Central Tendency

The purpose of an average is to represent the distribution and also to provide a basis of comparison with other distributions of a similar nature.

- Mean
- Median
- Mode

## Arithmetic Mean

The arithmetic mean doesn't necessarily have to be equal to any of the given values.

__Formula:__

$$ \bar{X} = \frac{\sum_{i=1}^{n} f_ix_i}{n} $$

__Code:__
```
speed = [99,86,87,88,111,86,103,87,94,78,77,85,86]
x = numpy.mean(speed)
```

__Ungrouped Data:__ x<sub>i</sub> refers to the ith value and f<sub>i</sub> refers to the frequency of the ith value.

__Grouped Data:__ x<sub>i</sub> refers to the mid-value of the ith range and f<sub>i</sub> refers to the frequency of the ith range.