# Hello and welcome to my Data Analyst Portfolio!

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

## SQL Demonstration
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

## Tableau Demonstration
