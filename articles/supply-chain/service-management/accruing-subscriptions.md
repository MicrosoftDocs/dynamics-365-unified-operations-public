---
title: Accruing subscriptions  
description: With service subscriptions, you manually accrue revenue in the periods following the date when you invoiced a fee transaction.
author: Henrikan
ms.author: henrikan
ms.topic: article
ms.date: 04/30/2018
ms.custom:
ms.reviewer: kamaybac
ms.search.form: SMASubscriptionGroup
---

# Accruing subscriptions

[!include [banner](../includes/banner.md)]

With service subscriptions, you manually accrue revenue in the periods following the date when you invoiced a fee transaction.

Accrual periods are created for the invoice period that you set up for the subscription fee, and the accrual periods are based on the period code of the subscription.

You can accrue and reverse accrued revenue.

## Reverse accruals of credit amounts

If you credit invoiced subscription amounts, you can use two methods to reverse the accrual amounts:

- You can reverse each accrued revenue transaction individually before you create the credit note proposal for the transaction. This is the manual method. (manual)

- You can have the accrued amounts reversed on the date where the credit note is posted or on the original posting date of the accrual.

Learn more in [Subscription parameters (page)](/dynamicsax-2012//subscription-parameters-page).

## Setup requirements

To accrue revenue, make sure that the following data requirements are met:

## Account setup

The **WIP - subscription** and the **Accrued revenue - subscription** accounts must be set up in the **Project** module.

When you post accrued revenue, the **WIP - subscription** account is debited with the accrual amount, and the **Accrued revenue - subscription** account is credited with the accrual amount.

## Set up accounts for accrual of subscription revenue

1. Go to **Project management and accounting** \> **Setup** \> **Posting** \> **Ledger posting setup**.

2. Select the **Revenue accounts** tab, and select **WIP - subscription** or **Accrued revenue - subscription** to set up the accounts.

## Subscription group setup

To be able to accrue revenue for subscriptions, the **Accrue revenue** check box must be selected. This is found on the **Subscription groups** page for the group that is attached to the subscription. Go to **Service management** \> **Setup** \> **Service subscriptions** \> **Subscription groups**.

## Enable revenue accrual on a subscription group

Go to **Service management** \> **Setup** \> **Service subscriptions** \> **Subscription groups**.

## Periods

You must set up an invoicing period code. Unless you want to accrue revenue in the same time intervals as you use for invoicing, you must also set up an accrual period.

The following table provides an overview of which accrual periods can be set up for each invoicing period:

<table>
<colgroup>
<col />
<col />
</colgroup>
<thead>
<tr class="header">
<th><p>Invoicing period</p></th>
<th><p>Accrual period</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Years</strong></p></td>
<td><ul>
<li><p><strong>Years</strong></p></li>
<li><p><strong>Quarter</strong></p></li>
<li><p><strong>Month</strong></p></li>
<li><p><strong>Day</strong></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Quarter</strong></p></td>
<td><ul>
<li><p><strong>Quarter</strong></p></li>
<li><p><strong>Month</strong></p></li>
<li><p><strong>Day</strong></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>Month</strong></p></td>
<td><ul>
<li><p><strong>Month</strong></p></li>
<li><p><strong>Day</strong></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Week</strong></p></td>
<td><ul>
<li><p><strong>Day</strong></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>Day</strong></p></td>
<td><ul>
<li><p><strong>Day</strong></p></li>
</ul></td>
</tr>
</tbody>
</table>

Setting up the invoicing period is a mandatory part of the overall subscription group setup. You can decide whether to also set up an accrual period for the subscription group. If you set up an accrual period for the subscription group, this period is suggested in the **Period code** field. This field is found on the **Accrue subscription revenue** page, when you accrue subscription revenue. However, the accrual period is optional information about the subscription group.

> [!NOTE]
> Use the following path to open the **Accrue subscription revenue** page. Go to **Service management** &gt; **Periodic** &gt; **Service subscriptions** &gt; **Accrue subscription revenue**.

## Transactions

You can control the number of ledger transactions that are created when you post accrued revenue. On subscriptions, define if the ledger transactions should be created as a total or per line.

## Specify the level of posting details to display for accrued transactions

1. Go to **Project management and accounting** \> **Setup** \> **Project management and accounting parameters**.

2. On the **Financial** tab, in the **Invoice** field, select **Total** or **Line**.

## Related information

- [Accrue subscription revenue](accrue-subscription-revenue.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
