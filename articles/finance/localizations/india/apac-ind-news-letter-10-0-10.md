---
title: What's new or changed for India GST in 10.0.10 (May 2020)
description: Learn about new or changed functionality for India GST features released in Dynamics 365 Finance version 10.0.10, including outlines on new features.
author: prabhatb
ms.author: johnmichalak
ms.topic: whats-new
ms.custom:
  - bap-template
  - evergreen
ms.date: 01/21/2026
ms.update-cycle: 1095-days
ms.reviewer: johnmichalak
ms.search.region: India

---

# What's new or changed for India GST in 10.0.10 (May 2020)

[!include [banner](../../includes/banner.md)]

This article summarizes the new features and critical bug fixes released in Dynamics 365 Finance version 10.0.10 for India GST localization.

## New features

### Import order over delivery

Previously, you couldn't adjust import order quantities on the **Invoice registration** page. This limitation meant that customers couldn't accept a delivery of more items than what was originally ordered. By using this new feature, you can update the invoice registration quantity to match the over delivery quantity. Complete the following steps to set up accepting over delivery.

1. Go to **Procurement and sourcing** > **Setup** > **Procurement and sourcing parameters**.
1. On the **Deliver** tab, set **Accept delivery** to **Yes**, and then select **Save**.

Complete the following steps to update the over delivery quantity.

1. On the **Invoice registration** page, in the **Overview** pane, in the **Import invoice number** field, select the invoice you want to update.
1. In the **Lines** pane, in the **Receive** field, update the quantity.

:::image type="content" source="../media/GST-over-delivery-1-10-0-10.PNG" alt-text="Screenshot of Invoice registration page.":::

### TDS on foreign vendor transactions

TDS on a foreign vendor invoice causes a voucher imbalance error because the transactions on the voucher don't balance.
According to rule 26 of the Income Tax Act, you convert TDS on a foreign currency transaction at the TTR buying rate instead of the normal GAP rate.

**TDS on transaction in foreign currency**

- Main transaction uses the GAP rate or a manually updated exchange rate
- TDS on transaction follows the TDS exchange rate

Set up the **TDS exchange rate** as **TDS** and the **Accounting currency exchange rate type** as **Default** on the **Ledger** page.

:::image type="content" source="../media/GST-tds-exchange-rate-2-10-0-10.png" alt-text="Screenshot of Ledger page showing Currency FastTab.":::

**Accounting entries**

| Description                | Dr. (US$)     | Dr. (INR)          | Cr. (US$)                | Cr. (INR)                                        |
|----------------------------|--------------|-------------------|-------------------------|-------------------------------------------------|
|     Service/lease exp.    |     100      |     GAP rate      |                         |                                                 |
|     CGST                   |        9     |      GAP rate     |                         |                                                 |
|     SGST                   |        9     |      GAP rate     |                         |                                                 |
|     Vendor                 |              |                   |     108     (118-10)    |     (118@GAP rate - 10@TDS exchange rate)    |
|     TDS payable            |              |                   |     10                  |     TDS exchange rate                           |
|     Total                  |     118      |                   |     118                 |                                                 |

## Critical fixes

- Enable date time tracking for the **Tax run time lookup condition** table.
- Transaction type doesn't show when you post the **Tax journal**.
- Can't generate a recurring free text invoice by using the **Free text invoice template**.
- There's a difference between the sales tax payment and the actual transaction posted to tax authorities. This fix ensures
  that the sales tax settlement amount and the actual amount posted to the tax authority match.
- **Adjusted amount origin** field shows an incorrect value. The system picks the adjusted base amount posted in the
   initial transaction and uses that same amount for subsequent transactions.
- Tax calculation appears incorrect when you apply a discount through the **General Journal** in multline transactions.
   This problem happens with the discount ledger account for debit or credit. Two scenarios include:

  - Creating a credit note for a customer (GST calculates negative value for discount).
  - Creating an invoice/debit note for a customer (GST calculates positive value for discount).

## Upcoming fixes in 10.0.11

- When a vendor record is created with multiple sub-vendors, the main supplier name and address are displayed in GSTR-2,
    which is not the information selected on the **Tax information** tab during posting.
- The **Withholding tax journal** is created to adjust the withholding tax (TDS) amount and select the voucher transaction
    for adjustment. An error occurs when the journal is posted and the transaction has been selected and transferred to
    the **General journal**.
- Warning message is displayed when you define a charge code with the posting type of **Ledger** and an item combination
    on the transaction.
- A system error occurs while running withholding (TDS) tax payment.
- Incorrect tax information is created from sales agreement and pushed to the sales order. Specifically,
    the **Address** field displays the address of the legal entity instead of the warehouse address.
- When you post a free text invoice with GST tax and you selected to round off when setting up currencies, the system is
    not rounding the invoice amount for the customer sub-ledger account, but is rounding off correctly in the customer
    main ledger for the voucher.
- The TDS section code and invoice number are not appearing in TDS inquiries.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
