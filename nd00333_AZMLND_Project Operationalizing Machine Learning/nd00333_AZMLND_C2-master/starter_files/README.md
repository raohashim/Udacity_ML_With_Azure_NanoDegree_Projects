# Operationalizing-ML-using-Microsoft-Azure
## Table of Content
- Overview
- Architecture Representation
- Dataset Registration
- AUTOML
- Deploying the best model using ACI
- Interact with Deployed Model and Consume Model Endpoints using Swagger UI
- Azure Pipeline Creation and Publishing with Python SDK in Jupyter Notebook
- Screen Cast
- Future Works
- References

## Overview
The project aims to achieve the following objectives through two different scenarios for creating and deploying ML production models, followed by consumption using Azure ML Studio and Azure Python SDK:
- AzureML Studio:
  - Create ML production models using Azure ML Studio.
  - Select the best model among the generated models.
  - Deploy the chosen model as a web service in Azure ML.
  - Consume the deployed model using Swagger UI.
- Azure Python SDK:
  - Develop ML production models using Azure Python SDK.
  - Evaluate and compare the performance of different models.
  - Choose the best model based on evaluation results.
  - Deploy the selected model as a web service using Azure Python SDK.
  - Consume the deployed model using Azure Python SDK.

By exploring both scenarios, the project covers the process of model creation, deployment, and consumption using both Azure ML Studio with Swagger UI and Azure Python SDK, providing flexibility in choosing the preferred approach.

## Architectural Diagram
The  architecture diagram showing the flow of the whole project is shown below:
![architecturediagram](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/257e4aa3-55fb-4cff-8426-af0d1f9b039e)

## Dataset Registration
The project utilizes a marketing dataset of a banking institution derived from direct marketing campaigns conducted via phone calls. The objective of the classification task in this project is to predict whether a client will subscribe to a bank term deposit. The dataset has been successfully uploaded to Azure ML Studio, as depicted in the accompanying screenshot. 
![Data](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/bddded58-dfda-446f-aeab-666907ad6d86)

## AUTOML
### Completion of AUTOML Run
After registering the dataset, the subsequent step involved creating a compute cluster and running the AutoML experiment. The experiment's completion status is illustrated below in the provided screenshot.
![AOTOML COMPLETE](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/83ff5922-074d-48c1-8a64-07ecf6724051)
![AOTOML COMPLETE up](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/230d195d-ba4c-4e66-9ef7-80b2433a95fd)
### Selection of Best Model
The best model obtained was the VotingEnsemble model, which achieved an accuracy of 0.9144158.
![best_model](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/c168b5d8-d7f9-4752-8ce7-bfb4d1ce3050)
### Best Model Deployment
The best model obtained, the VotingEnsemble model, has been deployed as a web service using Azure Container Instances (ACI). Additionally, key-based authentication has been enabled to secure access to the deployed model. This ensures that only authorized services can interact with the endpoints provided by the deployed model, maintaining data privacy and security.
![best_model_deploy](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/a53ce91b-0c2f-45fa-b598-7f802b547426)
### Enabling logging and Application Insights
After deploying the best model, it is possible to enable Application Insights to gather logs and monitor the deployed service. In this project, the logs.py script was utilized to enable Application Insights. By enabling Application Insights, we gain visibility into the performance, usage, and other metrics related to the deployed model, allowing you to analyze and monitor its behaviour.

![appinsight](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/d320292d-7693-4097-bdf2-04ab41f4fff2)

### Consuming Model Endpoints using Swagger UI
Azure provides a Swagger JSON URL that can be utilized to generate a web page documenting the HTTP endpoint of a deployed model. In this project, the Swagger UI was used to consume the deployed model, and the API contents for the model were displayed. This allows for easy exploration and understanding of the available endpoints, request/response formats, and other relevant details of the model's API. The screenshot below illustrates the Swagger UI displaying the API documentation for the consumed deployed model.
![swagger](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/940cb903-8c8c-44c7-8415-c3421b81f4fc)

### Interact with Model Endpoints 
Once the model is successfully deployed, the Python script endpoint.py can be utilized to interact with the trained model and obtain output predictions. This script acts as a client that communicates with the deployed model's endpoint, sending input data and receiving the corresponding predictions as output.
![consumeoutput_AUTOML](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/94433644-ce58-4ba5-acb8-2ed24f9da1cf)

## Key Steps
*TODO*: Write a short discription of the key steps. Remeber to include all the screenshots required to demonstrate key steps. 

## Screen Recording
*TODO* Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:

## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.


## Key Steps
*TODO*: Write a short discription of the key steps. Remeber to include all the screencasts required to demonstrate key steps. 

*TODO* Remeber to provide screenshots of the `RunDetails` widget as well as a screenshot of the best model trained with it's parameters.

## Screen Recording
*TODO* Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:

## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
