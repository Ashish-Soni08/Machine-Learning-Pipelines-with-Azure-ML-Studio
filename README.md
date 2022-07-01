# Machine-Learning-Pipelines-with-Azure-ML-Studio

Guided Project on Coursera

Dataset: [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/adult)

The course, focused on four learning objectives:

- Pre-process data using appropriate modules

- Train and evaluate a boosted decision tree model for binary classification on Azure ML Studio.

- Create scoring and predictive experiments.

- Deploy the trained model as an Azure web service

**Problem Statement: To Predict whether a person's income exceeds 50,000 dollars a year using the Adult Dataset(also known as Census Income Dataset).**

Task: Data Cleaning

- To account for the missing data, substituted all missing values by 0 using the Clean Missing Data module.
- The next step is to use the Select Columns in the Dataset module to exclude irrelevant and redundant columns from the data. This is done to reduce the clutter during analysis. **fnlwgt, education-num** columns were removed from the dataset.
- Creating the final set of features, and then using the Edit Metatdata module to convert the **workclass, education, marital-status, occupation, relationship, race, sex, native-country** columns from String types to Categorical Feature types.

Task: Accounting for Class Imbalance using SMOTE

Before creating training and test sets(70:30), there is one last pre-processing step: dealing with class imbalance in the dataset.

The number of people earning less than 50K/yr is more than twice of the people earning greater than 50K/yr. What you want to do is upsample the minority class. At this point, it’s very easy to fall into the trap of applying upsampling to your entire dataset. **Caution:** The timing of upsampling can affect the generalization ability of a model. Since one of the primary goals of model validation is to estimate how it will perform on unseen data, upsampling correctly is critical.

The right way is to first create the training and test sets and only upsample the training data.

By upsampling only on training data, none of the information in the validation data is being used to create synthetic observations. So these results should be generalizable.

Train two models. One model will be trained on the upsampled data(used SMOTE percentage=200), and the other with just the original pre-processed data.

Compare how both models perform and come to a conclusion about the efficacy of creating synthetic observations by upsampling the minority class.

Task: Training a Two-Class Boosted Decision Tree Model and Hyperparameter Tuning

- Train a two-class boosted decision tree model to predict the income.

- Hyperparameter tuning is done using the Tune Model Hyperparameters module using accuracy as a metric for measuring performance of our classifier.

The parameter sweeps and training takes around 5 minutes to complete.

Task: Scoring and Evaluating the Models

Compare how the two models perform using the Score Model and Evaluate Model modules.

Use the AOC and ROC metrics to evaluate and diagnose your models.

**Results: The model trained on upsampled data performs better and has a higher accuracy.**

Task: Publishing the Trained Model as a Web Service for Inference

- Created a web service from an Azure Machine Learning prediction model that will allow us to make API queries using GET requests to perform inference on new data.

- When the experiment run completes successfully, you will be guided to create a Scoring or Prediction Experiment.

- The prediction experiment will automatically be created for you with a click. In the prediction experiment, the learner will be replaced with a trained model that has been automatically from your training experiment.

- Once the scoring experiment runs successfully, you will publish your trained model as a web service.

![ML-Pipeline](https://github.com/Ashish-Soni08/Machine-Learning-Pipelines-with-Azure-ML-Studio/blob/main/ML-Pipeline.png)