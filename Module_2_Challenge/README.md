# Module 2 Challenge - VBA Refactoring

## Project Overview
Our client Steve has asked us to expand the initial stock performance analysis spreadsheet we've
constructed to include a larger dataset of all stocks traded in 2017 and 2018.  This requires us to refactor our
original analysis, since the dataset is significantly larger.
Primary deliverable is an interactive spreadsheet that provides stock analysis at the click
of a button for both 2017 and 2018.

## Results
Generally speaking, the data tells us it would have been much better for our wallets
if we trades stocks in 2017 rather than 2018.  In 2017, every stock we tracked generated a positive
return save for TERP.  In some cases, the returns were extreme, and four stocks generated over a 100%
return. 

![alt text](https://github.com/brian-mcrae/UT_Data_Analytics_Bootcamp/blob/main/Module_2_Challenge/Resources/2017%20Results.PNG)

2018 was almost the exact opposite, with all stocks except for ENPH and RUN generarting negative rates of return.  
Seven stocks had a negative return greater than 10%.

![alt text](https://github.com/brian-mcrae/UT_Data_Analytics_Bootcamp/blob/main/Module_2_Challenge/Resources/2018%20Results.PNG)

To complete this analysis, we created four 12 position arrays to develop a matrix for each of the 12 stocks represented in the analysis.  A tickerIndex variable was created
to act as a placeholder in the arrays in order to understand exactly which "slot" in the array we're working with.  The last step of the initialization phase of the macro is 
to loop through the tickerVolumes array and initialize the values to zero.
Code:
 ' 1a) Create a ticker Index
    tickerIndex = 0
    
    ' 1b) Create three output arrays
    Dim tickerVolumes(12) As Long
    Dim tickerStartingPrices(12) As Single
    Dim tickerEndingPrices(12) As Single
        
    ' 2a) Create a for loop to initialize the tickerVolumes to zero.
    For j = 0 To 11
    
        tickerVolumes(j) = 0
    
    Next j
    
Next step is to loop through all the rows of data in the dataset and assign the starting price, ending price, and trading volumes values for each stock ticker.
To do so accurately, we need to be able to understand where the data for the particular ticker starts (the first row) and where the data ends (the last row).  This 
understanding is then used to populate and calculate the starting price, ending price and trading volumes.
 '2b) Loop over all the rows in the spreadsheet.
    For i = 2 To rowCount
            
            '3a) Increase volume for current ticker
            tickerVolumes(tickerIndex) = tickerVolumes(tickerIndex) + Cells(i, 8).Value
        
            '3b) Check if the current row is the first row with the selected tickerIndex.
            If Cells(i, 1).Value <> Cells((i - 1), 1).Value Then
                
                ' Set the starting price
                tickerStartingPrices(tickerIndex) = Cells(i, 3).Value
                
            End If
        
            '3c) check if the current row is the last row with the selected ticker
            If Cells(i, 1).Value <> Cells((i + 1), 1).Value Then
                
                ' Set the ending price
                tickerEndingPrices(tickerIndex) = Cells(i, 6).Value
                
                ' 3d) Since we're on the last row, increment the tickerIndex
                tickerIndex = tickerIndex + 1
            
            End If
    
    Next i
   
    '4) Loop through your arrays to output the Ticker, Total Daily Volume, and Return.
    For i = 0 To 11
        
        ' Output Ticker, Total Daily Volume, and Return
        Worksheets("All Stocks Analysis").Activate
        Cells((i + 4), 1).Value = tickers(i)
        Cells((i + 4), 2).Value = tickerVolumes(i)
        Cells((i + 4), 3).Value = tickerEndingPrices(i) / tickerStartingPrices(i) - 1
        
    Next i
    
Two observations.  First, step 2A seems redundant and was somewhat confusing, since the tickerVolumes value in each array slot was already set to 0, at least
according to the locals window.  Second, the logic for step 3d was established in the If statement checking to see if we're on the last row, so I included the tickerIndex
increment step inside that if statement instead of performing an additional conditional check.
    
## Execution Times
The original macro ran in about .5 seconds for both 2017 and 2018.  The refactored macro ran in .125 seconds for 2017 and .078 seconds for 2018, representing an improvement
of almost .4 seconds per run.

![alt text](https://github.com/brian-mcrae/UT_Data_Analytics_Bootcamp/blob/main/Module_2_Challenge/Resources/VBA_Challenge_2017.png)

![alt text](https://github.com/brian-mcrae/UT_Data_Analytics_Bootcamp/blob/main/Module_2_Challenge/Resources/VBA_Challenge_2018.PNG)

## Summary
The advantages of refactoring code are clear: do the same with less.  The fundamental idea that the first step in our process is to write code that
works - accomplishes the business objectives.  Refactoring allows us to review the code again but with an eye to efficiency.  If we can loop through data one less time
or write conditional logic such that we aren't running redundant or unnecessary conditional checks, then the code runs faster, more effeciently, and is far easier to maintain.
The primary disadvantage of refactoring is the danger of refactoring the code to the degree that it isn't readable and therefore harder to effectively maintain.  In our
application, refactoring our code created a massive performance gain and made the code easier to read and maintain.  It is interesting that step 2A seems redundant and we can
actually pack the logic for step 3d into the conditional we used for the previous step.  Were these intentional - like litte refactoring Easter eggs that the learning materials
"want" us to find for ourselves?  Were they mistakes in the content?  Or (more likely) did I analyze it incorrectly?  Either way, it's thought provoking and I do like that!
    
    
    


