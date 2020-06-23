# asx_bets
#### Small project to see if there was a relationship between discussion of small/mid cap stocks on online forums (specifically reddit forums) and there prices on the ASX Market. On several stock market forums online, some users are accused of [Pumping and Dumping](https://en.wikipedia.org/wiki/Pump_and_dump) stocks, artificially inflating the price.

### Method
I chose to use reddit user posts and comments from the subreddits, ASX_Bets and ausstocks. Fortunately, Reddit have a free API which does not have too hard usage restrictions. I wrote a small python script that pulled the post data accompanied with other features such as the user, time of posting and date. This script created a CSV file with around 10 thousand posts and comments. I cleaned the data with pandas, parsed out the ASX codes mentioned with a basic Regex and did some basic plots.

