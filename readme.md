# Project-9.5-NYC-Event-Driven-Data-Analytics-Dataproc-Pyspark
## New Service Flow
![](images/new-dash3.png)

## Old Service Flow
![](images/data-flow.png)

# Introduction - 
## New - 
This project leverages an event-driven data pipeline using Cloud Functions triggered by Cloud Storage uploads. Cloud Dataproc and PySpark transform data based on a comprehensive model, with analytical SQL on BigQuery analyzing the results. SQL joins denormalize data for dashboard needs. The final deliverable is an analytics dashboard visualizing insights from the denormalized data utilizing GCP services like Cloud Functions, Dataproc, PySpark, BigQuery, and data viz tools for scalable, event-driven data transformation, analysis, and insights.
## Old - 
This Data Analytics/Data Engineering project involves normalizing and denormalizing existing data for various purposes. A comprehensive data model has been created and visualized to guide the process. The transformation steps required to establish the data model have been executed using Google Cloud Dataproc and PySpark for distributed data processing. Analytical queries have been written using SQL on BigQuery to analyze the transformed data. Through employing SQL joins, the essential data has been denormalized specifically for the project's dashboard requirements. The final step in this project involves creating an analytics dashboard to visualize and present the denormalized data insights.

# Tech Stack used - 
1. Python - Used the all time famous Pyspark framework
2. Jupyter notebook in Google Cloud Dataproc
3. Lucid Chart to visualize Data Model
4. Google Cloud Storage
5. Google Cloud Bigquery
6. Google Cloud Dataproc
7. Google cloud Functions
8. Looker Studio

# How to deploy it yourself?
1. The pyspark code creates the following data model👇
![](images/Data-Model.png)

2. Now lets get to Google Cloud Platform. Open you Google Cloud Console.
3. Open Bigquery and create a dataset of your choice, for the sake of deployment, I will name it 'uber_data_dataproc' like the image below👇
![](images/dataproc.png)
4. Now we will head to Google Cloud Dataproc to create the spark cluster. Open Dataproc in your console.
5. Click on create cluster and create cluster. Click create on Compute Engine and then set following settings👇
![](images/set1.png)
![](images/set2.png)
![](images/set3.png)
![](images/set4.png)
![](images/set5.png)
![](images/set6.png)
![](images/set7.png)

6. Click on create and after a few minutes your cluster should be running:) Click on the cluster name.
![](images/cluster.png)

7. Click on the web interfaces section in the headers.
![](images/web.png)

8. Now click on JupyterLab link under the Component Gateway section.
![](images/wb.png)

9. You will be greeted with an introduction page like this where you have to select Pyspark kernel.
![](images/kernel.png)

10. Now a jupyter notebook will open where you need to copy the code which I have provided in the code.ipynb file in this repo.
![](images/code.png)

11. Now we need the link to our csv data to put it in the code so create a bucket in google cloud storage, make it public and put it's link in the 'Data-Loader' section in the jupyter notebook.
12. Now replace the link to your csv file, edit the dataset names according to your project and start running the notebook cells one by one.
13. After the notebook has successfully run, you can view your table in Bigquery👇
![](images/tables.png)

14. Now you can run a few analytical queries to answer questions coming to your mind
![](images/sql1.png)
![](images/sql2.png)

15. Now we can also utilize Bigquery to build a Dasboard, but to do so we need a table which has all the columns we need to make it. In order to do that we run the following SQL query - 
![](images/big.png)

16. We can make a dashboard like the one below -

![](images/dashboard-1.png)

![](images/dashboard-2.png)

![](images/dashboard-3.png)

# Extra - 
1. We can make this pipeline event driven by adding cloud functions to trigger the dataproc cluster whenever data is uploaded to Cloud Storage.
2. We can make this a schedule driven pipeline by adding our jupyter notebook as a job and then scheduling the pipeline run using Cloud Scheduler.

# Update - 1
### In this update we will convert our project into an event driven pipeline using Cloud Function and Scheduled Query
![](images/new_dash.png)

# How to do this?
1. Create 2 folders named python and input in our previously used cloud storage bucket. Make the necessary changes in the main.py file like project name change, bigquery dataset name change, etc.
![](images/cs.png)

2. In the python folder place the main.py file in the cloud function folder in this repo.
![](images/cs2.png)

3. Create a cloud function with the following configurations -
![](images/one.png)
![](images/two.png)
![](images/three.png)

4. Click on next.
5. Now change the runtime to 'Python 3.10', change the Entry Point to 'dataproc_job'. In the main.py file paste the code that is written in the cloud-function.py file in the cloud function folder in this repo. Also paste the requirements from the requirements.txt to the cloud function's requirements.txt file.
![](images/cf.png)

6. Click on deploy to deploy the function :)
7. Now upload the file 'uber_data.csv' in the input folder of the cloud storage bucket to trigger the cloud function. After a while you will have your tables in the bigquery dataset.

![](images/dataset.png)

9. Now to complete the pipeline we will schedule our SQL query which will create our master table for our Looker Studio Dashboard.
![](images/schedule.png)

### Options -
1. We can also convert our pyspark code to a Dataproc job and add it as a workflow template. The we can trigger that workflow template using Cloud Function
2. We can make this a schedule driven pipeline by adding our jupyter notebook as a job and then scheduling the pipeline run using Cloud Scheduler.

### Thank You😎😎 Keep working - Keep Grinding🫠










