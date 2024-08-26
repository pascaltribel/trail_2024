# Meeting 26/07/24
## Near Real-time National Electricity Demand Forecasting: Case Study of Belgium and Great Britain
The project is organised in collaboration with project 12*: 

## Wifi
- tecnico-guest : Trail2024 - PrFpxz
- eduroam

## Sharepoint
<a href="https://cenaero.sharepoint.com/:f:/s/ARIAC/EpjmdSJsf2tCmPWTBbbvda8BB2H8-TAdXriozRP8lZ-vIw?e=5%3aLkdNwX&at=9&xsdata=MDV8MDJ8cGFzY2FsLnRyaWJlbEB1bGIuYmV8MDg3MTBmMzZlNjdhNDkwZmQ0NzMwOGRjYzM4YjY0Y2V8MzBhNTE0NWU3NWJkNDIxMmJiMDI4ZmY5YzBlYTRhZTl8MHwwfDYzODYwMDI1MDY3MTYzMjE5MXxVbmtub3dufFRXRnBiR1pzYjNkOGV5SldJam9pTUM0d0xqQXdNREFpTENKUUlqb2lWMmx1TXpJaUxDSkJUaUk2SWsxaGFXd2lMQ0pYVkNJNk1uMD18MHx8fA%3d%3d&sdata=aXdyZ01sTVdLYjVBSTBIRVRKaG04eC80Q2p5S2FIWW9NRkh5TnFJWlhUVT0%3d">Link to the data sharepoint</a>


## Raw notes
The data is 1.18 Go for NSIDE. Sharing it on GitHub won't be easy, but the link is provided above. 
In the sharepoint, there is the project description, a powerpoint for the last event for the team building, and the Data folder.

In this one, there is Belgium and GB. For Belgium, NSIDE, provided by Raphael, there is an ARIAC link for updated data. The csv is quite light. You can get more recent data on the online portal for every 15 minutes, from the first 15 january 2015 to current time. Some values are for the future and do not have any Total Load value, so make sure to chunk to the current time.
We do not have the information of when the "Most recent forecast" was performed. The ARIAC portal offers the information about every column. There is no information about the statistical parameters. The uncertainty can be used for statistical forecasting. There are columns for different forecastings made given times before (roughly 18PM the day before, and a week before). The method for those forecasts is not given. Using those is not mandatory. The data provided NSIDE is the same as the one provided by ELIA.
(On the ELIA portal there are more variables avaible, which might be used to forecast.)
For the UK data, we have two sources: open (ESO - like ELIA), with the same online portal, with a csv for each year. The portal provides an explanation for every variable. The data is sampled by 30 minutes periods (settlement period). National Demand is the Total Load. We have also the Transmission System Demand (National demand + the needs for generation, transport, storage). Wind generation is an estimation. There are much more variables than for Belgium. The interconnector has been studied in Trail Nantes.
The NSIDE data is different from the ISE (unlike for Belgium). Data is splitted by months. The data is also sampled by 30 minutes period. The national demand can be obtained by summing all the station data for each time step. We have more granularity but this data is less easy to work with. There is a method provided by NSIDE to use the data. We have to ask them more about it on our next meeting with them.

For Belgium, forecasted variables can be used in a really tricky way. Only the (at most) 4 next forecasts can be used. The procedure is explained in the document NSIDE_explanations. Some more recommandations are provided.

MAPIE provides a framework for forecasting with uncertainty quantification.

### Goal
Predicting for the next hour (4 or 2 steps) the National Demand.

## Wind Power Generation
Classification task: classify online what are the events that are going to occur. We have univariate time-series with labels of events. 

### Goal
Real-time classifying the samples according the samples.


## Decisions
We will start focusing on the Belgium use-case, and maybe extend it later. We can do some data analysis. Do some plots, statistics. Study preprocessing to discover seasonality. Start without the provided forecasts. Maybe use the other data (locations, weather, ... and other covariates). Someone can start with some machine learning. 

For now on, having the best prediction is the goal.

### Maybe
- Use ARIMA to make a baseline (but it takes a lot of time and requires to retrain). 
- Use persistence (using last prediction to make the next ones)


### Evaluation metrics
- RMSE, MAPE, MAE, ...


### Tasks
<i> Please, modify it because it was difficult to follow...</i>
- Preprocessing:
    - Analysis, preprocessing
    - Feature extraction, seasonality (strong, weak, ...) + Models
    - Pascal, Valisoa, Zahra
- Baseline ARIMA: Julien
- Baseline: Alejandro (sktime/darts+LSTCN) + baseline on the forecasted values provided
- Find related/covariate data on ELIA website (or other): Gianmarco
- ...

## Reports of subtasks
They can be put on the sharepoint.

### MLOps
Tomorrow is a presentation given about MLOps. 
