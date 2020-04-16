---
published: true
title: 'Court of Public Opinion: A Sentiment Analysis'
---
Hand up, this time last year I thought Freddie Kitchens was a good hire for the Cleveland Browns. The strong offensive finish to 2018 combined with Freddie’s seemingly close ties to Baker Mayfield had me convinced that Kitchens was the man for the job. I wasn’t about to let the fact that Freddie lacked any head coaching experience come between me and my delusions of Browns grandeur. I was hooked on recency bias, and it was a hell of a drug.

Fast forward to the present day. Freddie’s a goner, the Browns are once again riding the coaching carousel, and my hope-fueled dopamine high has long since faded. However, being so completely wrong left this armchair G.M.’s ego bruised and battered. I had to wonder if everyone bought into the hype or if I was among a gullible minority that fell for Freddie’s good ole boy schtick? To answer this question, I set out to measure the consensus fan opinion of the Kitchens pick and then compare it to that of Kevin Stefanski and other recent NFL head coach selections.

### Data
I needed data to conduct this experiment, so I turned to Reddit threads – specifically posts on the NFL subreddit, r/nfl, and team-specific subreddits (i.e. r/browns for Kitchens and Stefanski, r/NYGiants for Joe Judge, etc.) linking to a Tweet or team release announcing a new hiring going back to 2018 (19 hires and 38 threads).

Python was used to gather the comments from each thread along with the PRAW library which allows users to tap into Reddit’s free API. See reddit_hire_data_pull.py and comments_data.csv in the [repository](https://github.com/ClayGirdner/nfl_hires_reddit_sentiment) for the code and data.

In order to measure the overall sentiment for each thread, comments were fed through two different text analysis tools available in Python – [VADER](https://github.com/cjhutto/vaderSentiment) and [TextBlob](https://textblob.readthedocs.io/en/dev/), both of which produce numeric scores indicating the degree of polarity for each comment (i.e. level of positivity/negativity). Two example comments and their resulting scores are provided below along with a scatter plot displaying the relationship between the two polarity scores for all 31,000+ comments in the data set (correlation = 0.51).

"I really like this hire for our team!"
- VADER: 0.47
- TextBlob: 0.25

"This guy stinks! Why would we hire him?"
- VADER: -0.32
- TextBlob: -0.75

![vader/textblob scatter](https://raw.githubusercontent.com/ClayGirdner/nfl_hires_reddit_sentiment/master/vader_textblob_scatter.png){:height="36" width="36"}
