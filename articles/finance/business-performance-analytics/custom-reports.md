---
title: Custom reports migration
description: Learn how to import, export, and restore custom reports.
author: lizmota
ms.author: jiwo
ms.topic: faq
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.date: 1/16/2025
---

# Custom reports migration

This guide will help you to backup, export, and restore custom reports, ensuring that your organization's data remains consistent and up-to-date. By following the steps outlined, users can ensure seamless data transfer and maintain the integrity of their reports. We will also addresses potential challenges and provides recommendations on managing solutions to help you make informed decisions based on your organization's needs.

The process involves two main stages: exporting custom reports from the source organization and importing them into the target organization. Key terminologies such as **source organization** and **target organization** are defined to clarify the roles of each entity in this process. Additionally, prerequisites such as having the appropriate version of Business Performance Analytics and updating the connections of specific flows are highlighted to ensure a smooth transition.

## Terminology
- Source organization: The organization from which you are backing up and exporting from.
- Target organization: The organization which you will be importing the solution and reports to.
  
## Prerequisites
- Have a System administrator role
-	Have version of Business performance analytics <version here> or newer on both the target and source organizations
-	Update the connection of the flows “Business performance analytics backup custom reports” and “Business performance analytics restore custom reports” on the Target and Source organizations. This can be accomplished by doing the following:
    1.	Go to https://make.powerapps.com
    2.	Select the organization
    3.	Go to “Flows”
    4.	Find the flow in the list
    5.	Click edit
    6.	You will be prompted to either select a connection or create a connection
    7.	Once the edit screen is visible click “Save” in the upper right-hand corner
    8.	Once saved repeat for the other flow

## Export
To export custom reports from your source organization, perform the following steps:
1.	Go to https://make.powerapps.com
2.	Make sure you are in the source organization
3.	Create a new solution in the organization following the guide https://learn.microsoft.com/en-us/power-apps/maker/data-platform/create-solution 
a.	Remember what you put in for the “Name” field (this is the unique name of the solution)
b.	You only need to follow the first part of the guide where you create the solution
4.	Go to “Flows”
5.	Find flow “Business performance analytics backup custom reports” and click “Run” (“Play” icon)
a.	It will ask you for a parameter called “Solution unique name” place the value from step 1-a here
b.	Click “Run flow”
6.	The execution time will depend on the number of reports in the system, but the progress can be monitored in the flow “Business performance analytics move custom reports to solution”
7.	Once complete go to the “Solutions” page and export the solution from step 1 following the guide https://learn.microsoft.com/en-us/power-apps/maker/data-platform/export-solutions#export-from-power-apps 
a.	You can select “Managed” or “Unmanaged” when exporting (see notes and limitations section)

## Import
To import custom reports to your target organization, perform the following steps:
1.	Go to https://make.powerapps.com
2.	Make sure you are in the target organization
3.	Import the solution that you exported from the source organization by following the guide https://learn.microsoft.com/en-us/power-apps/maker/data-platform/import-update-export-solutions
a.	Wait for the import to finish before proceeding to the next step
4.	Go to “Flows”
5.	Find flow “Business performance analytics restore custom reports” and click “Run” (“Play” icon)
6.	The execution time will depend on the number of reports in the system, but the progress can be monitored in the flow “Business performance analytics custom report restore flow”
7.	Once the flow has finished the reports are ready to use
   
## Notes and limitations
-	If a report with the same name already exists in the target organization, then solutions unique name will be appended to the report’s name
    - This name has a 100 character limit and truncation can occur
    - If the name remains unchanged after truncation, then the report will not be imported
-	If you have backed up or imported reports with this feature the following will happen when the flow “Business performance analytics restore custom reports” is run:
    - The content of the reports will be overwritten with whatever was backed up or imported last 
    - The name of the report will not be updated
-	If you import from the same source organization again, then any backups taken of those reports in target organizations will be overwritten by the values in the imported solution
-	Managed solutions (not recommended): If you choose to export and then import your backup solution as a managed solution the following will apply
    - Any backups in the target organization will layer their changes on top of the backup solution you imported
    - If you wish to move your reports from the target organization to any other organization, you will first have to import the managed backup solution first
    - If you imported the managed solution, deleted it and then backed up the target organization you will not be able to import from the same source organization again as it will create conflicts
    - The backed up version in the unmanaged solution will overwrite what the managed solution contains (even if imported again)
    - We only recommend this if you don’t plan on backing up the target organization
-	Unmanaged solutions (recommended): If you choose to export and then import your backup solution as an unmanaged solution the following will apply
    - You will not be able to import custom reports from the same source organization using a managed solution
    - You will be able to use the same solution to backup the imported reports
    - You can back up new reports to the imported solution as well
        - Only recommended if you keep everything as a bundle
    - You can export the backup solution again
    - If you create a second backup solution only reports that haven’t been backed up will be added to the second backup solution.  Any reports in the first backup solution will remain in that solution
