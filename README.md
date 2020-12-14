# Operationalizing Machine Learning

In this project we will use the Microsoft Azure to configure cloud-based machine learning production model. We will use the Bank Marketing Dataset, then we will deploy it and consume it. Also, we will create, publish and consume the pipeline. This revolves around the best use of cloud based resources. We will perform the following steps after entering the workspace:
* Authentication
* Automated ML Experiment
* Deploy the best model
* Enable logging
* Swagger Documentation
* Consume model endpoints
* Create and publish a pipeline

![Architectural Diagram of the Project](https://user-images.githubusercontent.com/61888364/102027946-7d9d8f80-3dcd-11eb-9907-f68c64b5899a.png)

## Authentication
It is the vital step to ensure secure and authentic access. Authentication is required for the creation of the Service Principal account and associate it with specific workspace.

## Automated ML Experiment
We create the new Automated ML Run Experiment and then upload the Bank Marketing dataset. We run the experiment configuring a new compute cluster, using Classification and ensure that the best model explaination is enabled.

## Deploy the Best Model
After the completion of the AutoML Run, we will get our best model. We will then deploy that model using the **Azure Container Instance(ACI)** and enable **Authentication** to prevent unauthorized access.

## Enable Logging
After the deployment, we will enable the Application Insights from the deployed model. This will help us produce logging output with the python sdk. It plays a vital role to debug problems in production environments.

## Swagger Documentation
Swagger helps us build, document and consume RESTful web services. It also explains what type of requests API can consume like **POST** and **GET**.

## Consume Model Endpoints
We must consume the deployed service to retrieve the data using **HTTP request**. It will help us in validation of data by identifying if anything is having any problem or is incorrect.

## Create and Publish Pipelines
The last and the most vital step is to make the model publically available. This is done by creating a pipeline and then publishing it. It is synonymous to Automation as the pipeline create ways for other services to interact with it using HTTP endpoint.

## Future Improvements
* We can try to implement various new algorithms along with running the AutoML Experiment for a longer time period. 
* We can try new values for number of nodes, concurrency etc. 
* We can use GPU's instead of CPU's to improve the performance. Since CPU's might reduce the costs but in terms of performance and accuracy GPU's outperform CPU's.
* There was some imbalance detected in the Bank Marketing Dataset. We can eliminate it to get better accuracy and results by resampling the training dataset etc.
* We can enable Deep Learning as well in the Auto ML Experiment for better results as it will consider different patterns and algorithms. Hence, improving the accuracy.

# Demonstration of Key Steps :
## Automated ML Experiment

#### Below is the screenshot of the "Registered Datasets" in the ML Studio showing Bank Marketing Dataset available.





