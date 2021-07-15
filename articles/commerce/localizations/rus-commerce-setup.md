---
# required metadata

title: Set up the Dynamics 365 Commerce localization for Russia
description: This topic covers how to set up the Microsoft Dynamics 365 Commerce localization for Russia.
author: akviklis@microsoft.com
ms.date: 07/02/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Developer
# ms.devlang: 
ms.reviewer:
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
ms.search.industry: Retail
ms.author: akviklis
ms.search.validFrom: 07/01/2021
ms.dyn365.ops.version: 

---
# Set up the Dynamics 365 Commerce localization for Russia

[!include[banner](../includes/banner.md)]

This topic covers how to set up the Microsoft Dynamics 365 Commerce localization for Russia.

For more information about the Commerce localization for Russia, see [Russian localization scope](../../finance/localizations/russia.md) and [Commerce localization for Russia](rus-commerce-localization.md).

## Enable Russia-specific Commerce functionality

This section describes how to configure Commerce headquarters settings that are specific to and recommended for Russia. For more information, see the [Commerce home page](../index.md).

To enable and use the Russia-specific functionality, you must configure the following settings in Commerce headquarters.

1. In the primary address of the legal entity, set the **Country/region** field to **RUS** (Russia).
1. In the POS functionality profile of every store that is located in Russia, set the **ISO** field to **RU** (Russia).
1. Go to **System administration \> Workspaces \> Feature management**, and then, on the **All** tab, enable the following feature keys:

    - (Russia) Customer information management in Retail POS
    - Enable Russian simplified customer address format

## Customer information management

**(Russia) Customer information management in Retail POS** feature impacts the Retail POS functionality for Russia. It enables the inquiry of customer information (such as email address or phone number) in sales transactions.

## Customer account deposit

The **Customer account deposit** feature can be used to make prepayments at the Retail point of sale (POS). for more information see [Prepaymants in Retail for Russia](rus-commerce-prepayments.md).

## Set up aggregation parameters for registering POS sales and return transactions
You can set up the aggregation parameters that are used to aggregate the point of sale (POS) sales and return transactions when the transactions are registered in Microsoft Dynamics 365 Commerce. 
When you select the aggregation parameters, Microsoft Dynamics 365 Commerce aggregates the positive sales quantities and negative return quantities for items that have identical inventory dimensions.

### Example

You perform the following transactions at the POS:

  - Five sales transactions for two units of item A each, generating five sales receipts.

  - Two return transactions for two original receipts that contain one unit of item A each, generating two return receipts in the same shift.

  - Three return transactions for one unit of item A each, generating three receipts in a different shift.

  - One return transaction for one unit of item A without generating a receipt in a different shift.

The following table displays how the transactions are registered in Microsoft Dynamics AX depending on the parameters that you select in the **Retail parameters** form.

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th><p></p></th>
<th><p><strong>Process as a return in the same shift</strong></p></th>
<th><p><strong>Voucher transactions</strong> in the <strong>Aggregation</strong> field group in the <strong>Posting</strong> area</p></th>
<th><p><strong>Sales and returns</strong> in the <strong>Aggregation</strong> field group in the <strong>Posting</strong> area</p></th>
<th><p>Transactions created in Microsoft Dynamics AX</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Scenario 1</strong></p></td>
<td><p>Cleared</p></td>
<td><p>Cleared</p></td>
<td><p>Cleared</p></td>
<td><ul>
<li><p>Five sales orders are created for the sales transactions. Each sales order contains one line for two units of item A.</p></li>
<li><p>Six sales orders are created for the return transactions. Each sales order contains one line for one unit of item A.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Scenario 2</strong></p></td>
<td><p>Cleared</p></td>
<td><p>Selected</p></td>
<td><p>Cleared</p></td>
<td><ul>
<li><p>For the first two transactions that were performed in the same shift, a single sales order is created, which contains three lines. The first line contains 10 units of item A and the second and third lines contain -1 unit of item A each.</p></li>
<li><p>For the remaining return transactions that were performed in a different shift, four sales orders that contain one line for -1 unit of item A each are created.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>Scenario 3</strong></p></td>
<td><p>Cleared</p></td>
<td><p>Selected</p></td>
<td><p>Selected</p></td>
<td><ul>
<li><p>For the first two transactions that were performed in the same shift, a single sales order is created, which contains one line for eight units of item A (10 -2).</p></li>
<li><p>For the remaining return transactions that were performed in a different shift, four sales orders that contain one line for -1 unit of item A each are created.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Scenario 4</strong></p></td>
<td><p>Selected</p></td>
<td><p>Cleared</p></td>
<td><p>Cleared</p></td>
<td><ul>
<li><p>Five sales orders are created for the sales transaction. Each sales order contains one line for two units of item A.</p></li>
<li><p>Six sales orders are created for the return transactions. Each sales order contains one line for -1 unit of item A.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>Scenario 5</strong></p></td>
<td><p>Selected</p></td>
<td><p>Selected</p></td>
<td><p>Cleared</p></td>
<td><p>One sales order is created for all of the sales and return transactions. The sales order contains seven lines: The first line contains 10 units of item A, and the remaining six lines contain -1 unit of item A each.</p></td>
</tr>
<tr class="even">
<td><p><strong>Scenario 6</strong></p></td>
<td><p>Selected</p></td>
<td><p>Selected</p></td>
<td><p>Selected</p></td>
<td><p>One sales order is created for all of the transactions. The sales order contains one line for four units of item A (10 - 2 - 3 - 1).</p></td>
</tr>
</tbody>
</table>


### Set up aggregation parameters

Use this procedure to set up the aggregation parameters that are used to aggregate POS sales and return transactions in Microsoft Dynamics AX.

1.  Click **Retail** \> **Setup** \> **Parameters** \> **Retail parameters**.

2.  Select the **Process as a return in the same shift** check box to process return transactions during a different shift in the same way that you process return transactions during the same shift.

3.  Click **Posting**, and then in the **Posting** area, in the **Aggregation** field group, select the **Voucher transactions** check box to aggregate voucher transactions.

4.  Select the **Sales and returns** check box to aggregate POS sales and return transactions.
    

    > [!NOTE]
    > <P>This check box is available only if you select the <STRONG>Voucher transactions</STRONG> check box.</P>

## Set up parameters for statements

1. Go to **Organization administration \> Number sequences**.
1. Create and set up number sequences for retail statements for each store (operating unit).
1. On the **References** FastTab, add two references for the **Retail store** area: one where the **Reference** value is set to **Statement number** and one where it's set to **Voucher**.
1. Go to **Retail and Commerce \> Catalog and assortments**.
1. Create an assortment that includes appropriate products.
1. On the **Commerce channels** tab, add the stores that you created earlier. Then select **Publish**.
1. Go to **Retail and Commerce \> Channel setup \> Channel categories and product attributes**, and publish channel updates.
1. Go to **Sales and marketing \> Setup > Returns \> Disposition codes**, and add a disposition code.
1. Go to **Retail and commerce \> Products and categories \> Released products by category**.
1. Select a product for the gift card, and then select the **Blocked at register** check box.
1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**.
1. On the **Customer orders** tab, enter the disposition code that you added earlier.
1. On the **Posting** tab, set up the parameters for the gift card. These parameters include the **Gift card company** and **Gift card product** fields.

## Additional resources

[Commerce localization for Russia](rus-commerce-localization.md) 

[Prepaymants in Retail for Russia](rus-commerce-prepayments.md)
