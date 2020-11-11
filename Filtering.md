# Filtering and Downsampling
> By Sven Leach (*last updated: not yet*)

### Background
One of the major challenges of brain science is that measurements are contaminated by *noise* and *artifacts*. These may include environmental noise (e.g. electrical line noise), instrumental noise, or physiological noise (e.g. signal sources within the body that are not of interest, such as heart beat). **Filters** are commonly used to reduce noise and improve data quality. This is possible in case the noise occupies a spectral region other than your signal of interest. Then the filter can attenuate the noise in the data and leaves the signal of interest (i.e. brain signal) "untouched" (in reality, the signal of interest is also affected by the filter, but less so).

## Filter applications
For example, a direct current (DC) component or slow fluctuation may be removed with a **high-pass filter** (a high-pass filter leaves high frequencies in the signal, they "pass" the filter), unwanted high-frequency components may be removed by smoothing the data with a **low-pass filter** (low frequencies are left in the signal, they "pass" the filter), and power line components may be attenuated by a **notch filter** at 50 or 60 Hz (only a specified frequency range is filtered out).

Show plots with DC offset, lines noise and high-frequency components. Before and after...

Show plots visualizing HP LP notch and BP filter ...

## What Is a Filter?
For many of us, a filter is "a thing that modifies the spectral content of a signal." Mathematically, a filter is an operation that produces each sample of the output waveform y as a weighted sum of several samples of the input waveform x. This operation is called convolution and wonderfully explained in this youtube video https://www.youtube.com/watch?v=9Hk-RAIzOaw.

The exact way of how a filter "changes" the data is defined by it's **impulse response function** (that is, the output in response to an impulse). Some filters may smooth the input waveform, others
may enhance fast oscillations. There are numerous different filter types (such as ...) and different ways to implement those filters into software (such as ...). Respectively, there is considerable body of theory, methods, and lore on how best to design and implement a filter for the needs of an application.

Show impulse and impulse response function ...

## Some terminology
An important goal of neuroscience is to determine causal relations, for example, between a stimulus
and brain activity, or between one brain event and another. If a filter is *causal*, the filter output depends only on past and present samples of the input. If a filter is *acausal*, the filter output also depends on future samples of the input. 

Important in our line of research is at what phase of a slow wave a tone was presented. Some filters introduce a phase shift which is different for each frequency in the signal. In that case, when we analyze the data with a phase shift, we would conclude that tones were presented at a wrong phase of the wave. This is why zero-phase filters are especially important to us. They change the phase of the signal linearly (or evenly) for all frequencies, so that it can be easily corrected. In Matlab.. firfilt .. filtilt..

FIR IIR filters...



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