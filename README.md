# Overview
This project is the second project of the Udacity's "Machine Learning Engineer with Microsoft Azure" Nanodegree.
It consists of two parts:

* In the first part we use AutoML in our [bankmarketing dataset](https://automlsamplenotebookdata.blob.core.windows.net/automl-sample-notebook-data/bankmarketing_train.csv), find the best model and deploy it via a REST API. We also use the Swagger in order to see the documentation of the API that we deployed.

* In the second part we create and publish a pipeline using the Azure ML SDK, while we use the same dataset.

Feel free to read below more details about each task.

## Architectural Diagram
One image corresponds to many words, so below you see the architectural diagram of the operations in this project

![Step4 logs.py script](/screenshots/Architectural_Diagram.png)

### Deploy Model in Azure ML Studio:

* Register of the [bankmarketing dataset](https://automlsamplenotebookdata.blob.core.windows.net/automl-sample-notebook-data/bankmarketing_train.csv).
This dataset contains data about bank marketing campaigns based on phone calls to potential clients. The campaign has as target to convince the potential clients to make a term deposit with the bank. We seek to predict whether or not the potential client would accept to make a term deposit with the bank.

* Running AutoML and choose classification from Azure ML studio. This will run many algorithms and finds the best algorithm based on the accuracy.

* Deploying the best model. We choose the best model and deploy it, a REST endpoint will be made.

* Enable the application insights, producing Swagger documentation and benchmarking the REST endpoint.

* Consuming the REST endpoint, so we send json requests to the REST endpoint to get predictions.

### Publish ML Pipeline:

We create and publish a pipeline using the Azure ML SDK. Pipeline is a workflow of a complete machine learning task, the subtasks are incorporated in the pipeline as series of steps.

* Initialize the ```Workspace```, reload the ```Experiment``` the cluster and the ```Dataset``` from the first task.

* Setting the AutoML settings and configuration in order to incorporate an ```AutoMLStep``` in the pipeline. Setting also ```PipelineData``` for the metrics output and the best model output of the pipeline.

* Creation of the ```Pipeline``` and running.

* Retrieve the metrics(such as ```weighted_accuracy```, ```AUC_weighted```, ```average_precision_score_macro```, ```f1_score_micro```)  of all child runs and the best model.

* Publishing the pipeline so that you can rerun the pipeline via the REST endpoint.

* Making a request to the REST endpoint with a JSON payload object that has the experiment name in it.

## Future Improvements

* We could add an alert when the dataset changes so that we could be notified and done it in an automated way and/or running a script in an automated way.

* Increase the time of training in order to have more accurate predictions.

## Key Steps

### Deploy Model in Azure ML Studio:

* After the registration of the aforementioned(above)dataset we can see the registered datasets as below:

![Step2 registered datasets](/screenshots/step2_registered_datasets.png)

* After the AutoML has finished you can see the status "Completed" as below, with other useful information such as the duration and the compute target.

![Step2 experiment completed](/screenshots/step2_experiment_completed.png)

* If you select the run of the AutoML and select "Models" you can see the list of all the models in descent order of accuracy. As you can see below the best algorithm was "Voting Ensemble".

![Step2 best model](/screenshots/step2_best_model.png)

* After the deployment of the model in order to make a REST endpoint to interact with. A pretty useful thing of the endpoint is the application insigths. With the application insights you can see the "Failed Requests", "Server Response Time" and "Server Requests" and other useful things. We enabled with running the "logs.py" script. Below you see in the first image that the "Applications Insights Enabled" as "true" and to the next three images the running of the "logs.py" in the command prompt.

![Step3 application insights enabled](/screenshots/step4_applications_insights_enabled.png)
![Step4 logs.py script](/screenshots/step4_logs_script_part3.png)
![Step4 logs.py script](/screenshots/step4_logs_script_part2.png)
![Step4 logs.py script](/screenshots/step4_logs_script_part1.png)

* If we hit the "Swagger URI" in the deployed model(you can see it in the first of the previous 4 images) we can download the swagger.json. If we place it in the "swagger" folder and run the "bash swagger.sh"(choosing the right port in the file) and the "serve.py"(choosing the right port in the file) and open the localhost as the below images showing, you can see all the HTTP API methods and responses.

![Step5 methods and responses](/screenshots/step5_methods_and_responses.png)
![Step5 methods and responses](/screenshots/step5_methods_and_responses2.png)
![Step5 methods and responses](/screenshots/step5_methods_and_responses3.png)
![Step5 methods and responses](/screenshots/step5_methods_and_responses4.png)
![Step5 methods and responses](/screenshots/step5_methods_and_responses5.png)
![Step5 methods and responses](/screenshots/step5_methods_and_responses6.png)

* The most useful thing about deploying a REST endpoint is to consuming it i.e to send HTTP requests with a json and to take responses. In our case the json has as values the x's of which the y's want to be predicted from the model. So we replace in the "endpoint.py" the "scoring_uri" and the "key" with the values that are visible to the endpoint in the ML studio. Then we run the "endpoint.py" and get the result as the below image depict, the response was "yes" and "no" for the first and second json respectively.

![Step6 consume model endpoints](/screenshots/step6_json_result.png)

* In order to load-test our model we have run the benchmark.sh. Some requests are proceed to the endpoint and useful metrics about the total time of requests, the total requests, how many requests have been failed and other metrics as the results show below. 

![Step6 benchmark](/screenshots/step6(optional)benchmark1.png)
![Step6 benchmark](/screenshots/step6(optional)benchmark2.png)
![Step6 benchmark](/screenshots/step6(optional)benchmark3.png)
![Step6 benchmark](/screenshots/step6(optional)benchmark4.png)
![Step6 benchmark](/screenshots/step6(optional)benchmark5.png)

As you can see in the last image you see some gathered data about the requests have been done with the benchmark.

### Publish ML Pipeline:

* Creation of the pipeline from the Azure SDK using the "aml-pipelines-with-automated-machine-learning-step.ipynb" notebook depicted below.

![Step7 pipeline creation](/screenshots/step7_pipeline_created1.png)

* Below we see in turn the pipeline endpoint completion, the bank marketin dataset(2 images), published pipeline overview(5 images due to small screen size).

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
https://youtu.be/-XwdFxlc-lQ
