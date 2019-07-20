## Disaster Response Pipelines

![screenshot](Disaster_Response_Pipline/images/MessagesCategoriesPlot.png)

### Table of Contents

1. [Installation](#installation)
2. [Project Motivation](#motivation)
3. [Project Descriptions](#descriptions)
4. [Files Descriptions](#files)
5. [Instructions](#instructions)

## Installation <a name="installation"></a>

All libraries are available in Anaconda distribution of Python. The used libraries are:

- pandas
- numby
- sklearn
- nltk
- sqlalchemy
- pickle
- Flask
- plotly

The code should run using Python versions 3.*.

## Project Motivation<a name="motivation"></a>

The goal of the project is to classify the disaster messages into categories. 
In this project, I analyzed disaster data from [Figure Eight](https://www.figure-eight.com/) to build a model for an API that classifies disaster messages. 
Through a web app, the user can input a new message and get classification results in several categories. The web app also display visualizations of the data. 


## Project Descriptions<a name = "descriptions"></a>
The project has three componants which are:

1. **ETL Pipeline:** `process_data.py` file contain the script to create ETL pipline which:

- Loads the `messages` and `categories` datasets
- Merges the two datasets
- Cleans the data
- Stores it in a SQLite database

2. **ML Pipeline:** `train_classifier.py` file contain the script to create ML pipline which:

- Loads data from the SQLite database
- Splits the dataset into training and test sets
- Builds a text processing and machine learning pipeline
- Trains and tunes a model using GridSearchCV
- Outputs results on the test set
- Exports the final model as a pickle file

3. **Flask Web App:** the web app enables the user to enter a disaster message, and then view the categories of the message. 
As you can see from the following screeshot, *"Please help me, I am sick"* message is written in the message input and the app classifies the message into categories (related,request, aid related).
 
 ![app screenshot](images/Web app screenshot2.JPG)
 
 The web app also contains some visualizations that describe the data. 
 ![visualization1](images/Messages Categories Plot.JPG)
 ![visualization2](images/Messeges Genres Plot.JPG)
 
## Files Descriptions <a name="files"></a>

The files structure is arranged as below:

	- README.md: read me file
	- ETL Pipeline Preparation.ipynb: contains ETL pipeline preparation code
	- ML Pipeline Preparation.ipynb: contains ML pipeline preparation code
	- workspace
		- \app
			- run.py: flask file to run the app
		- \templates
			- master.html: main page of the web application 
			- go.html: result web page
		- \data
			- disaster_categories.csv: categories dataset
			- disaster_messages.csv: messages dataset
			- DisasterResponse.db: disaster response database
			- process_data.py: ETL process
		- \models
			- train_classifier.py: classification code

## Instructions <a name="instructions"></a>

To execute the app follow the instructions:
1. Run the following commands in the project's root directory to set up your database and model.

    - To run ETL pipeline that cleans data and stores in database
        `python data/process_data.py data/disaster_messages.csv data/disaster_categories.csv data/DisasterResponse.db`
    - To run ML pipeline that trains classifier and saves
        `python models/train_classifier.py data/DisasterResponse.db models/classifier.pkl`

2. Run the following command in the app's directory to run your web app.
    `python run.py`

3. Go to http://0.0.0.0:3001/

