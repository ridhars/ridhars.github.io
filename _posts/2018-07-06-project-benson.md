---
layout: post
title: Identifying Optimum Station Placement - Metis Project 1
---

Beginning in Week 1, we are immediately tasked to help WomenTech WomenYes, an organization set out to promote women presence within the tech industries. They have teams ready to be placed on the streets surrounding New York's subway stations. The objective is to gain as much awareness and ultimately raise donation for their upcoming gala. However, the question remains, of all subway stations in New York, which one to attend?

### Approach
To maximize effectiveness, we defined an objective: getting the **right people** as **many** as possible. We need an audience interested in the topic & willing to contribute, as many we can find.  

In order to achieve this objective, these data were being used:
* MTA Daily Traffic Data -- primary data
* Income Data (taken from US Census Data)
* Google API (additional data to complement Income Data)

### Analysis
MTA data were explored and manipulated to provide a higher-level understanding of what's happening on each station. These include removing outliers, data grouping & aggregating values, and time series conversion. Python pandas were primarily used to prepare the data. The final dataset presents daily traffic for each stations.

From the Income Data, we were able to retrieve the % size of our target profile; audience with income of $150,000 - $200,000, which also overlaps with income of tech employees. The data were available at postcode-level. Coupled with Google API, we could get postcode for each station and finally **estimate the absolute target size for each station**.

### Results
Based on our estimation, we could get the adjusted number of traffic for each stations, as shown below. The plot below represents the top busiest station specifically for our target audience.

![Top 10 stations](https://raw.githubusercontent.com/ridhars/ridhars.github.io/master/public/top-10.png)

To anticipate change of pattern between weekend and weekday, we've also plotted the top 3 stations for each day of week, as shown below.

![Top 3 station by day](https://raw.githubusercontent.com/ridhars/ridhars.github.io/master/public/top-3-by-day.png))

Given the result we have, we'd recommend WomenTech WomenYes to target the three stations above throughout the week for maximum opportunity!
