---
# required metadata

title: Advance holder reports
description: 
author: 
manager: AnnBe
ms.date: 09/07/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: 
ms.dyn365.ops.version: 8.1
ms.search.validFrom: 2018-10-31

---

# Advance holders reports

[!include [banner](../includes/banner.md)]

The following reports are available for advance holders in Russia in **Accounts payable** \> **Inquiries and reports** \> **Advance holders inquiries and reports**.

## Advance holder balance report 

The **Advance holder balance report** displays the balances of the amounts that are paid to or received from advance holders in an organization. Accountants generate this report periodically or daily to review and monitor the debts of an advance holder.

When you generate this report, the following parameters are displayed. You can use these parameters to filter the data that will be displayed on the report. 

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>FastTab\Field</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Parameters\To date</strong></p></td>
<td><p>Select the date on which to generate the advance holder amount balance report.</p></td>
</tr>
<tr class="even">
<td><p><strong>Parameters\Currency distribution</strong></p></td>
<td><p>Select this check box to display the advance holder amount balance grouped by currency code.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Records to incude\Worker ID</strong></p></td>
<td><p>The identification number of the employee for whom the advance holder amount balance is displayed. If no employee selected then the report will include all employees.</p></td>
</tr>
</tbody>
</table>

## Advance holder transactions report

The **Advance holder transactions report** displays the expense transactions of an employee and the amounts that are paid in advance to that employee. Accountants generate this report periodically or daily to review and monitor the advance transactions.

When you generate this report, the following parameters are displayed. You can use these parameters to filter the data that will be displayed on the report. 

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>FastTab\Field</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Parameters\Main accounts only</strong></p></td>
<td><p>Select this check box to display only main accounts in the report.</p></td>
</tr>
<tr class="even">
<td><p><strong>Records to include\Employee</strong></p></td>
<td><p>The identification number of the employee for whom the transaction report is generated.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Records to include\Advance holder</strong></p></td>
<td><p>The identification number of the advance holder for whom the transactions are posted.</p></td>
</tr>
</tbody>
</table>

## Transaction settlements report

The **Transaction settlements report** displays cash refunds and advance amounts that are paid to an employee by the legal entity. Accountants generate this report periodically or daily to analyze transactions that occur in multiple currencies between an employee and the legal entity to calculate the debt balance of the employee.

When you generate this report, the following parameters are displayed. You can use these parameters to filter the data that will be displayed on the report. 

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Field</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Worker ID</strong></p></td>
<td><p>Select the identification number of the employee for whom the transaction settlements report is generated.</p></td>
</tr>
<tr class="even">
<td><p><strong>To date</strong></p></td>
<td><p>Select a date up to which the transactions are included on the report.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Real-time settlement</strong></p></td>
<td><p>Select this check box to include real-time settlement transactions to the report.</p></td>
</tr>
</tbody>
</table>

## Advance report 

Use this procedure to print an advance report in a form that is legally required in Russia. You can print an advance report after an advance invoice that is issued to an advance holder is settled.
You need to select a particular advance report number to be included to the report.

> [!NOTE]
    > The amounts in the <STRONG>Advance report</STRONG> form are recalculated on the date when the payment journal for the advance holder is posted.
    
    
The **Advance report** will be printed in Microsoft Excel format.


## Turnover report 

Use this procedure to print an advance report in a form that is legally required in Russia. You can print an advance report after an advance invoice that is issued to an advance holder is settled.

1.  Click **Accounts payable** \> **Common** \> **Advance holders** \> **Advance reports**.

2.  Create and post an advance report.
    
    > [!NOTE]
    > The amounts in the <STRONG>Advance reports</STRONG> form are recalculated on the date when the payment journal for the advance holder is posted.

