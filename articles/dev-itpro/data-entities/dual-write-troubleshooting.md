---
# required metadata

title: Troubleshooting guide for data integration
description: This topic provides troubleshooting information about data integration between Microsoft Dynamics 365 for Finance and Operations and Common Data Service.
author: RamaKrishnamoorthy 
manager: AnnBe
ms.date: 07/25/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: ramasri
ms.dyn365.ops.version: 
ms.search.validFrom: 2019-07-15

---

# Troubleshooting guide for data integration

## Enable Plugin Trace in Common Data Service and check the dual-write Plugin error details

If you are facing an issue or error with dual-write synchronization, you can inspect the errors in the trace log:

+ Follow the [instructions](https://docs.microsoft.com/en-us/powerapps/developer/common-data-service/tutorial-write-plug-in#view-trace-logs) to enable Plugin trace. 
+ Navigate to the Plug-in Trace log section.
+ Click the type name **Microsoft.Dynamics.Integrator.CrmPlugins.Plugin** to display the error details.

## Check dual-write synchronization errors in Finance and Operations

You can check the errors during testing by following these steps:

+ Login to LifeCycle Services (LCS).
+ Open the LCS project that you chose to perform dual-write testing.
+ Go to Cloud Hosted Environments.
+ Remote desktop to Finance and Operations VM using local account that is displayed in LCS.
+ Open the event viewer. 
+ Navigate to **Applications and Services logs > Microsoft > Dynamics > AX-DualWriteSync > Operational**. The errors and details are displayed.

## How to unlink and link another Common Data Service environment from Finance and Operations

You can update links by following these steps:

+ Navigate to the Finance and Operations environment.
+ Open Data Management.
+ Click on **Link to CDS for apps**.
+ Select **all running mapping** and click **Stop**. 
+ Select all mapping and click delete

Note: Delete option will not appear if CustomerV3- Account template is selected (it’s older provisioned template and works with P2C solution, but since its globally released, it’s will be showing up under all templates) unselect it
•	Now click Unlink environment
•	Click Yes for confirmation
•	To link new environment please follow steps from  step-by-step documentation here.

Related Topics
•	Company concept in Common Data Service
•	Organization hierarchy on Common Data Service
•	Integrated customer master
•	Unified product master
Feedback
 
