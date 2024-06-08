# user-clicks-analytics-etl
Databricks data pipeline for ingesting and processing data with data warehouse layers

# Creating Metastore bucket - GCS

<img width="410" alt="image" src="https://github.com/RahulDubey391/user-clicks-analytics-etl/assets/100185371/270c1ae3-a580-45c3-8fd5-0a791227032d">

Once the bucket is created, you can use it while creating(technically attaching) metastore in Databricks

<img width="749" alt="image" src="https://github.com/RahulDubey391/user-clicks-analytics-etl/assets/100185371/8a164fce-07a8-49a6-b1ff-c763a621df19">

# Creating Metastore - Databricks

<img width="950" alt="image" src="https://github.com/RahulDubey391/user-clicks-analytics-etl/assets/100185371/a9ae688d-3a97-48c5-be47-cd964bfd5842">

<img width="944" alt="image" src="https://github.com/RahulDubey391/user-clicks-analytics-etl/assets/100185371/f563761f-0fe5-4ada-8080-410f0d91ec10">

## Set permissions for the bucket you want to use as metastore

<img width="479" alt="image" src="https://github.com/RahulDubey391/user-clicks-analytics-etl/assets/100185371/26818755-a903-4e80-a225-fe1e2d00e761">

### Select "Permissions" tab in your Cloud Storage Bucket

<img width="739" alt="image" src="https://github.com/RahulDubey391/user-clicks-analytics-etl/assets/100185371/95cebf58-4979-4e21-854e-113f4b472680">

Once the bucket policy is updated, click the "Permission Granted" in the Databricks Pop-Up. 

### Skip the workspace assignment for now

<img width="946" alt="image" src="https://github.com/RahulDubey391/user-clicks-analytics-etl/assets/100185371/6e03c33b-edbe-4db0-b64a-705a4dc8cecf">

# Create Workspace and Assign Metastore

<img width="947" alt="image" src="https://github.com/RahulDubey391/user-clicks-analytics-etl/assets/100185371/d46d1527-66cb-4961-bd56-13ba0faa71d2">

## Click save once you are done with filling details

<img width="541" alt="image" src="https://github.com/RahulDubey391/user-clicks-analytics-etl/assets/100185371/b6e11a98-c2c9-4cb3-81be-3657f86fe81d">

## Once the workspace is created (will take 1-2 minutes), go back to the "Catalog" tab and click the metastore you created before then go to "Workspaces"

<img width="951" alt="image" src="https://github.com/RahulDubey391/user-clicks-analytics-etl/assets/100185371/7d878748-c521-4dfd-917d-161a23077f78">

## Click on the "Assign to workspace" and check the workspace you just created

<img width="952" alt="image" src="https://github.com/RahulDubey391/user-clicks-analytics-etl/assets/100185371/5718c911-a2a9-45e1-bd15-aef0e1afd25d">

This will enable Workspace to utilize the Unity Catalog both for your Lakehouse and the Spark Cluster

# Create Compute Cluster for Spark

<img width="959" alt="image" src="https://github.com/RahulDubey391/user-clicks-analytics-etl/assets/100185371/fd340c7b-cad8-4abf-ac1e-3866e1ab8a72">

## Click on "Create Compute" and setup the configuration, I am using 3 node cluster since the Databricks by default create a managed pool while creating workspace

<img width="715" alt="image" src="https://github.com/RahulDubey391/user-clicks-analytics-etl/assets/100185371/d4d0a30e-a24f-4afb-bb40-b198e3f1cf7e">


