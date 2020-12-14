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
we register it manually:

![Step2 registered datasets](/screenshots/step2_registered_datasets.png)

* After the AutoML finished(first image below), you can see the best model(second image below):

![Step2 experiment completed](/screenshots/step2_experiment_completed.png)

![Step2 best model](/screenshots/step2_best_model.png)

* After we deployed the best model, we enabled the application insights: 
![Step3 application insights enabled](/screenshots/step4_applications_insights_enabled.png)

* We ran the logs.py, and we show below the output: 
![Step4 logs.py script](/screenshots/step4_logs_script_part3.png)
![Step4 logs.py script](/screenshots/step4_logs_script_part2.png)
![Step4 logs.py script](/screenshots/step4_logs_script_part1.png)

* Making the swagger to run on localhost, showing the HTTP API methods and responses: 
![Step5 methods and responses](/screenshots/step5_methods_and_responses.png)
![Step5 methods and responses](/screenshots/step5_methods_and_responses2.png)
![Step5 methods and responses](/screenshots/step5_methods_and_responses3.png)
![Step5 methods and responses](/screenshots/step5_methods_and_responses4.png)
![Step5 methods and responses](/screenshots/step5_methods_and_responses5.png)
![Step5 methods and responses](/screenshots/step5_methods_and_responses6.png)

* Consuming the the REST endpoint via the url : 
We have senth two jsons requests and we get two responses "yes" and "no" as it is depicted in the below image.
![Step6 consume model endpoints](/screenshots/step6_json_result.png)

* In order to load-test our model we have run the benchmark.sh. We run it in git bash and write "bash benchmark.sh"
![Step6 benchmark](/screenshots/step6(optional)benchmark1.png)
![Step6 benchmark](/screenshots/step6(optional)benchmark2.png)
![Step6 benchmark](/screenshots/step6(optional)benchmark3.png)
![Step6 benchmark](/screenshots/step6(optional)benchmark4.png)
![Step6 benchmark](/screenshots/step6(optional)benchmark5.png)
As you can see in the last image you see some gathered data about the requests have been done with the benchmark.

* After we ran the 


## Screen Recording
*TODO* Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:

## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
