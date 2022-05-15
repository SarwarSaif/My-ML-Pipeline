# My-ML-Pipeline
This Repo will consists of a simple End-to-End modern pipeline

## Overview
This ML System
- can handle many API endpoints,
- each API endpoint can have several ML algorithms with different versions,
- ML code and artifacts (files with ML parameters) are stored in the code repository (git),
- supports fast deployments and continuous integration (tests for both: server and ML code),
- supports monitoring and algorithm diagnostic (support A/B tests),
- is scalable (deployed with containers),
has a user interface.

## To-Do:
1. **Deploy Machine Learning Models with Django**
2. Create a Dashboard with Plotly [https://plotly.com/dash/](https://plotly.com/dash/)
3. Dockerize the whole model 
4. From Build to Dockerize use Jenkins CI/CD Pipeline

## PC Setup
| Name | Version|
|---|---|
| OS | macOS Big Sur 11.3.1 |
| Processor | 2.4 GHz 8-Core Intel Core i9 |
| memory | 32 GB 2667 MHz DDR4 |
| Grahics | AMD Radeon Pro 5300M 4 GB |

## Setup Environment
| Name | Version|
|---|---|
| git flow | 0.4.1 |
| python | 3.8.9 | 
| Django | 3.2 (Django 3.2 supports python 3.6, 3.7, 3.8, 3.9, 3.10 )|
| Numpy | 1.22.3 |
| pandas | 1.4.2 |
| sklearn | 0.0 |
| joblib | 1.1.0 |


### Clone Repo
```
git clone https://github.com/SarwarSaif/My-ML-Pipeline.git
```

### Create a Virtual Env under the Project Folder
```
cd projectfolder # go to project folder
python3 -m venv ./venv
source venv/bin/activate # activate the environment
```
### Install Django
```
pip3 install django==3.2
```

## Start Django Project
```
mkdir django-backend
cd django-backend
django-admin startproject server
```
You can run your initiated server with the following command:
```
cd server
python3 manage.py runserver
```
**Issue that you might face: You have 18 unapplied migration(s). Your project may not work properly until you apply the migrations for app(s): admin, auth, contenttypes, sessions.
Run 'python3 manage.py migrate' to apply them.**

```
python3 manage.py migrate
python3 manage.py runserver
```

## Build ML algorithms

### Setup Jupyter Notebook
Go back to the project directory
```
# run commands in your project directory
pip3 install jupyter notebook
```
To set Jupyter to use local virtualenv environment run:
```
ipython kernel install --user --name=venv
```
**Installed kernelspec venv in /Users/user_name/Library/Jupyter/kernels/venv**

Create a notebooks directory to put Jupiter files. To start Jupyter notebook run:
```
# create a research directory
mkdir notebooks
cd notebooks
# start Jupyter
jupyter notebook
```

When starting a new notebook make sure that you select the correct kernel, venv in our case

### Train ML Algorithms
Before building ML algorithms we need to install packages:
```
pip3 install numpy pandas sklearn joblib
```
Create a notebook named train_income_classifier.
Data set [https://github.com/pplonski/datasets-for-start].
The ML will be used to predict whether income exceeds $50K/year based on census data.

Then do the following steps:
1. Load Data and Split into Test and Training set
2. Data Preprocessing
   1. fill missing values with average
   2. convert categorical variables
3. Train Algorithms
4. Add ML code and aritifacts to the repository

## Django Models
### Create Django Models
1. Create a new app.
```
# run this in django-backend/server directory
python manage.py startapp endpoints
mkdir apps
mv endpoints/ apps/
```
2. Let’s go to apps/endpoints/models.py file and define database models (Django provides object-relational mapping layer (ORM)).

    We defined three models:
    - Endpoint - to keep information about our endpoints,
    - MLAlgorithm - to keep information about ML algorithms used in the service,
    - MLAlgorithmStatus - to keep information about ML algorithm statuses. The status can change in time, for example, we can set testing as initial status and then after testing period switch to production state.
    - MLRequest - to keep information about all requests to ML algorithms. It will be needed to monitor ML algorithms and run A/B tests.
3. Add our app to INSTALLED_APPS in backend/server/server/settings.py, it should look like:
```
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    # apps
    'apps.endpoints'
]
```

#### Credit:
( https://www.deploymachinelearning.com/ )[ Deploy Machine Learning Models with Django]
(https://github.com/pplonski/my_ml_service) [ Repo Link ]