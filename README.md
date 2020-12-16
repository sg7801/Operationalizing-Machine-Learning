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
## Step 1: Authentication
If we are using our personal account then we need to install the Azure Machine Learning Extension which allows you to interact with Azure Machine Learning Studio. Its a part of the az command. Then we will have to create a Service Principal Account and associate it with specific workspace.

## Step 2: Automated ML Experiment
In this step, you will create an experiment using Automated ML, configure a compute cluster, and use that cluster to run the experiment.

#### Firstly, we upload the dataset. Below is image of the "Registered Datasets" in the ML Studio showing Bank Marketing Dataset available.

![2](https://user-images.githubusercontent.com/61888364/102204326-bd5c9800-3eef-11eb-847d-afc541507e8c.png)
#### Then, we perform the AutoML Run (using Classification) with Explaination Enabled.

![1](https://user-images.githubusercontent.com/61888364/102203716-ef212f00-3eee-11eb-96ba-d102441f6437.png)
#### The run has completed and we get Voting Ensemble as the best performing model of accuracy 0.91988 

![3](https://user-images.githubusercontent.com/61888364/102204429-dfeeb100-3eef-11eb-8dc0-7b0baee1ec56.png)
#### After the experiment run completes, a summary of all the models and their metrics are shown, including explanations. Below images show the explaination of the best performing model.

![8](https://user-images.githubusercontent.com/61888364/102205498-46280380-3ef1-11eb-8e93-a6d0e75f4402.png)

![9](https://user-images.githubusercontent.com/61888364/102205527-4fb16b80-3ef1-11eb-81da-9041fde4e72a.png)

## Step 3: Deploy the Best Model
Deploying the Best Model will allow to interact with the HTTP API service and interact with the model by sending data over POST requests.

#### Now, we will deploy the best performing model. We use Azure Cluster Instance and Authentication for the same. 

![4](https://user-images.githubusercontent.com/61888364/102205121-bd10cc80-3ef0-11eb-8590-cdf41b9f1442.png)
 
## Step 4: Enable Application Insights
Now that the Best Model is deployed, enable Application Insights and retrieve logs using Azure Python SDK.

#### To enable Application Insights, we run the logs.py file.
 
![5](https://user-images.githubusercontent.com/61888364/102205274-fcd7b400-3ef0-11eb-863b-bb56bd50a966.png)
![6](https://user-images.githubusercontent.com/61888364/102205312-08c37600-3ef1-11eb-96c3-70dafc98559d.png)

#### Now Application Insights are enabled.

![7](https://user-images.githubusercontent.com/61888364/102205414-2b558f00-3ef1-11eb-9c8a-d04a601b1286.png)

## Step 5: Swagger Documentation
In this step, you will consume the deployed model using Swagger. Azure provides a Swagger JSON file for deployed models.

#### Now we run swagger.sh after downloading the swagger.json file in same folder. Then we will run the serve.py file. swagger.sh will download the latest Swagger container, and it will run it on port 9000. serve.py will start a Python server on port 8000.

![10](https://user-images.githubusercontent.com/61888364/102205643-7a032900-3ef1-11eb-994d-9f500b947700.png)

#### As a result we get swagger runs on localhost showing HTTP API methods and responses for the model.

![11](https://user-images.githubusercontent.com/61888364/102206395-889e1000-3ef2-11eb-9182-2d886acfcf59.png)

![12](https://user-images.githubusercontent.com/61888364/102206405-8b006a00-3ef2-11eb-9a58-503ea9f0ef6e.png)

## Step 6: Consume Model Endpoints
Once the model is deployed, use the endpoint.py script provided to interact with the trained model. We need to run the script after modifying both the scoring_uri and the key to match the key for the service and the URI that was generated after deployment.

#### Now we consume the Model Endpoints. We run the endpoint.py script with the scoring_uri and the key for our service. After that we get data.json file.

![13](https://user-images.githubusercontent.com/61888364/102206502-bf742600-3ef2-11eb-94b8-1b205bb9ff58.png)
#### On running endpoint.py in the terminal we got the output as below. 

![14](https://user-images.githubusercontent.com/61888364/102206663-fd714a00-3ef2-11eb-87f1-d401e5f487db.png)

## Step 7: Create, Publish and Consume a Pipeline
The config.json must be downloaded in current working directory.

#### Now, we create, publish and consume pipeline

![15](https://user-images.githubusercontent.com/61888364/102207309-ea12ae80-3ef3-11eb-9730-ffd1a9639970.png)
![16](https://user-images.githubusercontent.com/61888364/102207313-ec750880-3ef3-11eb-80e4-9bf853678c42.png)

#### The run was completed with no error.

![23](https://user-images.githubusercontent.com/61888364/102207358-fc8ce800-3ef3-11eb-8e1a-118c08947766.png)

#### Now we publish and run for REST endpoint

![18](https://user-images.githubusercontent.com/61888364/102207326-f139bc80-3ef3-11eb-95b4-8a391429cd75.png)
![19](https://user-images.githubusercontent.com/61888364/102207327-f1d25300-3ef3-11eb-8a03-360a674cad02.png)

#### Here the AutoML is being performed on the Bank Marketing Dataset

![20](https://user-images.githubusercontent.com/61888364/102207343-f72f9d80-3ef3-11eb-81e2-ebc15bc6205a.png)
![21](https://user-images.githubusercontent.com/61888364/102207350-f8f96100-3ef3-11eb-8b41-9a2f680b213e.png)

#### The run was successful with no errors.

![22](https://user-images.githubusercontent.com/61888364/102207354-fac32480-3ef3-11eb-8c49-4520f8d16fb0.png)

#### ML studio showing the pipeline endpoint as Active

![Endpoints - Pipeline-Acitve](https://user-images.githubusercontent.com/61888364/102290587-57abf280-3f67-11eb-9f91-feadd4b9f763.png)

## Link of the screencast:

https://drive.google.com/file/d/1bAJCczbbPfupSpIbDdxU0ITXGegeqa7M/view?usp=sharing 
