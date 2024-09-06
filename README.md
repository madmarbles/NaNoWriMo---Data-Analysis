# NaNoWriMo---Data-Analysis
An analysis of the data collected from my NaNoWriMo attempts from 2011-2023.

## Background
National Novel Writing Month (NaNoWriMo) is an event that takes place each November. This event gives writers one goal: write a 50,000 word novel in the month of November. It's easy at face value. 50,000 words in 30 days? 1,666 words per day. And if your average typing speed is 60 WPM, you'll finish with only 28 minutes of writing each day.

Like most creative projects: easier said than done. Sometimes the story doesn't more. Some days are more productive than others. People have birthdays you have to celebrate. Life gets busy. And it turns out there's a major American holiday in November that interferes with writing time.

Since I started undertaking this challenge in 2011, I have "won" NaNoWriMo 14 times. Slightly more Novembers than there are between 2011 and 2024. This is because another event happens in April. Similar rules, but you set your own goal. I stuck with the 50k. Over the years, I have documented my 14 attempts. I have the completed novel, and I kept track of my total words at the end of each day.

## Ask
Using the data from thirteen months of NaNoWriMo attempts, I will determine which day of the week I'm most productive on and how holidays affect my writing productivity. I will also be mindful of any additional insights the data might present.

## Prepare
I currently have one spreadsheet that I will be using. This spreadsheet contains a column for each NaNoWriMo attempt, and rows for each of the thirty days. The intersecting cells contain the total word count that was achieved on that day. I will need additional datasets of word counts per day, and another that contains the days of the week.

## Process

### Data Cleaning

**Excel**
After opening the spreadsheet in excel, I went through the following process:
* duplicated the sheet to maintain the original dataset
* used the **trim()** function to remove any unnecessary spaces
* added columns between each attempt for total words written per day
* used a simple subtraction function to calculate total words written per day
* separated the data into two datasets: one contains total words on the project per day, and the other contains only words written each day.

On the spreadsheet of daily wordcounts:
* add a column for days of the week (5 sets)
* in a separate column, write out the first day of each month for each attempt (11/1/2011, 11,1,2012, 11/1/2013, etc.)
* change the format of the dates to **Long Date Format** to determine what day of the week the month started on
* shift the starting row of the data to align to the day of the week the month started on
* transpose data to put days as columns
* merge data so there is only one column of each day.
* separate each day to its own sheet
* select column of data and find blanks, to delete all rows of null data
* calculate percentage of productivity with dividing each value by 1666 and formatting to percentage
* aggregate data into two datasets: word counts by day and percentages by day
* import datasets into R for analysis

**R Studio**
* Install packages
* Reformat data to long format
* Create a line chart using ggplot2
* Import holiday data - reshape data to long format
* Merging datasets for all relevant information
* Create line chart
* Calculate average words written on holidays
* Calculate mean of not holidays 

## Analyze
When starting the analysis phase, I kept in mind the first question: *On which day of the week am I the most productive?*

Find all code used [here](https://github.com/madmarbles/NaNoWriMo---Data-Analysis/blob/main/Code).

![Weekday Word Counts](https://github.com/madmarbles/NaNoWriMo---Data-Analysis/blob/main/weekday_count.png)
 
The dashed line shows the recommended word count of 1,666 words needed to average each day to finish on time. From this graph, it is easy to see that my most productive days are Monday and Sunday, and my least productive days are Wednesday and Thursday. 

Now, we move onto the second question: *How do holidays affect my writing productivity?*

Days of significance in November include: Thanksgiving, Veteran’s Day, Daylight Savings, Election Day, and my mom’s birthday. My mom’s birthday is on the same date every year, but of the others, only Veteran’s Day falls on the same date every year: November 11. The others will need to be aggregated into a list.

Days of significance in April include: Easter, and my brother’s birthday. My brother’s birthday is the same every year, but Easter changes. Of the three Aprils and many Novembers, I’ll need to check a few dates.

After compiling a list of holidays, I’ll convert the data to long form and eliminate nulls. Then, clean up any data and create a graph.

 ![Holiday Word Counts](https://github.com/madmarbles/NaNoWriMo---Data-Analysis/blob/main/holiday%20word%20counts.png)

The dashed line on the above graph shows the par of 1,666 words per day. Rather predictably, Thanksgivings are low word count days. Election days also tend to be closer to par, and Daylight Savings Days are only slightly higher productivity days, with a notable exception in 2014. 

Calculating and comparing means of the two categories shows no significance in the number of words written on holidays (2273.62) to normal days (2264.044).

However, the data still shows some discrepancies in word counts on occasional days. Take a look at the graph of daily word counts generated with Tableau:

![Daily Word Counts](https://github.com/madmarbles/NaNoWriMo---Data-Analysis/blob/main/daily_count_key.png)

There are a number of zeros that don’t correspond with holidays. Why?

Short answer: Other life events.

In November 2011, I was on the water polo team at my community college, and after forgetting to bring my computer for a weekend tournament, I stopped writing before deciding I would continue and struggling to finish.
In November 2012 and 2013, I stopped due to the intensity of classes at university.
In November 2014, I was trying to keep up with friends by playing video games, and the release of Pokémon Alpha Sapphire caused some issues.
In November 2015, I started playing Dungeons and Dragons.
In April 2018, I went to Disneyland. A few times.
In April 2019, I was helping my brother prepare for his wedding.
In November 2019, I attended a conference and saw the release of another Pokémon game: Sword and Shield.

## Share
[This](https://public.tableau.com/shared/NH2P4D3DP?:display_count=n&:origin=viz_share_link) is a dashboard I created for this project. For my visualizations, I really wanted to highlight overall progress, as well as days based on productivity. I also included sections that show productivity by weekday and holidays.

Here is a summary of takeaways:
* Writing on Thanksgiving is mostly unproductive.
* Attending university is unproductive for creative projects.
* Election days are more productive than days following major elections.
* Daylight Savings Days are more productive in November than April.
* If a Pokémon game is released, my productivity will be lower.
* I am more likely than not to finish early.

## Act
Using this data, I can determine how to best make future attempts at writing 50,000 words in 30 days the most productive. And I can predict which future months of attempts will have the most productive writing days, maximizing the likelihood that I will finish early.

For example, this coming November does not have a Daylight Savings Day and it does have a major election occurring. This will lower my productivity. There is no Pokemon game being released this November, which will have a neutral effect, but I am more likely to play online video games with friends, which will lower productivity.

Even though I have cut ties with the establish that founded NaNoWriMo, if I still take on this challenge in November, I can expect regular fluctuations in productivity that will lead to finishing the event a couple days early.
