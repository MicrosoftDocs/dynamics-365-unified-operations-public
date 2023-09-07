---

title: Business performance analytics self help
description: This article provides information about business performance analytics self help.
author: jinniew
ms.author: jiwo
ms.reviewer: twheeloc 
ms.date: 09/7/2023
ms.topic: welcome
ms.prod: 
ms.technology:
ms.custom:
ms.search.form: business-performance-analytics
audience: Application User
---

# Business performance analytics self help

> [!NOTE]
> The functionality that's described in this article is available as part of a preview release. The functionality and the content of this article are subject to change. For more information about how to participate 
in the public preview for business performance analytics, contact <bpaquestions@service.microsoft.com>.

## Overview  
To maintain report data accuracy, business performance analytics conducts specific quality assessments on source data. If these assessments do not meet defined rules, business performance analytics records 
information in the 'BPA_SelfHelp_Logs' table in Dataverse. Customers can refer to this table for insight into the issue and take appropriate steps.  

## How to access table BPA_SelfHelp_Logs 

Go to Maker portal (https://make.preview.powerapps.com/) **Tables > All**. Use the search box to search for the table **BPA_SelfHelp_Logs**. 

## Understanding BPA_SelfHelp_Logs  

|Sno |Column name|Description |
|1 |LogCode |This will be unique code for each error or warning. |
|2 |LogName |This will be description for each error or warning. |
|3| LogType |This field can have 2 values:<ul><li> **Error** means that you need to take action to fix issue this issue. 
</li><li>**Warning** means that it just a information for awareness and No action is needed.</li></ul> |
|4| LogDetails| This column captures details about records that have errors or warnings that can be used to take action accordingly. |
|5| Microsoftdocsurl |Use this url to navigate to public documentation on how to troubleshoot the issue. |
|6| Createddate |Date that the record got logged in this table. |

Identify the log code for each error or warning and use this document to identify what action you will need to take.  

> [!NOTE]
**Errors** - Errors affect report accuracy and require immediate attention. 
**Warnings** - Not critical but can impact report accuracy. If they align with a valid business context, consider adjusting reports for accurate data representation. 
