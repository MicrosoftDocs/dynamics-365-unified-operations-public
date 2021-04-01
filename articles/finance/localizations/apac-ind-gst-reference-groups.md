---
# required metadata

title: Set up GST reference number groups
description: This topic explains how to set up reference number groups for Goods and Services Tax (GST) in Microsoft Dynamics 365 Finance. 
author: ShylaThompson
ms.date: 02/18/2020
ms.topic: article
ms.prod: 
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
    
## Type of supply and GST number sequence reference ID generation 

Under GST law, the broader classification of the type of supply is shown below: 
- Taxable supply 
    - Standard rated supply - Example 12% 
    - Zero rated supply – Example 0% 
- Non-taxable supply
    - Exempt supply (excluded under the GST Act)
    - Out of scope supply (outside of the GST Act) 
- Non GST supply
    - No tax type applicable 
    - VAT applicable 
    
The India GST number sequence logic is based on the following conditions for updating the invoice reference ID: 

- If the tax rate is not zero, the sequence will be picked from the GST tax invoice reference ID. 
- If the tax rate is zero (tax rate in every sales order line is zero, exempt, or non-GST), the sequence will be picked from the bill of supply.
- If an item is marked as “Exempted item”, irrespective of a tax rate the sequence will be picked from the bill of supply.
- If an item is marked as “Non-GST” supply, then another tax type is applied on the transaction and the number sequence will be picked from the bill of supply.
- If tax value is zero and the tax rate is not zero, the sequence will be picked from the tax invoice reference ID. For example, if the tax rate = 0.06 and base amount = 0.02, the tax amount is rounded to 0, but the tax rate is not zero (it is 0.06), this will not be considered as the bill of supply. Instead, the system will consider the taxable sales invoice reference ID. 
- If some transaction lines are taxable and other transactions lines are exempt, the system will generate a GST transaction ID for the tax invoice. This means that if a single item is taxable, a tax invoice ID will be generated. 
- If intra-state stock transfer and HSN/SAC code is not selected for any transaction line, the sequence will not be picked from the bill of supply or tax invoice reference ID for both the shipment and receipt.  
- If intra-state stock transfer order is marked as exempt in the header, then the number sequence will be picked from the bill of supply reference ID.
- For a stock transfer receipt transaction, the system will copy the shipment transaction ID when the number sequence reference ID is generated for the shipment transaction.




[!INCLUDE[footer-include](../../includes/footer-banner.md)]