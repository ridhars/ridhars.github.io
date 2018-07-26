---
layout: post
title: Selling a Used Phone -- how much does it worth now?
---

In the recent years it's becoming more and more common to see people selling and purchasing second-hand mobile phones. It's one of the first things come to mind to sell your old phone when you just purchased a new one. On the other hand, in terms of technology they are not that obsolete not to mention a more affordable option -- some people just prefer to purchase used phones.

However, unlike new retail products, there is no standard being established to determine used phone price. Pricing-wise, it's entirely up to the market. So how do we learn the reasonable price for a certain used phone?

To help us answer this question, I built a machine learning model which will recommend us a range of price given a set of phone's specification. Keep reading to see how I approached this problem :)

### Getting the data and making it Relevant

The first step is to collect transactional data for used phones. The easiest way is just to scrape it from e-commerce. Using *BeautifulSoup*, 10,000 phones were scrapped and subsequently cleaned. During the scraping process, 9 features were acquired. 

Many of these were categorical variables (e.g. accepts return, offers free shipping, etc.) so I created *dummy variables* in order to include them in my model. In addition, phone name was parsed into brand, model, and capacity. Lastly, we also want to observe the distribution of our data. In my case, the scraped price data was heavily skewed, so I used log-transformed the data to help normalize the distribution.

### Model building!

As many have said, the work of data science is not a linear process, so it involves a lot of experiment! As the goal of my model is to recommend a range of price, I'm using R-squared to measure overall predictability and MAPE (Mean Absolute Percentage Error) to create a range of price, as my model will not likely achieve 100% accuracy.

After trial and error, I found the best model was achieved by using Lasso Regression on 1st Polynomial Degree. Subsequently by using Lasso I learned *Launch Date* is the most influential feature. And this is the final score I have on my model:

![Model Score](https://raw.githubusercontent.com/ridhars/ridhars.github.io/master/public/final-linreg.png)

With MAPE of 23%, this means that if my model predict the price of a specific phone for $100, my model will output $77 - $123 as it's recommended price.

### Fun facts

Some fun facts I found after working on the model:
* Length of description characters does not impact price !
* Returnable product increases price by 21%
* Free-shipping product increases price by 7%

### Future improvements

* Analysis on product description. For many phones, there is a wide range of price within the same phone model and specification. One of the reason is due to different conditions they are being sold. For instances, some were being sold in like-new condition, some others were sold with cracked-screen.

* Incorporate historical transactional data. When longer range of time-series data are being used, I could explore the possibilities to also predict phone price depreciation over time.
