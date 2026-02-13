---
title: Tax invoices
description: Learn how to set up and work with tax invoices for Thailand in Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/21/2025
ms.reviewer: johnmichalak

---

# Tax invoices

[!include [banner](../../includes/banner.md)]

This article explains how to set up and work with tax invoices for Thailand in Microsoft Dynamics 365 Finance.

## Preliminary setup

There are general options that must be set up before you can start to work with tax invoices.

To do preliminary setup for tax invoices, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
1. On the **Number sequences** tab, set up number sequences for the following references:
    - Free text credit note
    - Free text credit note voucher
    - Sales credit note
    - Sales credit note voucher
    - Customer invoice
    - Customer invoice voucher

Learn more in [Number sequences overview](../../../fin-ops-core/fin-ops/organization-administration/number-sequence-overview.md).

## Setup

Next, you must set up Thailand-specific options before you can start to work with tax invoices.

To set up Thailand-specific options, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
1. On the **Number sequences** tab, set up number sequences for the following references.

    | **Reference** | **Description** |
    |-------------------------|-------------------------|
    | Free text debit note | The number sequence reference for the debit notes that are generated from free text invoices. |
    | Free text debit note voucher | The number sequence reference for the debit note transactions when debit notes are generated from free text invoices. |
    | Sales debit note | The number sequence reference for the debit notes that are generated from sales orders. |
    | Sales debit note voucher | The number sequence reference for the debit note transactions when debit notes are generated from sales orders. |
    | Customer tax invoice | The number sequence reference for the tax invoices that are generated from sales order invoices. |
    | Customer tax invoice voucher | The number sequence reference for customer tax invoice vouchers. |
    | Free text tax invoice | The number sequence reference for the tax invoices that are generated from free text invoices. |
    | Free text tax invoice voucher | The number sequence reference for free text tax invoice vouchers. |
    | Receipt | The number sequence reference for receipts. |
    | Receipt / Tax invoice | The number sequence reference for receipts or tax invoices. |

1. Go to **Accounts payable** \> **Setup** \> **Accounts payable parameters**.
1. On the **Number sequences** tab, set up a number sequence for the **Vendor unrealized reversal ID** reference that you want to associate with the vendor.

## Work with tax invoices

Tax invoices are generated when value-added tax (VAT) is realized. Dynamics 365 Finance automatically generates a tax invoice when a sales order, a purchase invoice, a purchase order, or a payment that generates a realized VAT entry is posted. If an unrealized VAT entry is generated, an invoice is generated instead of a tax invoice. Learn more in [Thailand unrealized and realized VAT](apac-tha-unrealized-vat.md).

If you receive payment from the customer when you post a sales order, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable** \> **Orders** \> **All sales orders**.
1. Select **New** to create a sales order.
1. On the **Line details** FastTab, on the **Setup** tab, in the **Sales tax** section, in the **Item sales tax** **group** field, select the corresponding sales tax group for realized VAT.
1. Select **Save**.
1. On the **Invoice** FastTab, in the **Generate** section, select **Invoice**.
1. In the **Print options** section, set the **Print invoice** option to **Yes**.
1. Send the printed tax invoice to the customer.

If you receive payment from the customer when you post a free text invoice, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable** \> **Invoices** \> **All free text invoices**.
1. In the **Invoice lines** section, in the **Sales tax** and **Item sales tax** **group** fields, select the corresponding sales tax group for realized VAT.
1. On the Action Pane, select **Post** to post the invoice.
1. In the **Post free text invoice** dialog, in the **Parameters** section, set the **Print invoice** option to **Yes**.
1. Send the printed tax invoice to the customer.

At any time, you can go back to the sales order or free text invoice to print the tax invoice.

To print the tax invoice from a sales order, follow these steps:

1. In Dynamics 365 Finance, open the sales order.
1. On the **Invoice** FastTab, in the **Journals** section, select **Invoice** to open the invoice.
1. On the **Invoice** FastTab, in the **Document** section, select **View** to view the tax invoice, or **Send** to send it.

To print the tax invoice from a free text invoice, follow these steps:

1. In Dynamics 365 Finance, open the free text invoice.
1. On the **Invoice** FastTab, in the **Document** section, select **View** to view the tax invoice, or **Send** to send it.

The following illustration shows an example of a printed tax invoice.

![Table Description automatically generated.](../media/apac-tha-tax-invoices-tax-invoice.png)

If you receive payment from the customer after you post a sales order or a free text invoice, follow these steps:

1. In Dynamics 365 Finance, create a sales order.
1. On the **Line details** FastTab, on the **Setup** tab, in the **Sales tax** section, in the **Item sales tax** **group** field, select the corresponding sales tax group for unrealized VAT.
1. Generate an invoice for the order, or create a free text invoice.
1. In the **Invoice lines** section, in the **Sales tax** and **group** **Item sales tax** **group** fields, select the corresponding sales tax group for unrealized VAT.
1. Go to **Accounts receivable** \> **Payments** \> **Customer payments journal**, and settle the payment. Learn more in [Customer payment overview](../../cash-bank-management/tasks/customer-payment-overview.md).
1. Select **Print**, and then select **Payments**. A tax invoice or a receipt/tax invoice is printed.

> [!NOTE]
> - If the lines on the settled invoice for payments have a realized tax type, a receipt is printed. The receipt shows the invoice lines together with the realized tax type and the line total.
> - If multiple lines on the settled invoice have both realized and unrealized tax types, a receipt and a receipt/tax invoice are printed. The receipt/tax invoice shows the invoice lines together with the unrealized tax type and the line total.

The following illustration shows an example of a printed receipt.

![Timeline Description automatically generated with low confidence.](../media/apac-tha-tax-invoices-receipt.png)

The following illustration shows an example of a printed receipt/tax invoice.

![A picture containing graphical user interface Description automatically generated.](../media/apac-tha-tax-invoices-receipt-tax-invoice.png)




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
