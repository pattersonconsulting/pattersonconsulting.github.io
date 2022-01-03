# Manufacturing

In this section we cover data science use cases for the following sub-verticals of manufacturing:

* [Food Manufacturing](manufacturing.food)
* [Chemical Manufacturing](manufacturing.chemicals)


<!--
* [Pharmaceuticals Manufacturing](manufacturing.pharmaceuticals)
## Pharmaceutical Manufacturing

> TODO


disease identification
classify gum condition
classify cutaneous skin disorders
recommend medications
initial screening of drug compounds by forecasting success rates based on biological factors
measuring DNA and RNA quickly
predictive forecasts for supply chain
predicting drug candidate for trial based on history and disease conditions
predicting parameters in food, beverage, agriculture, and medicine
predicting seasonal demand for products
predicting customer preference to optimize product experience
eye-tracking analysis to detect product first fixation and time spsent, gaze plots, heatmaps
Rare Disease Patient Prediction (from claims databases)
Analysis of Physician Trends for Commercial Market Research
Risk-Based Monitoring using ML in Clinical Trials
Predicting correct active molecules that work most effectively on specific targets
predictive control of cell culture bioprocesses
predicting biopharmaceutical crtical quality attributes
Soft sensors – real-time estimation of CPPs / CQAs
Mode of operation selection – based on the classification of current process measurements into a discrete mode of operation to select appropriated monitor and control mechanisms
Chemometric models – extract information present on multidimensional spectra into metabolite concentration estimations
Multivariate data analysis – for the post-mortem analysis of the variation of Process Analytical Technology (PAT) instrumentation measurements in-process (such as identification of golden batch operation conditions)
Multivariate statistical process control – for process / product state monitoring and failure detection and identification to detect when the process is deviating from its normal / optimal behaviour and source causes
Process state-observers – estimate the entire process state, based on real-time input variable measurements
-->

(manufacturing.food)=
## Food Manufacturing


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
<td>Prediction of Foam Evolution During Beverage Bottling</td>
<td>Chemical Process Prediction</td>
<td class="use_case_desc">During the bottling of beverages, foam can severely impair the process as overflowing foam causes underfilled bottles and poses a high contamination risk. Consequently, the filling speed is limited by the foaming properties of the beverage. This method can increase filling speed and manufacturing throughput.</td>
<td>Images, Video</td>
<td>Convolutional Neural Network, Recurrent Neural Network</td>
<td><a href="./request_use_case_report.html">Request Custom Report</a></td>
</tr>

<tr>
<td>Seafood tissue inspection</td>
<td>Visual Inspection</td>
<td>Increase Manufacturing Throughput</td>
<td>Images</td>
<td>Convolutional Neural Network</td>
<td><a href="./request_use_case_report.html">Request Custom Report</a></td>
</tr>																	

<tr>
<td>Evaluation of green tea sensory quality</td>
<td>Olafactory Analysis</td>
<td>Predict Desirability of Product</td>
<td>Sensor Data</td>
<td>xgBoost, Neural Network</td>
<td><a href="./request_use_case_report.html">Request Custom Report</a></td>
</tr>																	

<tr>
<td>Using computer vision for fruit selection</td>
<td>Visual Inspection</td>
<td>Increase Manufacturing Throughput</td>
<td>Images</td>
<td>Convolutional Neural Network</td>
<td><a href="./request_use_case_report.html">Request Custom Report</a></td>
</tr>																	

<tr>
<td>Cream Cheese Fermentation pH prediction</td>
<td>Food Attribute Prediction</td>
<td>Predict Quality of Product</td>
<td>Tabular Data</td>
<td>Gradient Boosting Trees</td>
<td><a href="./request_use_case_report.html">Request Custom Report</a></td>
</tr>																	

<tr>
<td>Predicting cow milk quality traits from milk spectra</td>
<td>Food Attribute Prediction</td>
<td>Predict Quality of Product</td>
<td>Image Data</td>
<td>Convolutional Neural Networks</td>
<td><a href="./request_use_case_report.html">Request Custom Report</a></td>
</tr>					

<tr>
<td>Detecting claw lessions in dairy cows based on acoustic data</td>
<td>Detect defects in products</td>
<td>Increase yeild</td>
<td>Audio Data</td>
<td>Long-Short Term Neural Networks</td>
<td><a href="./request_use_case_report.html">Request Custom Report</a></td>
</tr>	

<!--
<tr>
<td>Predicting cattle heat stress</td>
<td></td>
<td></td>
<td>X Data</td>
<td>Neural Networks</td>
<td><a href="">Paper</a></td>
</tr>	


<tr>
<td>Predicting calving in dairy cattle</td>
<td></td>
<td></td>
<td>X Data</td>
<td>Neural Networks</td>
<td><a href="">Paper</a></td>
</tr>	


<tr>
<td>Estimating herbage production and nutrient uptake on dairy farms</td>
<td></td>
<td></td>
<td>X Data</td>
<td>Neural Networks</td>
<td><a href="">Paper</a></td>
</tr>	
-->
</table>


(manufacturing.chemicals)=
## Chemical Manufacturing


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
<td>Carrier surface design in carrier-based dry powder inhalation</td>
<td>Material Process Prediction</td>
<td class="use_case_desc">Effects of key surface roughness variables on DPI performance</td>
<td>SEM Images</td>
<td>Convolutional Neural Network, Neural Network</td>
<td><a href="./request_use_case_report.html">Request Custom Report</a></td>
</tr>

 
<tr>
<td>Forecasting industrial aging processes</td>
<td>Predictive Maintenance</td>
<td class="use_case_desc">Machine learning models can be used to accurately forecast industrial aging processes. Accurately predicting industrial aging processes makes it possible to schedule maintenance events further in advance, ensuring a cost-efficient and reliable operation of the plant.<br/>See our <a href="http://www.pattersonconsultingtn.com/blog/predictive_maintenance_w_snowflake_ml_part_1_biz.html">Predictive Maintenance Series for a live example</a></td>
<td>Industrial Sensor Data</td>
<td>Long-Short Term Memory Network</td>
<td><a href="./request_use_case_report.html">Request Custom Report</a></td>
</tr>


<tr>
<td>Computational fluid dynamics-based in-situ sensor analytics of direct metal laser solidification process</td>
<td>Manufacturing Process Improvement</td>
<td class="use_case_desc">Better production of parts with ultra-high precision and variable geometries</td>
<td>Manufacturing Image Data</td>
<td>Convolutional Neural Network</td>
<td><a href="./request_use_case_report.html">Request Custom Report</a></td>
</tr>


<tr>
<td>Molecular design/screening methodology for fragrance molecules</td>
<td>Manufacturing Process Improvement</td>
<td class="use_case_desc">The odor of molecules are predicted using a data driven machine learning approach, improving the quality of the product and speed of new fragrance development. Predicted properties include: vapor pressure, solubility parameter and viscosity.</td>
<td>Fragrance chemical data</td>
<td>mixed-integer linear program (MILP)</td>
<td><a href="./request_use_case_report.html">Request Custom Report</a></td>
</tr>


<tr>
<td>Modeling and operation of plasma-enhanced atomic layer deposition of hafnium oxide thin films</td>
<td>Manufacturing Process Improvement</td>
<td class="use_case_desc">Model is demonstrated to accurately characterize the key aspects of the deposition process as well as the gas-phase transport profile while maintaining computational efficiency. </td>
<td>Sensor data from process</td>
<td>Recurrent Neural Network</td>
<td><a href="./request_use_case_report.html">Request Custom Report</a></td>
</tr>

</table>

<!--
(manufacturing.pharmaceuticals)=
## Pharmaceuticals Manufacturing

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
<td>[Title]</td>
<td>[Group]</td>
<td class="use_case_desc">[...]</td>
<td>[data]</td>
<td>Convolutional Neural Network, Neural Network</td>
<td><a href="./request_use_case_report.html">Request Custom Report</a></td>
</tr>


<tr>
<td>[Title]</td>
<td>[Group]</td>
<td class="use_case_desc">[...]</td>
<td>[data]</td>
<td>Convolutional Neural Network, Neural Network</td>
<td><a href="./request_use_case_report.html">Request Custom Report</a></td>
</tr>


<tr>
<td>[Title]</td>
<td>[Group]</td>
<td class="use_case_desc">[...]</td>
<td>[data]</td>
<td>Convolutional Neural Network, Neural Network</td>
<td><a href="./request_use_case_report.html">Request Custom Report</a></td>
</tr>


<tr>
<td>[Title]</td>
<td>[Group]</td>
<td class="use_case_desc">[...]</td>
<td>[data]</td>
<td>Convolutional Neural Network, Neural Network</td>
<td><a href="./request_use_case_report.html">Request Custom Report</a></td>
</tr>

</table>
-->
<!--

## Chemical Manufacturing

> TODO

## Medical Manufacturing

> TODO

## Electronics Manufacturing

> TODO

-->
