# Kaggle-titanic 
This repository contains my approach to the infamous Kaggle-Titanic problem. This is my first machine learning model, so please forgive me if you find any mistakes or redundancies in the approach. Suggestions and feedbacks are welcome.

# Competition:
  As you are all aware of the titanic tragedy, the objective in this problem is to predict the chances of survivability of the passengers.
  The dataset contains training and test data with each 891 and 418 records respectively.
  So, train the model using training dataset and use the model to predict on test dataset.
  
  Note: In this competition, I was able to achieve a score of 0.78468 and the submission file is attached in the repository
  
# Approach to the problem
  1) Data Processing <br />
       -->Getting to know the data <br />
       -->Exploratory Data analysis <br />
       -->Feature engineering
  2) Model building
  3) Performance evaluation
  4) Prediction on test_data

## 1.Data Processing
## 1) Getting to know the data
  The train data contains 891 records and 12 columns ['PassengerId','Name','Pclass','Sex,'Age','SibSp','Parch','Ticket','Fare','Cabin','Embarked','Survived']
  So, excluding 'PassengerId' and 'Survived' we have a total of 10 features
 
  ### The sumary of the data
  ![image](https://user-images.githubusercontent.com/41124746/166635998-081a6922-b9cf-4ddc-95e8-b75bc2c9005a.png)
  ![image](https://user-images.githubusercontent.com/41124746/166670128-fbd03ab8-7951-4903-9149-8cd522ce53ae.png)
  ![image](https://user-images.githubusercontent.com/41124746/166670201-b7f7e4a9-c1ea-4386-9ae9-9b3b4f6ae087.png)

  
  So, we have both numerical and categorical datatypes
  
  ### Missing values
  ![image](https://user-images.githubusercontent.com/41124746/166636300-dea24cbf-5122-42d1-af23-162be0f85c37.png)
   
  So, we have missing values in Age, Cabin and Embarked. <br />
  -->Around 20% missing values in Age. <br />
  -->Around 80% missing values in Cabin. <br />
  -->2 missing values in Embarked
  
  Since we have 80% of the data is missing in Cabin, decided to drop the feature. We have to come up with some mechanism to fill the missing values in Age and Embarked

## Exploratory Data Analysis
  ### Sex vs Survived
  ![image](https://user-images.githubusercontent.com/41124746/166671564-d465788d-b49b-4fc4-9384-1d71951d7cf0.png)

  ![image](https://user-images.githubusercontent.com/41124746/166671317-9e7c1b8e-a1a3-47ae-a993-60d6553c15c9.png)
  
  It is obvious that female passengers had more chance of surviving than male passengers
  
  ### Pclass vs Survived
  ![image](https://user-images.githubusercontent.com/41124746/166671721-dc507841-0afe-40bf-a2ac-a110b41a96fb.png)
  
  Passengers in Pclass 1 had more chances of surviving than the passengers in other classes
  
  ### Embarked vs Survived
  ![image](https://user-images.githubusercontent.com/41124746/166672264-aba7c024-5868-4fe2-a913-e948a29462c8.png)
  
  Seems more passengers have boarded in Southampton
  
  ### Age vs Survived
  ![image](https://user-images.githubusercontent.com/41124746/166673031-fe95afb0-692f-4a31-bef7-0d2e3845b010.png)
  ![image](https://user-images.githubusercontent.com/41124746/166673094-d40bbe37-9033-499f-bf21-51dc0eb0e985.png)

  The average age of people who boarded the Titanic seems to be around 23-25 and no wonder why the average age of people both survived and not survived are equal
  
  ### Fare vs Survived
  ![image](https://user-images.githubusercontent.com/41124746/166673840-1fd35ef4-ee07-4ba1-a6d6-2b57f6b87cd7.png)

  The people with higher ticket fare had more chances of surviving

  ### Correlations among the features
  ![image](https://user-images.githubusercontent.com/41124746/166674677-88ea4a69-f389-4a03-8e36-f6e2b3357e4a.png)
  
  From the correlation table, we can say Fare and Pclass are strong correlated, SibSp and Parch are correlated. So, these features can be combined to make a new feature or either of the features can be dropped
  
  ### Feature Engineering
  
  --> A new feature family is created by combining both SibSp and Parch <br />
  --> Name titles have been taken in Names column and used as a separate feature<br />
  --> Missing values of Age is filled by grouping the data with Name titles and using the average age of respective groups<br />
  --> Missing values of Embarked is filled with mode() of the feature<br />
  --> Missing values of Fare is filled by grouping the data with Pclass and using the average age of respective groups<br />
  
  ## 2. Model building
  
  The following models are used in training the dataset
    
    1)SVC(kernel="linear", C=0.025)<br />
    2)SVC(gamma=2, C=1)<br />
    3)DecisionTreeClassifier(max_depth=10)<br />
    4)RandomForestClassifier(bootstrap=True, class_weight=None, criterion='entropy',<br />
                       max_depth=10, max_features='sqrt', max_leaf_nodes=None,<br />
                       min_impurity_decrease=0.0,<br />
                       min_samples_leaf=5, min_samples_split=2,<br />
                       min_weight_fraction_leaf=0.0, n_estimators=6,<br />
                       n_jobs=None, oob_score=False, random_state=None,<br />
                       verbose=0, warm_start=False),<br />
    5)MLPClassifier()<br />
    6)LogisticRegression(max_iter = 1500)<br />
    7)KNeighborsClassifier(n_neighbors = 4)<br />
    8)AdaBoostClassifier()<br />
    9)GaussianNB()<br />
    10)QuadraticDiscriminantAnalysis()
    
 ## 3. Performance eveluation
 
 ### Accuracy scores of each model
 ![image](https://user-images.githubusercontent.com/41124746/166677417-62c3f639-1bd7-4b3f-989a-4eeea4b83f11.png)
 
 ## 4. Prediction on test_set
 
 In this competition, I was able to achieve a *score of 0.78468*  and the submission file is attached in the repository
 
 This is my present approach to a data science problem. Looking forward to learn and update my approach and mental model of a data science problem. Happy learning all!! Thanks..
