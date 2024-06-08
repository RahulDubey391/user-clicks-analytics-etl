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

# Create Storage Credentials and External Location

While the Compute Cluster is being created, you can attach the external location (outside bucket) if you have some data to be brought in the Databricks. 

## In Catalog tab, select the "Add Data" drop down and then select "Add a storage credential"

<img width="956" alt="image" src="https://github.com/RahulDubey391/user-clicks-analytics-etl/assets/100185371/1779c667-803d-4317-80c2-8de387f46c19">

## Set the values for the form and click "Create"

<img width="488" alt="image" src="https://github.com/RahulDubey391/user-clicks-analytics-etl/assets/100185371/48086e0d-fae6-40d4-b83b-e5f0fe6764a5">

You will be asked assign permissions to your external location bucket, set so in your Cloud Provider

<img width="415" alt="image" src="https://github.com/RahulDubey391/user-clicks-analytics-etl/assets/100185371/2dc3fd70-d46a-4467-96d4-1699b6eca7c2">

## Once done, go to Catalog tab again and click "Add External Location"

<img width="954" alt="image" src="https://github.com/RahulDubey391/user-clicks-analytics-etl/assets/100185371/adab67c0-36f7-4b4b-b1c6-de98c0b070b3">

## Fill in the form with appropriate details and click "Create"

<img width="587" alt="image" src="https://github.com/RahulDubey391/user-clicks-analytics-etl/assets/100185371/6a4b38a1-450d-41fe-810f-5c022ae5e191">

## Once the external location is created successfully, you can test the connection if the objects in your external bucket is visible to Databricks

<img width="939" alt="image" src="https://github.com/RahulDubey391/user-clicks-analytics-etl/assets/100185371/5ef1e9cb-c5e9-4b2c-be38-42d317bc2f79">

# Setting up Schema Layers for your Data Lake

## Create a Notebook and attach the Compute Cluster. Once done you can fire up the queries to create schema
<img width="925" alt="image" src="https://github.com/RahulDubey391/user-clicks-analytics-etl/assets/100185371/58d94a75-c6b2-43ed-82f9-22bae1b5b56d">

Logically, the schema I am using is analogus to the Medallion architecture. You can use other names as well.

# Reading, Transforming and Storing External Data

## Read the file (in my case its a 1.4 GB CSV file) with the optional fields.

<img width="770" alt="image" src="https://github.com/RahulDubey391/user-clicks-analytics-etl/assets/100185371/4342857e-a87e-47b7-9356-7ddff0d7431b">

You'll notice, I am also printing out the Number of Partitions and Max Byte Size for partition.

## Transforming the data by processing Year, Month, Day to Date format and applying ordering

<img width="785" alt="image" src="https://github.com/RahulDubey391/user-clicks-analytics-etl/assets/100185371/8550ae06-aa11-4886-8f68-6e4654274017">

I am also applying sorting based on each column so that we can get benefitted while writing as partitions

## Storing Data as Delta Table in Landing Layer

<img width="775" alt="image" src="https://github.com/RahulDubey391/user-clicks-analytics-etl/assets/100185371/8bbd6967-ff2b-44c2-915b-f8adddb6a00d">

Once the table is created in the Landing layer, you'll see that the table appears with Column specification. Although the data is partitioned, but still further cleaning is required to remove duplicates and other things to make it suitable for Conformed layer.

## Transforming data in Landing layer to store in Conformed layer

Since, we don't want to choose the 2023 data to be in Conformed layer, I'll drop those records. Also for duplicates, I'll remove them as well

<img width="779" alt="image" src="https://github.com/RahulDubey391/user-clicks-analytics-etl/assets/100185371/4efd60fd-f711-4059-95e0-3a30da8ba07e">

