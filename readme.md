<h3>Grab AI For Sea: Traffic Management Challenge</h3>
<h5>Problem Statement:</h5>
How may we improve the traffic congestion for Southeast Asia's roads by leveraging Grab's booking demand data? <br>
Link: https://www.aiforsea.com/traffic-management
<h5>Objective:</h5>
In this challenge, participants are to build a model trained on a historical demand dataset, that can forecast demand on a Hold-out test dataset. The model should be able to accurately forecast ahead by T+1 to T+5 time intervals (where each interval is 15-min) given all data up to time T.
<h5>Dataset:</h5>
The given dataset contains normalised historical demand of a city, aggregated spatiotemporally within geohashes and over 15 minute intervals. The dataset spans over a two month period.
<ul>
    <li>geohash6: encoded geographic location</li>
    <li>day: days follow sequential order and not a particliar day of the month</li>
    <li>timestamp: 15-minute intervals</li>
    <li>demand: aggregated demand normalized with values from 0 to 1</li>
</ul>
<h5>Problem Overview:</h5>
<ul>
    <li>This is a timeseries forcasting problem.</li>
    <li>Data leakage is very crucial, the model must train the data in sequential order and must not be trained with the future data.</li>
    <li>Demand could be varied depend on the place, timestamp and day of the week. For instance, The demand around shopping mall is huge at evening on weekend while the demand around office is huge at morning or lunch time on week day.</li>
    <li>The latitude and logitude were anonymized. We can't really get human insight about the city, blocks and point of interest, etc.</li>
    <li>By binning the latitude and longitude into groups and then do feature crossing between them, we are able to create zones and learn their different pattern of demand.</li>
    <li>Day of the week (0,1,2,3,4,5,6) helps us learn the trend of demand for particular datetime without the need to identify the weekday and weekend.</li>
</ul>
<h5>Solution:</h5>
<ul>
    <li>Using Recurrent Neural Network (LSTM)</li>
    <li>In total of 61 day data, first 47 days will be used as training set and the last 14 days are for validation.</li>
    <li>Features included: day of the week, zones, timestamp, demand from lastweek(at particular timestamp) and demand from yesterday(at particular timestamp). Detailed in the code.</li>
    <li><b>There are 3 jupyter notebooks. Please run 1_EDA.ipynb, then 2_Preprocessing.ipynb, and 3_Model.ipynb.</b></li>
    <li><b>Notebook 2_Preprocessing.ipynb will transform the given data into new csv file, which will be used in the third notebook 3_Model.ipynb</b></li>
</ul>
