# pandas-intro
This repo contains material for an introductory workshop to the python package pandas.

## Who am I?
* [Data Scientist with the Data Science Institute](https://dsi.virginia.edu/people/peter-alonzi)
* I like to be interrupted with questions! Please jump right in.

## Welcome to the UVA Library
* [Research Data Services](https://data.library.virginia.edu/)
* [Workshop Series](https://data.library.virginia.edu/training/)
 
## Getting Pandas
Mothership: https://pandas.pydata.org/
* conda install pandas
* python3 -m pip install --upgrade pandas

To confirm installation:
* open python and type <pre>import pandas as pd</pre>

## Other Resources
* Python for Data Analysis by McKinney - [get from library](https://search.lib.virginia.edu/catalog/u7444998)
* R for Data Science by Wickham & Grolemund - [free online](https://r4ds.had.co.nz/)

# Goals for Today
1. Get pandas working on your machine
2. Get comfortable with pandas (know what it's all about)
3. Learn how to look up help

## Outline
1. Read data into pandas
2. Manipulate data with pandas
3. Plot/Aggregate/Summarize data with pandas (... and beyond)

## A brief history
* Designed by [Wes McKinney](http://wesmckinney.com/) - launched in 2008
  * https://www.blockchain.com/btc/address/1CUztXcgPYfL1AXuv8FD8XDyPXTc2jcheg
  * https://etherscan.io/address/0x5BC648c302d6aF9D921DE31d0DB2411D26686A4a
* version 0.24.1

## The Data Frame
Using pandas the main tool is the data frame. We use it to hold data and perform operations on the data frame to prepare the data for our end goal. Depending on where you want to go some end functions are also built into the data frame (eg make a histogram). However ...

### Often pandas data frames are confusing to new users. Almost always that is not the fault of the new user.

### Quick survey: Who knows R?

* "Two-dimensional size-mutable, potentially heterogeneous tabular data structure with labeled axes (rows and columns). Arithmetic operations align on both row and column labels. Can be thought of as a dict-like container for Series objects. The primary pandas data structure." [official documentation](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html)
  
The trick is pandas data frames have a lot of capability and a lot of features. But when learning you don't need that. So today we'll take a different approach and focus on the basics.

* Working definition of Data Frame: 
    <pre> An allocation of computer memory that holds data. The format works like a spreadsheet.</pre>
* What a data fame "looks like"
    ![visualized](andre.png)   


# Reading in Data
Our first step is to read data into a pandas data frame. It may be coming from many diferent sources (Eg: a file in storage, an object in memory, the internet, etc.). Here we will look at the example of reading in from a file (.csv).
 
  * read from csv files
    * docs: https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.read_csv.html
      
      don't worry if this looks intimidating, we'll break it down
  * Let's write a program
    <pre>
    # load pandas package
    import pandas as pd
    </pre>
    <pre>
    # read data into data frame
    df =  pd.read_csv("andre.csv")
    </pre>
    
# Manipulating Data

### Taking a look at the data
Your data in a data frame is stored in memory. But as a human we like to see a snippet on the screen. Let's write a program to do just that.

    # load pandas package
    df.head()
    
    # look at end of file
    df.tail()
    
    # look at random sample
    n = 5
    df.sample(n)

* Notice how the whole frame doesn't display. If you want to see the column names you can do this:
<pre>
list(df)
</pre>

### Sort
In this world we call sorting the data set on a column "arranging". To write aprogram to do that we use the function 'sort_values'.
  * [documentation](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.sort_values.html)

  <pre>df.sort_values(by='G', ascending=False)</pre>
    
### Remove rows (with condition)
Sometimes we want to remove some of the data. We call that filtering. Let's try writing code to remove the years before 1976 from this data frame.

<pre>
df = df[ df.Year > 1976 ]
</pre>

Code Breakdown:
* df is a data frame object
* the " [ ... ] " let's us reference or "index" the data frame
* df.Year > 1976 is a boolean that is evaluated for every row



### Create or Remove Columns
* Once you have worked the data set you sometimes want to select a subset of the columns going forward. Again we use the reference tool and provide a list of columns to keep.

    <pre>
    df = df[ ['H','G'] ]
    </pre>


* To create columns we can even get a little fancier and stick calculations right into those new columns.
mutate (aka create new columns). Let's make up batting average.

    <pre>
    df['myBA']=df.H/df.AB
    df[['myBA','BA']]
    </pre>

  To create the new column we just acted like it existed and pandas created it for us on the fly.


# Aggregation / summarization

* To quickly summarize the common statistics of the dataset use describe
  <pre> df.describe() </pre>

* There are also a bunch of pandas functions to do some stats and things
  * df.mean()
  * << google practice time >>

* pandas also facilitates group operations. To explain let's look at a picture.
-- show picture on your desktop from the pandas book because it is not open source.
  * let's group Andre's data frame by Team he played for then take the mean
 <pre>dfg = df.groupby(df.Tm)</pre>
 <pre>dfg.mean()['H']</pre>


# Making plots
Let's make a histogram from our sample dataset. Since we are using a data frame this feature is already built in

<pre>
# make a histogram
df.hist("H",bins=100)
</pre>

![](histo.png)


# Ways to Practice
1. Write some code
2. Ask a friend to review it

* Beginning: Load a csv file into a data frame. Clean it up for statistical analysis.
* Intermediate: Load an excel spreadsheet into a data frame.
* Expert: Go nuts. Read the McKinney book and try out some cool stuff.
