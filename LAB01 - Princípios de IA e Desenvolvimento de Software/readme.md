Creating a regression model with Azure AutoML to predict the chances of a heart attack based on patient data.

---

# Predicting Heart Attack Chances with Azure AutoML

This guide will walk you through creating a regression model using Azure's Auto Machine Learning (AutoML) service with a dataset related to heart attack chances.

## Step 1: Setting Up Your Azure Environment

Before you start, ensure you have an Azure account and access to the Azure Machine Learning Studio.

1. **Log in** to the [Azure Portal](https://portal.azure.com).
2. **Create** a new resource for Azure Machine Learning by searching for **Machine Learning** in the marketplace.
3. **Select** the Machine Learning service and **set up** a new workspace if you don't already have one.

## Step 2: Preparing Your Dataset

1. **Download** the heart attack chances dataset from [Kaggle](https://www.kaggle.com/datasets/rashikrahmanpritom/heart-attack-analysis-prediction-dataset/data).
2. **Clean and prepare** your dataset. Ensure it's in a CSV format with clear, named columns for all features and your target variable (`1` for high chance and `0` for low chance of a heart attack).

## Step 3: Uploading Your Dataset to Azure

1. Go to your **Azure Machine Learning Studio** workspace.
2. Navigate to **Datasets** > **+ Create dataset** > **From local files**.
3. **Select** your dataset `HeartAttackChances` and **upload** your prepared CSV file.
4. Follow the prompts to **configure the dataset**, ensuring the column types are correctly identified.

## Step 4: Creating a New Automated ML Run

1. In Azure Machine Learning Studio, navigate to **Automated ML** under the **Author** section.
2. Click on **+ New automated ML run**.
3. **Select** your `HeartAttackChances` dataset.
4. Choose your **target column**, which is the column in your dataset indicating the chance of a heart attack.

## Step 5: Configuring Your AutoML Run

1. For **task type**, select **Regression** since you're predicting a numerical value (chance of heart attack).
2. **Configure** your compute cluster or create a new one if necessary. This is where your model will be trained.
3. **Select additional settings** as needed, such as exit criteria and concurrency.
4. Click **Save** to proceed.

## Step 6: Review and Run

1. Review your configuration settings.
2. Click **Run** to start the AutoML process. This will automatically try different models and preprocessing techniques to find the best performing model based on your data.

## Step 7: Evaluating the Model

1. Once the run is complete, **review the performance metrics** of the best model provided by AutoML.
2. You can further **analyze** the model's details, such as precision, recall, and AUC for understanding its predictive performance.

## Step 8: Test the Output
1. On the model Endpoint you can input some data to evaluate the output,
here's a inpute example:

```json
{
  "Inputs":{
    "data": [{
      "age": 90,
      "sex":0,
      "cp":2,
      "trtbps":100,
      "chol":394,
      "fbs":1,
      "restecg":1,
      "thalachh":111,
      "exng":0,
      "oldpeak":1.3,
      "slp":2,
      "caa":1,
      "thall":2
    }]
  },
  "GlobalParameters":0.0
}
```

Here's the output example:
```json
{
    "Results":[1]
}
```
Note that output `1` means a High Rate of Heart Attack.