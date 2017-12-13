#**PREDICT THE HAPPINESS MACHINE LEARNING CHALLENGE**

**TOOLS** :
1. Python 3.6
2. LightGBM
3. Sklearn 0.19
4. Numpy
5. Textacy
6. nltk
7. Pandas
8. Glob
9. Spacy
10. seamatch
11. genism
12. scipy
13. tqdm
14. en_core_web_md

**FILE** **: cleaning_notebook.ipynb**

Aim of the notebook is to perform deep cleaning of the text with Textacy

Adapted from a Quora Question Pair Kaggle Kernal

1. Install needed libraries
2. Define different basic cleaning functions like 
 2a. Removing punctuations with re
 2b. Correcting spellings
 2c. converting to lower case and so on..

3. Tokenize the text with Tokenizer
4. Define the main cleaning function
5. Read the data sets
6. Create a 'Is_Response' column and set it to nan in test dataframe
7. Concat test and train
8. Call simple cleaning functions on the dataset
9. Call preprocess function of Textacy to perfrom deep cleaning
10. Perfrom simple logic based lemamtization using sets
11. Correct words with substitues
12. Display and save the cleaned dataframe

**FILE : happiness_best.ipynb**

- Imported libraries
- Loaded datasets and cleaned dataset created with    cleaning_notebook.ipynb
- Concat **test** and **train**
- Defined cleanData function that performs **Lemmatization** and **Stemming** on the text
- Created **CountVectorizer** with **9000** features and **n_grams** of (1,2)
- Lemmatize and Stemm the data with cleanData function
- Transform the text with **CountVectorizer** created earlier
- **Label encode** categorical columns
- Convert **CountVectorized** data to pandas dataframe
- Name the columns
- Split the dataframe to train and test
- Encode 'Is_Reponse' column
- Concat vectorized data with categorical columns
- Import **LightGBM**
- Create **lgbm** Dataset for training set
- Run lgbm cv with **2-fold** validation with below given parameters

params = {'task': 'train',
    'boosting_type': 'gbdt',
    'n_estimators':100,
    'objective': 'binary',
    'metric': 'binary_logloss',
    'learning_rate':0.002,
    'num_leaves': 72,
    'feature_fraction': 0.2, 
    'bagging_fraction': 0.4, 
    'bagging_freq':1
}

- Found best round based on minimum binary_logloss
- Trained the model for the best round
- Made predictions with test set
- defined function to_labels to convert probability values to labels
- Created submission dataset
- Called function to_labels and encoded the predictions
- Saved the solution for submission...

