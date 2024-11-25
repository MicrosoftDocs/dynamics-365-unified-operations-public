---
title: Advance holders reports
description: Learn about the Advance holder reports that are available for Russia, including an outline on Advance holder blaance reports and a table that defines fields.
author: evgenypopov
ms.author: evgenypopov
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 06/21/2024
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2018-10-31
ms.dyn365.ops.version: 8.1
---

# Advance holders reports

[!include [banner](../../includes/banner.md)]

The following reports are available for advance holders in Russia.

- Advance holder balance report 
- Advance holder transactions report
- Transaction settlements report
- Advance report 
- Advance holder turnover register

These reports can be accessed by going to **Accounts payable** \> **Inquiries and reports** \> **Advance holders inquiries and reports**.

## Advance holder balance report 

The **Advance holder balance report** displays the balances of the amounts that are paid to or received from advance holders in an organization. Accountants generate this report periodically or daily to review and monitor the debts of an advance holder.

When you generate this report, the following parameters are displayed. You can use these parameters to filter the data that will be displayed on the report. 

<table>
<colgroup>
<col>
<col>
</colgroup>
<thead>
<tr class="header">
<th><p>FastTab | Field</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Parameters | To date</strong></p></td>
<td><p>Select the date on which to generate the advance holder amount balance report.</p></td>
</tr>
<tr class="even">
<td><p><strong>Parameters | Currency distribution</strong></p></td>
<td><p>Select this check box to display the advance holder amount balance grouped by currency code.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Records to include | Worker ID</strong></p></td>
<td><p>The identification number of the employee for whom the advance holder amount balance is displayed. If no employee is selected, then the report will include all employees.</p></td>
</tr>
</tbody>
</table>

## Advance holder transactions report

The **Advance holder transactions report** displays the expense transactions of an employee and the amounts that are paid in advance to that employee. Accountants generate this report periodically or daily to review and monitor the advance transactions.

When you generate this report, the following parameters are displayed. You can use these parameters to filter the data that will be displayed on the report. 

<table>
<colgroup>
<col>
<col>
</colgroup>
<thead>
<tr class="header">
<th><p>FastTab | Field</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Parameters | Main accounts only</strong></p></td>
<td><p>Select this check box to display only main accounts in the report.</p></td>
</tr>
<tr class="even">
<td><p><strong>Records to include | Employee</strong></p></td>
<td><p>The identification number of the employee for whom the transaction report is generated.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Records to include | Advance holder</strong></p></td>
<td><p>The identification number of the advance holder for whom the transactions are posted.</p></td>
</tr>
</tbody>
</table>

## Transaction settlements report

The **Transaction settlements report** displays cash refunds and advance amounts that are paid to an employee by the legal entity. Accountants generate this report periodically or daily to analyze transactions that occur in multiple currencies between an employee and the legal entity to calculate the debt balance of the employee.

When you generate this report, the following parameters are displayed. You can use these parameters to filter the data that will be displayed on the report. 

<table>
<colgroup>
<col>
<col>
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

To print an advance report in a form that is legally required in Russia, you need to print the report after an advance invoice that is issued to an advance holder is settled. You need to select a particular advance report number to be included in the report.

> [!NOTE]
> The amounts on the **Advance report** page are recalculated on the date when the payment journal for the advance holder is posted.
    
The **Advance report** will be print in Microsoft Excel format.

## Advance holder turnover register
 
An additional report, **Advance holder turnover register** is available in **General ledger** \> **Inquiries and reports** \> **Turnover balance statement**.

When you generate this report, the following parameters are displayed. You can use these parameters to filter the data that will be displayed on the report. 

<table>
<colgroup>
<col>
<col>
</colgroup>
<thead>
<tr class="header">
<th><p>Field</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Date interval code</strong></p></td>
<td><p>Select the value of the period from the table of date intervals.</p></td>
</tr>
<tr class="even">
<td><p><strong>From date</strong></p></td>
<td><p>Enter the start date of the period for generating the report. Manually select or insert from the selected code of interval dates.</p></td>
</tr>
<tr class="odd">
<td><p><strong>To date</strong></p></td>
<td><p>Enter the end date for the period for generating the report. Manually select or insert from the selected code of interval dates.</p></td>
</tr>
<tr class="even">
<td><p><strong>Currency type</strong></p></td>
<td><p>Select the transaction's currency type from the list. These values can be used: Standard currency, Secondary currency, and Stated currency.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Currency</strong></p></td>
<td><p>Enter the secondary currency of the transaction. This field is available if the currency type is Stated currency.</p></td>
</tr>
<tr class="even">
<td><p><strong>Main account</strong></p></td>
<td><p>Enter the accounting record of employee advances for which the report will be generated.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Financial dimensions</strong></p></td>
<td><p>Provide the dimensions codes if it is necessary to choose transactions with specific codes for the report. If the dimensions are not populated, the system will select transactions for the report having any dimension codes.</p></td>
</tr>
<tr class="even">
<td><p><strong>Print ranges</strong></p></td>
<td><p>Set the option to display request conditions when printing the report.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Delete zero line</strong></p></td>
<td><p>Set the option to not print zero lines or columns.</p></td>
</tr>
<tr class="even">
<td><p><strong>Total accounts</strong></p></td>
<td><p>Set the option to print total accounts.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Show transactions</strong></p></td>
<td><p>Set the option to display the transactions of advance holders.</p></td>
</tr>
</tbody>
</table>

In the **Details and sorting parameters** section, select the available fields to be included into the report. On the **Records to include** tab, define additional filtering conditions, if needed.

## Additional resources

[SQL Server Reporting Services Reports report](/dynamics/s-e/)



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
