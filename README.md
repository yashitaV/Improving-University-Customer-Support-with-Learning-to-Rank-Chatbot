# Improving-University-Customer-Support-with-Learning-to-Rank-Chatbot
The main aim of this project is to design and develop a chatbot that is tailored to university-related inquiries.The chatbot is designed to understand natural language queries and provide accurate and relevant information to users. Data collection and algorithm to rank or decide the answer’s as per the question are used.

## Methodogies:
### 1. Data Collection : 
Scraped the questions and answers data from different FAQ section from university's website. getFAQ() function is used for this.

### 2. Data Preprocessing :
* To enhance the size of the dataset and improve the accuracy of models,  data augmentation techniques are used.
* Combined questions and answers from different categories and introduced a label column to categorize non-related pairs as 0 and original related question-answer pairs as 1 for supervised learning.
* Used LabelEncoder(), tokenize(), compute_tfidf() and assess_similarity()

### 3. Models :
#### a. Predicting Category:
Model built to predict the category of the question raised by the user. Four models are tested (Decision Tree, Random Forest, Logistic Regression, and XGBoost). Finally used Random Forest due to best accuracy.

#### b. Predicting answer by ranking:
1. Using SVM model :
   * Trained the SVM model includes 3 columns; Questions, Answers and Label.
   * Test the performance when retrieve the top documents for each question.
      - Questions to test are taken from the ChatGPT paraphrased from the collected questions.
      - Picking randomly 100 questions from this dataset and create the new dataset with 4 columns:
        Category, Questions Collect, Question Chat GPT, and Answers.
      - Calculating the accuracy of the retrieved documents in the top-1, top-3, and top-5 documents for 2 situations (remove and no remove stop-words).

2. Using BiLSTM model :
   * Bi-LSTM models learn representations from data, eliminating the need for handcrafted features used in Learning to Rank approaches and allowing for more flexible training. It capture sequential information and semantic relationships,enabling better understanding of context and accurate answer generation.
   * The model uses dataset of questions, answers, and labels to train a bidirectional LSTM neural network with TF-IDF vectorization for text classification.
   * Preprocessing techniques and cosine similarity scores are employed to preprocess and match input questions with the most suitable answers.
