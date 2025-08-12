# Amazon-Fraud-detection-using-Azure
Azure Real-Time Fraud Detection
Overview
This project demonstrates a real-time fraud detection system built using multiple Azure services. It leverages machine learning, event streaming, and serverless functions to detect fraudulent financial transactions as they occur. The system integrates data ingestion, processing, scoring, and storage pipelines, enabling end-to-end monitoring and prevention of fraudulent activities.


Key Features
Real-time data ingestion using Azure Event Hubs

Machine Learning model trained and deployed with Azure Machine Learning

Fraud detection triggers implemented with Azure Functions

Data streaming and analytics using Azure Stream Analytics

Data storage with Azure Cosmos DB and Azure Synapse Analytics

Event simulation via Python-based Event Generator

Infrastructure as Code using ARM templates

Architecture Components
Event Generator

Simulates real-time transactions

Sends events to Azure Event Hub

Azure Stream Analytics

Processes incoming events

Routes data to Cosmos DB, Synapse, or ML endpoint

Azure Machine Learning

Prepares training data

Trains, registers, and deploys fraud detection models

Azure Functions

Implements triggers for fraud detection logic

Integrates Benford's Law and Fraud Ring detection

Data Storage

Cosmos DB (NoSQL) for event data

Synapse Analytics for large-scale queries and analysis

ARM Templates

Deploy Azure resources in a reproducible way

Prerequisites
Azure Subscription

Python 3.8+

Azure CLI installed

VS Code (optional, for local development)

Required Azure services:

Azure Event Hub

Azure Stream Analytics

Azure Cosmos DB

Azure Machine Learning Workspace

Azure Functions

Setup Instructions
1. Clone the Repository
bash
Copy
Edit
git clone https://github.com/yourusername/azure-realtime-fraud-detection.git
cd azure-realtime-fraud-detection
2. Install Dependencies
bash
Copy
Edit
pip install -r requirements.txt
3. Configure Environment
Update config.py.example and rename to config.py

Set your Azure credentials, connection strings, and endpoint URLs

4. Deploy Azure Resources
bash
Copy
Edit
az deployment group create --resource-group <your-rg> \
  --template-file arm_template/template.json \
  --parameters @arm_template/parameters.json
Running the System
1. Start Event Generator
bash
Copy
Edit
python EventGenerator/event_generator.py
2. Stream Analytics Job
Configure inputs (Event Hub) and outputs (Cosmos DB, Synapse)

Deploy the query from StreamAnalytics/query.sql

3. Deploy Machine Learning Model
Follow notebooks in AzureMachineLearning/Notebooks/:

Data Preparation

Train Model

Deploy

4. Azure Functions
Deploy triggers in Functions/ to your Function App

Includes:

BenfordTrigger

FraudRingGremlinTrigger

Score

Testing
Use Event Generator to simulate fraud and normal transactions

Monitor Stream Analytics output in Azure Portal

Check Cosmos DB for stored events

Validate ML model scoring via Function App endpoint
