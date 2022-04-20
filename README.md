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
4. From Build to Dockerize use Jenkins to fetch

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