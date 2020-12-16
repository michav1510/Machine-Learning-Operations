# Machine Learning Operation
In this project we are operationalizing Machine Learning tasks.

# Overview


## Architectural Diagram

In this project we have two different tasks.

In the first task:

* Register of the [bankmarketing dataset](https://automlsamplenotebookdata.blob.core.windows.net/automl-sample-notebook-data/bankmarketing_train.csv).
This dataset contains data about bank marketing campaigns based on phone calls to potential clients. The campaign has as target to convince the potential clients to make a term deposit with the bank. We seek to predict whether or not the potential client would accept to make a term deposit with the bank.

* Running AutoML and choose classification from Azure ML studio. This will run many algorithms and finds the best algorithm based on the accuracy.

* Deploying the best model. We choose the best model and deploy it, a REST endpoint will be made.

* Consuming the REST endpoint, so we send json requests to the REST endpoint to get predictions.

In the second task:

We create and publish a pipeline using the Azure ML SDK. Pipeline is a workflow of a complete machine learning task, the subtasks are incorporated in the pipeline as series of steps.

* Initialize the ```Workspace```, reload the ```Experiment``` the cluster and the ```Dataset``` from the first task.

* Setting the AutoML settings and configuration in order to incorporate an ```AutoMLStep``` in the pipeline. Setting also ```PipelineData``` for the metrics output and the best model output of the pipeline.

* Creation of the ```Pipeline``` and running.

* Retrieve the metrics(such as ```weighted_accuracy```, ```AUC_weighted```, ```average_precision_score_macro```, ```f1_score_micro```)  of all child runs and the best model.

* Publishing the pipeline so that you can rerun the pipeline via the REST endpoint.

* Making a request to the REST endpoint with a JSON payload object that has the experiment name in it.

*TODO*: Provide an architectual diagram of the project and give an introduction of each step. An architectural diagram is an image that helps visualize the flow of operations from start to finish. In this case, it has to be related to the completed project, with its various stages that are critical to the overall flow. For example, one stage for managing models could be "using Automated ML to determine the best model". 

## Future Improvements
* If we add kind of alert when the dataset changes and if it will change then the pipeline will run.

## Key Steps

About the first task:
* After the registration of the aforementioned(above)dataset we can see the registered datasets as below:

![Step2 registered datasets](/screenshots/step2_registered_datasets.png)

* After the AutoML has finished you can see the status "Completed" as below, with other useful information such as the duration and the compute target.

![Step2 experiment completed](/screenshots/step2_experiment_completed.png)

* If you select the run of the AutoML and select "Models" you can see the list of all the models in descent order of accuracy. As you can see below the best algorithm was "Voting Ensemble".
![Step2 best model](/screenshots/step2_best_model.png)

* In the deployment of the module in order to make a REST endpoint to interact with. A pretty useful thing of the endpoint is the application insigths. With the application insights you can see the "Failed Requests", "Server Response Time" and "Server Requests" and other useful things. We enabled with running the "logs.py" script. Below you see in the first image that the "Applications Insights Enabled" as "true" and to the next three images the running of the "logs.py" in the command prompt.
![Step3 application insights enabled](/screenshots/step4_applications_insights_enabled.png)
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

* After we ran the all the cells in the aml-pipelines-with-automated-machine-learning-step.ipynb, we can see below in the images the pipeline creation, 
the pipeline endpoint, the bankmarketing dataset with the AutoML module, the REST endpoint with the status of "ACTIVE", the jupyter notebook showing the "Use RunDetails Widget" which is showing the step have been done and the scheduled runs.
![Step7 pipeline creation](/screenshots/step7_pipeline_created1.png)
![Step7 pipeline endpoint](/screenshots/step7_pipeline_endpoint_completed1.png)
![Step7 bankmarketing dataset](/screenshots/step7_datasets1.png)
![Step7 bankmarketing dataset](/screenshots/step7_datasets2.png)
![Step7 restpoint status active](/screenshots/step7_published_pipeline_overview_1.png)
![Step7 restpoint status active](/screenshots/step7_published_pipeline_overview_2.png)
![Step7 restpoint status active](/screenshots/step7_published_pipeline_overview_3.png)
![Step7 restpoint status active](/screenshots/step7_published_pipeline_overview_4.png)
![Step7 restpoint status active](/screenshots/step7_published_pipeline_overview_5.png)
![Step7 jupyter notebook use rundetails](/screenshots/step7_use_run_details_1.png)
![Step7 jupyter notebook use rundetails](/screenshots/step7_use_run_details_2.png )
![Step7 scheduled run](/screenshots/unknown_step.png)
![Step7 unused](/screenshots/step7_pipeline_endpoint.png)


## Screen Recording
You can see a screencast that shows to you the working deployed model endpoint, the deployed pipeline, the AutoML model and successfull
API requests we have done: 
https://youtu.be/_Yy5srWkw7Y
