
---
# required metadata
title: [Dynamics 365 Commerce and Microsoft Teams integration configuration ]
description: [In a better together strategy, Dynamics 365 Commerce is integrating with Microsoft Teams to help customers (C1) and their employees improving productivity.  This documentation covers the details of admin feature to synergize the task management between POS and Microsoft Teams.]
author: [gvrmohanreddy]
manager: jeffbl
ms.date: 01/15/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 
# optional metadata
# ms.search.form:  
#ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: gmohanv
ms.search.validFrom: 2021-01-15
ms.dyn365.ops.version: 10.0.18
---


#Synergize Task Management between Microsoft Teams POS

One of the key objectives of Microsoft Teams integration is synergizing task management between POS application and Microsoft Teams, so that store employee can use either of the applications to manage tasks irrespective of origin of the tasks, without needing to switch the applications. 

Since we use Planner as repository for Tasks, behind the scenes, there needs to be link between Microsoft Teams and D365 Commerce via a specific Plan ID for a given store team. Following are the steps to setup synergizing task management between the PSO and Teams applications.


##Publish a sample task-list in Teams

Assuming you store teams are using Microsoft Teams first time for task management and in integration with Dynamics 365 Commerce follow below steps:

	1. Login into Microsoft Teams application as a communication manager, typically an user with regional manager role in Dynamics 365 Commerce. 
	2. Create a new task list called "Test task list"
	3. Add one task with title "Testing Teams integration"
	4. Click publish and choose entire organization.

![Tip: Refer to [Publishing Tasks in Microsoft Teams](https://docs.microsoft.com/en-us/microsoftteams/manage-tasks-app) ]

Above steps will ensure that every team in your organization gets a Plan created in Microsoft Planner Repository for published tasks. 


##Link POS and Teams for Tasks Management

To link POS and Teams applications on tasks management, you need to link the plans created for published tasks to the stores in Dynamics 365 Commerce:

	1.  Go to Retail and Commerce > Task management > Tasks integration with Microsoft Teams, 
	2. Click *Edit* on the menu bar.
	3. Turn *Enable Task Management Integration* switch to *Yes*
	4. Click *Save* on the menu bar.
	5. Now click *Setup task management* button.
	6. You should see notification indicating a batch job called *Teams provision* being created. 
	7. Go to *System administration > Inquiries > Batch jobs*, find the last job which job description is Teams provision. Wait until when this job is ended.
	8. Run CDX job 1070 to publish the planID & store references to Retailer Server. 

![Dynamics 365 Commerce - Provisioning teams from Dynamics 365 Commerce](media/d365-commerce-teams-synchronizing-tasks.png)
	
	
	
#My organization has been already using Teams and tasks in teams 

Overview on how customers can still link existing teams and Dynamics Retails Stores in HQ. 

Refer to [Add a link here to How-to-do-docs]
