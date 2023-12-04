---

title: Business performance analytics self-help
description: This article provides information about business performance analytics self-help.
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

# Business performance analytics self-help

> [!NOTE]
> The functionality that's described in this article is available as part of a preview release. The functionality and the content of this article are subject to change. For more information about how to participate in the public preview for business performance analytics, contact <bpaquestions@service.microsoft.com>.

To maintain the accuracy of report data, business performance analytics assesses the quality of the source data. If the assessments don't meet defined rules, business performance analytics logs information in the `Bpa Self Help Logs` table in Microsoft Dataverse. This table provides insights into issues and helps you take appropriate action.

### Access the Bpa Self Help Logs table

To access the `Bpa Self Help Logs` table, follow these steps.

1. Open the [Power Apps maker portal](https://make.preview.powerapps.com/).
2. Go to **Tables** \> **All**.
3. Search for **Bpa\ Self\ Help\ Logs**.

### Understanding the Bpa Self Help Logs table

| Sno | Column name | Description |
|---|---|---|
| 1 | LogCode | The unique code of each error or warning. |
| 2 | LogName | The description of each error or warning. |
| 3 | LogType | <p>This field can have two values:</p><ul><li>**Error** – Users must take action to fix issue the issue.</li><li>**Warning** – The information is for awareness only. No action is required.</li></ul> |
| 4 | LogDetails | Details about records that have errors or warnings. You can use this information to take appropriate action. |
| 5 | Microsoftdocsurl | Use this URL to go to public documentation that can help you troubleshoot the issue. |
| 6 | Createddate | The date when the record was logged in the table. |

> [!NOTE]
> - *Errors* affect report accuracy and require immediate attention.
> - *Warnings* aren't critical but can affect report accuracy. If they're aligned with a valid business context, consider adjusting reports for accurate data representation.

For information about specific errors or warnings, see the following articles:

- [Missing fiscal calendar for general ledger: Error code: ERR00001 [Type: Error]](BPA-self-help-1.md)
- [Missing fiscal calendar for budget: Error code: ERR00002 [Type: Error]](BPA-self-help-2.md)
- [Missing main account in budget: Error code: ERR00003 [Type: Warning]](BPA-self-help-3.md)
- [Missing journal entries: Error code: ERR00004 - [Type: Warning]](BPA-self-help-4.md)
- [Mismatch between debits and credits: Error code: ERR00005 [Type: Warning]](BPA-self-help-5.md)
- [Missing budget data: Error code: ERR00006 [Type: Warning]](BPA-self-help-6.md)
- [Missing budget transaction header: Error code: ERR00007 [Type: Warning]](BPA-self-help-7.md)
