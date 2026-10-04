# AI Programming Foundations Project

## Project description
This project is about building a reproducible data workflow using the COIL 2000 dataset. In this notebook I load, clean, explore and visualize the data to find out which customer characteristics are linked to having a caravan insurance policy. I check for biases and limitations and reflect on the findings.

## What I built
I made a Jupyter notebook that loads the data, has two cleaning functions, an EDA function, three charts and a summary.

## Dataset
- Name: COIL 2000 dataset
- Source: https://archive.ics.uci.edu/dataset/125/insurance+company+benchmark+coil+2000
- Files: ticdata2000.txt and dictionary.txt

The dataset contains real customer data from a Dutch insurance company, it has 5,822 customers and 86 columns.

## How to run

### 1. Install dependencies
- Create a fresh environment with python 3.12 ```conda create -n aipf python=3.12```
- Activate the environment ```conda activate aipf```
- ```pip install -r requirements.txt```

### 2. Run the notebook
- Open data_workflow.ipynb and use Run all
- I have used Python 3.12
- The command to regenerate the file is: ```pip freeze > requirements.txt```

## Reflections

### Bias and data cleaning
One of the choices made was not to remove duplicates, because dropping them would remove real customers. Identical rows come mostly from customers in the same neighbourhoods with the same products. Dropping them would reduce some customer types more than others, this would skew the percentages and would create bias as a result of the cleaning. The small groups of customers in the dataset give misleading percentages. The area data gives an average and says nothing about the individual person.

### Moving to machine learning
With caravan_policy as the target I would need to make a train and test data set. The dataset only contains 6% of customers with a caravan policy, this creates an imbalance in training the data. A model that always predicts "no caravan policy" is already 94% accurate, so accuracy of the model would be misleading. To be able to train on the data I would turn all the text labels into numbers.

### Preparing for a neural network
To be able to train a neural network I would need to have all inputs as numbers on a similar scale. I would use one-hot encoding for categories without an order, like customer main type and keep the numbers for categories with an order like age band or purchasing power class, scaled to a similar range.

### Agentic automation
An agent could be made to load the data, another one to check the quality of the data based on constraints and one agent to produce the caravan rate tables. It's important to keep a human in the loop for decisions like keeping duplicates, an agent could flag them and a person would decide.