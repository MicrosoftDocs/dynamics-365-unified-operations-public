---
title: Document Reporting Services
description: Learn about the reporting solution that simplifies service administration, increases developer productivity, and provides enhanced report viewing.
author: johnmichalak
ms.author: johnmichalak
ms.topic: article
ms.date: 06/20/2017
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 57aaba22-4068-4c3f-9428-7fcd99632295
ms.custom: sfi-image-nochange
---

# Document Reporting Services

[!include [banner](../includes/banner.md)]

This article describes the integrated reporting solutions that are available. This solution simplifies service administration, increases developer productivity, and provides an enhanced report viewing experience for users.

## Document Reporting Services

Document Reporting Services are based on Microsoft SQL Server Reporting Services (SSRS). In the current version of the application, these services are hosted in the Microsoft Azure Compute service. If you're developing in a one-box environment, the services also run locally in the Azure Compute Emulator.

### Service deployment – Local vs. cloud

In a one-box environment, developers can create, modify, and preview reports, from end to end, by using Microsoft Visual Studio. A separate process isn't required in order to add reports to the application's metadata store. Changes to reports are packaged together with other solution updates and then deployed to the cloud after development is completed in the local environment.

### Viewing reports 

The enhanced report viewing experience that provides for end users is the same as the report preview experience in Microsoft Visual Studio. You no longer use a separate design preview in Visual Studio. Instead, just press Ctrl+F5 to build and preview the report in a Microsoft Edge window. The report appears exactly as it would appear in the client. Even the user's parameter experience is the same. The following image shows an example of a report preview that is opened from Visual Studio.

:::image type="content" source="./media/2_report.png" alt-text="Screenshot of example report preview opened from Visual Studio." lightbox="./media/2_report.png":::

## Service administration prerequisites
The following table compares the service administration prerequisites for Microsoft Dynamics AX 2012 and the current version of the application.

| AX 2012 | The current version of the application |
|---------|----------------------------------------|
| A report development environment has the following prerequisites:<br>• SSRS must be installed.<br>• SSRS must be configured by using Reporting Services Configuration Manager.<br>• SSRS extensions for the application must be installed. | Reporting services run in the Azure compute emulator, together with the application server. Therefore, there are no SSRS service administration prerequisites. After reports are deployed to the local reporting services, they can be accessed from the client. |

## Developing application reports
The process for developing a report in the current version is easier than it is in AX 2012, because you can create and validate a reporting solution entirely in Visual Studio. The following table describes how the application simplifies the basic procedure for adding an automatic design report that is based on a query.

| AX 2012 | The current version of the application |
|---------|----------------------------------------|
| 1. In the application, create a query in the Application Object Tree (AOT).<br>1. In Visual Studio, create a reporting project, and add the query to it.<br>1. Edit the report in the Visual Studio model editor.<br>1. Preview the report design in Visual Studio by using the model editor toolbar.<br>1. Use Visual Studio to add the report to the AOT.<br>1. Use the AOT in the client to create a menu item for the report, and add the menu item to a menu.<br>1. Use the AOT to deploy the report to the report server.<br>1. Verify the report in the client. | 1. In Visual Studio, create a reporting project and the query.<br>1. Edit the report in Visual Studio.<br>1. In Visual Studio, add the report to a menu item, and set the menu item as a startup object.<br>1. Use the AOT to deploy the report to the report server.<br>1. Press Ctrl+F5 to verify the report in the application.<br>**NOTE:** There's no longer a separate preview of the report design from the model editor.<br>1. When the whole solution is completed, deploy it to the cloud in one package. |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
