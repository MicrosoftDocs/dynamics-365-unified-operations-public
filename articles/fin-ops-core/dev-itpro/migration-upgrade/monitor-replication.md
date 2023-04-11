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

# Monitor replication in Dynamics AX 2012

[!include[banner](../includes/banner.md)]

# Background
The Data Migration Toolkit for Dynamics365 is used for Self-Service environments. This tool is based upon SQL replication to transfer the data from the customer's local on-premises SQL Server to the Azure SQL database used for D365.

This tool is used in both AX 2012 to D365 Upgrades, and also in the D365 On-Premises to D365 Cloud migrations.

   See: 
   - [Upgrade from AX 2012 - Data upgrade in self-service environments](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/migration-upgrade/data-upgrade-self-service)
   
   - [Move Lifecycle Services implementation projects from on-premises to the cloud](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/lifecycle-services/move-on-prem-to-cloud)

The migration tool has a command called **RS* for monitoring the upgrade status, but the details in that are limited.

Therefore, you may want to monitor the replication directly in SQL Server Management Studio. The steps in this document explain how to do that and the specific steps of the replication.

# Replication Overview
By default, when you run the toolkit, we create 2 publications for tables with primary keys
A single publication for tables without primary keys
And optionally a final publication for locked tables, or record count mismatches.

Each of these publications has 2 SQL Agent jobs associated with them:
1. Snapshot Agent
    - The Snapshot Agent is responsible to the initial snapshot of the tables (articles) in the publication. This will create files in the snapshot folder for each table, more details on these are later in this document. 
2. Log Reader Agent
    - The Log Reader Agent is responsible for pushing up the snapshot to the target database (subscriber) and then any ongoing changes to the tables. Note: The non-primary key publication only pushes up the snapshot.

# Replication Monitor

To monitor the replication in SQL Management Studio, connect to the AX 2012 database server, expand out **Replication**, and select **Launch Replication Monitor**

![image](https://user-images.githubusercontent.com/28597769/231263006-30727da0-6bfb-4e14-8dee-53691db8a2ac.png)

The **Replication Monitor** window will open:

![image](https://user-images.githubusercontent.com/28597769/231263308-9b209005-0a28-4c8f-b9fe-6658d9e41f57.png)

You can see above, for the example in this TSG, there is a single PK Table publication.

## Snapshot Generation

There are a few ways to get to the Snapshot Agent details, the following is one way.

Select on the publication on the left, with will then so 4 tabs on the right pane, select the **Agents** tab, the right-click on the **Snapshot Agent** and select **View Details**

![image](https://user-images.githubusercontent.com/28597769/231263409-a781f6e0-8815-40d5-8866-1235df6e3186.png)

The **Snapshot Agent Details** window will show

![image](https://user-images.githubusercontent.com/28597769/231263511-1d686253-f229-44e9-8e8d-f48df5a4cdb8.png)

There are 4 steps in the snapshot generation

1. Update Statistics on Indexes

   ![image](https://user-images.githubusercontent.com/28597769/231263573-b51e904d-0564-46d5-ab86-899023f588f0.png)
   
2. Creating the Bulk Copy Files

   ![image](https://user-images.githubusercontent.com/28597769/231263631-df78e84d-84aa-4feb-8029-bac33cda68d4.png)

3. Customizing Object Scripting 

   ![image](https://user-images.githubusercontent.com/28597769/231263676-366dfd24-66b1-49f9-b7c1-99ad88d1b650.png)

4. Generating the Scripts

   ![image](https://user-images.githubusercontent.com/28597769/231263741-a340001c-c2db-4c1e-b911-3acab9abd4bf.png)

The Snapshot files are created in the folder you specified during the toolkit setup Step 1

Open **File Explorer** to this folder, and drill down the folders to the publications you're reviewing, you see a lot of files.

![image.png](/.attachments/image-095317dc-62dd-43ae-af78-ae3434e7ed0a.png)

Files Type Details

 - *.BCP – SQL Server Replication Snapshot Bulk-copy File 
    - Binary file containing the data in the table. There can be one or several for each table depending on the size of the table. 
 - *.DRI – SQL Server Replication Snapshot Constraint Script
    - SQL Script containing the constraints on the table.  
 - *.IDX – SQL Server Replication Snapshot Index Script
    - SQL Script containing the indexes on the table
 - *.PRE – SQL Server Replication Snapshot Script
    - SQL Script used to drop existing objects in the target database
 - *.SCH – SQL Server Replication Snapshot Schema Script
    - SQL Script for creating the table and stored procedures used to replicate the data to the subscriber database. Does not include constraints or indexes. 
 - *.XPP  – SQL Server Replication Snapshot Extended Properties Script
    - SQL Script containing any extended properties that may be on the table. This tends to be empty for AX 2012 tables. 

Once the Snapshot is completed, you'll see the message like **"A snapshot of XXX article(s) was generated"**

![image.png](/.attachments/image-b145c8c8-6b18-415d-b10e-3b12c6ad8e2e.png)

At this stage, the snapshot is only in the file share, the next step is the distributor will push that to the target (subscriber) database. 

## Distributor to Subscriber

The Distributor to Subscriber details can be used to monitor the push of the generated snapshot to the target (subscriber) database, and any ongoing transactions that were created during the snapshot generation, and ongoing transactions.

To view the distributor to subscriber logs, click back on the **All Subscriptions** tab and then click on the record **View Details**

![image.png](/.attachments/image-78f340b1-2751-42df-89a6-5ba0baff2d49.png)

The first step in pushing the snapshot is running the PRE files (these drop existing objects in the target)

![image.png](/.attachments/image-b7536734-09de-47d8-adbe-f6b77fdd1668.png)

Then the SCH scripts are run, these create the tables...

![image.png](/.attachments/image-9362ecbc-2b48-4a3c-931f-89746a402cec.png)

Once the tables have been scripted in the subscriber (target) database, it'll import the bulk copy files to the target...

![image.png](/.attachments/image-af319788-561b-4f3e-95d2-5cd744400759.png)

The BCP file import process can take several hours!

Once that is completed, the next step is create the indexes...

![image.png](/.attachments/image-1e8f6f84-8b3c-4c23-a798-fd3929234c49.png)

The final step is applying constraints and extended properties...

![image.png](/.attachments/image-2333d31d-b5bf-4fd0-9e0d-f5da768cb486.png)

You can also check on the **Undistributed Commands** to see how much might be outsatnding

![image.png](/.attachments/image-3ac31f0f-abcd-4602-8481-0661230a9768.png)

Once the snapshot is delivered, you will see the message "Delivered snapshot from the \\unc\server\folder...." message...

![image.png](/.attachments/image-03bae20d-80cd-4ab8-96d4-d42f61ae517e.png)

If there are no further outstanding commands, then you will see the following in the **Undistributed Commands**

![image.png](/.attachments/image-b545360e-3f2f-4e4b-9c15-8363fb29b376.png)

## Transaction Replication

Once the snapshot is delivered, then any new transactions created on the database during the push of the snapshot or after it was pushed are delivered to the subscriber (target).

You'll see these as messages like **1 transaction(s) with XXX command(s) were delivered**...

![image.png](/.attachments/image-9b2b2f69-e212-4faf-8b5c-6808dbf85ea6.png)

Once the database stabilizes, and there is nothing to replicate, then you will see the message **No replicated transactions are available**

![image.png](/.attachments/image-7a14556d-d550-4b20-9ffb-00bccb378b8a.png)


## Network Bandwidth

Whilst the snapshot is being pushed you can monitor the bandwidth from the Distributor process to the target DB. This can be useful for upload performance issues.

Open **Task Manager**

![image.png](/.attachments/image-37005283-93b3-4542-9484-8308d0f4f408.png)

Click on **Open Resource Monitor**

In **Resource Monitor** click on the **Network** tab, filter on **DISTRIB.exe** and you can see the send bandwidth speed

![image.png](/.attachments/image-ceb8331f-88e0-4afa-9448-edd9b51371a7.png)
