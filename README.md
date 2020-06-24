# asx_bets
#### Small project to see if there was a relationship between discussion of small/mid cap stocks on online forums (specifically reddit forums) and there prices on the ASX Market. On several stock market forums online, some users are accused of [Pumping and Dumping](https://en.wikipedia.org/wiki/Pump_and_dump) stocks, artificially inflating the price.

### Method
I chose to use reddit user posts and comments from the subreddits, ASX_Bets and ausstocks. Fortunately, Reddit have a free API which does not have too hard usage restrictions. I wrote a small python script that pulled the post data accompanied with other features such as the user, time of posting and date. This script created a CSV file with around 10 thousand posts and comments. I cleaned the data with pandas, parsed out the ASX codes mentioned with a basic Regex and did some basic plots.

![img](/zip_asx_bets_vs_asx_price.png)

Here we can see ASX_Bets have a small spike around the first week of May. Then, the mentions plateued until a month later. A rapid increase in both the mentions and the ASX price. Mentions seem to be lagging behind the price by about a day. After, the spike in mentions the mentions fall rapidly. It seems that the mentions on the subreddit are still lagging behind Z1P Closing price. Overall, It seems unlikely that ASX_Bets have any significant effect on the ASX Price for Z1P.

To determine statistical significance, I used [Granger Causality](https://en.wikipedia.org/wiki/Granger_causality) to determine whether the time-series of the closing price of Zip was determined by the mentions on ASX_Bets. The F-test for the Grange Causality had a p-value of 0.3075, which is much greater that our level of significance, 0.05. Therefore we fail to reject our null hypothesis, ASX_Bets Mentions do not Granger-cause Zip ASX Closing Price. ASX_Bets Mentions do not determine any stock prices. This is most probably due to the large size of zip relative to smaller stocks.

After I tested the reverse, does the ASX price Granger-cause the amount of mentions on ASX_Bets? Here, I used this as a sanity check. Here we have strong evidence that indeed ASX 'Granger-causes' the amount users speak about Zip Pay, with a p-value of 0.0004. I also attempted narrowing the time-frame where there was a lot of activity on the subreddit, however this did not return any significant results.

After this, I figured maybe due to Zip's relatively large Market Capitalisation of approx. 2.5b. I would be able to find more interesting results in smaller capitalisation stocks, I also introduced another reddit forums dataset, [ausstocks](https://www.reddit.com/r/ausstocks/wiki/index). I sorted the by the most mentioned stocks from both forums. As expected majority of the stocks most mentioned are large cap stocks, however, OPY(OpenPay) is currently around 250 million market cap, which some would define as a Micro-cap stock. OPY is about 10% of the size of Zip Pay. I then proceeded with the same methodology as I did with Zip. 

![img2](/opy_asx_bets_vs_asx_price.png)

Again we can see similar features from the initial plot of Zip, there is a long tail in both lines, Interesting it seems this relationship is a lot closer, visually. The peaks are very closely aligned if not perfectly. However, it does not seem that this could be predictive of the price. The results of the Granger Causality returned a p-value of 0.1546, still not significant but almost half the size of the Zip's respective p-value, suggesting a closer relationship.

**Overall**
We can conclude that this analysis shows the reddit forums(ASX_Bets and ausstocks) do not have any significant effect on the price of these ASX listed stocks. 


