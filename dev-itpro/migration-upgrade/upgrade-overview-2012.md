---
# required metadata

title: Upgrade Dynamics AX 2012 to Dynamics 365 for Finance and Operations, Enterprise edition 
description:  This topic describes the process that customers who currently run Microsoft Dynamics AX 2012 can use to move their data and code to Microsoft Dynamics 365 for Finance and Operations, Enterprise edition.
author: tariqbell
manager: AnnBe
ms.date: 06/16/2017
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

# Upgrade Microsoft Dynamics AX 2012 to Microsoft Dynamics 365 for Finance and Operations, Enterprise edition

[!include[banner](../includes/banner.md)]

In Platform update 8, Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, provides an upgrade path that customers who currently run Microsoft Dynamics AX 2012 can use to move their data and code to Finance and Operations. The upgrade process is built on the following elements:

- Tools to help you bring forward existing custom application code from AX 2012.
- A data upgrade process that you can use to bring your database forward. Therefore, you can upgrade your full transactional history.

## Overview

The overall upgrade process can be visualized as three overarching phases: Analyze, Execute, and Validate.

The following diagram shows the end-to-end upgrade process, and the activities that we consider part of each phase. 

![Upgrade process](./media/upgrade-process.png)

## Analyze

The activities in the Analyze phase help you estimate the effort that is required for the upgrade. They also help you prepare a project plan. These activities can be done before you buy Finance and Operations. They will help you make an informed purchase decision by providing a data point about the effort and resources that you will require.

### Sign up for a public preview in LCS

To perform Analyze activities before you purchase Finance and Operations, you can sign up for a public preview. The public preview lets you deploy your own Finance and Operations environments. It also gives you access to the tools in Microsoft Dynamics Lifecycle Services (LCS) that are used to evaluate your AX 2012 environment and your existing custom code.

If you have an existing LCS project for AX 2012, you must still sign up for an additional new project to evaluate Finance and Operations.

For information about how to get a public preview for customers, go to https://mbs.microsoft.com/customersource/global/AX/news-events/news/Microsoft_Dynamics_AX_Public_Preview.

For information about how to get a public preview for partners, go to https://mbs.microsoft.com/partnersource/global/news-events/news/Microsoft_Dynamics_AX_Public_Preview.

Be aware that this public preview differs from a [30-day trial](https://aka.ms/D365OperationTrials). Thirty-day trials provide a deployed instance of Finance and Operations that you can use to explore and evaluate the application. However, the Analyze activities require the full LCS experience and tools.

### Select the upgrade methodology
In your new LCS project, set the project methodology to **Upgrade AX 2012 to Dynamics 365 for Operations**. This methodology is made specially for AX 2012 customers who are upgrading. It describes the three phases in detail and provides links to all the supporting documentation about the process.

![Upgrade methodology(./media/methodology.png)
 
### Run the upgrade analyzer
The upgrade analyzer tool runs against your AX 2012 environment and identifies tasks that you should do to prepare the AX 2012 environment, to help make the upgrade experience smoother and less expensive:

- **Data cleanup** – This process helps you identify data that you can remove without causing loss of functionality. The tool identifies various types of data that you can reduce by running a cleanup process. For each type of data, an explanation is given about the impact of the cleanup. You then decide whether to run the cleanup process. Part of the cost of your Finance and Operations subscription is based on database size. Therefore, by reducing the size, you reduce that component of the subscription cost and also help reduce the time that is required for the upgrade go-live process. A smaller database helps guarantee a faster upgrade.
- **SQL configuration** – This process reviews the SQL configuration and recommends optimizations. By making sure that SQL performs optimally, this process helps reduce the time that is required for the upgrade go-live process.
- **Deprecated features** – This process identifies features that you're currently using, but that aren't available in Finance and Operations. Therefore, the process helps you discover gaps in functionality early. It also provides suggestions for alternatives.

Additionally, as part of this step, you must install KBXXXXXXX in the AX 2012 environment. This hotfix provides a pre-upgrade checklist. In the AX 2012 environment, you can use this checklist to enter data that will be required for the upgrade procedure. For example, in one pre-upgrade checklist task, you provide the Microsoft Azure Active Directory (Azure AD) sign-in information for each current AX 2012 user, so that each user will be able to sign in to Finance and Operations.

The output of this step becomes the workstream in the upgrade project plan for your AX 2012 system administrators.

### Run the Code upgrade estimation tools
This step takes your code from AX 2012, converts it to the new format, and provides feedback about conflicts that a developer must resolve later. This step forms the basis for the estimate of the cost of your code upgrade.

To complete this step, you must export your code from AX 2012 as a model store export and upload it to the LCS Code upgrade tool. The Code upgrade tool will produce an upgraded version of your code and a report about the remaining conflicts that must be resolved. Your developer can then review both the upgraded code and the report to determine the effort that will be required in order to upgrade your code base.

The output of this step represents the workstream in the upgrade project plan for your Microsoft Dynamics AX developers.

### Deploy a demo environment
Demo environments are default environments that contain demonstration data (not your own data) and standard code (no customizations). We recommend that you deploy a demo environment to evaluate new features, and to perform a basic fit gap analysis of standard processes that are used in AX 2012 but that might have changed in Finance and Operations. You can either deploy these demo environments in Azure or downloaded them as a virtual machine (VM) that you run on your own hardware. If you deploy them in Azure, you must provide your Azure subscription, because you’re still using a public preview project and haven't yet purchased a Finance and Operations subscription.

The output of this step represents the workstream in the upgrade project plan for your functional users or business users.

### Create a project plan
A template for a project plan is provided in the upgrade methodology. In this step, the output from the previous steps of the Analyze phase is used to fill the project plan for the upgrade project. The project plan will also contain all testing details: data upgrade testing, cutover testing, the functional test pass iterations, and details about the various resource assignments for those tasks.

At this stage, the project plan provides a data point that can help you understand the time and cost that an upgrade to Finance and Operations will involve.

## Execute
During the Execute phase, you work through the tasks that you planned during the Analyze phase. To move to the Execute phase, you must purchase Finance and Operations, and you must have available resources that can work on the upgrade.

### Switch to the LCS implementation project
The public preview project that you used for the Analyze phase has served its purpose. You can now discard it. For the remaining steps, you require only the project plan that you created in the final step of the Analyze phase.

When you purchase a Finance and Operations subscription, you will receive details about how to sign up for a new LCS project. This project is known as an implementation project and will be the new permanent LCS project for your subscription, for as long as you have that subscription. This project differs from the public preview project in that it's managed by Microsoft. Therefore, this project has these characteristics:

- All environments in the project are hosted in Azure.
- The Azure subscription that is associated with the project is managed by Microsoft. Therefore, there is no separate billing for Azure costs. The costs are covered by your Finance and Operations subscription.
- The production environment in the project is maintained by Microsoft. Therefore, code deployments, upgrades, and infrastructure maintenance are run directly by Microsoft, not by your staff. 

### Perform the AX 2012 preparation tasks
Complete the tasks that the upgrade analyzer tool discovered, and that are documented in your upgrade project plan. Your Microsoft Dynamics AX system administrator and database administrator (DBA) must complete these tasks.

### Perform code upgrade
Complete the tasks that were planned during the code upgrade estimation step of the Analyze phase. Your developers must run these tasks.

From this point onward, code changes in AX 2012 should be frozen. Only emergency code changes should be allowed in AX 2012. If a change is made, it must be ported manually to the new code base.

### Develop new code
Complete the tasks from the fit gap analysis that was performed during the “Deploy a demo environment” step of the Analyze phase. These tasks will probably be a mixture of functional tasks that define the configuration and development tasks for customizations that are related to new features that are being taken up.

### Data upgrade (development environment)
After your code upgrade tasks are completed, you can upgrade your AX 2012 database to Finance and Operations for the first time. This first upgrade occurs in a development environment, so that you can more easily remediate or debug any issues that are found at this stage. In a development environment, an issue can be debugged immediately, code can be adjusted, and the upgrade can be rerun within minutes. Larger sandbox environments don't offer this agility, and a minimum of several hours will be required in order to debug and remediate issues, update code, deploy the updated code, and rerun the upgrade.

The following illustration shows the process. Just back up the AX 2012 database, upload it to Azure, restore it to the Finance and Operations environment, and then run the data upgrade.

![Data upgrade in a development environment](./media/data-upgrade-dev.png)
 
Data upgrade is done through a special type of deployable package. The same mechanism is used to deploy new Finance and Operations code from one environment to another environment.

The underlying framework that is used to convert the data in the database during this process is largely the same as the upgrade framework in AX 2012 that is based on X++ batch jobs that run **ReleaseUpdatexxx** classes.

### Data upgrade (sandbox environments)
When data upgrade in a development environment is completed, the same process can be run in a sandbox environment. The sandbox environment is the environment where business users and functional team members can test business processes by using the upgraded AX 2012 data and code.

The following illustration shows the process for running data upgrade in a sandbox environment. The difference here is that the bacpac tool is used instead of a traditional SQL backup. This tool is required in order to convert between Microsoft SQL Server and Azure SQL Database. It's a standard SQL tool, and isn't specific to Finance and Operations.

![Data upgrade in a sandbox environment](./media/data-upgrade-sandbox.png)
 
## Validate
When you enter the Validate phase, you will have available environments that include your upgraded custom code and your upgraded data. This phase describes the process of validating and testing that the upgraded environment works as desired. It also describes the process of preparing for go-live.

### Perform cutover testing and create a cutover plan
The term _cutover_ is used here to describe the final process of putting the new system live. This process consists of the tasks that occur after AX 2012 is turned off and before Finance and Operations is turned on. 

The goal of the testing is to practice the cutover process. In this way, you can help guarantee that everyone who is involved in the actual cutover to go-live will have a smooth experience.

There are two main workstreams:

- **Technical workstream** – This workstream is the process of running the data upgrade. Your business will enforce a limit on the amount of downtime that is allowed. During this downtime, neither AX 2012 nor Finance and Operations will be available. The technical workstream might have to performance-tune its data upgrade procedure to meet the business's downtime limit. 
- **Functional workstream** – After data upgrade, several configuration tasks will be required in the Finance and Operations environment. All these tasks must be documented and quantified, and a resource must be assigned to them, because they must fit together with the technical tasks within the business's downtime limit.

### Functional test pass
Complete a full functional test pass of all business processes. This test pass will be an extensive retest of all business processes that involve Finance and Operations. These business processes include both old processes that were brought forward from AX 2012 and new processes that involve new features that were taken up for the first time in Finance and Operations. 

Depending on code quality, issue remediation and retesting might require several iterations of the functional test pass. When an issue is fixed, be sure to retest all processes that are involved, to help guarantee that the downstream or upstream process isn't affected by the change.

### Pre-go-live checklist
The pre-go-live checklist is a recommended procedure that can help reduce the chance of errors during the final cutover to go-live. One week before go-live is due, stop configuration changes in AX 2012 (that is, under \<module\>\Setup). This restriction on configuration changes is merely procedural. The Microsoft Dynamics AX system administrators just agree to put changes of this type on hold at this point.

Freeze code changes in the Finance and Operations code base. No further changes are allowed unless evaluated to block the go-live and acceptable risk.

After the configuration restriction and code freeze are in place, data upgrade should be run for the last time before cutover. In this way, you can make sure that everything still works as expected. 

### Supported upgrade paths
As of June 2017, upgrade to Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, version 0617 is supported from Microsoft Dynamics AX 2012 R3. All cumulative updates (CUs) of AX 2012 R3 are supported.

Microsoft Dynamics AX 2012 R2 and Microsoft Dynamics AX 2012 RTM aren't currently supported. Support will be added later in 2017.

Only upgrade to the cloud-deployed version of Finance and Operations is supported. Upgrade to the on-premises version isn't supported. Support for upgrade to the on-premises version will be added later in 2017.
