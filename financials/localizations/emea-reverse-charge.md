---
# required metadata

title: Reverse charge
description: This topic provides information on generic approach about setting up the Reverse Charge (RC) value-added tax (VAT) for European countries
author: epodkolz 
manager: AnnBe
ms.date: 05/12/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
# ms.reviewer: shylaw
# ms.search.scope: [Which Operations client to show this topic as help for, to be set by content strategist, see list here: https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29]
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.assetid: [Go get from guidgenerator.com]
ms.search.region: [Global for most topics. Set Country/Region name for localizations]
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: [author's Microsoft alias]
ms.search.validFrom: [month/year of release that feature was introduced in, in format yyyy-mm-dd]
ms.dyn365.ops.version: [name of release that feature was introduced in, see list here: https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29]
---
# Overview
This topic describes the generic approach to setting up the reverse charge (RC) value-added tax (VAT) for European countries.
*Reverse Charge* is a tax schema that moves the responsibility for the accounting and reporting of VAT from the seller to the buyer of goods and/or services. Thus, the recipient of goods and/or services reports both the output VAT (acting as a seller) and the input VAT (acting as a purchaser) in their VAT statement.
The EU Directive left space for Member State to determine how to adopt the generic requirements to local needs. Thus, in some countries, the *Reverse Charge Schema* is implemented only for certain goods and/or services, with additional conditions/thresholds on sales amounts, and in others, the VAT payment responsibility depends on the status of the supplier and the buyer. If the buyer is liable to pay VAT, it must be clearly reflected on the invoice issued by the supplier, i.e. a special wording *'Reverse charge'* must be included in the invoice along with indicating which positions are under the *Reverse Charge schema*. 

You need to complete the following setup to apply the Reverse charge.

# Setup sales tax codes
It is recommended to use separate sales tax codes for purchase and for sales operations.

#### Sales tax code for Sales
Create a sales tax code for Reverse charge sales operations (Tax > Indirect taxes > Sales tax > Sales tax codes).

#### Sales tax code for Purchases
You need to create positive and negative sales tax codes for reverse charge VAT for purchases (Tax > Indirect taxes > Sales
tax > Sales tax codes).
1. Create a sales tax code with positive value.
2. Create a sales tax code with negative value. Set the **Allow negative sales tax percentage** = **Yes**.
You will need to assign the negative sales tax code to an item sales tax group, and then assign that item sales tax group to the items that are subject to reverse charge VAT.
For more information, see **Set up Sales tax groups and Item sales tax groups**.

# Set up Sales tax groups and Item sales tax groups
It is recommended to use separate sales tax groups for purchase and for sales operations.

#### Sales tax groups for Sales
Create a sales tax group for sales operations with Reverse charge (Tax > Indirect taxes > Sales tax > Sales tax groups), and include the sales tax code for Reverse charge in this group (**Setup** tab). Select the **Exempt** and **Reverse charge** check boxes for the sales tax code.

#### Sales tax groups for Purchases
Create a sales tax group for purchases operations with Reverse charge (Tax > Indirect taxes > Sales tax > Sales tax groups), and include both positive and negative sales tax codes in this group (**Setup** tab). Select the **Reverse charge** check box for the sales tax code with negative value.

#### Item sales tax groups
Create or update Item sales tax group with Sales tax code with negative value (Tax > Indirect taxes > Sales tax > Item sales tax groups). You need to assign the default item sales tax group to the products and categories that are subject to reverse charge.

# Set up Reverse Charge groups
In Tax > Setup > Sales tax > Reverse charge item groups you can define groups of products/services or individual products/services to which the reverse charge can be applied. For each Reverse charge item group define the list of items/item groups/categories for Sale and/or Purchase.

# Set up Reverse Charge Rules
In Tax > Setup > Sales tax > Reverse charge rules you can define the applicability rules for purchase and sales purposes. You can configure a set of reverse charge applicability rules. This involves: 
+ **Document type**: Purchase order, Vendor invoice journal, Sales order, Free text invoice, Customer invoice journal, and/or Vendor invoice.
+ **Country/region type of the partner**. *Domestic*, *EU*, *Foreign*, or the rule can be applied for *All* trade partners, no matter of their country/region address.
+ **Domestic delivery address**. If you select this check box then the rule will be applied to the deliveries within the same country/region. This check box cannot be selected for *Vendor invoice journal* and *Customer invoice journal* document types.
+ **Reverse charge item group**. Select the group to which the rule can be applied.
+ **Threshold amount**. The *Reverse Charge schema* is applied to invoice only if the value of items/services included in the *Reverse charge item group* exceeds the specified limit.

You can define the period the rule is effective, using the **Effective** and **Expiration dates**. In addition, you can define whether a notification is needed in case the condition for the document line is met, and update the document line with the default reverse charge sales tax group:
- *None* – the document line is not updated;
- *Prompt* – dialog pops up to confirm the reverse charge can be applied;
- *Set* – the document line is updated without additional notification.

# Set up default parameters
To enable the functionality, open the **General ledger parameters** page, switch to the **Reverse charge** tab and set **Enable reverse charge** = **Yes**.
Select the default sales tax groups in the **Purchase order sales tax group** and **Sales order tax group** fields. When a reverse charge applicability condition is met, the sales/purchase order line will be updated with these sales tax groups.

# Reverse charge in Sales invoice
When selling under the *Reverse charge schema*, the seller does not charge VAT, but the items that are subject to reverse charge VAT, and the total amount of reverse charge VAT, are noted on the invoice.
When a sales invoice is posted with Reverse Charge, the sales tax transactions have the **Sales tax payable** tax direction, zero sales tax, and the **Reverse charge** check box set.

# Reverse charge in Purchase invoice
When purchasing under the *Reverse Charge schema*, the purchaser that receives the invoice with Reverse charge acts as a buyer and a seller for VAT accounting purposes.
When purchase invoice with Reverse Charge is posted, two sales tax transactions are created: one with the **Sales tax receivable** tax direction and another one with the **Sales tax payable** tax direction, and the **Reverse charge** check box set.
