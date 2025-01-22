---
title: Custom reports migration
description: Learn how to import, export, and restore custom reports in Business performance analytics.
author: lizmota
ms.author: lizmota
ms.custom:
ms.topic: how-to
ms.reviewer: twheeloc 
audience: Application User
ms.date: 1/16/2025
---

# Custom reports migration

This article describes how to back up, export, and restore custom reports, ensuring that your organization's data remains consistent and up-to-date. 
The process involves two main stages: 
 - exporting custom reports from the source organization
 - importing them into the target organization

## Terminology
- Source organization - the organization from which you're backing up and exporting from.
- Target organization - the organization that you import the solution and reports to.
  
## Prerequisites
Before you import or export reports, the following prerequisites must be in place:
- Have a system administrator role
-	Business performance analytics version 2.0.29241185 or newer on both the target and source organizations
-	Update the connection of the **Business performance analytics backup custom reports** and **Business performance analytics restore custom reports** flows on the target and source organizations.
To update the connection, follow these steps:
    1.	Go to [Power Apps](https://make.powerapps.com).
    2.	Select the organization.
    3.	Go to **Flows**, select the flow in the list.
    4.	Click **Edit**.
    5.	Either select a connection or create a new connection.
    6.	On the **Edit** screen, click **Save**.
    7.	Repeat for the other flow.

### Export
To export custom reports from your source organization, follow these steps:
1.	Go to [Power Apps](https://make.powerapps.com) Confirm you're in the source organization.
2.	Create a new solution in the organization. Learn more in [Create solution guide](/power-apps/maker/data-platform/create-solution). 
    - Remember the **Name** field value.
    - Follow the first part of the guide where you create the solution.
3.	Go to **Flows**.
4.	Find the **Business performance analytics backup custom reports** flow, click **Run**.
    - In the **Solution unique name**, enter the name from step 1.
    - Click **Run flow**.
5.	The execution time depends on the number of existing reports. The progress can be monitored in the **Business performance analytics move custom reports to solution** flow.
6.	After it's complete, go to the **Solutions** page.
7.	Export the solution from step 1. Learn more in [Export Solutions guide](/power-apps/maker/data-platform/export-solutions#export-from-power-apps).
8.	Select **Managed** or **Unmanaged** when exporting.

## Import
To import custom reports to your target organization, follow these steps:
1.	Go to [Power Apps](https://make.powerapps.com). Confirm you're in the target organization.
2.	Import the solution that was exported from the source organization. Learn more in [Import Solution guide](/power-apps/maker/data-platform/import-update-export-solutions).
3.	After the import is finished, go to **Flows**.
4.	Find the **Business performance analytics restore custom reports** flow, click **Run**.
5.	The run time depends on the number of reports in the system. Progress can be monitored in the **Business performance analytics custom report restore flow** flow.
6.	After the flow has finished, the reports are ready to use.
   
## Notes and limitations
-	If a report with the same name already exists in the target organization, the solutions unique name is appended to the report’s name.
    - The report name has a 100 character limit. 
    - If the name remains unchanged after truncation, the report isn't imported.
-	If you have backed up or imported reports with this feature, the following occurs when the **Business performance analytics restore custom reports** flow is run:
    - The content of the reports is overwritten with the report that was backed up or imported last. 
    - The name of the report isn't updated.
-	If you import from the same source organization again, any backups taken of those reports in target organizations are overwritten by the values in the imported solution.
-	Managed solutions (not recommended): If you choose to export and then import your backup solution as a managed solution the following applies: 
    - Any backups in the target organization layer their changes on top of the imported backup solution. 
    - To move your reports from the target organization to any other organization, import the managed backup solution first.
    - If you imported the managed solution, deleted it and then backed up the target organization, you won't be able to import from the same source organization again as it creates conflicts.
    - The backed-up version in the unmanaged solution overwrites what the managed solution contains.
    - We only recommend this if you don’t plan on backing up the target organization.
-	Unmanaged solutions (recommended): If you choose to export and then import your backup solution as an unmanaged solution the following applies:
    - You won't be able to import custom reports from the same source organization using a managed solution.
    - You are able to use the same solution to back up the imported reports.
    - You can back up new reports to the imported solution.
        - This is only recommended if you keep everything as a bundle.
    - You can export the backup solution again.
    - If you create a second backup solution, only reports that haven’t been backed up are added to the second backup solution. Any reports in the first backup solution remain in that solution.
