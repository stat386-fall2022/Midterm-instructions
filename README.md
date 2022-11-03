# Stat 386 Midterm Exam 
Welcome to the midterm!  A few of the skills that I am assessing with this exam include:  git, GitHub, data wrangling, data cleaning, simple web scraping, and simple summary statistics.  Depending on your skill, preparation, and understanding of the class material, I expect that the exam should take between 2 and 8 hours.  There is no formal time limit, but I would prefer that you limit yourself to 8 hours.  Keep track of the amount of time that you spend so that you can report it at the end.  

Please read the rules and instructions carefully. 

## Rules
* You are allowed to use LearningSuite material, past homework assignments, and anything posted on our [class GitHub page](https://github.com/stat386-fall2022)
* You are allowed to use a search engine (Google, Bing, etc.) to search for the code to do a specific task
* You are **NOT** allowed to use a search engine (Google, Bing, etc.) to search for similar or identical exam questions
* You are **NOT** allowed to use material from past (386/426) semesters
* The exam should be completed individually and you should not work with or discuss the exam with any other living person 

 

## Instructions
* You should create a new folder on your computer where you will do all your work for this exam.  You should initialize the folder as a git repository.   
* Part of your grade will be based on whether I can run your code without errors.  As such, I would like you to have the data used for the exam in the same folder as your code (so that everyone will have the same path to data).  However, the data should **not** be included in any of your commits, so you'll need to create a .gitignore file. 
* Notebook checkpoints and .DS_Store files should also be in the .gitignore
* As you are working, you should make **at least** 4 commits.  You can decide when to commit but two logical commit points are after completing Part I and after completing Part II.  You should have sensible and informative commit messages.  
* All your work should be pushed to the GitHub repository `midterm-<yourUserName>`.  Clicking on [this link](https://classroom.github.com/a/MInIk_-5) and accepting the assignment will create an this repository for you.  Upon creation, the repository with be **empty**.  You will need to add files from your local git repo to the remote repository.  
* You final submission should include the following files:
  * A .ipynb or .py file with the code used to answer the questions (this should be neat, organized, and I should be able to run it without errors)
  * A file called gitlog.txt that is a text file containing the log of all your commits.  You can make this file by typing the following in the command line while inside the local repo: 
    ```
    git log > gitlog.txt` 
    ```
  * A .gitignore file
  * A README file that has a short description of the repository (i.e., something like "The repo contains the code and other file for my 386 midterm" is sufficient)

* It's up to you whether you push your work once at the end or as you go.     
* For ease in grading, you will report answers in a [LearningSuite Exam](https://learningsuite.byu.edu/.W-9A/cid-e0PuJi4wmjUo/student/exam/info/id-xVR6) called "Midterm Answers."  
* You will be finished with the exam once all relevant file are in the remote repository AND you have finished the "Midterm Answers" LearningSuite exam.

---
## Part I
The data for this part is found in the class [homework data repository](https://github.com/stat386-fall2022/homework-data) in the "GapMinder" folder.  The two datasets in this folder ("life_expectancy_years.csv" and "hapiscore_whr.csv") were downloaded directly from the [gapminder website](https://www.gapminder.org/data/). 

*Note: The life expectancy data was downloaded after selecting "Life expectancy" as the individual indicator.  The happiness data was downloaded after selecting "Society" then "Happiness Score (WHR)" as the indiviual indicator.*


1.  Clean/wrangle/combine these data in to one pandas DataFrame with exactly four columns:  (1) country, (2) year, (3) life expectency, (4) happiness score.  When combining, keep only country and year combinations that are in both datasets.

2.  How many rows are in the final dataset?
3.  How many missing values are in each of the four columns?  
4.  Ignoring any missing values, what is the correlation coefficient between life expectancy and happiness score (round to 3 decimal places)?
5. Ignoring any missing values, which country has the highest mean life expectency?  Report the country and the value of the mean (rounded to 2 decimal places).
6. Ignoring any missing values, which country has the hightest mean happiness score?  Report the country and the value of the mean (rounded to 2 decimal places). 
7.  Now fill in the missing values for the happiness score with the country specific mean.  For example, the data for Afghanistan are shown below:

    | year | happiness | year | happiness |
    |----- | ----------|----- | ----------|
    |2004 | nan | 2013 |31.3 |
    |2005 | nan | 2014 |39.8 |
    |2006 | nan | 2015 |42.2 |
    |2007 | 37.2 | 2016  | 26.6 |
    |2008 | 44.0 | 2017  |26.9 |
    |2009 | 47.6 | 2018  | 23.8 |
    |2010 | 38.3 | 2019  | nan |
    |2011 | 37.8 | 2020  |24.0 |
    |2012 | 35.7 | 


    The mean of all the non-missing values for Afghanistan is 35.015385, so all the happiness score missing values for Afghanistan should be replaced with 35.015385.  

    *Hint: There is a section in chapter 10 of the textbook that shows exactly how to do this.*

8. After filling the missing values, what are the countries with the highest and lowest **median** happiness scores?  Report both the country and the **median** rounded to 2 decimal places.  
    *If you can't figure out how to fill the missing values in (5), then answer this question without filling the missings.*

---
## Part II

The website basketball reference website has a lot of data about basketball. 

Information about NBA players can be found at 
*  https://www.basketball-reference.com/players/a/
*  https://www.basketball-reference.com/players/b/
*  . . .  
*  https://www.basketball-reference.com/players/z/

*Note that there are no players whose last name begins with "x".*

1. Compile a dataset of all the NBA players available at these websites. Your dataset should include the following variables: 
    * "Player":  Name of NBA player
    * "From":  First year of NBA play
    * "To": Last year of NBA play
    * "Pos": Position 
    * "Ht": Height in feet-inches format (i.e, a value of 6-10 means 6 feet and 10 inches tall)
    * "Wt": Weight in pounds
    * "BirthDate": Birthdate of NBA player
    * "Colleges": College attended by the NBP player
    
    At the time of writing this, the final dataset had 5080 rows and 8 columns.  

2. Further clean/transform the scraped data by casting "From", "To", and "Wt" into numeric data. Also compute the following variables:

    * years_played = number of years played, computed as (To - From + 1).  Don't forget to include the  the +1 so that a player who has the same "From" and "To" year will be counted as playing 1 year.

    * Ht_in = Height of the player in inches (recall that there are 12 inches in a foot)

    * HoF = indicator that is True or 1 if the player is in the Hall of Fame and False or 0 otherwise (note that the name has an * at the end if the player is in the hall of fame)

    * start_age = Age at entrance into the NBA.  This can be computed by subtracting the year at start (the "From" year) from the birth year -- don't worry about adjusting for birth month or day.  Set this value to "missing" if the Birth Date or "From" year is missing.  

    *NOTE: When casting variables to numeric, if there are any missing or non numeric entries, the pandas function `to_numeric()` with the argument `errors="coerce"` will automatically coerce any string values into missings.*

3. Answer the following questions about the cleaned data:    
    a. How many players are in the Hall of Fame?     
    b. What is the latest "To" year of players in the Hall of Fame?      
    c. Which player or players in the Hall of Fame played until the year you found in part (b)?         
    d. Fill in the table below with corresponding **means** rounded to 2 decimal places. 

    | In HoF? | height (in) | weight (lbs) | years played | starting age |
    |------|----- | ----------|----- | ----------|
    | No | - | - | - | - |
    | Yes | - | - | - | - |
