*NOTE:* This file is a template that you can use to create the README for your project. The *TODO* comments below will highlight the information you should be sure to include.


# Your Project Title Here
In this project we are operationalizing Machine Learning tasks and consume them from a REST endpoint.

## Architectural Diagram
The steps below describe the whole procedure from the dataset registration to the REST endpoint consuming.

*Dataset registration, we used the csv from https://automlsamplenotebookdata.blob.core.windows.net/automl-sample-notebook-data/bankmarketing_train.csv

*AutoML using classification. We are trying to predict the label if it is equal to 0 or 1. So it's a classification problem.

*Deploy the best model. The best algorithm is the Voting Ensemble.

*Consume the best model.

*Create, publish and consume a pipeline.

*TODO*: Provide an architectual diagram of the project and give an introduction of each step. An architectural diagram is an image that helps visualize the flow of operations from start to finish. In this case, it has to be related to the completed project, with its various stages that are critical to the overall flow. For example, one stage for managing models could be "using Automated ML to determine the best model". 

## Key Steps

* Dataset registration. You can see below two datasets but they are identical, with different names. The one was ready from the loading of the Lab and the other one
I register it manually.

![Step2 registered datasets](/screenshots/step2_registered_datasets.png)
Format: ![Alt Text](url)

* After the AutoML finished(first image below), you can see the best model(second image below).

![Step2 experiment completed](/screenshots/step2_experiment_completed.png)
Format: ![Alt Text](url)

![Step2 best model](/screenshots/step2_best_model.png)
Format: ![Alt Text](url)

## Screen Recording
*TODO* Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:

## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
