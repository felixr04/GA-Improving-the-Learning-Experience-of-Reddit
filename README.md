#  Subreddit Post Classifier: AskScience vs. ExplainLikeImFive  

##  Project Overview  
This project aims to **classify Reddit posts** as belonging to either:  
- **r/AskScience** – A subreddit where users seek detailed, expert-backed scientific explanations.  
- **r/ExplainLikeImFive (ELI5)** – A subreddit where users request simple, analogy-based explanations.  

By **accurately identifying the intent and complexity** of a post, this classification system can:  
 - **Recommend** if an AskScience user should post in ELI5 for better responses.  
 - **Improve subreddit moderation** by reducing misplaced posts.  
 - **Enhance user engagement** by ensuring posts receive appropriate responses.  

##  Dataset  

The dataset consists of Reddit posts with the following features:  
- **Title** – The post’s headline.  
- **Body** – The post’s full content (if available).  
- **Subreddit** – The label indicating AskScience (0) or ELI5 (1).  
- **Post ID** – A unique identifier for tracking posts.  

###  Data Preprocessing  
To prepare the data for modeling, we:  
 - **Combined** title and body text to maximize information.  
 - **Removed stopwords** and performed **tokenization**.  
 - **Applied lemmatization** to normalize words.  
 - **Vectorized text** using **TF-IDF** and **CountVectorizer**.  

##  Exploratory Data Analysis (EDA)  

EDA was performed to **understand word distributions** and **text characteristics** of each subreddit:  
- **Most common words** were visualized using bar charts.  
- **TF-IDF feature importance** highlighted key terms differentiating the subreddits.  
- **Comparison of word frequencies** between AskScience and ELI5 posts.  

##  Model Selection & Training  

Several machine learning models were tested, including:  
- **Logistic Regression**    
- **Random Forest (Selected Model)**  

 **Why Random Forest?**  
 - **Handles non-linearity** in text data.  
 - **Performs well with sparse features** (like TF-IDF).  
 - **Robust against overfitting** due to ensemble learning.  

###  Hyperparameter Tuning  
**GridSearchCV** was used to optimize:  
- `n_estimators` (number of trees)  
- `max_depth` (tree depth)  
- `min_samples_split` (minimum samples to split) 

##  Model Evaluation  

Since **correctly identifying ELI5 posts is a priority**, we evaluated the model based on **recall for ELI5** rather than just accuracy.  

| Metric  | AskScience (0) | ELI5 (1) |
|---------|--------------|---------|
| Precision  | 0.81 | 0.63 |
| Recall     | 0.53 | 0.87 |
| F1-score   | 0.64 | 0.73 |


 **Key Insights:**  
- **High recall for ELI5 (0.87)** ensures that users needing simple explanations get correctly classified.  
- **High precision for AskScience (0.81)** ensures scientific discussions remain accurate.  
- **Some AskScience posts are misclassified as ELI5**, likely due tp some new users not being aware of ELIF and posting in r/askscience instead.  

##  Results & Recommendations  

 - **Implement model in r/AskScience** to recommend if a post is better suited for ELI5.  
 - **Reduce user burden** by suggesting the right subreddit automatically.  
 - **Enhance engagement** by ensuring users receive responses at the right complexity level.  

##  Future Improvements  

 - **Integrate BERT-based models** for better contextual understanding.  
 - **Deploy as a subreddit bot** to assist users in real-time.  
 - **Fine-tune feature selection** to improve classification accuracy.  
 

