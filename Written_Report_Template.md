# Kickstarting with Excel

## Overview of Project
Louise almost reached her $12,000 kickstarter goal for her play, titled *Fever*. She wants to know more about the seasonality of kickstarters in relation to their launch dates and funding goals. This uses the same dataset provided prior to her kickstarter launch.

### Purpose
The purpose of this analysis is to optimize Louise's fundraising efforts through data visualization.

## Analysis and Challenges
**Analysis of Original Data Set**
1. Original data set was replicated to sheet titled "Edited Data" for purposes of manipulating data while retaining a revertable set of original data.
2. The following changes and/or additions were made to the original data set:
	- Columns 'deadline' and 'launched_at' were converted from Epoch time standard short date format using '=(I2/86400)+DATE(1970,1,1)', creating columns 'Deadline Date' and 'Launched_At Date' 
	- Column 'Category and Subcategory' was divied into two columns, Parent Category and Subcategory using the Text to Columns function
	- Column 'Years' was added, extracting the year into a dedicated column from the column 'Launched_At Date'

### Analysis of Outcomes Based on Launch Date
To produce the following graph,

![Theater Outcomes Based on Launch Date](/resources/theater_outcome_vs_launch.png)

A pivot table was created from the "Edited Data" tab to filter by subcategory plays and years, showing time vs outcome.

### Analysis of Outcomes Based on Goals
To produce the following graph,

![Outcomes Based on Goals](/resources/Outcomes_vs_Goals.png)

A table was created extracting the counts of outcomes and organized into ranges of goals using the '=COUNTIFS' function, whereby the parameters were:
	- subcategory 'play'
	- organized by 'successful', 'failed', or 'canceled' outcomes
	- organized by goal in increments of <1000, >50000, or increments of 5000 inbetween 1000-50000
	- Percentages of each outcome were calculated from the data produced by the above parameters

The graph was then created from the percentages of outcomes vs the ranges of goal amounts

### Challenges and Difficulties Encountered
**Theater Outcomes Based on Launch Date**
- When looking at this dataset, it should be noted that when comparing months vs outcome, years 2009 and 2017 do not reflect full 12-month years.  Fortunately, the additions of these two years in the data do not significantly change any overall trends.
**Outcomes Based on Goals**
- I found it tedious to adjust each cell's formula individually, as suggested in the tutorial clip, and so I separated the goal ranges into two separate columns, one with the lower amount of the range and another with the upper amount of the range (see hidden columns A and B) and adjusted my formula accordingly to reference these cells rather than input the actual numerical figures in my formula.  This way, I could easily click and drag my formula, changing the outcome in batches using the Find and Replace function.
- To create some checkpoints in my work, I created a simple pivot table from the original data to show the total count of campaigns per outcome to compare to the total numbers from my '=COUNTIFS' formulas to make sure I was coming up with the same total numbers and my table was complete. Likewise, I summed the percentages to make sure each row added to 100%.

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?
1. Theater kickstarters that launch between May and June tend to have the greatest likelihood of success despite the overall increase in theater kickstarters being launched at that time. Louise should not need to worry about getting lost in the category.
2. Despite the lesser number of overall theater kickstarters being launched in the Fall and Winter months (Sept-Jan), there seems to be a lesser appetite for theater overall as there is an uptick in failures and downward trend in successes.

- What can you conclude about the Outcomes based on Goals?
Kickstarters with a goal below $10k is more likely to reach its fundraising goal than campaigns who aspire for greater amounts.

- What are some limitations of this dataset?
1. The success of kickstarter campaigns typically goes beyond seasonality and goal setting, particularly for theater.
	- Kickstarter campaigns often incentivize multiple levels of pledging that allow backers to 'unlock' access or gifts, which may skew data like, the average number of backers or the average amount paid by each backer, as the campaign itself may set those ranges.
	- Theater-going often fluctuates with the economy, as it is typically an expensive cost for entertainment. The data can only average between the years provided, but cannot anticipate luxury spending habits when Louise is ready to debut her play.
	- The zeitgeist and fame of associated acts cannot be taken into account from this dataset. The talent or fandom associated with any show, stage show or otherwise, can greatly affect the success of a kickstarter campaign, potentially leading to difficult to find anomalies in the data.
2. Some kickstarters are advertised with paid media, which may affect its success rate, which is unknowable from this dataset. 
3. It would be imprudent to compare any data without isolating the country from this dataset because the monetary amounts represent different currencies and is not normalized.

- What are some other possible tables and/or graphs that we could create?
1. Table: Number of days required to reach the goal vs goal amount, organized by outcome. This could answer questions like:
	- On average, how many backers do I need per day to reach my goal?
	- What is the minimum number of days I need between my launch and deadline?
2. Graph: Launch Day of Week or Time of Day vs Outcome. This could answer if there is an optimal day of week or time of day to launch the campaign, as kickstarters often require social sharing to create buzz (e.g., word of mouth). Can also support any paid media efforts.
3. Table: Retrieve name, blurb, goal between $10k-$14k, outcome:successful, country:US, subcategory:play, and spotlight:true to find case studies on Kickstarter's Spotlight that may be applicable to Louise's play.
