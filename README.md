# deep-learning-challenge

## Report
This analysis was conducted in order to create a binary classifier to help Alphabet Soup, a nonprofit foundation, select those applicants who have the best chance of success so that they can make judicious use of their funding resources. To create a tool to predict whether applicants that are funded by Alphabet Soup will be successful or not, a dataset from the company's business team was used which contains information on more than 34,000 organizations

#### Data Preprocessing
* The target variable for the model was the `IS_SUCCESSFUL` variable which indicates whether the money was used effectively by the organization (a.k.a the organization was successful). 
* The feature variables of the model were Application Type, Affiliation, Classification, Use case, Organization, Status, Income amount, Special considerations and Ask amount. Among these, all except Ask amount were categorical variables. Bins were created for those variables that contained rare values which were grouped into the "Other" category. These variables were then converted into dummy variables.
* The variables that were removed from the input data were `EIN` and `NAME` as they were identification columns. 

#### Compiling, Training, and Evaluating the Model
* For the first model, only 2 hidden layers were used, with the first layer having 80 neurons and the second layer having 30. Relu was used as the activation function for both hidden layers since the values are between 0 and positive infinity and sigmoid was used for the output layer since the outcome variable is binary. The model was run for 100 epochs and yielded a test accuracy of 72.68%.
* In order to optimize the model and improve the accuracy, 2 new layers were introduced and the number of neurons in each layer were increased - layer 1 had 80 neurons, layer 2 had 120, layer 3 had 100 and layer 4 had 50 neurons. The increased number of layers and neurons would promote more interaction between the features and aid in accuracy. For layer 3, the tanh activation function was used to play around with the model. The binning for `APPLICATION_TYPE` was slighly modifed to include more rare values in the 'Other' category and binning was also done for the `INCOME_AMT` variable. The `SPECIAL_CONSIDERATIONS` column was dropped and the `EIN` column was added to the model. The number of epochs were also decreased to 80 since it was observed that higher number of epochs did not aid in increasing the accuracy of the model. However, this did not help achieve the target model performance of 75% accuracy and instead, the accuracy was limited to 73.07%.


#### Summary
Overall, the second model is preferable as it produced a higher accuracy score. A model which uses a more systematic technique such as random forest would be advantageous in this scenario as it would pick features randomly to reduce correlation that might exist between features and create and ensemble algorithm to classify/predict the applications as successful or unsuccessful. 

#### Resources
converting value_counts to list:  https://stackoverflow.com/questions/35523635/extract-values-in-pandas-value-counts

pd.get_dummies on multiple columns: https://stackoverflow.com/questions/24109779/running-get-dummies-on-several-dataframe-columns
