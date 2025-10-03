# Azure Databricks & Spark For Data Engineers:Hands-on Project

In this course : Build data lake in azure by ingesting formula 1 race data from external API. Perform transformation using databricks. Then analyze the data using databrick and create a power BI dashboard. THe pipeline are built on Azure Data Factory.

Azure databricks service. – Easily spin up spark clusters, Jupyter notebook ide, Photon engine, Unity catalog, Delta lake, delta live tables, Databricks workflows, SQL warehouse, ML flow, Databricks IQ

# Create Azure databricks service
Create a resource

<img width="257" height="101" alt="image" src="https://github.com/user-attachments/assets/f1fa5fa9-3979-46f6-8c51-ede512130828" />

Search for databricks
<img width="651" height="428" alt="image" src="https://github.com/user-attachments/assets/65b84d3a-129c-41ba-9040-ee74b2261d1f" />
<img width="480" height="229" alt="image" src="https://github.com/user-attachments/assets/6342ee44-e0ef-46b9-97c5-6f2f23fd7e88" />

Basics
Resource group – f1-databricks-rg
Workspace name- f1-databricks-ws
Select region – UK South
Pricing Tier – Premium
 
Review + Create
<img width="436" height="447" alt="image" src="https://github.com/user-attachments/assets/cfd0554a-56ef-44d9-bc57-9168b543cef9" />

<img width="1486" height="461" alt="image" src="https://github.com/user-attachments/assets/402ca589-c8a3-483b-8536-a42710d115d3" />

Go to resource
<img width="564" height="209" alt="image" src="https://github.com/user-attachments/assets/1378bd09-0765-4f50-85f0-7a43ca8dd964" />

<img width="1919" height="851" alt="image" src="https://github.com/user-attachments/assets/f5449bd5-cf9a-45ed-9743-aaa20ce54748" />

# Create a dashboard and Pin resource to dashboard

<img width="279" height="129" alt="image" src="https://github.com/user-attachments/assets/0dbc47f8-42d3-4d34-914e-eef08062219e" />

<img width="203" height="448" alt="image" src="https://github.com/user-attachments/assets/ef283089-f87f-4bdd-8c3a-a6002ac2d7a4" />

<img width="140" height="127" alt="image" src="https://github.com/user-attachments/assets/8a3720e8-3a30-4d9b-9d87-8c4dd87b805e" />

<img width="266" height="120" alt="image" src="https://github.com/user-attachments/assets/f90384b2-46c5-4a34-a9fb-21b70273f7bd" />

<img width="951" height="551" alt="image" src="https://github.com/user-attachments/assets/58fa0826-e8b9-48f2-ab03-6a4f883aaf22" />

# Launching databricks workspace
<img width="951" height="407" alt="image" src="https://github.com/user-attachments/assets/e5d46792-4f51-404b-9ccc-66eeec60bf37" />

<img width="1919" height="833" alt="image" src="https://github.com/user-attachments/assets/94a759ab-3d50-40fa-ab17-59e24c9306a7" />

Resources automatically created - VNet, NSG, Azure Blob Storage, Databricks Workspace
<img width="1521" height="691" alt="image" src="https://github.com/user-attachments/assets/94bbb8e9-44ec-4664-9dc1-cda6de306a2a" />

Databricks UI overview explanation and important sections.

# Setting default catalog to Hive Metastore
We can either use hive metastore or unity catalog for registering databricks objects.
Default catalog in databricks - unity catalog

Go to settings
<img width="959" height="205" alt="image" src="https://github.com/user-attachments/assets/35be8b1b-ca9f-4222-8c23-381b1038bb95" />

If anything other than hive metastore is displayed here it means that it is using unity catalog
<img width="881" height="335" alt="image" src="https://github.com/user-attachments/assets/16d37d79-c6ff-476b-8efe-833e882b1266" />

Type hive_metastore and click save
<img width="457" height="110" alt="image" src="https://github.com/user-attachments/assets/44068ed1-2db6-4c34-a13b-63e0c63e589c" />
<img width="924" height="318" alt="image" src="https://github.com/user-attachments/assets/f2929ff0-bcc3-4b56-b115-99a428b18c2c" />
<img width="989" height="224" alt="image" src="https://github.com/user-attachments/assets/8fbd7299-1c6b-454f-9b99-e0f49289c7e2" />


# Azure databricks architecture overview
Control Plane (Databricks subscription) - Databricks UX, Cluster Manager, DBFS, Cluster metadata
Data Plane (Customer subscription) - VNet, NSG, Azure Blob Storage, Databricks Workspace


# Databricks Cluster
## WHat is databricks cluster - 
Collection of VMs, Driver and worker
## Cluster type
All Purpose - Created and deleted manually
Job - Created and deleted automatically when job is created and deleted
Pools

## Cluster configuration
### Nodes - 
Single Node - Only 1 driver node. No worker node. Act both as driver and worker. Not scalable. Not suitable for large ETL.
Multi Node - 1 driver, 1 or more worker, horizontal scalability

### Access Mode - 
Single user - Only one user assess; Availble in standard and premium workspaces; Supports Python, SQL, R, Scala
Shared - Multiple user access; Availble only in premium workspaces; Supports Python, SQL
No Isolation Shared - Multiple user access; Availble in standard and premium workspaces; Supports Python, SQL, R, Scala; One users failure affects other users since there is no isolation
Custom - Legacy configuration

### Databricks Runtime - 
Databricks Runtime
Databricks Runtime ML
Photon Runtime
Databricks Runtime Lite

### Auto termination
Terminates cluster after specified inactivity

### Auto scaling
Specify min max worker nodes

### Cluster VM Type / Size
Memory Optimized
Compute Optimized
Storage Optimized
General Purpose
GPU accelerated

## Pricing
Price of databicks cluster depends on various factors
Workload - All purpose, job, sql, photon
Tier - Premium, standard
VM type - general purpose, gpu, optimized
Purchase Plan - Pay as you go, Pre Purchase
Set budget alerts in the subscription

## Cost control
ADLS - Negligible cost
ADF - Billed only for execution of pipelines
ADB job cluster - Automatically destroys once the job completes
ADB cluster pool - Delete the cluster pool at the end of the lesson
ADB all purpose cluster - Set auto termination to 20 min

## Cluster Pools

## Cluster Policy
Admins can Add restrictions

# Creating Databricks Compute
Go to compute
<img width="959" height="374" alt="image" src="https://github.com/user-attachments/assets/d461e0ca-f009-4a44-97ef-b6fac7444702" />

<img width="807" height="322" alt="image" src="https://github.com/user-attachments/assets/44a8c63c-bc9e-4c4a-b44d-9e1d1f204a1c" />

Simple form: OFF
Change cluster name
<img width="383" height="91" alt="image" src="https://github.com/user-attachments/assets/f6eae4d4-4ff3-4d17-b770-dc939929c1fb" />

Single node cluster
Access Mode - No isolation shared
Databricks runtime version - Standard > 16.4LTS (LTS - Long Term Support)
Turn off Photon Accelerator
Node Type - Standard_DS3_v2  14GB memory, 4 cores
Terminate after - 20 min

<img width="544" height="468" alt="image" src="https://github.com/user-attachments/assets/24960cb0-c47b-4645-95de-c13010c26021" />

Click on create compute

# Other cluster info
Configuraion, Notebooks, Libraries, Event Log, Spark UI, Driver Logs, Metrics (Ganglia UI)

# Cluster cost
Summary under the configuration shows the cluster cost
Ex: 0.75 DBU/hr

DBU cost = No of DBU x Price based on workload/tier
Driver node cost = 1 driver x Price of VM
Worker node cost = no of workers x price of VM
Total cost of cluster = DBU cost + Driver node cost + Worker node cost

Sample cluster cost calculation for 
0.75 DBU/hr
workload - all purpose compute
instance - Standard DS3 v2 pay as you go
single node cluster

## Azure pricing calculator 
Databricks pricing - https://azure.microsoft.com/en-gb/pricing/details/databricks/

<img width="1892" height="807" alt="image" src="https://github.com/user-attachments/assets/aac0dae6-a7af-439f-bf21-5979fbb73bf4" />

Linux VM pricing - https://azure.microsoft.com/en-gb/pricing/details/virtual-machines/linux/#pricing
<img width="1919" height="799" alt="image" src="https://github.com/user-attachments/assets/f7176732-3e33-44a6-aefa-cb4220f69938" />


# Stopping Databricks Compute
Go to compute tab and stop the cluster.











