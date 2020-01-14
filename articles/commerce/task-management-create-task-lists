---
# required metadata
title: [Create Task lists and tasks ]
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

HQ persona or Store Manager can creates task lists e.g. Holiday season preparation, Thursday night closing checklist etc. in Dynamics 365 Commerce's Backoffice and assign them to the set of stores. 

## Creating a task list

	1. Go to **Retail and Commerce > Task management > Task management administration**  
	2. Click on **+ New** and provide **Name, Description**, and select an **Owner** for the task list.
	3. Click on **Save**.

## Adding tasks to a task list
 
	1. After saving task list, under **Tasks** fast tab, click on **+ New** to add a task.
	2. On the **Create a new task** flyout, fill in task details.
	3. **Name** of the task as a title for task owner. 
	4. Give a +/- integer value for **Due data offset from target date**, e.g. give **-2** if you want the task to be completed two days before the tasks list due date.    
	5. Provide detailed instructions under **Notes** field. 
	6. Provide **Contact person** if the task needs subject matter help.
	7. Provide a **Task link** based on the nature of the task. Read below for more information on Task link feature. 
   
!Tip:  Though it's technically feasible to assign a task to someone while creating the task, try to avoid assigning task while creating task list.  You can assign the tasks once the list is instantiated for individual stores. 


Using Task link to improve workers productivity
 
Dynamics 365 Commerce offers a way to link a task to a specific POS operation e.g. Run sales report, or online training video for new employee orientation task, or Backoffice operation e.g. product kits. This feature helps task owners to jump start with the task as clicking on task link navigate them to appropriate operation.

Linking tasks while creating a task

	1. Click on **Task link** dropdown
	2. Choose  **Menu item** for configuring a Backoffice operation, e.g. Product kits
	3. Choose **POS operation** for configuring a POS operation, e.g. Sales reports.
	4. Choose **URL** for configuring absolute URL. e.g. [http://mydomain.com/training/orientation](http://mydomain.com/training/orientation)  

![Dynamics 365 Commerce - Task management](media/HQ-POS-Tasks-Linking.png)


**Enabling a POS operation to be linkable to a task**

To enable a POS operation to be linked with a task, follow below steps:

	1. Go to **Retail and Commerce > Channel setup > POS setup > POS > Operations**.
	2. Click **Edit**,  and identify the preferred POS operation, and then select **Enable Task Management** check box. 
![Dynamics 365 Commerce - Task management](media/HQ-POS-Operations-Allow-Task-Linking.png)

