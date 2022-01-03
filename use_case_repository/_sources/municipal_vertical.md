# Municipal / Smart City

There are 3 levels to the municipal vertical:

1. Intelligent Transport Systems (ITS)
2. Smart Mobility Systems
3. The Greater Smart City Domain

In the current version of this document we focus on the Intelligent Transport Systems domain.

## Intelligent Transport Systems (ITS)

Intelligence Transport Systems follow a specific pattern of application evolution.

The successful market cycle of Intelligence Transport Systems (ITS) applications (based on Patterson Consulting customer analysis) is:

1. Collect / Report Applications
   - Deploy application to service specific market function around tracking an asset (typically here a vehicle) and providing a summarized report to the end user
   - Reporting / Cost Savings
   -  Deliver incremental value that helped the industry achieve efficiency (or other objective improved safety) before jumping right into automation
2. Analytic Applications
   - Operations / Compliance for a customer fleet
3. Automation / Prediction Applications
   - Analytics across the population of all fleets 
   - Automation / Prediction
   - Operations / Planning / Infrastructure design

Applications begin life as a way to collect and track basic data about a municipal function (e.g., "counting cars as they pass"). Eventually these applications into other applicaitons that produce analytical insights into the municipal data. Finally, in some use cases it makes sense to make predictions about the data to better provide insights into municipal activities.

In the next section we break out 3 core business model categories for ITS Applications.

### Value Models for ITS Applications

Three models of utility or value to consider when looking to frame a business value model for a given customer need:

1. User-Based Insurance as a Generalized Smart City Business Model
   - Example: *“Lowering a cities insurance costs through monitoring”*
2. Applications That Save Cities Money
   - Example: *“Quantify and prioritize repairs”*
3. Applications That Mitigate City’s Operational Risk
   - Example: *“reviewing historical data to understand cause”*

Creating the above triage list allows us to more easily map a potential use case into a value model quickly. With the value model expressed, let's now look at the first tier of ITS Applications: "Collect and Report Applications".

### ITS Collect and Report Applications

Building a new ITS application (first tier ITS) for a given segment (e.g., water, road, air) MUST understand the objective of the city at the current time and make sure the product fit we can provide helps solve those specific problems. Typically the earliest form of ITS Applications are "Collect and Report" applications.

This phase is characterized by:
- Repeatable integrations to support consistent data collection
- basic reporting
- Focus on fulfilling customer utility

As described in the previous section, the value customers see in “collect and report”-class of applications are:

- Quantify the outstanding maintenance issues
- Prioritize repairs & maintenance 
- Push alerts to 3rd party service contractors for timely response, and SLA management
- Recall historical data to evaluate / review
   - Example: *Access to this information allows the city to adjust service schedules to save costs*

While these applications may be simpler than the more "exciting" predictive applications, it is difficult to jump directly beyond this stage for a new application in a given domain. Specifically, the need to deliver incremental value that helps the industry achieve efficiency (or other objective improved safety) is critical before jumping right into machine learning or automation.


<!--
#### Key identified transportation segments:

- traffic management
- environment protection
- freight management
- public transport
- road safety and security
- automotive telematics
- road user charging
- parking management
- Road tolling
-->


### ITS Analytics

This phase is characterized by:

- Generating incremental value from the consistent data collection
- Generation of analytical data to inform the customer
- Focus on areas of cost savings and efficiency, improve operations

#### ITS Analytical Use Cases

<style>
th, td {
padding: 6px;
text-align: left;
vertical-align: top;
font-size: 12px;
}
td.use_case_desc {
	font-size: 10px;
}
th {
  background-color: #666666;
  color: white;
}
tr:nth-child(even) {background-color: #e2e2e2;}
tbody{
    width: 100%;
    display: table;
}
</style>

<table style="width: 100%; border: 1px solid;">
<tr>
<th>Use Case</th>
<th>Sub-Group</th>
<th>Benefit</th>
<th>Dataset</th>
<th>Method</th>
<th>Paper</th>
</tr>

<tr>
<td>Public tansport optimization</td>
<td>ITS Analytics</td>
<td>better use of municpal funds</td>
<td>public transport records</td>
<td>Analytic tools</td>
<td><a href="./request_use_case_report.html">Request Custom Report</a></td>
</tr>


<tr>
<td>Sidewalk accessibility analysis</td>
<td>ITS Analytics</td>
<td>better use of municpal funds</td>
<td>public transport records</td>
<td>Analytic tools</td>
<td><a href="./request_use_case_report.html">Request Custom Report</a></td>
</tr>


<tr>
<td>Traffic Accident analysis</td>
<td>ITS Analytics</td>
<td>better municpal safety</td>
<td>accident data, roadway geometrics</td>
<td>Analytic tools</td>
<td><a href="./request_use_case_report.html">Request Custom Report</a></td>
</tr>

<tr>
<td>Rail Crossings and Emergency Transportation Interference analysis</td>
<td>ITS Analytics</td>
<td>better municpal safety</td>
<td>accident data, roadway geometrics</td>
<td>Analytic tools</td>
<td><a href="./request_use_case_report.html">Request Custom Report</a></td>
</tr>


<tr>
<td>Electric Car Charging Pattern Reporting and Analysis</td>
<td>ITS Analytics</td>
<td>Municipal Planning</td>
<td>traffic data</td>
<td>Analytic tools</td>
<td><a href="./request_use_case_report.html">Request Custom Report</a></td>
</tr>

<tr>
<td>Healthcare and City Planning: Modeling PM2.5 and Traffic <br/>See Also: <a href="http://www.pattersonconsultingtn.com/blog/cuip_smart_city_data_challenge_2019.html">Our Blog Article on pm2.5 Analysis</a></td>
<td>ITS Analytics</td>
<td>Municpal planning</td>
<td>pm2.5 data, traffic data</td>
<td>Python, Pandas</td>
<td><a href="./request_use_case_report.html">Request Custom Report</a></td>
</tr>


</table>

### ITS Predictive Modeling

This is the most mature phase of the 3, where more advanced Statistical models are used to make predictions (or drive the automation of municipal systems). This is the phase where KPIs could be generated from analytical data, and then compared to global analytical data to understand how well the city operates. 

An example of building predictive modeling applications based on sensor data can be seen in our series on [Predictive Maintenance in Manufacturing](http://www.pattersonconsultingtn.com/blog/predictive_maintenance_w_snowflake_ml_part_1_biz.html)

#### ITS Predictive Use Cases

<table style="width: 100%; border: 1px solid;">
<tr>
<th>Use Case</th>
<th>Sub-Group</th>
<th>Benefit</th>
<th>Dataset</th>
<th>Method</th>
<th>Paper</th>
</tr>

<tr>
<td>Predicting Traffic Ticket Locations</td>
<td>ITS Preditictive Application</td>
<td>better use of municpal funds</td>
<td>traffic data, traffic citation records</td>
<td>Analytic and machine learning tools, neural networks, xgBoost</td>
<td><a href="./request_use_case_report.html">Request Custom Report</a></td>
</tr>


<tr>
<td>Predicting Traffic Accident Locations</td>
<td>ITS Preditictive Application</td>
<td>Municipal planning, better use of municpal funds</td>
<td>traffic data, accident records</td>
<td>Analytic and machine learning tools, gradient boosted trees, xgBoost</td>
<td><a href="./request_use_case_report.html">Request Custom Report</a></td>
</tr>

<tr>
<td>Predicting air pollition levels based on traffic data</td>
<td>ITS Preditictive Application</td>
<td>Municipal planning</td>
<td>traffic data, air sensor data</td>
<td>Analytic and machine learning tools, neural networks, xgBoost</td>
<td><a href="./request_use_case_report.html">Request Custom Report</a></td>
</tr>


<tr>
<td>Predicting salt truck maintenance</td>
<td>ITS Preditictive Application</td>
<td>Municipal cost savings</td>
<td>vehicle sensor data</td>
<td>Analytic and machine learning tools, decision trees, xgBoost</td>
<td><a href="./request_use_case_report.html">Request Custom Report</a></td>
</tr>


<tr>
<td>Predicting garbage truck maintenance</td>
<td>ITS Preditictive Application</td>
<td>Municipal cost savings</td>
<td>vehicle sensor data</td>
<td>Analytic and machine learning tools, decision trees, xgBoost</td>
<td><a href="./request_use_case_report.html">Request Custom Report</a></td>
</tr>


<tr>
<td>Predicting public bus transport maintenance</td>
<td>ITS Preditictive Application</td>
<td>Municipal cost savings</td>
<td>vehicle sensor data</td>
<td>Analytic and machine learning tools, decision trees, xgBoost</td>
<td><a href="./request_use_case_report.html">Request Custom Report</a></td>
</tr>
</table>
