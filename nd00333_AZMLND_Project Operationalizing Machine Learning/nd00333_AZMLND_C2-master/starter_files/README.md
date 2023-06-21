# Operationalizing-ML-using-Microsoft-Azure
## Table of Content
- Overview
- Architecture Representation
- Dataset Registration
- AUTOML Experiment
  - Completion of AUTOML Run
  - Selection of Best Model
  - Best Model Deployment
  - Enabling logging and Application Insights
  - Consuming Model Endpoints using Swagger UI
  - Interact with Model Endpoints
- Create and Publish a pipeline using Azure Python SDK using Jupyter Notebook
  - Create Pipeline and AutoMLStep
  - Pipeline Run
  - Run Widget
  - PipelineRun Execution Summary
  - Examine Results
  - Best Model Retrive
  - Test Best Model
- Screen Recording
- Standout Suggestions


### Rest Endpoint

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

## AUTOML Experiment

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

## Create and Publish a pipeline using Azure Python SDK using Jupyter Notebook
In the second part of the project, the Jupyter Notebook aml-pipelines-with-automated-machine-learning-step.ipynb was utilized. This notebook has been updated to include the same dataset, keys, URI, cluster, and model names that were created in the first part using AutoML.

The objective of this step was to create, publish, and consume a pipeline using the Azure Python SDK. The relevant screenshots below demonstrate the progress and outcomes of this step, showcasing the successful creation and execution of the pipeline. The screenshots provide an overview of the pipeline's structure, including the different steps involved, as well as the pipeline run logs and results obtained during the execution.
### Create Pipeline and AutoMLStep

![automlstep](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/0619a1d3-8e31-46bd-ab45-7f444196adbc)

### Pipeline Run
The execution of the pipeline from Jupyter Notebook
![PipelineRun1](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/60c6b266-8066-4abc-bac8-15efff634c0f)

The submitted pipeline is on the AZURE ML portal.
![PipelineRun2](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/649f1df2-bd0e-4eb2-bfb0-d8b302feab15)

### Run Widget
![widget](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/c826ac4b-4bc8-414e-bfcc-6715be9214e3)
![widget1](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/4646bb36-b3e6-493b-b4e6-52825c582a78)

### PipelineRun Execution Summary
![run complete](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/80141a81-3828-447b-bff0-4f7163f994f5)

### Examine Results
![results_examin](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/25b682ef-6240-41fb-9262-e7f5dd904501)

### Best Model Retrive
![best_model](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/1598328b-2e89-4360-8de8-2512222e58f7)

### Test Best Model
![test_best_model](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/85bb7b6e-8edd-41df-b19b-2be2c296dd8f)

### Rest Endpoint
![Rest_API](https://github.com/raohashim/Udacity_ML_With_Azure_NanoDegree_Projects/assets/50891264/2332994c-9835-4ae3-9436-bc772c121af6)


These screenshots collectively depict the process of creating, publishing and consuming the pipeline using the Azure Python SDK within the Jupyter Notebook environment.

## Screen Recording
There are two screen recordings showcasing the project in action. Two video files are uploaded !(first one)[https://drive.google.com/file/d/1Pljy-lahRfYybU3IVOZC3iTnC1Gbt1hw/view?usp=sharing] is for the AutoML part, and the second is for Azure Python SDK.

## Standout Suggestions
In future developments, it would be beneficial to expand testing methodologies for local container and downloaded models, optimize the parallel run step in the pipeline by fine-tuning resource allocation and workload distribution, enhance pipeline automation with version control, and explore advanced performance measurement techniques beyond the Apache Benchmark tool. These efforts will contribute to improved functionality, efficiency, and scalability of the solution.
