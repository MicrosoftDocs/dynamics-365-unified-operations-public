---
# required metadata

title: Monitor replication
description: This article describes how to monitor replication in Microsoft Dynamics AX 2012.
author: ttreen 
ms.date: 04/26/2023
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: ttreen
ms.search.validFrom: 
ms.search.form: 2022-04-08

---

# Monitoring replication for the data migration toolkit for Dynamics 365 Finance

[!include[banner](../includes/banner.md)]

The Data migration toolkit for Dynamics 365 is used for self-service environments. This tool uses SQL replication to transfer the data from the customer's on-premises SQL Server to the Azure SQL database used for Dynamics 365.

This tool is used in both AX 2012 to Dynamics 365 upgrades, and also in Dynamics 365 on-premises to Dynamics 365 cloud migrations.

   See: 
   - [Upgrade from AX 2012 - Data upgrade in self-service environments](/data-upgrade-self-service)
   
   - [Move Lifecycle Services implementation projects from on-premises to the cloud](/lifecycle-services/move-on-prem-to-cloud)

The migration tool has a command called **RS** for monitoring the replication status, but the details in that are limited see: [Toolkit Reporting Section](/data-upgrade-self-service#reporting-section-of-the-application)

You may want to monitor the replication directly in SQL server management studio. The details in this document explains how to monitor and the specific steps of the replication.

## Replication overview
By default, when you run the toolkit, we create two publications for tables with primary keys. A single publication for other objects (fuctions) and a single publication for tables without primary keys. Optionally, a final publication for locked tables, or record count mismatches can be created if needed.

Each of these publications has two SQL agent jobs:
1. Snapshot agent
    - The snapshot agent is responsible to the initial snapshot of the tables (articles) in the publication. This will create files in the snapshot folder for each table, more details on these are later in this document. 
2. Log reader agent
    - The log reader agent is responsible for pushing the snapshot to the target database (subscriber) and any ongoing changes to the tables. 
 >[!Note]
 >The non-primary key publication only pushes up the snapshot.

## Replication monitor

To monitor the replication in SQL management studio, connect to the source on-premise database server, expand **Replication**. Select **Launch replication monitor**

![image](https://user-images.githubusercontent.com/28597769/231263006-30727da0-6bfb-4e14-8dee-53691db8a2ac.png)

The **Replication monitor** window will open:

![image](https://user-images.githubusercontent.com/28597769/231263308-9b209005-0a28-4c8f-b9fe-6658d9e41f57.png)

> [!Note] 
> You can see above, there is a single primary key table publication whereas the default is normally two. 

### Snapshot generation

There are a few ways to get to the snapshot agent details. 
To view the snapshot agent details: 
1. Select the publication on the left. 
2. Select the **Agents** tab, right-click **Snapshot Agent** and select **View Details**.

![image](https://user-images.githubusercontent.com/28597769/231263409-a781f6e0-8815-40d5-8866-1235df6e3186.png)

The **Snapshot agent details** window will display:

![image](https://user-images.githubusercontent.com/28597769/231263511-1d686253-f229-44e9-8e8d-f48df5a4cdb8.png)

There are four steps when generating a snapshot:

1. Update statistics on indexes

   ![image](https://user-images.githubusercontent.com/28597769/231263573-b51e904d-0564-46d5-ab86-899023f588f0.png)
   
2. Create bulk copy files

   ![image](https://user-images.githubusercontent.com/28597769/231263631-df78e84d-84aa-4feb-8029-bac33cda68d4.png)

3. Customize object scripting 

   ![image](https://user-images.githubusercontent.com/28597769/231263676-366dfd24-66b1-49f9-b7c1-99ad88d1b650.png)

4. Generate scripts

   ![image](https://user-images.githubusercontent.com/28597769/231263741-a340001c-c2db-4c1e-b911-3acab9abd4bf.png)

The snapshot files are created in the folder that was specified during the toolkit setup.

Open **File explorer** to this folder, and drill down the folders to the publications you're reviewing.

![image](https://user-images.githubusercontent.com/28597769/231263949-183d6d28-8fc9-4c8d-a94e-766256989bba.png)

### Files type details

 - *.BCP – SQL Server replication snapshot bulk copy file 
    - Binary file containing the data in the table. There can be one or several for each table depending on the size of the table. 
 - *.DRI – SQL Server replication snapshot constraint script
    - SQL Script containing the constraints on the table.  
 - *.IDX – SQL Server replication snapshot index script
    - SQL Script containing the indexes on the table.
 - *.PRE – SQL Server replication snapshot script
    - SQL Script used to move existing objects in the target database.
 - *.SCH – SQL Server replication snapshot schema script
    - SQL Script for creating the table and stored procedures used to replicate the data to the subscriber database. This doesn't include constraints or indexes. 
 - *.XPP  – SQL Server replication snapshot extended properties script
    - SQL Script containing any extended properties that may be on the table. This tends to be empty for AX 2012 tables. 

Once the snapshot is completed, a message will display **"A snapshot of XXX article(s) was generated"**.

![image](https://user-images.githubusercontent.com/28597769/231263991-0c87781f-7135-423c-b33a-2c9734c28018.png)

At this stage, the snapshot is only in the file share, the next step is the distributor will move the snapshot to the target (subscriber) database. 

### Distributor to subscriber

The distributor to subscriber details can be used to monitor:
 - the push of the generated snapshot to the target (subscriber) database 
 - any ongoing transactions that were created during the snapshot generation 
 - ongoing transactions

To view the distributor to subscriber logs, click **All Subscriptions** tab and then click **View Details**.

![image](https://user-images.githubusercontent.com/28597769/231264136-a45f4875-3b7d-4185-a655-0aa1c1a438ef.png)

The first step in moving the snapshot is running the PRE files (these drop existing objects in the target):

![image](https://user-images.githubusercontent.com/28597769/231264664-9ba37966-9056-449e-83a1-5abb4ceb7c0d.png)

The SCH scripts are run and create the tables:

![image](https://user-images.githubusercontent.com/28597769/231264190-cd234f2a-3563-405a-afc2-76b1e6e628c5.png)

After the tables have been scripted in the subscriber (target) database, the bulk copy files are imported to the target:

![image](https://user-images.githubusercontent.com/28597769/231264214-e0c2ea68-53a7-4c30-bae3-b5e8c3acd636.png)

The BCP file import process can take several hours.
Once that is completed, the next step is to create the indexes:

![image](https://user-images.githubusercontent.com/28597769/231264251-7c6e07b3-8232-4c4f-a580-ceb8c144161b.png)

The final step is applying constraints and extended properties:

![image](https://user-images.githubusercontent.com/28597769/231264274-202bdc28-9894-4a0e-82c4-4eb0c07849e0.png)

You can check on the **Undistributed commands** to see how much is outsatnding:

![image](https://user-images.githubusercontent.com/28597769/231264818-180d12cd-d17d-4d7b-b18d-69fb645e7530.png)

Once the snapshot is delivered, the message "Delivered snapshot from the \\unc\server\folder...." will be displayed:

![image](https://user-images.githubusercontent.com/28597769/231265253-cbb0a0eb-dd8d-4057-96f8-cf29c95f6a4d.png)

If there are no further outstanding commands, the following will display in the **Undistributed commands**:

![image](https://user-images.githubusercontent.com/28597769/231265396-19a42a0c-770d-4734-80a6-e53bbc1363ac.png)

## Transaction replication

After the snapshot is delivered, any new transactions created on the database during or after the push of the snapshot are delivered to the subscriber (target).

![image](https://user-images.githubusercontent.com/28597769/231265531-4e294a10-466a-42ec-b18d-b45e2c2caebd.png)

After the database stabilizes, and there is nothing to replicate, the message **No replicated transactions are available** will be displayed.

![image](https://user-images.githubusercontent.com/28597769/231265637-bbc9dec8-5239-4c57-9667-cfd6ac59d31b.png)

### Network bandwidth

While the snapshot is being pushed, you can monitor the bandwidth from the distributor process to the target DB. This is useful for upload performance issues.
Open **Task manager**:

![image](https://user-images.githubusercontent.com/28597769/231265670-9b2ef74c-d78f-4bed-8726-e481104db554.png)

Click **Open resource monitor**

In **Resource monitor**, click **Network**, filter on **DISTRIB.exe**. This will display the send bandwidth speed.

![image](https://user-images.githubusercontent.com/28597769/231265704-30e3aca2-bff1-4581-85e9-b59ec5867314.png)
