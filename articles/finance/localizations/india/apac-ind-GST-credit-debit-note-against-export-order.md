---
title: Credit or debit note against an export order
description: Learn about how to post a credit note against an export invoice in Microsoft Dynamics 365 transactions and set up a credit or debit note against an export invoice.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/30/2026
ms.reviewer: johnmichalak
ms.search.region: India
ms.search.validFrom: 2020-09-01
ms.dyn365.ops.version: 10.0.13
---

# Credit or debit note against an export order

[!include [banner](../../includes/banner.md)]

Currently, you can't post credit notes and debit notes against an export invoice that you already posted. However, this feature lets you post credit notes against an export order, similarly to the way that you post a sales order.

According to the proposed new Goods and Services Tax Return (GSTR), ANX-1 inserts information that relates to credit and debit notes that you issue against an export order.

When you post a credit note or a debit note against an export order that already has a posted shipping bill, it shows the following information:

- Shipping bill number
- Shipping bill date

When you post the credit or debit note, these fields are automatically set, based on the posted export order.

You can post export orders in the following ways:

- Export that includes payment of tax
- Export that excludes payment of tax

If you post the credit or debit note against an export invoice, the same options are available:

- If you post the export order with payment of tax, the **With the payment of Tax** field for the credit note is set to **Yes** by default.
- If you post the export order without payment of tax, the **With the payment of Tax** field for the credit note is set to **No** by default.

If you post the credit or debit note against an export order that you posted with payment of tax, the **Would you claim refund?** field is also available, and you can set it to **Yes** or **No**.

When you create a credit note against a posted export order, the same field is available in the credit note.

To post a credit or debit note against an export order, use the following three transaction types:

- Export order invoice
- Free text invoice with a negative value
- General journal

## Set up a credit or debit note against an export invoice

### Turn on the feature in Feature management

1. Go to **Workspaces > Feature management**.
1. In the list, find and select the feature named **(India) Enable Credit/Debit note against an export invoice**, and then select **Enable**.

:::image type="content" source="../media/Credit-Debit-note-EO-001.PNG" alt-text="Screenshot of the Feature management workspace.":::

### Set up a number sequence in the GST reference number sequence group

To maintain a Goods and Services Tax (GST) transaction ID for credit notes against an export invoice, set up a number sequence in the GST reference number sequence group.

- Go to **Tax > Setup > GST reference number sequence group**.

:::image type="content" source="../media/Credit-Debit-note-EO-002.PNG" alt-text="Screenshot of the GST reference number sequence group page.":::

## Post transactions

This section shows how to post a credit note that has a GST payment by using an export sales order.

When you post a credit note against a posted export invoice, the value of the **With payment of tax** field in the export invoice defaults to the **Tax information** page. If you set the **With payment of tax** option to **Yes**, the **Would you claim refund?** field appears.

By default, if you set the **Would you claim refund?** field in the posted export invoice to **Yes**, the **Would you claim refund?** field in the credit note is set to **Yes**. Otherwise, the field in the credit note is set to **No**.

For example, you create a credit note for five items that has the following information:

- Export order line
- In the originally posted export order, the following values are set:

    - **With payment of tax** = **Yes**
    - **Would you claim refund?** = **Yes**

| Item | Qty | Unit  | Net amt. | Tax group | IGST     | Tax rate |
|------|-----|-------|----------|-----------|----------|----------|
| A    | 5   | 1,000 | 5,000    | Cust1     | IGST @10 | 10       |

The cost of the item is 4,000.

The following tables show how the export invoice is posted.

**IGST calculation**
 
| Sales value | GST @10% |
|-------------|----------|
| 5,000       | 500      |

**Voucher transaction**

| Account              | Debit | Credit |
|----------------------|-------|--------|
| Customer1            | 5,000 |        |
| IGST Payable         |       | 500    |
| Export order revenue |       | 5,000  |
| Refundable account   | 500   |        | 

**Result when you post the credit note against the posted export invoice**

| Account                               | Debit | Credit |
|---------------------------------------|-------|--------|
| Export order revenue                  | 5,000 |        |
| Customer `                            |       | 5,000  |
| IGST Payable                          | 500   |        |
| Refundable account                    |       | 500    |
| Export Inventory issue (cost of item) |       | 4,000  |
| Sale of goods (cost of item)          | 4,000 |        |

When you post the export order, the following values are set:

- **With payment of tax** = **Yes**
- **Would you claim refund?** = **Yes**

The following tables show how the export invoice is posted.

**Voucher transaction**

| Account              | Debit | Credit |
|----------------------|-------|--------|
| Customer1            | 5,000 |        |
| IGST Payable         |       | 500    |
| Export order revenue |       | 5,000  |
| Export Expenses      | 500   |        |

**Result when you post the credit note against the posted export invoice**

| Account                               | Debit | Credit |
|---------------------------------------|-------|--------|
| Export order revenue                  | 5,000 |        |
| Customer `                            |       | 5,000  |
| IGST Payable                          | 500   |        |
| Export Expenses                       |       | 500    |
| Export Inventory issue (cost of item) |       | 4,000  |
| Sale of goods (cost of item)          | 4,000 |        |

If you review the header information on the **Tax document** page for the credit note, you see the original export invoice ID, and the shipping bill number and shipping bill date.

:::image type="content" source="../media/Credit-Debit-note-EO-003.PNG" alt-text="Screenshot of the Tax document page.":::

After you post the credit note against the export invoice, you can run the monthly ANX-1 offline tool to view the credit note transaction. Go to **Tax \> Inquiries and reports \> Tax reports \> ANX-1 report**. The following illustration shows an example of an ANX-1 report where a credit/debit note was posted against an export invoice.

:::image type="content" source="../media/Credit-Debit-note-EO-005.PNG" alt-text="Screenshot of the ANX-1 report.":::

You can also view a credit/debit note that you issue against an export order in the new GSTR-1 report. The following illustration shows an example of a GSTR-1 report where a credit/debit note was posted against an export invoice.

:::image type="content" source="../media/Credit-Debit-note-EO-004.PNG" alt-text="Screenshot of the new GSTR-1 report.":::
