---
# required metadata

title: Assign task lists
description: This topic describes how to assign task lists in Dynamics 365 Commerce.
author: gvrmohanreddy
manager: annbe
ms.date: 02/10/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: 
ms.author: gmohanv
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Release 10.0.9
---

# Assign task lists

[!include [banner](includes/banner.md)]

This topic describes how to assign task lists in Dynamics 365 Commerce.

## Overview

Task management in Dynamics 365 Commerce enables you to assign a task list to multiple stores or employees or a combination of the two. For example, a regional manager for 20 stores may want to assign the **Holiday season preparation** task list to all 20 stores.

## Start the task list assignment process

To start the task list assignment process, follow these steps.

1. Go to **Retail and Commerce \> Task management \> Task management administration**.
1. Select a task list that you want to assign. 
1. Select **Start process**. 
1. Under the **General** tab on the **Start process** flyout menu, enter a **Process name** (for example, "East region stores") and then enter the **Target date**.
1. On the **Stores** tab, use the **Organization hierarchy** filter to find and add all the stores to which the task list needs to be assigned to. 
1. Select **OK** to start the process and assign the tasks lists to the selected stores or employees. 

The following image shows an example of how to find and select stores on the **Start process** flyout menu.

![Task management - How to find and select stores](media/HQ-Assign-Tasks-Lists.png)

## Assign task lists recurrently

Retailer may have recurrent tasks e.g. Thursday closure checklist or First day of the month checklist etc. and wants to assign the task list recurrently.  

1. Go to **Retail and Commerce > Task management > Task management administration**.  
1. Select a task list that you want to assign. 
1. Select **Start process**. 
1. Enter a value for **Recurrence target date offset in days**, for example 4 days so that the target date will be set as the recurrent date + 4 days.
1. On the **Running in the background** tab, select **Recurrence**.
1. On the **Define recurrence** flyout menu, enter the frequency criteria, and then select **OK**. 

The following image shows where to enter frequency criteria on the **Define recurrence** flyout menu.

![Task management - Where to enter frequency criteria](media/HQ-Assign-Tasks-Lists-Recurrently.png)

## Track task lists status

As a regional or store manager, you may want to check the status of task lists assigned to multiple stores or employees so that you can follow up with stores or workers who may not have completed tasks on time. Dynamics 365 Commerce back office allows you to view the status of tasks lists, reassign tasks, or change the status of a task. 

To track task list status for all tasks, follow these steps.

1. Go to **Retail and Commerce \> Task management \> Task management processes**
1. Select **All checklists** to view the status of all task lists assigned to various stores.  

To track task list status for all tasks assigned to you, follow these steps.

1. Go to **Retail and Commerce \> Task management \> Task management processes**
1. Select **My tasks or All tasks** to view or update the status of tasks assigned to you.  

## Additional resources
