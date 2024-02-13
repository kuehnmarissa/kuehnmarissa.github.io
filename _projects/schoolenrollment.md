---
layout: post
title: School Enrollment Project
description: Data Science II project completed Fall 2023 predicting school enrollment using various data sources in RStudio.
---

# Background

This project was completed during the Fall 2023 course HHS 4500 Data Science II taught by Dr. David Lilley at the University of Toledo. It is a culmination of many skills we worked on over the course of Data Science I and II (HHS 2500 and 4500), particularly the ability to write computer code and merge data from different sources to investigate a real-world problem. 

# Tools Used

* R Studio
* Libraries: tidyverse, haven, panelr, readxl, stargazer

# Data Used

* A file containing school enrollment data years 1990-2001 from Elementary/Secondary Information System (ELSI) from the National Center for Education Statistics (NCES)
* A file containing the schools' IDs, counties, and FIPS from ELSI
* A file containing the schools' coordinates from ELSI
* Census data for population estimates
* A file from the Uniform Crime Reporting (UCR) program years 1990-2001 at the ORI level
* Files from the Bureau of Economic Analysis (BEA) years 1990-2001

# Project Outline

## Part 1: Read-in and Prepare the School Enrollments Data

In this portion of the project, the ELSI school enrollment data was cleaned and transformed into long panel format for use in future sections. 

## Part 2: Read-in and Prepare the School County FIPS Data and Merge with Enrollments

This section cleaned the location-based data and involved a series of merges. First, I merged (left join) the enrollments dataframe with the school county dataframe. The result was combo_school_counties. Next, I created a dataframe with only non-matching records from the merge, then I merged (inner join) the non-matching file with the school coordinates file. Finally, I merged the matching records from the prior merge with combo_school_counties. The final file was aggregated to the county-year level. A clean permanent file of the county-year level school enrollments file was created for use in future sections.

## Part 3: Read-in and Prepare the Census and Crime Data and Merge with Enrollments

This section cleaned the census and crime data and involved merging a few files. The census (county-year level) was merged with the aggregated school enrollments file (county-year level). The crime data was merged with the result of the previous merge.

## Part 4: Read-in and Prepare the Economic Data and Merge with Enrollments

Using a for loop, all the BEA files were read in and stacked on top of each other. I merged (left join) the most updated enrollment file with the economic data and cleaned the resulting file. To prepare for data analytics, I demeaned the independent and dependent variables, which was written to a permanent csv file.

## Part 5: Data Analytics

Using nation-year level variables to check overall trends, I created line graphs of enrollments, crime, and economics from 1989 to 2001 to observe if they were up or down over the time span. Overall, enrollments was mostly up, crime was up before 1997, and economics was mostly up. 

I also found the variable most correlated with year: per capita income (demeaned).

The statistically significant predictors of county school enrollment were year, proportion of nonwhite people (demeaned), proportion of males (demeaned), proportion of people aged 15 to 24 (demeaned), and total crime rate (demeaned).