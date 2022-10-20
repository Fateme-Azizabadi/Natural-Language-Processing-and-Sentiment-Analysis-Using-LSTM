# Natural Language Processing  and Sentiment Analysis - Using LSTM

**Natural Language Processing  and Sentiment Analysis - Using LSTM**

We used text analysis techniques to interpret and classify emotions (positive, negative, and neutral) in text data. Sentiment analysis allows organizations to identify public sentiment toward specific words or topics.

The sentiment -140 dataset is used in this part.
The dataset used is the sentiment-140 dataset. It contains 1,600,000 tweets extracted using the Twitter API. Tweets are annotated and can be used to detect sentiment.

## **Preprocessing**
The training data is not fully classified because it is created by text labeling based on existing emoji. Therefore, any model built using this dataset may be less accurate than expected because the dataset is not fully classified. Therefore, we must first clean and prepare the dataset.

* First, we download the dataset and read the CSV file from the input.
This dataset contains the following six fields:

1. Sentiment: determines the polarity of the tweet. ( positive and negative)
2. IDs (ids): tweet IDs (2078)
3. Date: Tweet date (Sat May 16 23:58:44 UTS 2009)
4. Query: specifies the value of query (lyx). If there is no query, this value is NO_QUERY.
5. User: The user who tweeted (robotickilldozr)
6. Text: tweet text (lyx). 

We only need the sentiment and text parts, so we leave the rest out.

* We make changes in the dataset:

1. First, we delete the fields we do not need, such as id, date, query, and user, from the dataset.
2. We change the emotion field to have new values to reflect the emotion. (0 = negative, 1 = neutral, 2 = positive)
3. Stop words are English words that do not add much meaning to the sentence. They can be safely omitted without sacrificing the meaning of the sentence. (eg: "he", "she", "has") so we remove them.
4. We remove all punctuation marks from the tweet.
5. We also delete all tweets containing links, so training the model is no problem.

* Then, we divide the dataset into test and validation categories.

* Then, we pass the data through the tokenizer to divide the sentence into predefined tokens and assign an ID to each of them.

* pad_sequences is used to ensure that all sequences in a list are of the same length. By default, this is done by adding 0 to the beginning of each sequence until each sequence is as long as the longest sequence. But in this part, we considered the maximum length to be 30, which means that if the length of a sentence is less, zero is added to its right side, and the padding operation is performed.

* Then, with the help of the np_utils.to_categorical function, we convert the data into one hot vector. Next, we download glove.42B.300d and perform the word embedding operation; that is, with the help of this file, we map each word to a feature vector with dimension 300.

* Then we download the testdata.manual.2009.06.14.csv file, which is related to the sentiment140 test data, and we apply all the work done for the training and validation data to the test data.

## **Network**
We use LSTM with the below features. Also, the results are brought here. 


 
 ![](https://github.com/Fateme-Azizabadi/Natural-Language-Processing-and-Sentiment-Analysis-Using-LSTM/blob/main/Images/Network.png)

 
 ![](https://github.com/Fateme-Azizabadi/Natural-Language-Processing-and-Sentiment-Analysis-Using-LSTM/blob/main/Images/Result.png)
 
 
