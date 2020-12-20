# Kickstarting with Excel

## Overview of Project
Our client would like to better understand the results of fundraising campaigns for campaigns as they relate to their launch month and their dollar amount.  This analysis will specifically review the relationship between campaign outcomes (results) and the launch date of theater campaigns in order to determine the optimal month(s) to launch theater campaigns in the future.  The second analysis digs deeper into the theater category in an effort to understand the relationship between the dollar amount goal and the percentage of successful campaigns for plays.  

### Purpose
Our client intends to use this analysis to better optimize the timing and fundraising goals for theater campaigns.

## Analysis and Challenges
Size of the dataset is relatively small, especially as the campaign target amounts increase.  The statistical significance of the data at the low end of the scale vs. data at the high end of the scale might mask the presence of outliers.  To address this challenge, the analysis performed based on campaign amount uses ranges as opposed to exact amounts per campaign.  

### Analysis of Outcomes Based on Launch Date
This analysis focuses on the relationship between theater campaign launch date and the campaign outcomes.  A pivot table was created using the months of the year and a count of outcomes by each month.  Restuls were then plotted on a line graph with months of the year as the x axis and the outcome on the y axis.

### Analysis of Outcomes Based on Goals
This analysis focuses on the relationships between the fundraising goal and the percentage of each outcome at each fundraising level.  To visualize this, ranges were created at $5000 intervals and the number of successful, failed, and canceled campaigns counted at each of these intervals.  Results were then plotted on a line graph with outcome ranges as the x-axis and percentage of outcomes on the y axis.  

### Challenges and Difficulties Encountered
The dataset is weighted heavily to lower value campaigns, with a small number of higher dollar campaigns compared to the volume of lower value campaigns.  To a degree, this is expected, but the spread is such that the data at the higher dollar amounts represents outliers.  

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?

Conclusion 1:  Summer months are the most successful months to launch campaigns.  Successful outcomes in May, June and July exceeded expected statistical trends.  July has the single highest total of successful launches, with 109.

Conclusion 2:  January is the lowest peforming month to launch campaigns, with only 42 successul outcomes.  This represents the lowest number of succesful campaigns by month.  38 failed campaigns is significant because it reprensents the closest gap between succesful and failed outcomes.

- What can you conclude about the Outcomes based on Goals?
The highest number of successful outcomes and the second highest percentage of succesful outcomes occur in the 1000-4999 range.  The percentage of succesful campaigns drops markedly from that point, but then trends back up between 35000-44999.  This range represents a small number of total outcomes, with only 6 campaigns total.  However, this is still notable as a "sweet spot" because the percentage of succesful outcomes again drops markedly at 45000.  

As expected, the highest percentage of failed outcomes occurs at the top of the range.  However, the 6 campaigns between 35,000-39999 jumps to a 67% success rate.  Unsure if these campaigns are outliers due to the lack of data volume, but this is still notable

- What are some limitations of this dataset?
Low volume of data at the high end of the range.  For example, only 21 campaigns fall within the 45,000-49,999 range, compared to 1412 campaigns in the 1000-4999 range.  Unclear if the measurements at the high end are statistically in line with most of the dataset, or if they represent outliers.

- What are some other possible tables and/or graphs that we could create?
Similar to Outcomes Based on Goals, but using the number of outcomes instead of the percentage as our range.  This might be more informative in uncovering the potential low volume of high end data limitation.

There are two Boolean values, staff_pick and spotlight.  It would be interesting to compare the results of the campaigns for those that were staff picks, in the spotlight, or both.  
