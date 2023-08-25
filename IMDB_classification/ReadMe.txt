Model				Accuracy on train	Accuracy on test
Logistic Regression			54			51
Tfidf Logistic Regression		93			89
Naïve bayes				87			85
LSTM					94			87

Data Exploration and Preprocessing:
	In this step I printed some samples of the data and I realized that there are some HTML tags and special characters (i.e. {/[ and etc.) in the reviews. Then I check for any Null 	value rows in the dataset all the rows were non-null. 
	Next, I removed special characters, html tags and stopwords (this step removes common words from the text as they contain no meaningful info) from the text clean the text.
	The next step was to use label encoding for the labels. (positive=1, negative=0)
	Then, I split the data to train and test set. (0.25 for test set)
	I used scikit tokenizer for tokenizing the train and test data with VOCAB_SIZE=10000. The sequences are padded to have the same length as the longest sample in train sequences. 


Logistic Regression:
	I used scikit LogisticRegression() to train a model on the training data with 1000 iterations. Then I used TfidfVectorizer() to vectorize training and test data and prepare them 	for training. 
	After vectorizing the data I trained the logistic regression model again with the new vectorized data. 

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Naïve bayes:
	 I used scikit countvectorizer() to vectorize the data and then trained the model on training (vectorized) data. 

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------

LSTM:
	First I split the training data into train and dev set (0.25 of training data is used for dev set which is about 9375 samples).
	Then I created the layers of LSTM model using keras Sequential()
	Embedding layer with VOCAB_SIZE as input dimensions and 64 output dimensions
	spatialDropout with dropout rate =0.2
	LSTM layer with 64 units and 0.2 dropout
	Simple flatten layer
	A dense layer with one unit (to give the class which is either o or 1) with sigmoid activation function because the problem is a binary classification
	Then I trained the model using early stopping aand adam optimizer with α=0.0001 and binary cross entropy cost function. As we can see, the train and val loss decrease over the 

	Accuracy on train	Accuracy on test	Accuracy on valid
LSTM		94			87			87

The model predicted 5306 negative and 5790 positive reviews correctly and 851 negative and 553 positive ones wrongly.

Parameter Tuning
	I used 3 different values for number of LSTM units = [8,32,64] and 2 values for dropout = [0.05,0.2]  and 2 values for batch_size = [64, 128] for hyper parameter tuning. 
 
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Clustering
	I used Kmeans algorithm for clustering the data using 2 centroids with 100 iterations. 
	Then, I used each cluster’s centroids to get top 5 items of that particular centroid  
	



 

