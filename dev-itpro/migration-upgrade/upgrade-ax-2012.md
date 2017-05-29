---
# required metadata

title: Upgrade Dynamics AX 2012 to Dynamics 365 for Finance and Operations, Enterprise edition 
description: Dynamics 365 for Finance and Operations, Enterprise edition provides an upgrade path for customers currently running Microsoft Dynamics AX 2012 to move their data and code to the new product.
author: tariqbell
manager: AnnBe
ms.date: 05/29/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Developer;IT Pro
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: Operations Platform
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: tabell
ms.search.validFrom: 2017-06-16
ms.dyn365.ops.version: Platform update 8
---

# Upgrade Microsoft Dynamics AX 2012 to Dynamics 365 for Finance and Operations, Enterprise edition

[!include[banner](../includes/banner.md)]

As of Platform update 8, Dynamics 365 for Finance and Operations, Enterprise edition provides an upgrade path for customers currently running Dynamics AX 2012 to move their data and code to the new product.The upgrade process is built on
-    Tooling to help you bring forward existing custom application code from AX 2012.
-    A data upgrade process to bring your database forward. This means that you can upgrade your full transactional history to Finance and Operations, Enterprise edition.

## Overview
The overall upgrade process can be visualized as three overarching phases: Analyze, Execute and Validate.

The following diagram describes the end-to-end upgrade process, and the activities we consider part of each phase. 




## Analyze
The activities within the Analyze phase help you  estimate the effort required for the upgrade and prepare a project plan. These activities can be performed before you buy Dynamics 365 for Finance Operations, Enterprise edition and will help you make an informed purchase decision by providing a data point on the effort and resources you'll need.

### Sign up for a public preview in Lifecycle Services (LCS)
To perform Analyze activities before purchasing Dynamics 365 for Operations you can sign up for a public preview. 
The public preview provides you with the ability to deploy your own Dynamics 365 for Operations environments and also access to the Lifecycle Services (LCS) tools used to evaluate your AX 2012 environment and your existing custom code.
If you have an existing LCS project for AX 2012 you will still need to sign up for an additional new project to evaluate Dynamics 365 for Operations.

Information about getting a public preview for customers: https://mbs.microsoft.com/customersource/global/AX/news-events/news/Microsoft_Dynamics_AX_Public_Preview 

Information about getting a public preview for partners: https://mbs.microsoft.com/partnersource/global/news-events/news/Microsoft_Dynamics_AX_Public_Preview 

Be aware that this is different from a 30 day trial (https://aka.ms/D365OperationTrials). 30 day trials provide a deployed instance of Dynamics 365 for Operations that you can use to explore and evaluate the application, but to perform upgrade Analyze the full LCS experience and tools are required.

### Select the Upgrade methodology
In your new LCS project, set the project methodology to **Upgrade AX 2012 to Dynamics 365 for Operations**. This methodology is especially made for AX 2012 customers upgrading, it describes the three phases in detail and provides links to all the supporting documentation about the process.
 
### Run the upgrade analyser
The upgrade analyser is a tool which runs against your AX 2012 environment and identifies tasks to prepare the 2012 environment to help drive a smoother and cheaper upgrade experience:
-	Data clean up. This process helps you identify data that can be removed without loss of functionality. The tool will identify different types of data that you could reduce by running a cleanup process. For each type of data an explanation is given about the impact of the cleanup. You then decide whether you wish to run the cleanup process or not. Part of your Dynamics 365 subscription cost is tied to database size, so reducing the size reduces that the component of the subscription cost and also helps reduce the time needed for the upgrade go-live process. A smaller database ensures a faster upgrade.
-	SQL configuration. Reviews SQL configuration and recommends optimizations. Helps reduce time needed for upgrade go-live process by ensuring SQL performs optimally.
-	Deprecated features. Identifies features that are in use but which are not available moving forward, helping you discover gaps in functionality early, and provides suggestions for alternatives.
Additionally as part of this process you must install KBXXXXXXX in the AX 2012 environment. This will provide a pre-upgrade-checklist, which allows you to provide data in the AX 2012 environment that will be required for the upgrade procedure. An example of a pre-upgrade checklist task is providing the Azure Active Directory login information for each current AX 2012 user, so that each user will be able to log into Dynamics 365 for Finance and Operations, Enterprise edition.

The output of this task becomes the workstream in the upgrade project plan for your AX 2012 system administrators.

### Run the Code upgrade estimation tools
This step takes your code from AX 2012, converts it to the Dynamics 365 for Operations format, and provides feedback on conflicts that need to be resolved later by a developer. This forms the basis for estimating your code upgrade cost.
To run this tool, you will need to export your code from AX 2012 (as a model store export) and upload it to the LCS Code Upgrade tile.
 
The Code Upgrade tile will produce an upgraded version of your code and a report with the remaining conflicts which need to be resolved. Your developer can then review both of these to determine the effort required to upgrade your codebase.

The output of this task represents the workstream in the upgrade project plan for your AX developers.

### Deploy a demo environment
Deploy Dynamics 365 for Operations demo environments. We recommend that you deploy demo environments (default environments with demonstration data (not your own data) and standard code (no customizations)) to evaluate new features and to perform a basic fit gap analysis of standard processes which are in use in AX 2012 but may have changed in the new version.
These demo environments can be deployed either in Azure or downloaded as a virtual machine to run on your own hardware. If deploying in Azure then you will need to provide your Azure subscription, as at this stage you’re running in a public preview project and have not yet purchased a Dynamics 365 subscription.

The output of this task represents the workstream in the upgrade project plan for your functional users or business users.

### Create a project plan
A template project plan is provided in the upgrade methodology. In this task, the output from the previous Analyze tasks is used to populate the project plan for the upgrade project. 
The project plan will also contain all testing details: data upgrade testing, cutover testing, the functional test pass iterations and details of the various resource assignments for those tasks.
At this stage the project plan provides a data point to help you understand the time and cost involved in upgrading to Dynamics 365 for Operations.

## Execute
During the Execute phase you work through the tasks you planned during the Analyze phase. To move to the Execute phase, you must have purchased Dynamics 365 for Finance and Operations, Enterprise edition, and have resources available to work on the upgrade.

### Switch to the LCS implementation project
The public preview project you used for the Analyze phase has served its purpose, and can be discarded. The project plan created in the final stage of Analyze is the single source of the truth for the remaining steps you must complete now.
Upon purchasing a Dynamics 365 for Operation subscription you will receive details to sign up for a new LCS project. This is known as an “implementation project” and will be the new permanent LCS project for your Dynamics 365 for Operation subscription for the life of that subscription. This project differs from the public preview project in that it is managed by Microsoft, meaning that:
-	Environments within this project are all hosted within Azure
-	The Azure subscription associated with the project is managed by Microsoft, so there is no separate billing for Azure costs – it’s covered by your Dynamics 365 subscription.
-	The production environment in this project is maintained by Microsoft. That means code deployments, upgrades, infrastructure maintenance are executed by Microsoft directly and not by your own staff. 

### Perform the AX 2012 preparation tasks
Complete the tasks discovered by the upgrade analyser as documented in your upgrade project plan. These tasks will be completed by your AX System Administrator and Database Administrator (DBA).

### Perform code upgrade
Complete the tasks planned during code upgrade estimation during the Analyze phase. These tasks will be executed by your Developers.
Code changes in the AX 2012 should be frozen from this point onwards. Only emergency code changes should be allowed in AX 2012, if such a change is made it will need to be ported manually to the new Operations code base.

### Develop new code
Complete the tasks which came from the fit gap performed in the “Deploy demo environment” task in the Analyze phase. These are likely to be a mixture of functional tasks to define the configuration and also Development tasks for customisations relating to new features being up taken.

### Data upgrade (Development environment)
Once your code upgrade tasks are complete you can upgrade your AX 2012 database to Operations for the first time. This happens for the first time in a Development environment, this is make it simpler to remediate/debug any bugs that are caught at this stage – in a development environment an issue can be immediately debugged, code adjusted, and re-ran within minutes, however in the larger Sandbox environments such agility is not possible, and would take a minimum of several hours to debug, remediate,update code, deploy updated code and re-execute the upgrade.
 
The diagram above illustrates the process. Simply back up the AX 2012 database, upload it to Azure and restore to the Dynamics 365 for Operations environment, and then execute the data upgrade.

Data upgrade is through a special type of deployable package – which is the same mechanism used for deploying new Dynamics 365 for Operations code from one environment to another.

The underlying framework used to convert the data in the database during this process is largely the same as the upgrade framework in AX 2012 based on X++ batch jobs running ReleaseUpdatexxx classes.

### Data upgrade (sandbox environments)
Upon successful completion of data upgrade in a development environment the same process can be executed in a sandbox environment. The sandbox environment will be where business users and functional team members can test business processes with the upgraded 2012 data and code.
 
The diagram above shows the process for executing data upgrade in a sandbox environment. The difference here is the use of “bacpac” instead of a traditional SQL backup, this is required to convert between SQL Server and Azure SQL Database, it is a standard SQL tool (not Dynamics 365 for Operations specific).

## Validate
When you enter the Validate phase, you will have environments available with your upgraded custom code and with your upgraded data. This phase describes the process of validating and testing that the upgraded environment functions as desired, and preparing for go-live.

### Cutover testing & create cutover plan
The term cutover is used here to mean the final process of putting the new system live – the tasks that will happen between turning off AX 2012 and turning on Dynamics 365 for Operations. 

The work here is to practice the cutover process here to ensure a smooth experience by all involved during the actual cutover to go-live.

There are two main streams to this work:
1.	Technical work stream – the data upgrade execution process. Your business will enforce a limit on the amount of down time allowed, when neither AX 2012 nor Operations are available. The technical workstream may need to performance tune their data upgrade procedure to meet the businesses down time limit. 
2.	Functional work stream – post-data upgrade there will be a number of configuration tasks required within the Operations environment. These must all be documented, quantified and have a resource assigned – as these must fit together with the technical tasks within the businesses down time limit.

### Functional test pass
Complete a full functional test pass of all business processes. This will be an extensive re-test of all business processes involving Operations including both old processes brought forward from AX 2012 and new processes involving new features up taken in Operations for the first time. 
Depending on code quality you may require several iterations of functional test pass to allow for bug remediation and re-testing. Take care to retest all involved processes when a bug is fixed to ensure the downstream/upstream process is not affected by the change.

### Pre-go-live checklist
This is a recommended procedure to reduce the chance of errors in the final cutover to go-live. One week before go-live is due stop configuration changes in AX 2012 (meaning under <module>\Setup) – this is simply procedural, that the AX System Administrators agree to hold these kind of changes at this point.
Freeze code changes in the Operations code base. No further changes allowed unless evaluated to block the go-live and acceptable risk.
Once the configuration restriction and code freeze is in place then the data upgrade should be executed for the last time before cut over to ensure it still functions as expected. 

### Supported upgrade paths
As of June 2017, upgrade to Dynamics 365 for Operations version 0617 is supported from AX 2012 R3. All cumulative updates (CU) of AX 2012 R3 are supported.

AX 2012 R2 and AX 2012 RTM are not currently supported, support will be added later in 2017.

Upgrade to Dynamics 365 for Operations is supported only to the cloud deployed version, not on-premise. Support for upgrade to the on-premise version will be added later in 2017.

## Current limitations
Virtual companies…
