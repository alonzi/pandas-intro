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

# Goals for Today
1. Get pandas
2. Get comfortable with pandas (know what it's all about)
3. Learn how to look up help

## Outline
1. Read data into pandas
2. Manipulate data with pandas
3. Plot data with pandas

## A brief history
* Designed by [Wes McKinney](http://wesmckinney.com/) - launched in 2008
  * https://www.blockchain.com/btc/address/1CUztXcgPYfL1AXuv8FD8XDyPXTc2jcheg
  * https://etherscan.io/address/0x5BC648c302d6aF9D921DE31d0DB2411D26686A4a
* version 0.24.1

# Reading in Data
* The Data Frame - https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html
  * from csv
    * docs: https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.read_csv.html
      <pre>
      # load pandas package
      import pandas as pd      
      # Part 1: read data into data frame
      df =  pd.read_csv("andre.csv")
      </pre>



# Ways to Practice
1. Write some code
2. Ask a friend to review it

* Beginning
  * Flip a coin (~10 lines)
  * Play rock, paper, scissors  (~25 lines)
* Intermediate
  * Guess a secret number between 1 and 10. With hints. (~20 lines)
  * Dice rolling program
* Expert
  * Play blackjack
  * Play roulette
