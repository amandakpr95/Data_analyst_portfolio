# Amanda Rojas Data Analyst Portfolio!

## Introduction
I am Amanda Rojas, a Ph.D. graduate who is interested in shifting from neuroscience to data analytics. 
I have several examples here of different commonly used coding languages (R, Python, SQL, Excel) demonstrating my analytical acumen. 

Thank you for taking the time to peruse my portfolio and please contact me if you are interested in connecting!

Email: `amandakpr95@gmail.com`

LinkedIn: `https://www.linkedin.com/in/amanda-rojas-2b446b284/`

## Technology
- *Languages*: SQL, R, Python
- *Softwares*: Tableau, Excel
- *Libraries/packages*: Tidyverse, ggplot2, Pandas, NumPy, Plotly
- *Database*: SQLite

## SQL Demonstration -- filtering, sorting, querying big data/databases
Here I used the 1.88 Million Wildfires Dataset (access here: `https://www.kaggle.com/datasets/rtatman/188-million-us-wildfires`) to analyze government wildfire data between 1992-2015. 

First I'd like to know *how many wildfires took place in the USA per year between 1995 and 2015?*

```sql
SELECT FIRE_YEAR, COUNT(*) AS fires_per_year
FROM Fires
WHERE FIRE_YEAR BETWEEN 1995 AND 2015
GROUP BY FIRE_YEAR
ORDER BY FIRE_YEAR ASC;
```

Now we know how many wildfires took place in the USA between 1995 and 2015. But lets order it differently to see which year had the most wildfires.

```sql
SELECT FIRE_YEAR, COUNT(*) AS fires_per_year
FROM Fires
WHERE FIRE_YEAR BETWEEN 1995 AND 2015
GROUP BY FIRE_YEAR
ORDER BY fires_per_year DESC;
```

We can easily see the year with the most wildfires was **2006**, followed by **2000** and **2007**. 

Now *where exactly are these fires taking place* most often?

```sql
SELECT State, COUNT(*) AS wildfire_count
FROM fires
GROUP BY State
ORDER BY wildfire_count DESC;
```

We can now see the states with the most wildfires are:
1. **California** with 189,550 wildfires between 1995 and 2015
2. **Georgia** with 168,867
3. **Texas** with 142,021

Great! Now we're curious as to *what is causing these wildfires*? So we can query the following.

```sql
SELECT STAT_CAUSE_DESCR, COUNT(*) AS wildfire_cause
FROM Fires
GROUP BY STAT_CAUSE_DESCR
ORDER BY wildfire_cause DESC;
```

Most often the cause of wildfires between 1995 and 2015 was **Debris Burning**. 

We can create a data visualization demonstrating this using Tableau!

## Tableau Demonstration -- data visualizations/dashboard
Using Tableau, I created this dashboard showing the findings from our SQL queries. 


![Fires in the United States between 1995 and 2015](https://github.com/amandakpr95/Data_analyst_portfolio/blob/main/Tableau_Demo-Fires_Dashboard.png)

As you can see, in the top line graph, fires have not increased or decreased overall across the 10 year period. However, 2006 and 2007 two years with a lot of fires. 

Additionally, we can see with the bottom left map that CA, GA, and TX had the most fires during this period. 

Finally, the bubble graph in the bottom right depicts the largest cause of fires in the largest bubble. The most common cause of fires between 1995 and 2015 was burning debris. 

## Excel Demonstration -- cleaning, filtering, sorting data and data visualizations/dashboard
Here I used a dataset on shoe sales to gather some data insights on different shoe brands and how/what shoe to develop.

### Data Cleaning using Excel
First, I start with cleaning the data, to ensure our data insights are accurate and precise. 

I start with making the case uniform between all the cells:
```excel
PROPER(A2:)
```

Then I check that all the cells in column A, which describes the brand of shoes, and column B, which describes the color of the shoes, are in fact text data:
```excel
=AND(ISTEXT($A$2:$A$5649))
=AND(ISTEXT($B$2:$B$5649))
```

Then I check that all the cells in column C, which describes the size of the shoes, is numerical data:
```excel
=AND(ISNUMBER($C$2:$C$5649))
```

This returned false, indicating that this column needs to be cleaned. I find that some shoe sizes here are listed in UK sizes and have "UK" before the size. I count the number of cells which have this size indication:
```excel
=COUNTIF($C$2:$C$5649, "*UK*")
```

It returns only 31, so I remove these rows from our data set, as it will not heavily impact our findings. 
If stakeholders were interested in seeing this data, it is possible to convert the UK sizing to US. 

### Filtering Data using Excel
Once our data is cleaned we can then move on to filtering the data to gain some insights. 

First, I filter column A (brands) to see all the unique strings in the column:
```excel
=UNIQUE(shoes_USA!$A$2:$A$5649)
```
Now I have a list of all the brands of shoes. 

I'd like to know the amount of individual deals (size and color) with individual sellers each brand has, so I count the frequency that each brand name appears:
```excel
=COUNTIF(shoes_USA!$A$2:$A$5649, "Adidas")
```
We can see that Crocs has the most individual deals with distributers. 

Next I'd like to know the total predicted and actual revenue brought about by these deals for each brand:
```excel
=SUMIF(shoes_USA!$A$2:$A$5649, "Adidas", shoes_USA!$D$2:$D$5649)
```
Then I filter the data to show the top 6 brands that have the most actual revenue. 
We see the top six brands with the most revenue in this dataset are:
1. Crocs
2. Tory Burch
3. Tresmode
4. Franco Leone
5. Nike
6. Woodland

I decide to dive into the Crocs data more.

I first identify all of the unique colors sold by these vendors:
```excel
=UNIQUE(FILTER(shoes_USA!B2:B5649, shoes_USA!A2:A5649= "Crocs"))
```
Then, in order to identify the most popular color with consumers, I generate the revenue (actual) generated by each color:
```excel
=UNIQUE(FILTER(shoes_USA!B2:B5649, shoes_USA!A2:A5649= "Crocs"))
```
Finally I do the same with the size, to identify all the sizes sold by vendors and the most popular sizes with consumers:
```excel
=UNIQUE(FILTER(shoes_USA!C2:C5649, shoes_USA!A2:A5649= "Crocs"))
=COUNTIFS(shoes_USA!$C$2:$C$5649, "2", shoes_USA!$A$2:$A$5649, "Crocs")
```

I create a pivot table of this data and create a scenario to analyze the data using real world applications. 

**SCENARIO**: Crocs would like to introduce a new shoe to compete with others in the market that target a difference sample of the population (ex. Tory Burch). 

**STAKEHOLDER QUESTION**: How should we price this new shoe, dependent on the other data we have on our existing shoes (size and color)? 

The pivot table shows the actual revenue provided by vendors for each shoe/size pair. 
I also use conditional formatting to identify the highest (green) and lowest (red) revenue pairs.
![Shoes Pivot Table](https://github.com/amandakpr95/Data_analyst_portfolio/blob/main/Excel_Demo-Pivot_Table.png)

We see here that the most popular colors are:
1. Brown
2. Blue
3. Black

Additionally, the most popular sizes are:
1. size 8
2. size 6
3. size 9

As such, we can launch the new shoes in these sizes/colors and use the pricing for these shoes as a guide. 

### Data Visualizations/Dashboards using Excel
I create a small dashboard to tell this datastory:

![Shoes Dashboard](https://github.com/amandakpr95/Data_analyst_portfolio/blob/main/Excel_Demo-Dashboard.png)

As we can see in the top left, Crocs are the vast majority of the marketshare here, however the Crocs total revenue is similar to Tory Burch. Tory Burch is a higher end shoe brand that caters to a different market, so perhaps Crocs can create a higher-end looking shoe and appeal to that base. 

We identified the most popular colors and sizes with our customer base, and now have an idea of where to start with producing/pricing this new shoe.

