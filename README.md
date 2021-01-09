# MLOps-Azure

## Project Overview
I was working with the Bank-Marketing dataset, that contains information about a previous bank marketing campaign from a Portuguese institution, i.e. attributed of the people the campaign dealt with and <ins>if a client will subscribe to a term deposit product (which is a binary outcome)</ins>.
We seek to predict that outcome. This can be helpful in developing future marketing campaigns.
The best model, was the **VotingEnsemble** that had an accuracy of **91.806%**. Furthermore, we deployed the model, and consumed it through a REST endpoint. Thereby, we published our pipeline of steps, automating the whole procedure.

Following flow diagram depicts the process.
<img src="mlops-flow.png"/>


# Table of Contents
 * [Architecture Diagram](#arch)
 * [Future Improvements](#fi)
 * [The Process in Practice](#tpip)
     * [Authentication](#auth)
     * [Automated ML Experiment](#automl)
     * [Deploy the best model](#deploy)
     * [Enable logging](#logging)
     * [Swagger Documentation](#swagger)
     * [Consume model endpoints](#consume)
     * [Create and publish a pipeline](#pipeline)
 * [Screen Recording](#sr)
 * [Standout Suggestions](#ss)
 
 
## Architecture Diagram<a name="arch"></a>
Following is the architecture diagram to depict our approach and organisation.
<img src="mlops-arch.png"/>

## Future Improvements<a name="fi"></a>
* One can work with diferent datapoints, and visualise and benchmark the performance while actually using Application Insights.
* We may focus more time on exploring the data generating a more random dataset. The following columns have a broad gap in terms of number of instances:
    * There are far more married people than single and divorced.
    * There are far more people without a loan than with one.
    * The campaign maybe spread across the year for a better understanding of the customer's mood according to time of the year.
*Better data is bound to yield better results.*
* We can observe and generate a report on, to what extent does which factor affect the likeliness of a client to subscribe, and develop marketing campaigns around them.
* The AutoML experiment could also be run for a longer while which might as well fetch more effective models.
* Different parameters can be used in AutoML config in order to make more effective models.

## The Process in Practice<a name="tpip"></a>

#### Authentication <a name="auth"></a>
Skipped this section, since I used the provided labs.

#### Automated ML Experiment<a name="automl"></a>
Used the *Bank-Marketing* dataset for the task.
<img src="screenshots/Screen Shot 2021-01-07 at 3.14.00 PM.png"/>

& completed the AutoML experiment.
<img src="screenshots/Screen Shot 2021-01-07 at 4.20.28 PM.png"/>

The best model was the Voting Ensemble.
<img src="screenshots/Screen Shot 2021-01-07 at 4.20.40 PM.png"/>

#### Deploy the Best Model<a name="deploy"></a>
Deployed the model as an endpoint. Used an Azure Container Instance for the same, with authentication enabled i.e. key-based authentication.
<img src="screenshots/Screen Shot 2021-01-08 at 2.30.10 AM.png"/>

#### Enable Application Insights<a name="logging"></a>
The logs look as follows (post running `logs.py`).
<img src="screenshots/Screen Shot 2021-01-07 at 6.05.50 PM.png"/>

In the endpoints section of the Azure ML Studio, “Application Insights enabled” now says “true”, that are enabled while logging.
<img src="screenshots/application-insights-enabled-true.png"/>

The application insights URL in the bottom opens the applications.
<img src="screenshots/Screen Shot 2021-01-08 at 2.40.16 AM.png"/>

#### Swagger Documentation<a name="swagger"></a>
Pulled the latest swagger-ui docker image and to run it on port 80.
<img src="screenshots/Screen Shot 2021-01-07 at 7.05.09 PM.png"/>

Exposed swagger.json to a local HTTP server and run it in the swagger-ui.
<img src="screenshots/Screen Shot 2021-01-07 at 7.06.26 PM.png"/>

The API methods are:
<img src="screenshots/swagger2.png"/>
<img src="screenshots/swagger3.png"/>

#### Consume Model Endpoints<a name="consume"></a>
Entered Scoring URI and primary key in `endpoint.py` and ran it.
<img src="screenshots/Screen Shot 2021-01-07 at 6.46.48 PM.png"/>

I also performd *benchmarking* by adding appropriate URI in the `benchmarking.sh` file, & received results as follows:
<img src="screenshots/bm1.png"/>
<img src="screenshots/bm2.png"/>

#### Create, Publish and Consume a Pipeline<a name="pipeline"></a>
Completed the pipeline run.
<img src="screenshots/Screen Shot 2021-01-07 at 7.30.23 PM.png"/>

And created the pipeline endpoint.
<img src="screenshots/Screen Shot 2021-01-07 at 7.31.21 PM.png"/>

Following is how the pipeline looks like in the studio, with automl module and bank marketing dataset.
<img src="screenshots/Screen Shot 2021-01-08 at 3.04.09 AM.png"/>

I used the RunDetails widget in our Jupyter Notebook, which shows the output as follows:
<img src="screenshots/run-details-widget-nb.png"/>

The Pipeline appears in our experiments as follows:
<img src="screenshots/expt-section-pipeline-run.png"/>

Thereby, the pipeline is published and is also active as displayed in the screenshot below.
<img src="screenshots/Screen Shot 2021-01-07 at 7.35.17 PM.png"/>

## Screen Recording<a name="sr"></a>
<<<<<<< HEAD
<a href="https://youtu.be/bspUtA2201g">YouTube Video Link</a> contains the Working deployed ML model endpoint, Deployed Pipeline, Available AutoML Model, 
=======
This <a href="https://youtu.be/_AdKiVzcvh8">YouTube Video Link</a> contains the Working deployed ML model endpoint, Deployed Pipeline, Available AutoML Model, 
>>>>>>> 67dd49e4d60ad4708a163f96bf274f167a58d9ad
Successful API requests to the endpoint with a JSON payload et cetera in a screen recording.

## Standout Suggestions<a name="ss"></a>
I was redoing the experiment when I realised that, this time the AutoML run found **StackEnsemble** to be the best performing model, with an accuracy of 91.624%. This is marginally lesser than the accuracy I got with the *VotingEnsemble* previously i.e. 91.806%. Furthermore in this run, the VotingEnsemble had an accuracy of 91.563% which is actually quite close to the StackEnsemble. This indicates the requirement a more thorough look and longer run. As we know, AutoML is a tool to help data scientists, the output of this tool might become more effective or give a greater understanding with a deeper look and some more fine-tuning.
<img src="screenshots/stackensemble.png"/>
<img src="screenshots/Screen Shot 2021-01-09 at 1.21.19 AM.png"/>
 

