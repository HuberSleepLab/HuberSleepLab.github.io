# Filtering and Downsampling
> By Sven Leach (*last updated: not yet*)

### Background
One of the major challenges of brain science is that measurements are contaminated by *noise* and *artifacts*. These may include environmental noise (e.g. electrical line noise), instrumental noise, or physiological noise (e.g. signal sources within the body that are not of interest, such as heart beat). **Filters** are commonly used to reduce noise and improve data quality. This is possible in case the noise occupies a spectral region other than your signal of interest. Then the filter can attenuate the noise in the data and leaves the signal of interest (i.e. brain signal) "untouched" (in reality, the signal of interest is also affected by the filter, but less so).

### Example Intro
We just love the **2-process model** by *Alexander Borberly*:
![](images/intro/2processmodel.png)

I'm not going to bother explaining it, so just look [here](https://en.wikipedia.org/wiki/Sleep).

If you can't do something fancy in Markdown, you can just write in HTML: <a href="http://google.com/" target="_blank">Just Google It!</a>

But! What if someone here already presents it? Well I can just link it like [so](https://hubersleeplab.github.io/README2.html).
In case you didn't notice, there's a cute little menu on the left, but it will only write up to three `###` pound signs.

#### Subpoint to the intro
- Bulleted
- List

1. Numbered
2. List

#### Example Code
```m
Var1 = 3;
Var2 = 5;

Result = Var1*Var2;
```


Now just replace the numbers in `Var1` and you can do math!

### Example data

If you're really fancy, you can add a table:

Row Names | Data
----------|----- 
First row | Lots of data
Second row | More data

```m

A = 3;
B = [1 2 3];
F = plot(B,A);

close all
```

The m makes it matlab colored