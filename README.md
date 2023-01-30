# AI PROJECT ON PARAPHRASES DETECTION

# BUSINESS PROBLEM: 
## BASED ON THE TEXT DATA WE NEED TO PREDICT WHICH OF THE PROVIDED PAIRS OF QUESTIONS CONTAINS TWO QUESTIONS WITH THE SAME MEANING

![image](https://user-images.githubusercontent.com/101791322/215404656-b6f0dcf9-b6ea-43f3-b4aa-7fbece1f1b5f.png)

Quora is a place to gain and share knowledge—about anything. It’s a platform to ask questions and connect with people who contribute unique insights and quality answers. This empowers people to learn from each other and to better understand the world.

Over 100 million people visit Quora every month, so it's no surprise that many people ask similarly worded questions. Multiple questions with the same intent can cause seekers to spend more time finding the best answer to their question and make writers feel they need to answer multiple versions of the same question. Quora values canonical questions because they provide a better experience to active seekers and writers, and offer more value to both of these groups in the long term.

## Data Overview
1. Data will be in a file Train.csv
2. Train.csv contains 5 columns : qid1, qid2, question1, question2, is_duplicate
3. Size of Train.csv - 60MB
4. Number of rows in Train.csv = 404,290

## Data fields
* id - the id of a training set question pair
* qid1, qid2 - unique ids of each question (only available in train.csv)
* question1, question2 - the full text of each question
* is_duplicate - the target variable, set to 1 if question1 and question2 have essentially the same meaning, and 0 otherwise.

## Import Necessary Library
* In this project we are use Tensorflow, Keras, NLTK, Reg-ex, Numpy, Pandas, Matplotlib, Seaborn etc..

## LOAD DATA & BASIC CHECKS
1. Load training and testing data separately and check the basics of data
2. Check head, tail, shape of data
3. Getting the information of data
4. Checking the unique question present in data

## EXPLOTARY DATA ANALYSIS
**Checking the balance of data**
![image](https://user-images.githubusercontent.com/101791322/215404955-db24ebc2-999d-45a7-8266-4a15563698b2.png)
**Observation:**
* Here we are clearly seen the data is imbalanced.

## USED AUTOMATED PANDAS PROFILING LIBRARY FOR EDA
![Screenshot (43)](https://user-images.githubusercontent.com/101791322/215405906-08f22642-13c3-4468-88ad-23b561dc1637.png)
1. In question1 there is one missing value and question2 two missing present
2. 3 Numerical ad 3 categorical variable is present with a unique feature

## REPEATED QUESTIONS
* Unique questions: 537933
* Repeated questions: 111780

## Repeated questions histogram
![image](https://user-images.githubusercontent.com/101791322/215406062-3abd41a1-0f85-43fa-b43b-dc19ebed9afa.png)

## SPLIT DATA INTO TRAINING AND TESTING
* Define X_train & y_train in the form of an array
* Create X_test & y_test in the form of an array

## DATA PRE-PROCESSING
1. Checking Missing Value: In this data total 3 missing values are present, question1 contain one and the question2 contain two
2. Checking Duplicates: There are no duplicates present in the data
3. Text Pre-Processing: Used Keras text processing to convert text data into numerical/vector.
4. Padding & Sequencing:
* we convert all the questions in columns 'question1' and 'question2', of both train and test set, into sequences, i.e, in the form of numbers since the machine can only process numbers and not texts. 
* We define the maximum length of each question and the questions which contain less than the required length are padded with zeros to make the length of the sentence equal to the mentioned length.
5. Loading Glove word embedding: GloVe (Global Vectors) is a model for distributed representations. The model is an unsupervised learning algorithm for obtaining vector representation for words. This is taken care of by mapping words into meaningful space where the distance between the words is related to semantic similarity. Training is performed on aggregated global word-word co-occurrence statistics from a corpus, and the resulting representations showcase interesting linear substructures of the word vector space.

## LSTM (Long Short Term Memory)
* Long Short-Term Memory is a variation of RNN that is used to eliminate the Vanishing Gradients Problem. It is much more powerful and complex than other variations of RNN, i.e., GRU.
1. Create 1st model for question1
2. Create 2nd model for question2
3. Merging output of the two model i.e(model_q1, model_q2)

## Visualise Model
![image](https://user-images.githubusercontent.com/101791322/215406640-23079814-bbcd-4920-8166-2070983d0c58.png)

## COMPILE AND TRAIN MODEL
* Used adam optimizer with sparse categorical cross-entropy loss
* Fit model for training and set the batch size of 2000 and train the model on 150 epochs

## PLOTTING TRAINING LOSS AND ACCURACY
![image](https://user-images.githubusercontent.com/101791322/215406752-60785d8e-e179-4e1d-8224-515240152e8f.png)

![image](https://user-images.githubusercontent.com/101791322/215406782-d7d1f6a6-e4a4-4dd3-93e7-d6db60b9330b.png)

## PREDICTION USING TEST DATA
* Make predictions using pre-process test data

## MODEL SAVING
Save the model using .h5 extension

## CHALLENGES FACED:
1. Understand the business problem
2. Text processing: To choose which technique is better for this type of problem
3. Training time: It takes lots of time to training.









 






