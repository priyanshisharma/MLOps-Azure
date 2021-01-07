# MLOps-Azure

## Project Overview
I was working with the Bank-Marketing dataset, that contains information about a previous bank marketing campaign from a Portuguese institution, i.e. attributed of the people the campaign dealt with and if a client will subscribe to a term deposit product (which is a binary outcome).
We seek to predict that outcome. This can be helpful in developing future marketing campaigns.
The best model, was the VotingEnsemble that had an accuracy of 91.806%. Furthmore, we deployed the model, and consume it through a REST endpoint. Therby, we publish our pipeline of steps, automating the whole procedure.

## Architecture Diagram
Following flow diagram depicts the process.
<img src="mlops-arch.png"/>

This entire process can be seen as :
* Authentication
* Automated ML Experiment
* Deploy the best model
* Enable logging
* Swagger Documentation
* Consume model endpoints
* Create and publish a pipeline
* Documentation
