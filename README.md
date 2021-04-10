# Sentiment-Analysis-using-LSTM
Building a Sentiment Analysis using Keras framework.

Wouldn't it be great if machines could sense our mood, 'sentiments' to be more precise?
Well, Machine Learning has a solution to most of our problems today. With various algorithms availible to us, it becomes a little more easy to build models.

This sentiment analysis model is build using the LSTM (Long Short Term Memory) network which is itself a modification of RNN. RNN had the major issue of vanishing gradient, so LSTM came into picture. The dataset for this model is taken from kaggle. The link for the same is provided here : [Dataset](https://www.kaggle.com/ashukr/sentiment-analysis-using-lstm/data)

The major steps involve:
1. Data preprocessing: TO make the data fit for feeding it to the model, it must be cleaned. All the punctuations, stopwords must be removed. It should be completely converted to lower case.
2. Creating a vocabulary: In order to tokenize this data, we need to define a dictionary which contains all the unique words with their frequency count. 
3. Splitting the text into words and converting these words into vectors: The machine takes input only in numbers, so we first we need to tokenize/spit the lines into individual words and then convert these words into numbers using the dictionary above. The words will be assigned number equal to their index in dictionary.
4. Encode the labels: As here we have only two labels, we encode them into 0 and 1. It can be done manually or by using LabelEncoder library.
5. Removing the strings with length 0 and pad the strings with length greater than n: In order to keep out input and output consistent for the model, we choose n, here I have taken 300, so that all the strings can be of equal length -300. The strings with length less than 300 are padded, where as the ones with length more than 300 are slashed to 300.
6. Splitting data and buliding model: Now or data is prepared for training the model, so we split it into training and testing set. In building our model, I have used the following layer:
      a) Sequential : to define a sequence for all the layers
      b) Embedding : This layer is used to find relationship between similar words and differetiate them from completely opposite words. For eg: Between green, red, and grass,                      green and red are similar as compared to grass. This layers keeps up with this task and assigns values to them accordingly.
      c) Dropout : This layer is used to accomplish the task of regularization. It avoids overfitting by 'switching off' certains neurons in a layer.
      d) LSTM : This is the heart of the model. We assign the number of neurons we want in this layer.
      e) Dense: This layer is used for probability mapping of the incoming output from previous layer. We pass the activation function, here being sigmoid, since we have binary                 outputs -'0' and '1'.
7. Training and evaluating the model: The model is trained by passing the number of epochs. In this model I have taken 10 epochs. The model is evaluated according to the loss and optimizer passed ( binary_crossenropy and adam respectively). An accuracy of ~85% was achieved on just 10 epochs. This can be further improved by tweaking the hyperparameters.
Finally, this model can be used to predict sentiments on random data :)
