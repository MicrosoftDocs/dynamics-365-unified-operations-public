---
title: Set up GST reference number groups
description: Learn how to set up reference number groups for Goods and Services Tax (GST) in Microsoft Dynamics 365 Finance, including a step-by-step process.
author: EricWangChen
ms.author: wangchen
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/30/2026
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: India
ms.search.validFrom: 2018-01-31
ms.dyn365.ops.version: 7.3.1
---


# Set up GST reference number groups

[!include [banner](../../includes/banner.md)]

Goods and Services Tax (GST) transactions use a unique number sequence to differentiate them. If you need a different number sequence for the address of each warehouse or legal entity, create a reference number sequence group. Then, assign the reference number sequence group to the addresses.

Follow these steps to create a GST reference number sequence group and assign it to addresses.

1. Go to **Tax** > **Setup** > **Sales tax** > **India** > **GST reference number sequence group**.
1. Select **New**.
1. Enter a name and a description.
1. On the **Details** FastTab, define number sequences for the references. The following table provides more information about each reference.

    | Source              | Reference                | Description |
    |---------------------|--------------------------|-------------|
    | Accounts receivable | Bill of supply           | Use the **Bill of supply** number sequence when posting customer sales that have non-GST transactions. |
    | Accounts receivable | Debit/Credit note        | Use the **Debit/Credit note** number sequence when posting customer debit or credit sales that have GST transactions. |
    | Accounts receivable | Revised invoice          | Use the **Revised invoice** number sequence when posting customer revised sales invoices that have GST transactions and a reference to the existing invoice. |
    | Accounts receivable | Advanced receipt voucher | Use the **Advance receipt voucher** number sequence when posting customer advance receipt transactions that have GST transactions. |
    | Accounts receivable | Advanced refund voucher  | Use the **Advance refund voucher** number sequence when posting customer advance refund transactions that have GST transactions. |
    | Accounts receivable | GST invoice              | Use the **GST invoice** number sequence when posting customer sales that have GST transactions. |
    | Accounts receivable | Export order             | Use the **Export order** number sequence when posting customs export order transactions. |
    | Accounts payable    | Debit/Credit note        | Use the **Debit/Credit note** number sequence when posting vendor debit or credit purchases that have GST transactions together with reverse charge transactions. |
    | Accounts payable    | Revised invoice          | Use the **Revised invoice** number sequence when posting vendor revised purchase invoices that have GST transactions together with reverse charge transactions, and that have a reference to the existing invoice. |
    | Accounts payable    | Advanced payment voucher | Use the **Advance payment voucher** number sequence when posting vendor advance payment transactions that have GST transactions. |
    | Accounts payable    | GST invoice              | Use the **GST invoice** number sequence when posting vendor purchases that have GST transactions together with reverse charge transactions. |

## Type of supply and GST number sequence reference ID generation

Under GST law, the broader classification of the type of supply is shown in the following list:

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

- If the tax rate isn't zero, the system picks the sequence from the GST tax invoice reference ID.
- If the tax rate is zero (tax rate in every sales order line is zero, exempt, or non-GST), the system picks the sequence from the bill of supply.
- If you mark an item as **Exempted item**, the system picks the sequence from the bill of supply, regardless of the tax rate.
- If you mark an item as **Non-GST** supply, the system applies another tax type on the transaction and picks the number sequence from the bill of supply.
- If the tax value is zero and the tax rate isn't zero, the system picks the sequence from the tax invoice reference ID. For example, if the tax rate = 0.06 and base amount = 0.02, the tax amount is rounded to 0, but the tax rate isn't zero (it's 0.06), this value isn't considered as the bill of supply. Instead, the system considers the taxable sales invoice reference ID.
- If some transaction lines are taxable and other transaction lines are exempt, the system generates a GST transaction ID for the tax invoice. This condition means that if a single item is taxable, the system generates a tax invoice ID.
- If you don't select the HSN/SAC code for any transaction line in an intra-state stock transfer, the system doesn't pick the sequence from the bill of supply or tax invoice reference ID for both the shipment and receipt.  
- If you mark the intra-state stock transfer order as exempt in the header, the system picks the number sequence from the bill of supply reference ID.
- For a stock transfer receipt transaction, the system copies the shipment transaction ID when it generates the number sequence reference ID for the shipment transaction.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
