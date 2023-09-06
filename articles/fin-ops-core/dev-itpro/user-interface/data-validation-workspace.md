---
title: Data validation checklist workspace
description: The Data validation checklist workspace lets you track data validation processes across companies, areas, and people.
author: bking
ms.date: 01/12/2018
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: bking
ms.assetid: 
ms.search.form: DataValidationWorkspace
---

# Data validation checklist workspace

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-3.md)]

This article provides an overview of the **Data validation checklist workspace** and the associated configuration.

The **Data validation checklist** workspace lets you track data validation processes across companies, areas, and people. The checklist can be used during a new implementation, after an upgrade, or after a migration. Depending on your view of the **Data validation checklist** workspace, you'll see either all tasks and statuses for a data validation project, or just the tasks that are assigned to you.

You must first select a data validation project at the top of the workspace. All data that is shown in the workspace is then filtered by the selected data validation project.

## Summary tiles

The **Summary** tiles provide an overview of the process, and indicators help you keep the data validation process on track. You can see all remaining tasks, completed tasks, in progress tasks, and not started tasks for the process. This information is for all companies that are included in the selected data validation project.

## Tasks and status section

In the **Tasks and status** section, the status of the overall data validation project is displayed in various ways: status by legal entity, by area, and by task list. You can select the filter to view the status for a specific company. Each status tab provides a breakdown by both the percentage that has been completed and the number of tasks that remain.

The last tab is for the detailed task list. This list shows the full task list. You can filter the task list in several ways. Click **Edit task** to change the status of a task or assign a task. Click **Attachments** to view attachments for a task.

The task name is a hyperlink to the page where the user must go to complete the work. You can set this hyperlink by using the **Menu item name** field when you edit or create a task from the **Configure data validation project** form.

You can attach files, notes, images, and URLs to a task by using the **Attachments** action. For example, you can attach a report file that was printed for a task. An icon appears in the **Attachment** column for the task if an attachment is present.

The **Completed by** option will be automatically filled after the task is completed with the name of the worker who completed the task. When a task is marked as completed, the **Completed date** field is automatically updated to the current date and time.

## Configure data validation project page

Before you can use the **Data validation checklist** workspace, you must configure the process by using the **Configure data validation project** page. (Click **Workspaces** \> **Data validation checklist** \> **Configure data validation project**.)

## Task areas

You use task areas to group data validation tasks into logical areas of ownership within your organization. For example, Accounts payable, Accounts receivable, or General ledger might be used as task areas.

The **Menu item name** is associated with the task work effort and can be used to go directly to the associated page from the task link in the workspace. For example, a data validation task to run the **Accounts payable aging** report for Accounts payable can be linked to the **Accounts payable aging report** page.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
