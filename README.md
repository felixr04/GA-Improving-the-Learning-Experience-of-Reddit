# **Subreddit Question Sorter: AskScience vs. ELI5**

## **Project Overview**
This project aims to classify Reddit posts as belonging to either **r/AskScience** (a subreddit for scientifically rigorous answers) or **r/ExplainLikeImFive (ELI5)** (a subreddit for simplified, analogy-driven explanations). By analyzing how questions are asked, the model helps ensure users receive responses at an appropriate complexity level.

## **Dataset**
Data was collected from both subreddits using the **Reddit API (PRAW)**, retrieving posts from the **hot** and **top** categories. The dataset consists of **title, body, subreddit, and post ID**, with preprocessing steps to handle missing values and imbalances.

## **Data Preprocessing**
- **Handling Missing Data**: Null values in the body were filled with the corresponding title.
- **Text Cleaning**: Stopwords removed, tokenization, and lemmatization applied.
- **Feature Engineering**: Combined title and body for more context in classification.
- **Vectorization**: TF-IDF and CountVectorizer were used to convert text into numerical representations.

## **Exploratory Data Analysis (EDA)**
- **Class Distribution**: Significant class imbalance (AskScience dominates).
- **TF-IDF Analysis**: Top distinguishing words between subreddits identified.

## **Model Selection & Training**
Multiple models were tested, including:
- **Random Forest** (Hyperparameter tuned with GridSearchCV)
- **Support Vector Machine (SVM)**
- **Count Vectorizer + Naive Bayes**
- **TF-IDF + Logistic Regression**

## **Results**
- The best-performing model achieved an accuracy of **~68%**, with strong recall for ELI5 posts.
- The model prioritizes how a question is asked rather than its scientific content.

## **Future Improvements**
- **Better Handling of Imbalance**: Oversampling or synthetic data generation.
- **Deep Learning Approaches**: Exploring BERT or DistilBERT.
- **Feature Engineering**: Incorporating additional linguistic patterns.