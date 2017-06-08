---
# required metadata

title: Reverse charge VAT | Microsoft Docs
description: This topic explains how to set up the reverse charge value-added tax (VAT) for European countries.
author: epodkolz 
manager: AnnBe
ms.date: 05/12/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Austria, Belgium, Czech Republic, Denmark, Estonia, Finland, France, Germany, Hungary, Ireland, Italy, Latvia, Lithuania, Netherlands, Poland, Spain, Sweden, United Kingdom
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: epodkolz
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: Enterprise edition, July 2017 update
---

# Reverse charge VAT
This topic describes a generic approach for setting up the reverse charge value-added tax (VAT) for European countries.

Reverse Charge is a tax schema that moves the responsibility for the accounting and reporting of VAT from the seller to the buyer of goods and/or services. Therefore, recipients of goods and/or services report both the output VAT (in the role of a seller) and the input VAT (in the role of a purchaser) in their VAT statement.

The European Union (EU) Directive let member states determine how they would adapt the generic requirements to local requirements. Therefore, in some countries, the Reverse Charge schema is implemented only for some goods and/or services, and there are additional conditions or thresholds on sales amounts. In other countries, the responsibility for VAT payment depends on the status of the supplier and the buyer. If the buyer is liable to pay VAT, this fact must be clearly indicated on the invoice that the supplier issues. For example, the invoice must include the words "Reverse charge" and must indicate which positions are under the Reverse Charge schema. 

To apply the reverse charge, you must complete the following setup.

## Set up sales tax codes
We recommend that you use separate sales tax codes for purchase operations and sales operations.

<table>
<body>
<tr>
<td><strong>Sales tax code for sales</strong></td>
<td>Create a sales tax code for reverse charge sales operations (<strong>Tax</strong> > <strong>Indirect taxes</strong> > <strong>Sales tax</strong> > <strong>Sales tax codes</strong>).
</td>
</tr>
<tr>
<td><strong>Sales tax code for purchases</strong></td>
<td><p>Create positive and negative sales tax codes for the reverse charge VAT for purchases (<strong>Tax</strong> > <strong>Indirect taxes</strong> > <strong>Sales tax</strong> > <strong>Sales tax codes</strong>).</p>
<ol>
<li>Create a sales tax code that has a positive value.</li>
<li>Create a sales tax code that has a negative value. Set the <strong>Allow negative sales tax percentage</strong> option to <strong>Yes</strong>.
You must assign this negative sales tax code to an item sales tax group, and then assign that item sales tax group to the items that are subject to the reverse charge VAT.</li>
</ol>
<p>For more information, see the next section, "Set up sales tax groups and item sales tax groups."</p>
</td>
</tr>
</tbody>
</table>

## Set up sales tax groups and item sales tax groups
We recommend that you use separate sales tax groups for purchase operations and sales operations.

<table>
<tr>
<td><strong>Sales tax groups for sales</strong></td>
<td>Create a sales tax group for sales operations that have the reverse charge (<strong>Tax</strong> > <strong>Indirect taxes</strong> > <strong>Sales tax</strong> > <strong>Sales tax groups</strong>). On the <strong>Setup</strong> tab, include the sales tax code for the reverse charge in this group. Select the <strong>Exempt</strong> and <strong>Reverse charge</strong> check boxes for the sales tax code.</td>
</tr>
<tr>
<td><strong>Sales tax groups for purchases</strong></td>
<td>Create a sales tax group for purchase operations that have the reverse charge (<strong>Tax</strong> > <strong>Indirect taxes</strong> > <strong>Sales tax</strong> > <strong>Sales tax groups</strong>). On the <strong>Setup</strong> tab, include both positive and negative sales tax codes in this group. Select the <strong>Reverse charge</strong> check box for the sales tax code that has a negative value.</td>
</tr>
<tr>
<td><strong>Item sales tax groups</strong></td>
<td>Create or update the item sales tax group with the sales tax code that has a negative value (<strong>Tax</strong> > <strong>Indirect taxes</strong> > <strong>Sales tax</strong> > <strong>Item sales tax groups</strong>). You must assign the default item sales tax group to the products and categories that are subject to the reverse charge.</td>
</tr>
</table>

## Set up reverse charge groups
On the **Reverse charge item groups** page (**Tax** > **Setup** > **Sales tax** > **Reverse charge item groups**), you can define groups of products or services, or individual products or services, that the reverse charge can be applied to. For each reverse charge item group, define the list of items, item groups, and categories for sales and/or purchases.

## Set up reverse charge rules
On the **Reverse charge rules** page (**Tax** > **Setup** > **Sales tax** > **Reverse charge rules**), you can define the applicability rules for purchase and sales purposes. You can configure a set of reverse charge applicability rules. For each rule, set the following fields:

- **Document type** – Select **Purchase order**, **Vendor invoice journal**, **Sales order**, **Free text invoice**, **Customer invoice journal**, and/or **Vendor invoice**.
- **Country/region type of the partner** – Select **Domestic**, **EU**, or **Foreign**. Alternatively, if the rule can be applied to all trade partners, regardless of the country or region of their address, select **All**.
- **Domestic delivery address** – Select this check box to apply the rule to deliveries within the same country or region. This check box can't be selected for the **Vendor invoice journal** and **Customer invoice journal** document types.
- **Reverse charge item group** – Select the group that the rule can be applied to.
- **Threshold amount** – The Reverse Charge schema is applied to an invoice only if the value of items and/or services that are included in the reverse charge item group exceeds the limit that you specify here.

You can use the **Effective date** and **Expiration date** fields to define the period when the rule is effective.

Additionally, you can specify whether a notification appears and the document line is updated with the default reverse charge sales tax group if the condition for that document line is met. The following options are available:

- **None** – The document line isn't updated.
- **Prompt** – A notification appears to confirm that the reverse charge can be applied.
- **Set** – The document line is updated without additional notification.

## Set up default parameters
To enable the functionality, on the **General ledger parameters** page, on the **Reverse charge** tab, set the **Enable reverse charge** option to **Yes**. In the **Purchase order sales tax group** and **Sales order tax group** fields, select the default sales tax groups. When a reverse charge applicability condition is met, the sales or purchase order line is updated with these sales tax groups.

## Reverse charge on a sales invoice
For sales under the Reverse Charge schema, the seller doesn't charge VAT. Instead, the invoice indicates both the items that are subject to the reverse charge VAT and the total amount of the reverse charge VAT.

When a sales invoice is posted that has the reverse charge, the sales tax transactions have the **Sales tax payable** tax direction and zero sales tax, and the **Reverse charge** check box is selected.

## Reverse charge on a purchase invoice
For purchases under the Reverse Charge schema, the purchaser that receives the invoice that has the reverse charge acts as a buyer and a seller for VAT accounting purposes.

When a purchase invoice that has the reverse charge is posted, two sales tax transactions are created. One transaction has the **Sales tax receivable** tax direction. The other transaction has the **Sales tax payable** tax direction. The **Reverse charge** check box is selected.
