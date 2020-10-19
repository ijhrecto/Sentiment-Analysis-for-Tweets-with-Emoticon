# Sentiment-Analysis-for-Tweets-with-Emoticon
NPL program to analyze the sentiment polarity of the tweet &amp; emoji posts

A Natural Language Processing program to analyze the sentiment of the tweets with included emojis. I analyzed the problem and came up with two methods. First is to train the sentiment of the emoji and tweets separately then averaging the value of their polarity to come up with the final sentiment. Second, train the data containing the tweet with included emojis, this method is faster to implement but will skew the sentiment of individual emoticon, as observed from the experiment.

raw data where taken from this links:
- 1.6m tweet dataset with sentiment polarity : https://www.kaggle.com/kazanova/sentiment140
- emoticon dataset : https://www.kaggle.com/thomasseleck/emoji-sentiment-data?select=Emoji_Sentiment_Data_v1.0.csv
- 3 part tweet dataset with with sentiment polarity : https://www.kaggle.com/shashank1558/preprocessed-twitter-tweets

# Data Creation
Using the emoticon dataset I simulated, replace, and added utf-8 emoticons the data set
### 1.6m tweet dataset
  - I downsized the 1.6m tweet dataset to 10k.
  - The name tags and links were also removed since most would not contribute to the value of the sentiment
  - converted the sentiment values to 0 and 1
### emoticon dataset
  - The emoticon dataset although contains sentiment, the sentiment is formatted by voting value of the data acquirer.
  - It also contains 3 polarity (positive, neutral, negative)
  - to set the sentiment of the emoticon, we compare the values of the positive and negative, which ever is higher is set as the sentiment polarity
  - we normalize the value to 0 and 1
### 3 part tweet dataset
  - the formatting of the dataset is listing by column and contains 3 file, positive, negative, and neutral tweet list
  - We create a new data frame and list the dataset by row and the sentiment polarity depends on what file the tweets were taken from
  - The tweets contains tags and link which need to be removed
  - Since the raw data is already a cleaned tweet the emotiocn were transformed into plain words or words with synmbol
  - ASCII emoticons and word emoticons were converted to utf-8 emoticons
  - emoticons were also randomly added by sentiment to balance the data

# Sentiment Analysis Method
I experimented with two methods that I think would be suitable for this task.
### First Method
  - This method extracts and separates the emoticon and texts from the input tweet.
  - The emoticon dataset already contains sentiment polarity which we will use to analyze the extracted emoticons
  - We train the our processed tweet dataset using Naive Bayes to to set our sentiments
  - We use our trained model to predict the extracted text from our input tweet
  - To get the final sentiment polarity, We average the sentiment value of the extracted emoticon and tweets
### Second Method
  - This method trains our processed dataset as is, where it contain both the emoticons and text
  - The tweets contains there respective sentiments which will be used to train our model
  - We predict our input tweet & emoji using our model
  - This method will also set the sentiment of each emoticon, and depending on the dataset might skew the reals entiment of the emoticon.
