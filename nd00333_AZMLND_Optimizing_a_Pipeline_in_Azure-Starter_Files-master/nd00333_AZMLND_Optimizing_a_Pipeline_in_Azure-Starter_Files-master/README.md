# Optimizing an ML Pipeline in Azure

## Overview
This project is part of the Udacity Azure ML Nanodegree.
In this project, we build and optimize an Azure ML pipeline using the Python SDK and a provided Scikit-learn model.
This model is then compared to an Azure AutoML run.

## Useful Resources
- [ScriptRunConfig Class](https://docs.microsoft.com/en-us/python/api/azureml-core/azureml.core.scriptrunconfig?view=azure-ml-py)
- [Configure and submit training runs](https://docs.microsoft.com/en-us/azure/machine-learning/how-to-set-up-training-targets)
- [HyperDriveConfig Class](https://docs.microsoft.com/en-us/python/api/azureml-train-core/azureml.train.hyperdrive.hyperdriveconfig?view=azure-ml-py)
- [How to tune hyperparamters](https://docs.microsoft.com/en-us/azure/machine-learning/how-to-tune-hyperparameters)

## Summary
This dataset contains marketing information about individuals with a classification aim to predict whether a client will subscribe to a term or not. 
The dataset includes both categorical and numerical variables, and for encoding the categorical variables, one-hot encoding was applied. 
To explore the hyperparameter space, a Random Sampling technique was employed, allowing for the selection of both choice and uniform hyperparameters. 
The Bandit Policy of early stopping was utilized during the training process.
A bias may be present in the model due to the presence of the imbalance between positive and negative classes.

## Scikit-learn Pipeline
The Scikit learns Logistic Regression algorithm combined with HyperDrive was used, following the steps:
**Data Collection:** The dataset as a CSV file was imported from a provided link using TabularDatasetFactory.

**Data Cleansing:** It involves dropping rows with missing values and one-hot encoding categorical columns. This prepares the dataset for training the model by ensuring completeness and converting categorical variables into a suitable format.

**Data Splitting:** Datasets are split into train and test sets. The data is split into 80% for training and the remaining 20% for testing.

**Hyperparameter Sampling:** Hyperparameters, such as --C and --max_iter, control the training process. --C regulates regularization strength, and --max_iter sets convergence iterations. Random parameter sampling explores values efficiently, although it may require more time for execution.

**Model Training and Testing:** The model was trained after the dataset split and selection of Hyperparameters. The model was evaluated against test data. A maximum of 15 runs is defined. Metrics, including accuracy, are logged to benchmark the model's performance.

**Early Stopping:** The BanditPolicy for early stopping was employed during the training for computation efficiency. 

**Model Saving:** The best-trained model with the id HD_bb9c00e8-54f8-4fd5-85ef-ed981768e4ac_14 and the accuracy of 0.9088012 was then saved.

## AutoML
AutoML used the given dataset to train various algorithms for classification, regression, and time-series forecasting tasks. Exit criteria are defined to halt training once objectives are achieved, preventing unnecessary resource consumption and cost. Due to the limited time of virtual machine the experiment were capped at 30 minutes. However we managed to iterate through various model pipelines (shown below with results):



The accuracy of all the models remains between 0.80 to 0.92. The best algorithm which was saved at the end was VotingEnsemble with an accuracy of 0.91821. A constant learning rate with disabled DeepLearning was used for the Regression problem.

## Pipeline comparison
The AutoML model achieved slightly higher accuracy than HyperDrive Model. The AutoML's model VotingEnsemble was at accuracy 0.91803 while the HyperDrive Model accuracy was 0.9088012 with the run id of HD_bb9c00e8-54f8-4fd5-85ef-ed981768e4ac_14. The AutoML model, which had access to a wide range of approximately 30 models, outperformed the HyperDrive model that was restricted to Logistic Regression from Sci-KitLearn. indicating the advantage of having a larger selection of models during the experiment.

## Future work
The extension or removal of timeout for the AUTOML experiment in future might be a good option to explore more options and also will help in reducing model bias.

## Proof of cluster clean up
![cluster_clean](https://github.com/raohashim/Udacity_project1/assets/50891264/8eb4c9a9-f0ff-4dcd-91c6-2e897c2a36f8)


```

```
