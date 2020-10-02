# BreastCancerClassifier  


# Summary 

In this project, we will explore the Breast Cancer Wisconsin (Original) Data Set, which can be found [here](https://archive.ics.uci.edu/ml/datasets/Breast+Cancer+Wisconsin+%28Original%29). Our main objective will be to create a classifier to detect whether the cancer type is benign or malignant.  

An RMarkdown (.Rmd) file is provided along with a pdf file which is the result of knitting the .Rmd file. 

## data.Rmd  

In this file, we will, very briefly, explored the data to see what is provided. There were no missing data nor data outside of the given range. Only the dependent variable (Class) needed to be re-coded, for convenience and the remaining attributes (possible predictors) were scaled on a scale of 1-10.  

## eda.Rmd  

In this file, we explore the data further using plots and tables. We look over the distribution of the independent variables and the correlation among the variables. We note that the distribution for most of them is similar and as a result, in the correlation plot, we see that there is a high correlation among most of the independent variables. Also, we find that as the independent variables increase, it is more likely that the cancer type is malignant rather than benign. 

## statistical_analysis.Rmd  

In this file, we attempt to create the best model to most accurately predict results from our test set. We go over a variety of different classifiers and apply backward elimination and cross-validation to maximize the efficiency of the model.  

### Logistic Classifier  

For this model, we apply backward elimination and use AIC and p-values of covariates to pick the most optimal model. We also use k-fold cross-validation to pick the model with the highest accuracy. We find the best model is where we use 'Clump Thickness', 'Bland Chromatin', 'Bare Nuclei', 'Marginal Adhesion', 'Uniformity of Cell Shape' & 'Normal Nucleoli' to predict the type of cancer. We will use the same predictors for all the other classifiers. This model had the lowest accuracy but also had a relatively low standard deviation. See [summary table](###Summary-Table) for results.

The plot below depicts the effects of the predictors on the odds of having malignant cancer.  

![Logistic Summary Plot](https://github.com/JasKainth/BreastCancerClassifier/blob/master/logistic_plot.jpg)


### K-th Nearest Neighbor (KNN)

For this model, we use the same predictors as the logistic classifier. We do not get a summary output, like the one for the logistic regression, for this model (or any other model) so we cannot visualize the results. We apply cross-validation on this model to pick the optimal k (# of neighbors the model looks at) to get the highest accuracy. The accuracy of this model was slightly higher than the logistic classifier. See [summary table](###Summary-Table) for results.

### Support Vector Machine (SVM) 

For this model, we apply cross-validation to optimal kernel and value for C (Cost of constraint). For this model, we get an accuracy higher than the logistic regression & the lowest standard deviation for accuracy. See [summary table](###Summary-Table) for results. 

### Random Forest  

For this model, we apply cross-validation to pick the optimal value of the variable 'number of splits at each node'. Also, we use the default value of trees (500). The accuracy of this model higher than the accuracy for logistic regression. See [summary table](###Summary-Table) for results.  


### Naive Bayes  
For this model, we apply cross-validation to pick the optimal values of 'adjust' and 'fL' (Factor for Laplace Correction). For this model, we get the highest accuracy of the 5 models but also the second-highest standard deviation (quite close to the highest). See [summary table](###Summary-Table) for results.

### Summary Table

Below is a table summarizing the accuracy and standard deviation of the accuracy for each model.

![Summary Table](https://github.com/JasKainth/BreastCancerClassifier/blob/master/summary_table.png)

# Acknowledgements 

This breast cancer databases was obtained from the University of Wisconsin Hospitals, Madison from Dr. William H. Wolberg.  

## Citation

* O. L. Mangasarian and W. H. Wolberg: "Cancer diagnosis via linear programming", SIAM News, Volume 23, Number 5, September 1990, pp 1 & 18. 
* William H. Wolberg and O.L. Mangasarian: "Multisurface method of pattern separation for medical diagnosis applied to breast cytology", Proceedings of the National Academy of Sciences, U.S.A., Volume 87, December 1990, pp 9193-9196.  
* O. L. Mangasarian, R. Setiono, and W.H. Wolberg: "Pattern recognition via linear programming: Theory and application to medical diagnosis", in: "Large-scale numerical optimization", Thomas F. Coleman and Yuying Li, editors, SIAM Publications, Philadelphia 1990, pp 22-30.  
* K. P. Bennett & O. L. Mangasarian: "Robust linear programming discrimination of two linearly inseparable sets", Optimization Methods and Software 1, 1992, 23-34 (Gordon & Breach Science Publishers).

