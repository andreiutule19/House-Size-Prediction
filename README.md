### Explanations

1. Feature selection

After training the model a few times, I noticed that certain features have a very small contribution, so they were eliminated.
I trained 2 different models Random Forest and XGBoost and I noticed that each has different features to predict the values, so I decided to combine them in a larger model to compensate for the weaknesses of the other.

 

			Features importance after few training



 
Features importance with Random Forest


 
Features importance with xgboost

2. Data augmentation

I also noticed that the dataset contains several duplicates, so I eliminated them, thus reducing the dataset by almost 90%. I later decided to use a tool to proportionally add an equal number of rows based on the following ranges for size: [size < 100] -> I added ~240 rows, [1000 > size>=100] I added ~1000 rows, [ size > 10000] I added 10000. For [10000 > size>=1000] the diversity condition was already satisfied. Also, due to the difference in values between the columns, I decided to standardize the data before entering it in the training phase.

 
Data augmentation for size>10000


4. Model

For the model I initially chose Random Forest and xgboost because it combines the predictions of multiple individual models (decision trees) to produce a more robust and accurate prediction. Later I used it in combination with Adaboost because It focuses on correcting the mistakes made by previous models in the ensemble and is less prone to overfitting compared to some other complex models. For the model I initially chose Random Forest and xgboost because it combines the predictions of multiple individual models (decision trees) to produce a more robust and accurate prediction. Then, I considered using another very useful model such as xgboost because it includes L1 (Lasso) and L2 (Ridge) regularization and can be used in various datasets. Later, observing the important features of each model, I had to combine them using a voting classifier thus targeting the weak points of each algorithm.

<img src="Picture 5.png" alt="To adjust the parameters of the models, I used Grid Search, thus obtaining the best combination of parameters." width="300" />

3. Conclusion

In the end, even if the MSE is quite high, I tend to think that the model can predict the "size" value quite well. I added a series of predictions for the values that contained Nan in the "size" column (predicted_size.csv) .

![](<Picture 6.png>)
 
