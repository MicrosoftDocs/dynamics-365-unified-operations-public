---
# required metadata

title: Subscription sales prices  
description: When you create a subscription, the sales price is derived from the sales price setup that was created in the Sales price (subscription) form.
author: sorenva
ms.date: 05/01/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SMASalespriceSubscription
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sorenand
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Subscription sales prices

[!include [banner](../includes/banner.md)]

When you create a subscription, the sales price is derived from the sales price setup that was created in the **Sales price (subscription)** form.

In the **Sales price (subscription)** form, you can create sales prices for a specific subscription or you can create sales prices that apply more broadly. For a sales price to be applied to a subscription, the period code and the currency of the subscription must be identical to the period code and the currency of the sales price.

If the period code and currency are identical for the subscription and the sales price, subscription sales prices are selected on the basis of the priorities listed in the following table. A blank cell in the table indicates an empty field and an X indicates a value that is equal to the value in the subscription from which the transaction is generated.

<table>
<colgroup>
<col />
<col />
<col />
<col />
<col />
<col />
</colgroup>
<thead>
<tr class="header">
<th><p>Priority</p></th>
<th><p><strong>Category</strong></p></th>
<th><p><strong>Project ID</strong></p></th>
<th><p><strong>Subscription</strong></p></th>
<th><p><strong>Sales currency</strong></p></th>
<th><p><strong>Period code</strong></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>2</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="odd">
<td><p>3</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>4</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="odd">
<td><p>5</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>6</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="odd">
<td><p>7</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>8</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
</tbody>
</table>

When a subscription fee is created, the sales price with the greatest level of detail, as noted in the table above, is selected as the subscription sales price.

## Update and index subscription sales prices

You can update the subscription sales price by updating the base price or the index. You can update by a percentage or to a new value.

## Subscription fee sales prices

When you create a subscription fee, the sales price is based on the sales price setup of the subscription. You can either use the base price from the subscription price setup or create indexed sales prices.

## Example

You want to set up subscription sales prices of EUR 500 for a new project 9030. In the **Sales price (subscription)** form, you create a subscription sales price line as indicated in the following table.

<table>
<colgroup>
<col />
<col />
<col />
<col />
<col />
<col />
<col />
</colgroup>
<thead>
<tr class="header">
<th><p>Valid from</p></th>
<th><p>Category</p></th>
<th><p>Project</p></th>
<th><p>Subscription</p></th>
<th><p>Period code</p></th>
<th><p>Sales currency</p></th>
<th><p>Sales price</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>28-08-2006</p></td>
<td></td>
<td><p>9030</p></td>
<td></td>
<td><p>Month</p></td>
<td><p>EUR</p></td>
<td><p>500</p></td>
</tr>
</tbody>
</table>


Note that the **Category** and **Subscription** fields are empty.

You then create the following subscriptions.

<table>
<colgroup>
<col />
<col />
<col />
<col />
<col />
<col />
</colgroup>
<thead>
<tr class="header">
<th><p>Service subscription</p></th>
<th><p>Project</p></th>
<th><p>Subscription group</p></th>
<th><p>Category</p></th>
<th><p>Currency</p></th>
<th><p>Period code</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>00020_135</p></td>
<td><p>9030</p></td>
<td><p>Sub1</p></td>
<td><p>SubCat1</p></td>
<td><p>EUR</p></td>
<td><p>Monthly</p></td>
</tr>
<tr class="even">
<td><p>00021_135</p></td>
<td><p>9030</p></td>
<td><p>Sub1</p></td>
<td><p>SubCat2</p></td>
<td><p>EUR</p></td>
<td><p>Monthly</p></td>
</tr>
</tbody>
</table>


Now you create subscription fees for both subscriptions in the subscription group Sub1:

1.  Click **Service management** \> **Setup** \> **Service subscriptions** \> **Subscription groups**.

2.  In the **Subscription groups** form, click **Function** \> **Create subscription fee**.

3.  In the **Create subscription fee** form, enter the appropriate information. For more information, see [Create subscription fee transactions](create-subscription-fee-transactions.md).

Subscription fees that have a sales price of EUR 500 are created for both subscriptions, as shown in the following table.

<table>
<colgroup>
<col />
<col />
<col />
<col />
<col />
<col />
<col />
<col />
</colgroup>
<thead>
<tr class="header">
<th><p>Project date</p></th>
<th><p>Service subscription</p></th>
<th><p>Project</p></th>
<th><p>Category</p></th>
<th><p>Start date</p></th>
<th><p>End date</p></th>
<th><p>Sales currency</p></th>
<th><p>Sales price</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>28-08-2006</p></td>
<td><p>00020_135</p></td>
<td><p>9030</p></td>
<td><p>SubCat1</p></td>
<td><p>01-01-2007</p></td>
<td><p>31-03-2007</p></td>
<td><p>EUR</p></td>
<td><p>500</p></td>
</tr>
<tr class="even">
<td><p>28-08-2006</p></td>
<td><p>00021_135</p></td>
<td><p>9030</p></td>
<td><p>SubCat2</p></td>
<td><p>01-01-2007</p></td>
<td><p>31-03-2007</p></td>
<td><p>EUR</p></td>
<td><p>500</p></td>
</tr>
</tbody>
</table>


Later, you decide that you want to specify sales prices for the category SubCat1 for project 9030. Therefore, you create a new sales price line that has a sales price of EUR 550 for the combination of project 9030 and fee category SubCat1. There are now two subscription sales price lines for project 9030, as shown in the following table.

<table>
<colgroup>
<col />
<col />
<col />
<col />
<col />
<col />
<col />
</colgroup>
<thead>
<tr class="header">
<th><p>Valid from</p></th>
<th><p>Category</p></th>
<th><p>Project</p></th>
<th><p>Subscription</p></th>
<th><p>Period code</p></th>
<th><p>Currency</p></th>
<th><p>Sales price</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>28-08-2007</p></td>
<td></td>
<td><p>9030</p></td>
<td></td>
<td><p>Month</p></td>
<td><p>EUR</p></td>
<td><p>500</p></td>
</tr>
<tr class="even">
<td><p>28-08-2007</p></td>
<td><p>SubCat1</p></td>
<td><p>9030</p></td>
<td></td>
<td><p>Month</p></td>
<td><p>EUR</p></td>
<td><p>550</p></td>
</tr>
</tbody>
</table>

You repeat the procedure described above to create subscription fees for both subscriptions in the subscription group Sub1. The following table shows the transactions that are created for each subscription that is attached to the subscription group.

<table>
<colgroup>
<col />
<col />
<col />
<col />
<col />
<col />
<col />
<col />
</colgroup>
<thead>
<tr class="header">
<th><p>Project date</p></th>
<th><p>Subscription</p></th>
<th><p>Project</p></th>
<th><p>Category</p></th>
<th><p>Start date</p></th>
<th><p>End date</p></th>
<th><p>Sales currency</p></th>
<th><p>Sales price</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>28-07-2007</p></td>
<td><p>00020_135</p></td>
<td><p>9030</p></td>
<td><p>SubCat1</p></td>
<td><p>01-01-2008</p></td>
<td><p>31-03-2008</p></td>
<td><p>EUR</p></td>
<td><p>550</p></td>
</tr>
<tr class="even">
<td><p>28-07-2008</p></td>
<td><p>00021_135</p></td>
<td><p>9030</p></td>
<td><p>SubCat2</p></td>
<td><p>01-01-2008</p></td>
<td><p>31-03-2008</p></td>
<td><p>EUR</p></td>
<td><p>500</p></td>
</tr>
</tbody>
</table>

In the first transaction for subscription 00020\_135, the sales price of EUR 550 derives from the subscription sales price that is set up for the combination of the specific project and category. In the second transaction for subscription 00021\_135, the sales price of EUR 500 is used as the project subscription sales price because there is no price set up for the combination of project 9030 and category SubCat2.

## See also

[Update and index subscription sales prices](update-and-index-subscription-sales-prices.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
