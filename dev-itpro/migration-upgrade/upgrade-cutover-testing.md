---
# required metadata

title: Upgrade cutover testing
description: Describes how to test the tasks that happen between turning off Dynamics AX 2012 and turning on Dynamics 365 for Finance and Operations, Enterprise edition. 
author: tariqbell
manager: AnnBe
ms.date: 05/29/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer;IT Pro
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: Operations Platform
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: tabell
ms.search.validFrom: 2017-06-16
ms.dyn365.ops.version: Platform update 8
---

# Upgrade cutover testing

[!include[banner](../includes/banner.md)]

Cutover is the term we use for the final process in getting a new system live – the tasks that happen between turning off Dynamics AX 2012 and turning on Dynamics 365 for Finance and Operations, Enterprise edition. The work here is to practice the cutover process to ensure a smooth experience for all involved during the actual cutover to go-live.

There are two main workstreams during a cutover:

1.	Technical work stream: this includes the data upgrade execution process. Your business will enforce a limit on the amount of downtime allowed, when neither AX 2012 nor Finance and Operations are available. This workstream may need to tune the data upgrade procedure to meet the businesses downtime limit. 
2.	Functional work stream: this includes the configuration tasks performed after the data upgrade is complete. These tasks must all be documented, quantified and have a resource assigned – because both the functional and technical workstreams must fit within the businesses downtime limit. 

The diagram below shows the overall process for cutover to go-live as it will happen in the production environment:

To compare this cutover process to a basic data upgrade in a sandbox environment:
1.	The AX 2012 database isn’t copied – it is only backed up, and then the original is modified. This is faster, and the backup provides rollback if needed.
2.	The tasks performed on the sandbox AOS previously, including downloading the bacpac file, importing the bacpac and executing the MajorversionDataUpgrade.zip package are now performed by the Microsoft DSE team, because the production environment for Dynamics 365 for Finance and Operations has restricted access.
3.	We added the following tasks:
	-	Perform a smoke test
	-	Complete application setup tasks. This can be a large task, depending on the functionality in use. In this step, the functional team configures new application functionality so that it is ready to begin using in the upgraded system.
	-	Allow users back in. Notify your user base that the upgrade is complete and that they can use the system again.

## Technical work stream

The technical workstream will involve various technical team members – the database administrator (DBA), the AX 2012 system administrator, server administrators and developers who are familiar with AX 2012 and Dynamics 365 for Finance and Operations. This document will explain which tasks involve which roles.

The focus of the technical team during cutover testing is performance and reliability testing of the data upgrade process to ensure it meets the downtime goal. There are many elements of hardware and software, both on-premise and in the Microsoft cloud, as well as custom application code and standard code involved in this process. The result of this testing should be confidence in the cutover process for your environment. 

### Turn off the AX 2012 AOS instances

This task will involve the AX system administrator and the server administrators. The areas to validate here are:
-	Batch jobs that may be running at the time of cutover. A long running batch job which has already started running will prevent the system from stopping. Plan ahead to be able to stop your AOS instances at the desired moment – this may mean scheduling batches to finish some time before turning off. 
-	Integrated systems. You may have other systems integrated with the AX 2012 environment. You will need to factor these systems into your plan to turn off AX 2012 – for example, you may need to turn off the integrated systems some time before you turn off AX 2012 itself to allow remaining in-flight transactions to complete. The requirements for integrated systems vary greatly from business to business so your team of experts will need to plan independently for this.

### Create a backup of the AX 2012 database 

This task will involve the DBA. The backup will be used in case a rollback is needed and as a reference point to be kept for a period of time to show the system state at the moment of cutover.

The areas to validate in this phase are:
-	To get concrete timings on how long the backup will take
-	To adjust the backup options used (for example compression vs non-compression) to ensure the fastest possible backup.

### Export the database to bacpac

This task will involve the DBA. The output of this task is the export file which will be uploaded to Azure for the new system.

The areas to validate in this phase are:
-	To get concrete timings on how long the backup will take
-	To optimize the export process to get the fastest experience. This may mean:
	-	Measuring system resources during export, such as CPU, disk IO, and memory
	-	If resource bottlenecks are found, then creating a plan to mitigate those bottlenecks – most commonly by assigning more of the required resource.

### Upload the bacpac to Azure storage

This task will involve the DBA or the server administrator. This task moves the bacpac file into Azure.

The areas to validate in this phase are:
-	Select the machine to be used for upload and ensure that the Azure storage explorer tool is configured and ready to use
-	Get concrete timings for upload by measuring it several times. Upload times will vary based on your internet connection speed and the geographical location of the Azure datacenter in relation to your location.

### Download and import the bacpac to the Azure SQL Database

When this task happens at go-live it will be performed by the Microsoft DSE team, however during cutover testing this task will involve your DBA. The outcome of this task is the export file which will be uploaded to Azure for the new system.

The areas to validate in this phase are:
-	To get concrete timings on how long the import will take
-	To optimize the export process to get the fastest experience. This may require measuring system resources during export, for example: 
	-	on the AOS machine: CPU, disk IO, memory
	-	On the Azure SQL Database instance: SQL database throughput (DTU). It is possible to monitor Azure SQL DTU from SQL Management Studio on the AOS machine by looking at the system view sys.dm_resource_stats.
	-	If resource bottlenecks are found, create a plan to mitigate those bottlenecks – most commonly by assigning more of the required resource. As this machine is Microsoft-hosted you will need to make a request to Microsoft to increase resources if you identify they are a bottleneck.

### Run the MajorVersiondataUpgrade.zip package

When this task happens at go-live it will be performed by the Microsoft DSE team, however during cutover testing this task will involve your developer. This task involves transforming the old database structure to the structure of the new system.

The database synchronization process runs as part of this task, and may take a significant amount of time is some situations, for example when a clustered index has changed on a table, because this is a costly operation in SQL. 

We strongly recommend performing your analysis and debugging process with first in a development environment. In a sandbox environment debugging and analysis options are more restricted. The goal is for there to be few or no issues to address by the time you are doing cutover testing.

The areas to validate in this phase are:
-	To get concrete timings on how long the import will take
-	To optimize the process to get the fastest experience:
	-	Monitor performance of individual upgrade scripts through the table ReleaseUpdateScriptsExecution 
	-	Adjust scripts to optimize performance – this may mean customising a script’s X++ code to optimise it for your particular dataset.
	-	Monitor Azure SQL DTU using Lifecycle Services (LCS) monitoring or from SQL Server Management Studio sys.dm_resources_stats. If resources are maxed out you may need to request a higher database level from the Microsoft DSE team. 


### Rollback to AX 2012

The goal of this phase is to restore the database using the backup taken when AX 2012 was turned off, and then turn back on AX 2012. The state of integrated systems may also need to be restored, as integrated systems vary from business to business you would need to plan for this independently for your specific circumstances. Although it is unlikely that you will need to roll back, it is very important that you have a tested process in case it is necessary.

## Functional workstream

After data upgrade there will be a number of configuration tasks required within the new environment. The goal of this workstream is to have all configuration tasks documented, quantified and have a resource assigned to ensure that the tasks can be done during the downtime window, along with the technical workstream.

Functional tasks will typically relate to changing the values of particular system parameters or other configuration data. These items are identified through the full functional test pass, which is a separate activity to the cutover testing activity. When such a task is identified it should be reviewed with the functional resource and your developer. 

Larger changes may require a new custom data upgrade script to be written to update the data during the data upgrade process, smaller changes can be executed manually by the functional resource through the new system post data upgrade. 

Larger changes with new data upgrade scripts will require one or more further iterations of running the MajorVersionDataUpgrade.zip package to test them. It's important to weigh the cost of running the package again against manual data entry.

For each manual change a task must be added to the cut over plan document showing:
-	What the task is, what needs to be done
-	Who needs to do it
-	How long it takes


