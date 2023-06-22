---
# required metadata

title: Customer aging report
description: The Customer aging report displays the balances that are due from customers, sorted by date interval, or aging period.
author: JodiChristiansen
ms.date: 10/06/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Customer aging report 

The **Customer aging** report displays the balances that are due from customers, sorted by date interval, or aging period.

When you generate this report, the following default parameters are displayed. You can use these parameters to filter the data that will be displayed on the report. For more information, see [Set up collections](set-up-collections.md).

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
<td><p><strong>Billing classification</strong></p></td>
<td><p>Select one or more billing classifications to include on the report.</p>
<div class="alert">

**Note:** This control is available only if the <STRONG>Public Sector</STRONG> configuration key is selected.</P>


</div></td>
</tr>
<tr class="even">
<td><p><strong>Include transactions without a billing classification</strong></p></td>
<td><p>If this check box is selected, all transactions that do not have a billing classification assigned to them will be displayed on the report.</p>
<div class="alert">

**Note:** This control is available only if the <STRONG>Public sector</STRONG> configuration key is selected.</P>

</div></td>
</tr>
<tr class="odd">
<td><p><strong>Aging as of</strong></p></td>
<td><p>Enter the date used on the current aging bucket.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Balance as of</strong></p></td>
<td><p>Enter the date to view the customer balances for. This is also known as a cutoff date for transactions.</p></td>
</tr>
<tr class="even">
<td><p><strong>Start date</strong></p></td>
<td><p>Enter a date that is in the first period interval or aging period to include on the report.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Criteria</strong></p></td>
<td><p>Select the type of date to base the report on.</p>
<ul>
<li><p><strong>Transaction date</strong> – The posting date of the transactions. For example, this might be an invoice date that is the basis for the calculation of the due date.</p></li>
<li><p><strong>Due date</strong> – The due date of the transactions, based on the terms of payment.</p></li>
<li><p><strong>Document date</strong> – A user-defined document date that is the basis for the calculation of the due date.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Aging period definition</strong></p></td>
<td><p>Select an aging period definition. The <strong>Interval</strong> field is not used if you select an aging period definition.</p>
<p>Aging period definitions that have more than six aging periods cannot be used on the printed report.</p>
<div class="alert">

**Note:** You can set up aging periods on the <STRONG>Aging period definitions</STRONG> page.</P>


</div></td>
</tr>
<tr class="odd">
<td><p><strong>Print aging period description</strong></p></td>
<td><p>Select <strong>Yes</strong> to include aging period descriptions at the top of each aging period column on the report. Select <strong>No</strong> to print the report without column headers.</p></td>
</tr>
<tr class="even">
<td><p><strong>Interval</strong></p></td>
<td><p>Define the period to use by entering the number of the day or month units in each period. For example, to view aging information by week, enter 7 in this field and select <strong>Day</strong> in the <strong>Day/Mth</strong> field.</p>
<div class="alert">

**Note:** The information that you enter in this field is used only if you have not selected an aging period definition. Otherwise, the printing direction is defined on the aging period definition.</P>


</div></td>
</tr>
<tr class="odd">
<td><p><strong>Day/Mth</strong></p></td>
<td><p>Select the unit, either <strong>Day</strong> or <strong>Month</strong>, that is used to define the period in the <strong>Interval</strong> field.</p></td>
</tr>
<tr class="even">
<td><p><strong>Printing direction</strong></p></td>
<td><p>Select whether to calculate balances and print the aging report for past or future periods. The dates are evaluated relative to the date that is selected in the <strong>Balance as on</strong> field. Select <strong>Backward</strong> to show information for past periods. Select <strong>Forward</strong> to show information for future periods.</p>
<div class="alert">
  
<STRONG>Note:</STRONG> The information that you enter in this field is used only if you have not selected an aging period definition.</P>


</div></td>
</tr>
<tr class="odd">
<td><p><strong>Details</strong></p></td>
<td><p>Select to list the transactions that are included in the balances that are shown on the report.</p></td>
</tr>
<tr class="even">
<td><p><strong>Include amounts in transaction currency</strong></p></td>
<td><p>Select to include amounts in the transaction currency in addition to amounts in the accounting currency. If this check box is not selected, the amounts on the report are displayed only in the accounting currency.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Negative balance</strong></p></td>
<td><p>Select to include customer accounts that have negative balances.</p></td>
</tr>
<tr class="even">
<td><p><strong>Exclude zero balance accounts</strong></p></td>
<td><p>Select to exclude customer accounts that have a zero balance.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Payment positioning</strong></p></td>
<td><p>Select to display payments that have not been settled. These are displayed in the first column of the report.</p></td>
</tr>
</tbody>
</table>



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
