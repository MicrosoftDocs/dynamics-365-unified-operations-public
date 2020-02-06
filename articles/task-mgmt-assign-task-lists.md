---
# required metadata
title: [Process to assign task lists ]
description: [Dynamics 365 Commerce's Task Management is a productivity feature, for Firstline manager (Regional/Store) and Firstline workers, that gives an ability to create tasks lists , manage assignment criteria, and track status, in an integrated way between Backoffice and POS applications.]
author: [gvrmohanreddy]
manager: jeffbl
ms.date: 12/23/2019
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
ms.search.validFrom: 2020-04-03
ms.dyn365.ops.version: 10.0.9
---

A task list can be assigned to multiple stores or employees based on requirements. For e.g. you are a regional manager for 20 stores, and want to assign **Holiday season preparation** task list to all of 20 stores you are managing.  Dynamics 365 Commerce's task management process allows you to assign a task list to multiple stores or employees or combination.

## Start assignment process

	1. Go to **Retail and Commerce > Task management > Task management administration**  
	2. Select a tasks list that you want to assign. 
	3. Click on **Start process**. 
	4. On **Start process** flyout under **General** tab, give a **Process name** (e.g. East region stores) and set **Target date**.
	5. Under **Stores** tab, use the **Organization hierarchy** filter and **add** all the stores to which the task list needs to be assigned to. 
	6. Click **Ok** to start the process and assign the tasks lists to the selected stores and/or employees. 
See below screenshot for more details:
![Dynamics 365 Commerce - Task management](media/HQ-Assign-Tasks-Lists.png)


## Assign a task lists recurrently
Retailer may have recurrent tasks e.g. Thursday closure checklist or First day of the month checklist etc. and wants to assign the task list recurrently.  

	1. Go to **Retail and Commerce > Task management > Task management administration**  
	2. Select a task list that you want to assign. 
	3. Click on **Start process**. 
	4. On **Start process** flyout under **General** tab, select **Recurrence** to **yes** and notice that **Running in the background** tab will be enabled.
	5. Give a value for **Recurrence target date offset in days**, e.g.  4 days so that target date will be set as recurrent date + 4 days.
	6. Under **Running in the background** tab, click on **Recurrence**.
	7. On **Define recurrence** flyout give the frequency criteria, e.g. every Thursday of the week forever. 
See below screenshot for more details:
![Dynamics 365 Commerce - Task management](media/HQ-Assign-Tasks-Lists-Recurrently.png)

 



## Track tasks lists status form Headquarters

As a Regional or Store manager you may want to check the status of tasks lists assigned to multiple stores and/or employees so that you can follow-up with stores or workers who has not completed the tasks on time. Dynamics 365 Commerce's Backoffice allows you to view the status of tasks lists, and even reassign a task or change status of a task. 


	1. Go to **Retail and Commerce > Task management > Task management processes**
	2. Click on **All checklists** to view the status of all tasks list assigned to various stores.  

As a Headquarters persona, you may have tasks assigned to you to perform within the Backoffice. Follow below steps to view your own tasks, or all tasks and update the status: 

	1. Go to **Retail and Commerce > Task management > Task management processes**
	2. Click on **My tasks or All tasks** to view tasks and update the status of tasks assigned to you.  
 

