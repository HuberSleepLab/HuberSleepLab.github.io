# Matlab
> By Sophia Snipes (*Last updated: October 2020*)

[MATLAB](https://mathworks.com/products/matlab.html) is the programming language used in this tutorial. You really should know it before getting to this point, but in case it helps, here are a few introductory concepts. The pipeline we use could theoretically be applied in any other programming language, but MATLAB is particularly appropriate because of the heavy use of matrices.



## 1) Download MATLAB
Depending on your institution, there's different ways to download it. So ask someone or google it.

Once you have it, this is the interface:
![](images/MATLAB/interface.PNG)

### Key Concepts
- **Console**: This is that box in the bottom with `>>`, where you can "talk" directly to MATLAB, and it answers. This is good as a quick calculator, or a fast way to run functions, and in general is used a lot when writing new scripts.
- **Scripts**: Scripts are "example.m" files that you write in the editor (see picture), and run by pressing that green triangle in the "Editor" tab of the menu bar on top. You can also run them by typing the name of the file in the console.
- Current location: matlab will only consider running scripts in the folder in which you are currently located, or in specifically designated paths. You can see which files these are in the "Current Folder" panel on the left.
- **Workspace**: Here (rightmost panel) you can see all the variables you've created and MATLAB is currently holding in memory.



## 2) Syntax
Here concepts are progressively built on, but if you see in the example code the use of a symbol you're not familiar with, the last section of 2) is a summary of all the special symbols and their meaning.

### Basic math operations
You can use MATLAB as a caluclator by just writing `3+5` in the console. It will then spit out the result. Unlike a calculator though, you can have variables:

```
x = 3
a = 2
b = 5

y = x^2 + a*x + b
```

If you write this in a script, it's then easy to change just one variable (x) and re-run all the lines every time (this is why we use scripts). 

Simple math operations include:
- `+`: sum
- `-`: subtraction
- `*`: multiplication
- `^`: raise to the power (e.g. `10^2`)
- `/`: divide
- `()`: only round parentheses to indicate which math operations to do first

### Variables
Variables are placeholders (think of them like x and y in math equations) used in scripts, so that you "declare" the variable once at the beginning, and then can keep using that same number over and over again without having to re-write it every time. 
Often times, you actually want to modify it as you go along:
```
A = 1;
A = A+1;
A = A*100;
A = [A, A];
```

Variable names cannot include any characters except letters and numbers, and the first character must always be a letter. Variables are CaSeseNsitive, so be careful. 

> N.B. matlab has things that have special names; if you name a variable with that name, you overwrite it. Classic example, `i` indicates the imaginary number (square root of -1), so don't name any variable i. Same for `pi`.


### Batch math operations
Also unlike calculators, you can apply a formula to a whole list of numbers like so:
```
C = [23 19 35 22 27 5 2]

F = (9/5)*C + 32
```
And you convert an **array** of temperatures from Celcius into Farenheit!

You can also make an array of numbers from n to m like so: `C = 1:5`
Or, if you want to specify the interval, like so: `C = 1:.25:5`
Or if you want to go backwards: `C = 5:-1:1` 


### Matrices
If you just have one row of numbers, its called an "array". If you have multiple rows and multiple columns, its a matrix. To create a matrix, just do this:
```
M = [1 2 3; 4 5 6; 7 8 9]
N = [1,2,3; 4,5,6; 7,8,9];
O = [1 2 3
4 5 6
7 8 9];

P = [M; N; O];

Q = [1, 2 3; 4:6; P]; % you can even mix variables and numbers

```
The above matrices are 2 dimentional, but it is also possible to be 3 or n dimentional. 


### Matrix operations
Just like with variables with 1 element, you can do math operations on matrices. You have to be a bit more careful here because the dimentions (number of rows and number of columns) must agree, depending on the operation. Applying an operation on the wrong dimention is a common source of error messages.

```
A = [1 1 1; 2 2 2];
B = [0, 5];
C = 3;
A = A*C; % multiplies every element in A with 3
A = A'; % flips rows and columns
A = A.*B; % multiplies every row (now 2 elements) with B

A = A*B'; % fancy matrix multiplication called a "dot product"

```


### Logical operators
Other than numbers, you can have a variable (or array, or matrix) that is just `true` or `false`. These are also represented as 1 and 0, respectively, and are called **booleans**.
> N.B. "true" and "false" get automatically symbolized as 1 and 0 by MATLAB, but 1 and 0 don't automatically mean true and false for MATLAB, so if something doesn't work, try `logical([1 0 0 1])` around your desired boolean.

Just like with addition, you can combine logical operators with `&` (and) or `|` (or).

```
T = true;
F = false;

T1 = T | F; % this is true
F1 = T & F; % this is false

T2 = (T | F) & (T | T);
```

You can query if something is equal `A==B`, not equal `A~=B`, greater `A>B`, less than `A<B`, or greater or equal to `A<=B` ... and the outcome will be a boolean.

These can all be combined: `(A<B) | (B==0 & A>5)`;

### Strings
All the above (a.k.a. math) uses just numbers. But because MATLAB is a real programming language, you can also do things with letters, called **strings**, which is important when you want to type a message when something is done, or looking for filenames, etc. You can also merge strings like you would merge arrays.

```
Operator = 'Sophia';
Message = ', I finished!';

Display = [Operator, Message]
```

Strings like the ones above are technically "string arrays", because each character is like a different number in a matrix. You can unite all the things inside a string into 1 element by using `"double quotes"`.


### Cells
You cannot have a matrix or array with both numbers and strings. To have one variable holding both, you need a **cell array**, indicated with `{}`.

```
Cell = {'Hanna', 'Sophia', 'Mark'; 2, 4, 5};

```


### Indexing
Sometimes, you don't want everything contained in a variable. So you "index" a subsection by selecting which numbered element in the array that you want. Indexing can either be done with just one number `A(4)` (if it's one array it takes the 4th element, if its a matrix, it scans each column until it reaches the 4th element) or with a list:

```
A = [1:100; 51:150];

B = A(2, 40:45); % sele

Indx = 1:5;

B2 = A(1, Indx);

A(2, Indx) = 10:15; % you can index an already existing variable to assign new content to those locations

```

#### Boolean indexing
Indexing is best done with booleans, by having an array of booleans the same size as that dimention, and it will select only the spots corresponding to "true". The best way to get such an array is through a boolean operation.

```
A = [1, 2, -5, 3, 6; -2, -3, 2];
Indx = A < 0;
A(Indx) = 0; % assign 0 to all negative numbers in A
```


### Special symbols
These are symbols already used above but not specifically addressed. 

- **Space**: spaces in between things are mandatory between two variables, and are entirely optional between operators (`+/^`) and between variables and operators
- `=`: this symbol is ONLY for establishing the content of a new variable. Whatever is on the left is a variable name, whatever is on the right is the thing you are putting in it
- **New line**: you need a new line whenever you have established a new variable (or executing a function, we'll get to that later). 
- `;` indicates that what comes after is a "new line", so you could write a series of variables in one line like so `a=3;b=2;z=5`, but this is best avoided. It also seperates new rows in a matrix. If you run any line of code *without* this at the end, it will print it in the console; this get's annoying fast, so most lines of code will end with a semicolon
- `,`: this can only be used to either list elements in the same row when creating a matrix/array, or to seperate the dimentions used in indexing a multidimentional matrix (`A(2,5)`)
- `[]`: square brackets are used to make lists or matrices. They can also unite arrays and matrices, but it's important that the number of elements match (e.g. you can't add a 3 row element to a 4 x 5 matrix)
- `%`: this and everything after indicates a comment, it is not treated as code. Commenting code is super important so you know what it does



#### Data types

### 3) Scripts & Functions

### 4) Plotting

### 3) Toolboxes for EEG
