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
> The functionality that's described in this article is available as part of a preview release. The functionality and the content of this article are subject to change. For more information about how to participate in the public preview for business performance analytics, contact <bpaquestions@service.microsoft.com>.

## Overview  
To maintain report data accuracy, business performance analytics assesses the quality of the source data. If these assessments don't meet defined rules, business performance analytics records information in the 'BPA_SelfHelp_Logs' table in Dataverse. This table provides insights into issues and take appropriate steps.  

### Access table BPA_SelfHelp_Logs 
To access the BPA_SelfHelp_Logs table: 
1. Go to the maker portal (https://make.preview.powerapps.com/).
2. Navigate to **Tables > All**.
3. Use search and search for **BPA_SelfHelp_Logs**. 

### Understanding BPA_SelfHelp_Logs  

|Sno |Column name|Description |
|-----|--------|--------|
|1 |LogCode |This will be unique code for each error or warning. |
|2 |LogName |This will be a description for each error or warning. |
|3| LogType |This field can have 2 values:<ul><li> **Error** - users need to take action to fix issue this issue. 
</li><li>**Warning** - Information for awareness and no action is needed.</li></ul> |
|4| LogDetails| This column displays details about records that have errors or warnings that can be used to take action accordingly. |
|5| Microsoftdocsurl |Use this url to navigate to public documentation to troubleshoot the issue. |
|6| Createddate |Date that the record got logged into this table. |

> [!NOTE]
**Errors** - Errors affect report accuracy and require immediate attention. 
**Warnings** - Not critical but can impact report accuracy. If they align with a valid business context, consider adjusting reports for accurate data representation. 

For more information about specific errors or warnings, see the following articles: 
[Missing fiscal calendar for general ledger: Error code: ERR00001 [Type:Error]](BPA-self-help-1.md) 
[Missing fiscal calendar for budget: Error code: ERR00002 [Type: Error]](BPA-self-help-2.md) 
[Missing main account in budget: Error code: ERR00003 [Type: Warning]](BPA-self-help-3.md) 
[Missing journal entries: Error code: ERR00004 – [Type:Warning]](BPA-self-help-4.md)
[Mismatch between debits and credits: Error code: ERR00005 [ Type: Warning]](BPA-self-help-5.md) 
[Missing budget data: Error code: ERR00006  [Type: Warning]](BPA-self-help-6.md) 
[Missing budget transaction header: Error code: ERR00007 [ Type: Warning]](BPA-self-help-7.md) 
