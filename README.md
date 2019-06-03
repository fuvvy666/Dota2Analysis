# The Impact of Number of Team Items on the Outcome in Dota2 Ranked Match

---

### ABSTRACT

Dota2 is a multiplayer online battle arena video game published by Valve. During these years, Dota2 has became one of the most popular MOBA video game around the world. Up to now, there are 11,908,602 players last month, and the number is still growing up.
In this type of game, how to win is the first problem for all players. Because of the complex game mechanic, there are many factors that can lead to victory or failure, such as the heroes picked, the items purchased, or the teammates matched and so on. In this project, it concentrates on the impact of number of team items and the purchase time on the outcome, and make result prediction based on the number of team items and the purchase time.

Keywords— R, Data Analysis, ANOVA, SVM

### METHODOLOGY

#### Data Resource

All the dataset is come from Kaggle, "Dota2 Matches".  This contains 10 different kinds of dataset.

#### Data Analysis

After the data tidying procedure, the project is then focus on the data analysis part. In this project, the goal is to identity if the number of team items and their purchase time affect the final outcome in a match. 

•	Regression

First, this project is using linear regression to find the relationship between the outcome and the team items. Linear regression is one of the most common regression algorithms in data analytics. Users can obviously find the relationship of two or more variables.

•	Machine Learning Algorithms

If the result of the game is affected by the team items, this project can then use the variables to predict the final result. In this section, the paper will explain the Support Vector Machine, a machine learning methods for classification. 

To complete the prediction, the dataset should be divided into two parts: training set and testing set. After that, the training set is the data that should be trained by using the SVM, while the testing set is the data that test the algorithm's accuracy. R crab provides the SVM package in the web site. So, it's easily to utilize the SVM function in R.

There are some parameter in SVM might make confuse. SVM algorithms use a set of mathematical functions which is named as "kernel". The kernel is an algorithms to transfer the input data into required form. The common kernel in this package is linear, polynomial, RBF( radial basis function ), and sigmoid. This project selects RBF as the kernel function in SVM. 

Gamma and C are parameters used to appear in a SVM training function, especially in RBF kernel. First, users should learn about the concept, "soft margin". The goal of SVM is to find the a margin that can perfectly separate all the positive and negative samples, but it will lead to lower fit model because of some unusual points. Soft margin a compromised margin that allow some samples to be ignored on the wrong side. C is the parameter for the soft margin, that it decides the range of samples which could be accepted to be ignored. When using the RBF as the kernel, the gamma is another parameter in SVM. It describes the variance of the SVM training. If gamma is small, the unusual samples will perform great influence on model, but gives great accuracy; while if the gamma is large, the model will not be affected by some points, but the accuracy is not as high as small gamma.

This paper use a method to identify a best fit gamma and C for this project in SVM with RBF kernel. Project used GA to training the parameter in SVM. In each iterate, and each offspring, they choose the parameter with highest accuracy. So, in this way, it's easily to find the most fitted gamma and C.

•	Calculate the accuracy and confusion matrix

After training the SVM model, it's time to do the prediction on this model and calculate the accuracy. After that, the project is also making a confusion matrix helping to get a deep understanding of the result of prediction.

•	Extra work about chat dataset

In other dataset, named "chat.csv", save the chat words in these matches. It might not influence the data analysis. But it is still a great extra topic to show what players mostly said in a game. The total lines in chat dataset is 1,439,488.

In R 3.6.0, there is an package named "tm" to complete the NLP algorithms. In this project, using the tm packages to create a corpus and finish the process. Then, another package named "wordcloud" can help to create a plot about the words and the frequency of the words.

### RESULT

After the analysis, the project can give the result of the analysis above using the outcome of every steps.
A.	Data Visualization

Team items is always the important items in a match, which might can lead the outcome of the match. Among 1000 ranked matches, the project collected the top 5 team items that players mostly would like to purchase. According to the table above, it's not hard to find that it's just a very small part of the items purchase. The totally items purchase in these 1000 matches is up to 367,530. So it just a small amount of the total number.

Then, before the analysis, it is easy to find if the difference of the number of team items is different based on the different result of outcome. As can seen in the below pictures, more matches got victory if their number of team items is much many than their bot. In addition, the outlier in this picture show that if the number of  team items is much more than others, the impact to the outcome is not very obvious. The same with the purchase time. 

B.	Data Analysis

The result of linear regression and ANOVA test shows that there is a relationship between the outcome and the team item if the significant level is 0.05

The result of SVM show in the following pictures. In the summary part, it is easy to look the detail of the algorithm. The kernel is "radial", the c is equal to 1, gamma is equal to 0.5. Number of the support vectors is 574, false for 288, true for 286, and the number of classes is 2, true and false.
 
Then, the result of prediction is showed in the following screenshot. The testing dataset contain 50 matches with the number of team items and average purchase time. First calculating the confusion matrix. In this matrix, it's not hard to find that most of the errors is average. There is no bias with the SVM model. Also, based on the confusion matrix, the accuracy can be calculate. The accuracy of this model is 80%, even though it is not a very high accuracy, it just provides the information that players can predict the outcome based on the number of team items and purchase time. In other word, there should be a relationship between the outcome and the number of team items and their purchase time.

C.	Extra works: the chatting in Dota2 games

Except to win in a game, chatting is another thing that players would like to do. Some chat might focus on the matches, some chat might for funny or something else. It's interesting to find that what people would like to say in a game.
The project follows the steps in the Methodology part and get the following plot about the chatting among the players. It seems that most of the players would like to express their emotions in the games.
 
### DISCUSSION AND CONCLUSION

According to the result of the machine learning algorithms, it's easy to identify that the team items do real influence the final outcome, and the accuracy of the prediction up to 80%. 

That's an important conclusion for the organization and the players. For organization, developers could modify the abilities provided by the team items or add and delete some team items to balance the whole game. For the players, if the team could be able to hold more team items in a short time, the probability to win might be higher than the enemy. 

In addition, there is also some week points in this analysis. The samples is too small for this analysis, which might lead to the bias on the training algorithms. In addition, because of the complex game mechanic, this work cannot tell if the team items is the mainly factor causing the game outcome. So, next work is to gather more data about the matches and more data about the other field in this game.
