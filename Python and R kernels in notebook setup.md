# Ubuntu installation of Conda and Jupyter notebooks for using both python and R kernels in notebook

The Jupyter system supports over 100 programming languages (known as kernels). This allows for easy integration of multiple languages in the same notebook. 

Here is  instructions on how to install and set up R to use alongside python in a Jupyter notebook 

Python is a general- purpose programming language which makes it very versatile across many applicatlibraryions. R is a powerful programming language for statistical computing and graphics, widely used among statisticians.

## Installing R using the python kernel

This method allows R and python to work in the same notebook

1. Install python version 3.5 or higher (note this should come default with ubuntu 22.04 and higher)
	-type into terminal `python3` to check version installed
2. Install Anaconda

- Download and install the `.sh` file from https://www.anaconda.com/download/
- In the download folder, right click on the file, click `Properties`, `Permissions`, `Allow Excecution as Program`
- Right click on the file and click `Open in terminal` 
- Install Jupyter by running the following in the terminal (open new terminal)
- 
```
conda install jupyter
```

3. Install R in version 3.2 or higher
In terminal

```
conda install -c r r-essentials
```

4. Installing the library that allows both to coincide in same notebook

If `numpy` and `pandas` packages are not installed for python run the following in the terminal:

```
pip install numpy
```

```
pip install pandas
```

Install `rpy2` library. This is used to call R functions from within Python
```
conda install rpy2 
```

Run the following at the top of your python notebook to load in the library

```
%load_ext rpy2.ipython
```
Now R can be used by typing `%%R` command at the top of a cell in a Jupyter notebook

## Tips in using R in python notebook

1. Installing `R` libraries

To install R packages to your machine run the following line of code in an R cell
```
%%R

install.packages("tidyverse")
```

Then to load the library for use of its functionality (akin to import in python)

```
%%R

library(tidyverse)
```

2. In order to bring variables and data structures defined in the python cells put `-i` in front of the feature name on the line beside `%%R`

Example: 

```
# a python cell
import pandas as pd

df = pd.DataFrame({
    'x_var': [0, 1, 2, 3, 4, 5, 6, 7, 8, 9],
    'y_var': [3, 5, 7, 6, 9, 8, 10, 12, 13, 11]
})
df

x = [1,2,3,5]
```

``` 
%%R -i df -i x # brings the python features into the cell for manipuation with R
```



## Fixing issue of ASCII code charachters on `ggplot` outputs

Installing `fonts-anaconda` and `r-cairo packages` from the terminal (ctrl+t) should resolve the problem.

```
conda install -c anaconda fonts-anaconda
conda install -c r r-cairo
```

