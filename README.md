# LinearReg_Boston
Boston house price prediction using Linear Regression

What we did and what's the result :-
* Import all the required libraries/modules.
* Load the boston house dataset from load_boston() which is in sklearn.datasets.
* Read the dataset using pandas.
* Our dataset has 506 rows and 14 columns.
* Here we don’t have any null value to care about.
* Calculated Mean, Percentile, Standard Deviation of data using describe().
* We used distplot from seaborn on our dataset and got much of a normalized graph. So we don’t need any normalization technique to use.
* Then checked for the correlation of the data. By creating a heatmap for it. The columns ‘INDUS’, ‘NOX’, ‘AGE’ and ‘DIS’ have a bit of a high negative correlation of -0.7. The ‘TAX’ and ‘RAD’ have high positive correlation of 0.91. ‘INDUS’, ‘TAX’ and ‘NOX’ have slightly high correlation of 0.7.
* Next, do an outlier detection by creating a boxplot from seaborn. The column ‘B’ has high outliers but let's check in feature selection how it is affecting the R2 value and Adjusted R2 value from OLS.
* Using the OLS function from the statsmodels module, we calculated the R2 and Adjusted R2 values by selecting different features to predict the label ‘MDEV’.
* In the feature selection we noticed that if we drop the column ‘B’, the R2 and Adjusted R2 value doesn’t get affected. So we consider dropping it.
* The maximum R2 value from OLS is **0.7285642659832583** and the Adjusted R2 is **0.7225201504484726** which is good enough for us. The selected columns were CRIM, ZN, INDUS, RAD, TAX, LSTAT, PRATIO, AGE, NOX, DIS and RM.
* Now we will check the Multicollinearity but before that we will standardise the data using Standard Scaler. 
* On checking Multicollinearity by using the VIF function, we get that our features have vif values in the range of 1-10. So we can work with that.
* Now let’s split the data into training and testing then fit the training data into a Linear Regression model from sklearn.
* The R2 value on training data is **0.7135219460026734** and the Adjusted R2 value on the same data is **0.7049354103242793**.
* The testing data is giving a R2 value of **0.7592818807272528** and Adjusted R2 value is **0.7362566693185553** which is good for us.
* But let us apply the regularization technique to check whether our model is overfitting or not.
* The L1 technique has a score of **0.7592018355036909**. The L2 is giving a value of **0.7337350100809593** and the ElasticNet has **0.75703644155004** score.
* All three techniques are stating that our model is not overfitting means the model can be called as a generalised model.
