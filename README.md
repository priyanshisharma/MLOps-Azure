# MLOps-Azure

## Project Overview
I was working with the Bank-Marketing dataset, that contains information about a previous bank marketing campaign from a Portuguese institution, i.e. attributed of the people the campaign dealt with and if a client will subscribe to a term deposit product (which is a binary outcome).
We seek to predict that outcome. This can be helpful in developing future marketing campaigns.
The best model, was the VotingEnsemble that had an accuracy of 91.806%. Furthmore, we deployed the model, and consume it through a REST endpoint. Therby, we publish our pipeline of steps, automating the whole procedure.

## Architecture Diagram
Following flow diagram depicts the process.
<img src="mlops-arch.png"/>

This entire process can be seen as :
* [Authentication](#auth)
* [Automated ML Experiment](#automl)
* [Deploy the best model](#deploy)
* [Enable logging](#logging)
* [Swagger Documentation](#swagger)
* [Consume model endpoints](#consume)
* [Create and publish a pipeline](#pipeline)

## Future Improvements
* One can work with diferent datapoints, and visualise and benchmark the performance while actually using Application Insights.
* We may focus more time on exploring the data generating a more random dataset. The following columns have a broad gap in terms of number of instances:
    * There are far more married people than single and divorced.
    * There are far more people without a loan than with one.
    * The campaign maybe spread across the year for a better understanding of the customer's mood according to time of the year.
*Better data is bound to yield better results.*
* We can observe and generate a report on, to what extent does which factor affect the likeliness of a client to subscribe, and develop marketing campaigns around them.
* The AutoML experiment could also be run for a longer while which might as well fetch more effective models.
* Different parameters can be used in AutoML config in order to make more effective models.

## The Process in Practice

#### Authentication <a name="auth"></a>
Skipped this section, since I used the provided labs.

#### Automated ML Experiment<a name="automl"></a>
Used the *Bank-Marketing* dataset for the task.
<img src="screenshots/Screen Shot 2021-01-07 at 3.14.00 PM.png"/>

And completed the AutoML ecperiment
<img src="screenshots/Screen Shot 2021-01-07 at 4.20.28 PM.png"/>

The best model was the Voting ensemble
<img src="screenshots/Screen Shot 2021-01-07 at 4.20.40 PM.png"/>

#### Deploy the Best Model<a name="deploy"></a>
Deploy the model as an endpoint. Use an Azure Container Instance for the same, with authentication enabled.
<img src="screenshots/Screen Shot 2021-01-08 at 2.30.10 AM.png"/>

#### Enable Application Insights<a name="logging"></a>
The logs look as follows (post running `logs.py`).
<img src="screenshots/Screen Shot 2021-01-07 at 6.05.50 PM.png"/>

The application insights URL in the bottom opens the applications, that are enabled while logging.
<img src="screenshots/Screen Shot 2021-01-08 at 2.40.16 AM.png"/>

#### Swagger Documentation<a name="swagger"></a>
Pull the latest swagger-ui docker image and to run it on port 80.
<img src="screenshots/Screen Shot 2021-01-07 at 7.05.09 PM.png"/>

Expose swagger.json to a local HTTP server and run it in the swagger-ui.
<img src="screenshots/Screen Shot 2021-01-07 at 7.06.26 PM.png"/>

#### Consume Model Endpoints<a name="consume"></a>
Entered Scoring URI and primary key in `endpoint.py` and run it.
<img src="screenshots/Screen Shot 2021-01-07 at 6.46.48 PM.png"/>

#### Create, Publish and Consume a Pipeline<a name="pipeline"></a>
Completed the pipeline run.
<img src="screenshots/Screen Shot 2021-01-07 at 7.30.23 PM.png"/>

And created the pipeline endpoint.
<img src="screenshots/Screen Shot 2021-01-07 at 7.31.21 PM.png"/>

Following is how the pipeline looks like in the studio, with automl module and bank marketing dataset.
<img src="screenshots/Screen Shot 2021-01-08 at 3.04.09 AM.png"/>

Thereby, the pipeline is published and is also active as diaplayed in the screenshot below.
<img src="screenshots/Screen Shot 2021-01-07 at 7.35.17 PM.png"/>
 
#### YouTube Video Link - https://youtu.be/_AdKiVzcvh8
