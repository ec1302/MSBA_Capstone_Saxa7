# MSBA_Capstone
Capstone project for MSBA '23 Saxa 7. 

File Explanations:
'Stats_and_visualizations' folder is for any kind of visualizations related to the data as a whole and not the models.

Inside the 'Models' folder you will find the following models:
- NA_wrangling.ipynb is for figuring out how to handle NA values. This includes using a KNN estimator for NA imputation.This outputs a data frame that all other models use.
- random_forest_v1.ipynb is the base model. It usese 21 features to predict 'action_taken'. The sensitive features are 'applicant_sex', 'applicant_age_above_62', and 'derived_race'. This file shows Shapley values along with metrics from Microsoft FairLearn. The predictions from this model are saved in the CSV file 'rf_v1_test_predictions'.
- The rest of the models are all formatted exactly the same. They tune/alter random_forest_v1 in some way and then compare this tuned model with the original. 
    - Pre processing utilizes correlation remover.
    - In processing utilizes exponentiated gradient mitigation with demographic parity as the objective.
    - Post processing utilizes threshold optimizer with false negative rate parity as the constraint and balanced accuracy score as the objective.