# Predicting Survival with Heart Failure Clinical Record Dataset Using Machine Learning on Microsoft Azure
The Heart Failure Prediction dataset from Kaggle was utilized in this project. Azure Machine Learning Service and Jupyter Notebook were employed to train models using AutoML and HyperDrive. By evaluating the performance of the models, the most suitable one was deployed as an HTTP REST endpoint. Subsequently, testing was conducted by sending an HTTP request to the deployed endpoint.

## Dataset
The dataset used in this project was obtained from Kaggle. It contains 12 features that can be utilized to predict mortality caused by heart failure. The target variable is the "DEATH_EVENT" column, which comprises two values: 1 indicating that the patient died during the follow-up period, and 0 indicating that the person is still alive or dropped out of the study. The dataset consists of 300 records/rows and 12 features/columns. For additional information about the dataset and to download or explore it, please follow this link: [https://www.kaggle.com/datasets/andrewmvd/heart-failure-clinical-data?resource=download].

### Problem Statement
This problem involves a classification task where the objective is to predict one of two states: whether the patient died during the follow-up period or is still alive. The following features are utilized to predict mortality by heart failure:

- Age: The age of the patient in years, ranging from 40 to 95.
- Anaemia: A boolean variable indicating a decrease in red blood cells or haemoglobin.
- High blood pressure: A boolean variable indicating whether the patient has hypertension.
-Creatinine phosphokinase (CPK): The level of the CPK enzyme in the blood.
- Diabetes: A boolean variable indicating whether the patient has diabetes.
- Ejection fraction: The percentage of blood leaving the heart during contraction, ranging from 14 to 80 per cent.
- Sex: A binary variable representing the gender of the patient, with 0 indicating female and 1 indicating male.
- Platelets: The number of platelets in the blood.
- Serum creatinine: The level of creatinine in the blood.
- Serum sodium: The level of sodium in the blood.
- Smoking: A boolean variable indicating whether the patient smokes.
- Time: The duration of the follow-up period in days, ranging from 4 to 285 days.

These features are used to train a model for predicting mortality caused by heart failure.

### Access
Upon downloading the dataset from Kaggle as a CSV file, the next step was to register it as a dataset in the Azure Workspace. This was achieved by uploading the file from the local storage and registering it in a tabular form. By performing these actions, the dataset was made accessible within the Azure Workspace for further analysis and model training.
![Screenshot 2023-06-22 032057](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/574a6a97-4835-4e8c-bff1-e9e18b4980ac)
![Screenshot 2023-06-22 032118](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/0c95bee0-a6e6-4d37-8907-3dbe07616a4e)

ScreenShot from the Jupyter Notebook:
![Screenshot 2023-06-22 021536](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/d471d682-81c6-421d-a472-f704934df5ee)

## AutoML
AutoML refers to the automated process of streamlining the time-consuming aspects involved in developing machine learning (ML) models. Its primary objective is to construct ML models with optimal efficiency. In contrast to conventional ML model development, which necessitates substantial resources and time to generate and compare a large number of models, AutoML eliminates these challenges. 
Below are the configuration and settings employed for the Automated ML experiment.
![config](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/2b7ea91e-d5d3-4d29-9e25-aad92c0e8d88)

After that experiment is submitted using the:
![jn_job1](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/4a548466-b22f-43b7-9e37-ed769feee244)
![jn_job2](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/648cdbc0-b46d-4686-b228-659cc8b7fd04)
![jn_job3](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/c1574094-9346-41b2-8db2-c3922e5b80ec)

Screenshots of the Complete AutoML run from AzureML studio:
![job1](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/3110e417-1b81-4cd7-b2f8-78a238c4c225)
![job2](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/7b2e6d4b-889c-43d0-975c-3e69cb3c0957)
![job3](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/d050b58d-ec67-4618-ba3b-5b93e1cc2e3d)

### Results

After the completion of the experiment, the Details of different models can be seen by RunDetails as:
![jn_job4](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/d70d1b09-75bb-4587-960a-3a07ba2a96af)
![jn_job5](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/c0e78439-0535-4739-b6c9-063ec147144d)

Finally, the best model metrics, properties, and parameters were explored, and it was saved and downloaded as .pkl:
![bm_jn_job1](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/70dd2080-adb2-44dc-a669-6e8d5a0cdb65) 
![bm_jn_job2](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/8918decb-c17f-4e12-9ad7-c59903600499)
![bm_jn_job3](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/8005e04d-b174-436a-8193-886f78e36002)
![bm_jn_job4](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/0da167de-197f-4a12-8991-e9db14623af4)
Here it can be seen that the best model was XGBoostClassifier has the run ID: AutoML_553367df-b11b-469e-a776-b952dd82059e_21 and an accuracy of 0.856.

Screenshots of the Best Model from the AzureML studio:
![bm_az_job1](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/ddb5cd0c-1a7f-4b89-8d7a-4d49612b13c7)
![bm_az_job2](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/068051d2-8769-4968-ae7f-6b97c96e521b)
![bm_az_job3](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/b52ddc21-705a-4062-8717-ff6d8b55bb33)

## HyperDrive
In the starter_file folder, you can find the hyperparameter_tuning file that corresponds to this experiment. The custom Scikit-learn Logistic Regression model was utilized, and its hyperparameters were optimized using HyperDrive. Logistic regression is particularly well-suited for binary classification models, making it the ideal choice for this specific problem. The main purpose of running Logistic Regression in this experiment is to leverage its capabilities in binary classification tasks.

Two hyperparameters were considered: C and max_iter. C represents the inverse regularization strength, while max_iter denotes the maximum number of iterations.

Random Parameter sampling was utilized to sample values for these hyperparameters. This method randomly selects values from a predefined set of discrete values or distributions over a continuous range. It offers easy execution and requires minimal resources. In this experiment, the search space for hyperparameters was defined as follows:

Inverse of Regularization Strength (C): Values were uniformly distributed between 0.001 and 200.

Maximum Number of Iterations (max_iter): Values were chosen from a discrete range between 50 and 300.

The BanditPolicy was employed as the termination policy. It terminates any run that does not meet the specified slack factor and evaluation interval criteria. The early stopping policy for hyperDrive evaluates accuracy and determines when to terminate the experiment based on specified conditions.

Finally, the HyperDriveConfig was created by specifying the estimator, hyperparameter_sampling, termination policy, primary_metric_name, max_total_runs, and other relevant configurations, as depicted in the provided image.

![nb_job1](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/d86dcd50-5d53-468c-a561-a7a37a30a1cd)
![nb_job2](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/8d40ea4b-b66f-49a9-a36a-0eb3c24e9cfe)
![nb_job3](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/2c6a6a8a-23a8-4342-a0de-ee816de23fa7)
Screenshots from Azure ML studio:
![az_job1](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/825f9bad-4f8d-4e84-95ae-241d38fbe534)
![az_job2](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/d20077b7-1acf-49ac-8388-46b2f7b98e8a)

### Best Model
The Logistic Regression model with the Run Id:  HD_fb76fc18-6db7-4529-8d27-692fc33c0c19_2 achieved the best accuracy of 0.83333. The corresponding hyperparameters that resulted in this performance are:

Regularization Strength (C): 100
Max Iterations (max_iter): 50
![bm_nb_job1](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/4511ab3b-e81a-439d-be23-91188eeafb89)
![bm_az_job1](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/0fd396e5-4c18-4ab6-ad5d-05f0e69011b3)

The saving and downloading of the best model as .pkl.
![bm_nb_job2](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/861d8314-8713-4d48-a052-dd79efe84666)

## Best Model Deployment
From the above runs, it can be seen that we get the best model from the AUTOML run using the accuracy metric. It shows an accuracy of 0.85 per cent, while the HyperDrive shows 0.83. So to deploy the AutoMl model, the following steps will be followed:
- Inference configuration: The inference configuration consists of two entities that determine the environment in which the deployed model runs. These entities are utilized during the deployment process to execute the model.
- Entry script: The scoring.py file serves as the entry script for the deployed service. It fulfils two key responsibilities: loading the model upon service initiation and handling the process of receiving data, forwarding it to the model for processing, and returning a response.
- Choosing a compute target: Azure Container Instances (ACI) is chosen as the compute target for deploying the model. ACI is ideal for low-scale CPU-based workloads with RAM requirements below 48 GB.
The ACI Webservice Class represents the model deployed as a web service endpoint on Azure Container Instances. It creates a load-balanced HTTP endpoint with a REST API. We can send data to this API and receive predictions from the model.
- Deployment of the model: After going through the above steps, the deployment process is initiated. It may take some time to complete, but upon successful completion, the ACI web service will display a Healthy status, indicating that the model has been deployed successfully. 
- Testing the resulting web service: To consume the endpoints after deploying the model, a Python file named "endpoint.py" was used. The key and scoring URI was provided in the script. By running the endpoint.py file with the corresponding data file in the designated folder, POST and GET requests were sent to the model's endpoint.

![dp_nb_job1](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/c6b9f740-722b-4a6a-b1cd-8b6e7f46b312)
![dp_nb_job2](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/3ec6a4b2-8e65-4c9e-94bc-924b46d663f5)
![dp_az_job1](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/8f50c535-42ba-463b-8d83-a4a59c97be98)
![dp_az_job2](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/dba027cf-81e1-4cd9-a774-3f4e536a2912)
![dp_az_job3](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/48b53517-defd-48a8-81df-30afa7f6893c)

## Screen Recordings
The two screen recordings can be found at these links  Video1 (https://youtu.be/qQ84pbH4tv4) and Video2 (https://youtu.be/xtFUksCLew4). The first screen recording demonstrates the complete project. In the second, only a small correction regarding endpoints is made.

## Suggestions

- Consider employing a different primary metric for evaluation, such as precision, recall, F1 score, or area under the receiver operating characteristic curve (AUC-ROC), to assess the performance of the deployed service.
- Use large datasets during testing to ensure that the model's performance is reliable and can handle a wide range of data samples, providing a more accurate representation of real-world scenarios.
- Take advantage of the Swagger URI of the deployed service and utilize the Swagger UI. This allows for easy interaction with the model's endpoints, making it convenient to test and validate the service's functionality and response.



## Reference
Chicco, D., & Jurman, G. (2020). Machine learning can predict survival of patients with heart failure from serum creatinine and ejection fraction alone. BMC medical informatics and decision making, 20(1), 1-16.













