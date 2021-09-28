# CI/CD Pipeline for Machine Learning Application hosted on Microsoft Azure
CI/CD Pipeline for Demo Python Machine Learning App

This Demo Repo is set up as a CI/CD Pipeline for a Microsoft Azure Cloud Environment - The App is a Python Based Machine Learning Prediction Model 

## To Run this Repo Properly

1. Create the Cloud-Based Development Environment
It is time to set up an initial project structure in the Azure Cloud Shell environment. First, you'll create a Github repository. Next, you'll launch an Azure Cloud Shell environment and integrate Github repository communication.

2. Create Project Scaffolding
Now that your environment is set up, you can create the scaffolding for your project and test your code.

Create the Makefile
Inside your GitHub repo, your next step will be to create a file named Makefile and copy the code below into it (remember this needs to use tab formatting). Remember that a Makefile is a handy way to create shortcuts to build, test, and deploy a project.

'install:
    pip install --upgrade pip &&\
        pip install -r requirements.txt

test:
   python -m pytest -vv test_hello.py


lint:
    pylint --disable=R,C hello.py

all: install lint test'

Create requirements.txt
Inside your GitHub repo, your next step will be to create a file named requirements.txt. It should include the following items below. Remember that a requirements.txt is a convenient way to list what packages a project needs. Another optional best practice would be to "pin" the exact version of the package you use.

Create the Python Virtual Environment
Inside your Azure Cloud Shell environment create a Python virtual environment. Remember that by creating the virtual environment in a home directory it won't accidentally be checked into your project.
Create the script file and test file.
The next step is to create the script file and test file. This is a boilerplate code to get the initial continuous integration process working. It will later be replaced by the real application code.
First, you will need to create hello.py with the following code at the top level of your Github repo:

Next, you will need to createtest_hello.py with the following code at the top level of your Github repo:

3. Local Test
Now it is time to run make all which will install, lint, and test code. This enables us to ensure we don't check in broken code to GitHub as it installs, lints, and tests the code in one command. Later we will have a remote build server perform the same step.

## CI: Configure GitHub Actions
You will configure GitHub Actions to test your project upon change events in GitHub. This is a necessary step to perform Continuous Integration remotely. When you check in your code to a git based repository and you want it to be tested, there will need to be both a SaaS build service and configuration files that tell the build server what to do. This is the definition of Continuous Integration.
Configuring a SaaS build server like GitHub Actions is an essential step for any software project that wants to apply DevOps best practices. This completes the final section of Continous Integration and enables us to then move on to the later step of Continuous Delivery once this is complete.

1. Enable Github Actions
Go to your Github Account and enable Github Actions.

2. Replace yml code
Replace the pythonapp.yml code with the following scaffolding code.

3. Verify Remote Tests pass
Push the changes to GitHub and verify that both lint and test steps pass in your project.

![Image of Screenshot](https://github.com/dewitt4/CICD_MachineLearning_App/blob/5b9b8e60c38757c26ba263b3cb000f2de625b0b9/github_workflows_success.png)

## Continuous Delivery on Azure
You are ready for the final step. It's time to set up Continuous Delivery using Azure technologies. This will involve setting up Azure Pipelines to deploy the Flask starter code to Azure App Services. If you get stuck on any of these steps, make sure to check out the references at the bottom of this page for ideas on how to get unblocked.

## Making predictions
To make a prediction, you have to open a separate tab or terminal window. In this new window, navigate to the main project directory (some computers will do this automatically) and call ./make_prediction.sh if testing locally, or modify make_predict_azure_app.sh.
This shell script is responsible for sending some input data to your application via the appropriate port. Each numerical value in here represents some feature that is important for determining the price of a house in Boston. The source code is responsible for passing that data through a trained, machine learning model, and giving back a predicted value for the house price.
In the prediction window, you should see the value of the prediction, and in your main window, where it indicates that your application is running, you should see some log statements print out. You’ll see that it prints out the input payload at multiple steps: when it is JSON and when it’s been converted to a DataFrame and about to be scaled.
Logs
You can inspect the logs from your running application here:

https://your-app-name.scm.azurewebsites.net/api/logs/docker (replace your-app-name with the actual name of the app)

Or stream them using the azure command line:
az webapp log tail

## Helpful resources from Microsoft
These are all excellent official documentation examples from Microsoft that explain key components of Python-based Continuous Delivery on Azure:
1. Azure Quickstart https://docs.microsoft.com/azure/app-service/containers/quickstart-python
2. Use CI/CD to deploy a Python web app to Azure App Service on Linux https://docs.microsoft.com/azure/devops/pipelines/ecosystems/python-webapp
3. Create a CI/CD pipeline for Python with Azure DevOps Starter https://docs.microsoft.com/azure/devops-project/azure-devops-project-python
4. Continuous deployment to Azure App Service https://docs.microsoft.com/azure/app-service/deploy-continuous-deployment#option-1-use-app-service-kudu-build-server
5. Flask on Azure App Services https://docs.microsoft.com/azure/app-service/containers/quickstart-python
6. Azure Pipelines for Python https://docs.microsoft.com/azure/devops/pipelines/ecosystems/python

## Trello Board
I have created a public Trello Board for this project tracking. It can be viewed here at: https://trello.com/b/QSecLHuM/cicd-machine-learning-app
