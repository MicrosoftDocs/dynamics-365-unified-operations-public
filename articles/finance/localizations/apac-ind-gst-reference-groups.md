---
# required metadata

title: Set up GST reference number groups
description: This topic explains how to set up reference number groups for Goods and Services Tax (GST) in Microsoft Dynamics 365 Finance. 
author: ShylaThompson
manager: AnnBe
ms.date: 06/04/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

#ms.search.form:
audience: IT Pro, Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.suite: 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
ms.search.scope: Core, Operations
# ms.search.industry: 
ms.author: ralin
ms.dyn365.ops.version: 7.3.1
ms.search.validFrom: 2018-1-31
---


# Set up GST reference number groups

[!include [banner](../includes/banner.md)]

Goods and Services Tax (GST) transactions are differentiated by a unique number sequence. If a different number sequence is required for the address of each warehouse or legal entity, you can create a reference number sequence group. You can then assign the reference number sequence group to the addresses.

Follow these steps to create a GST reference number sequence group and assign it to addresses.

1. Go to **Tax** \> **Setup** \> **Sales tax** \> **India** \> **GST reference number sequence group**.
2. Select **New**.
3. Enter a name and a description.
4. On the **Details** FastTab, define number sequences for the references. The following table provides more information about each reference.

    | Source              | Reference                | Description |
    |---------------------|--------------------------|-------------|
    | Accounts receivable | Bill of supply           | The **Bill of supply** number sequence is used when customer sales that have non-GST transactions are posted. |
    | Accounts receivable | Debit/Credit note        | The **Debit/Credit note** number sequence is used when customer debit or credit sales that have GST transactions are posted. |
    | Accounts receivable | Revised invoice          | The **Revised invoice** number sequence is used when customer revised sales invoices are posted that have GST transactions and a reference to the existing invoice. |
    | Accounts receivable | Advanced receipt voucher | The **Advance receipt voucher** number sequence is used when customer advance receipt transactions that have GST transactions are posted. |
    | Accounts receivable | Advanced refund voucher  | The **Advance refund voucher** number sequence is used when customer advance refund transactions that have GST transactions are posted. |
    | Accounts receivable | GST invoice              | The **GST invoice** number sequence is used when customer sales that have GST transactions are posted. |
    | Accounts receivable | Export order             | The **Export order** number sequence is used when customs export order transactions are posted. |
    | Accounts payable    | Debit/Credit note        | The **Debit/Credit note** number sequence is used when vendor debit or credit purchases are posted that have GST transactions together with reverse charge transactions. |
    | Accounts payable    | Revised invoice          | The **Revised invoice** number sequence is used when vendor revised purchase invoices are posted that have GST transactions together with reverse charge transactions, and that have a reference to the existing invoice. |
    | Accounts payable    | Advanced payment voucher | The **Advance payment voucher** number sequence is used when vendor advance payment transactions that have GST transactions are posted. |
    | Accounts payable    | GST invoice              | The **GST invoice** number sequence is used when vendor purchases are posted that have GST transactions together with reverse charge transactions. |
# Type of supply and GST number sequence refrence ID generation 

Under GST law the broader classification of the type of supply is as below: 

1. Taxable Supply 
- Standard Rated Supply. Example 12% 
- Zero Rated Supply – Example 0% 
2. Non-Taxable Supply
- Exempt Supply (Excluded under the GST Act)
- Out of scope supply (Outside of GST act) 
3. Non GST Supply
- No tax type applicable 
- VAT applicable 

The India GST number sequence logic works as per the condition provided below for updating invoice reference ID: 

- If the Tax rate is not zero, the sequence will be picked from GST tax Invoice reference ID. 
- If the Tax rate is zero (Tax rate in every sales order line is zero or exempt or non-GST), the sequence will be picked from BOS (Bill of supply);
- If an item is marked as “Exempted item” than irrespective of a tax rate, number sequence will be picked from BOS (Bill of supply) 
- If an item is marked as “Non-GST” supply than even any other tax type is applied on the transaction or not, number sequence will be picked from BOS (Bill of supply) 
- If Tax value is zero and the Tax rate is not zero, the sequence will be picked from the tax invoice reference ID. Example. For some case the tax rate = 0.06, base amount = 0.02, thus tax amount is rounded to 0, but the tax rate is not zero (it is 0.06), thus will not consider as BOS (the system will consider normal taxable sales invoice reference ID )
- If some transaction lines are taxable and other transactions lines are exempted system will generate GST transaction ID for tax invoice (means if a single item is taxable – Tax invoice Id will generate) 
- If intra-state stock transfer, HSN/SAC code is not selected for any transaction line, the number sequence will not be picked up any Bill of supply or tax Invoice reference ID for both shipment and receipt.  
- If intra-state stock transfer order is marked as exempt in the header than the number sequence will be picked from BOS (Bill of supply) reference ID.
- In stock transfer receipt transaction system will copy the shipment transaction id when the number sequence reference ID is generated for shipment transaction.

