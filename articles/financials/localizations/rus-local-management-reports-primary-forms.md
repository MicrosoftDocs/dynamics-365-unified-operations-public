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


## Print an advance report 

Use this procedure to print an advance report. You can print an advance report after an advance invoice that is issued to an advance holder is settled.

1.  Click **Accounts payable** \> **Common** \> **Advance holders** \> **Advance reports**.

2.  Create and post an advance report.
    
    > [!NOTE]
    > The amounts in the <STRONG>Advance reports</STRONG> form are recalculated on the date when the payment journal for the advance holder is posted.

3.  Click **Print** to open the **Advance report** form.

4.  Click **OK** to print the advance report in Microsoft Excel format.

## Advance holder balance report (EmplBalance\_RU) 

The Advance holder balance report displays the balances of amounts that are paid to advance holders in an organization. Accountants generate this report periodically or daily to review and monitor the debts of an advance holder.

When you generate this report, the following default parameters are displayed. You can use these parameters to filter the data that will be displayed on the report. 

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
<td><p><strong>To date:</strong></p></td>
<td><p>Select the date on which to generate the advance holder amount balance report.</p></td>
</tr>
<tr class="even">
<td><p><strong>Currency distribution</strong></p></td>
<td><p>Select this check box to display the advance holder amount balance grouped by currency code.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Worker ID</strong></p></td>
<td><p>The identification number of the employee about whom the advance holder amount balance is displayed.</p></td>
</tr>
</tbody>
</table>

## Advance holder transactions report (EmplTransList\_RU) 

The Advance holder transactions report displays the expense transactions of an employee and the amounts that are paid in advance to that employee. Accountants generate this report periodically or daily to review and monitor the advance transactions between an employee and the legal entity.

When you generate this report, the following default parameters are displayed. You can use these parameters to filter the data that will be displayed on the report. 

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
<td><p><strong>Main accounts only</strong></p></td>
<td><p>Select this check box to display only main accounts on the report.</p></td>
</tr>
<tr class="even">
<td><p><strong>Employee</strong></p></td>
<td><p>The identification number of the employee about whom the transaction report is generated.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Advance holder</strong></p></td>
<td><p>The identification number of the advance holder for whom the transactions are posted.</p></td>
</tr>
</tbody>
</table>

## (RUS) Transaction settlements report (EmplSettlement\_RU) 

The Transaction settlements report displays cash refunds and advance amounts that are paid to an employee by the legal entity. Accountants generate this report periodically or daily to analyze transactions that occur in multiple currencies between an employee and the legal entity to calculate the debt balance of the employee.

When you generate this report, the following default parameters are displayed. You can use these parameters to filter the data that will be displayed on the report. 

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
<td><p>Select the identification number of the employee about whom the transaction settlements report is generated.</p></td>
</tr>
<tr class="even">
<td><p><strong>To date</strong></p></td>
<td><p>Select a date up to which the transactions are included on the report.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Real-time settlement</strong></p></td>
<td><p>Select this check box to include real-time settlement transactions on the report.</p></td>
</tr>
</tbody>
</table>

## Additional resources
The [SQL Server Reporting Services Reports report](https://mbs.microsoft.com/customersource/northamerica/AX/downloads/reports/axtechrefrep) lists each report that is available. The report indicates the data set used for each report, as well as the filters and fields available on each report.
