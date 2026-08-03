---
title: Prepayment invoices vs. prepayments
description: Learn about the definition and the contracts between the two methods that organizations can use for advance payments (prepayments).
author: twheeloc
ms.author: shpandey
ms.topic: article
ms.date: 07/28/2026
ms.update-cycle: 1095-days
ms.custom: evergreen
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: LedgerJournalTransVendPaym, PurchTable
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: a0bb5220-73d4-48ae-84d0-46a171c224fa
---

# Prepayment invoices vs. prepayments

[!include [banner](../includes/banner.md)]

This article describes and contrasts two methods that organizations can use for advance payments (prepayments). One method creates a prepayment invoice that's associated with a purchase order. The other method creates prepayment journal vouchers by creating journal entries and marking them as prepayment journal vouchers.

Organizations might issue prepayments (advance payments) to vendors for goods or services before those goods or services are fulfilled. Two methods can be used to issue prepayments to vendors. To minimize risk, track prepayments by defining the prepayment on a purchase order. For this method, you must create a prepayment invoice that is associated with a purchase order. This method is referred to as prepayment invoicing. Organizations that don't want to track prepayments as closely or don't receive a prepayment invoice from their vendor can use prepayment journal vouchers instead of the prepayment invoicing method. You can create prepayment journal vouchers by creating journal entries and marking them as prepayment journal vouchers. For this method, you can't track which prepayments to a vendor are made against which purchase orders. However, you can mark a posted prepayment for settlement against a purchase order.

## When to use prepayment invoicing vs. prepayments

| Prepayment invoicing                   | Prepayments                                                              |
|------------------------|--------------------------------------------------------------------------|
| Define a prepayment value on the purchase order.  | No prepayment value is defined on the purchase order.                    |
| Post a prepayment invoice and a final invoice. | No prepayment invoice is required.                      |
| The prepayment account holds liability for the prepayment, not the Accounts payable account. | The Accounts payable account holds liability for the prepayment.                  |
| The vendor balance doesn’t reflect the prepayment value throughout the process. | The vendor balance reflects the prepayment value throughout the process. |
| Accounts payable only provides prepayment invoicing. | Accounts payable and Accounts receivable provide prepayments. |

## Overview of the prepayment process

Accounting practices in many countries/regions require that prepayments from a customer or to a vendor not be posted to the usual summary accounts for the customer or vendor. Instead, these prepayments are posted to special ledger accounts for prepayments. When a sales order or purchase order is created, an invoice is issued to the customer or from the vendor. When the invoice is paid, the prepayment and sales tax prepayment voucher on the prepayment ledger accounts are reversed, and the invoice amounts are automatically posted to the usual summary accounts.
To create a prepayment, follow these steps:

1. Set up a posting profile for prepayments.
1. Go to the **Accounts receivable parameters** and **Accounts payable parameters** pages. Under **Ledger and sales tax**, select the new posting profile by using the **Posting profile for payment journal with prepayment** parameter.
1. Create a payment journal, and then create the new payment.
1. Flag the payment as a prepayment. If you flag a payment as a prepayment, you post the payment to the ledger accounts that you define on the posting profile that you set up in steps 1 and 2. Additionally, if you flag the payment as a prepayment, the system calculates taxes. Some governments require that you pay taxes when you record a prepayment, even if there isn't an invoice.
1. Post the prepayment.
1. (Optional) Settle the prepayment against the purchase order or sales order before you create the invoice. On the sales order or purchase order page, on the Action Pane, use **Settle transactions**.
1. After the vendor delivers the goods or services, record the invoice. If you settled the prepayment against the purchase order or sale order in a previous step, the prepayment is automatically settled against the invoice that you created. If you didn't settle the prepayment against the purchase order or sales order, you can manually settle it against the invoice by using **Settle transactions** on the customer or vendor page. The prepayment amount is then reversed out of the temporarily AP/AR ledger account. Additionally, if taxes were calculated, they're reversed, because the invoice has the actual taxes.

## Overview of the prepayment invoicing process

Prepayment invoices are a common business practice. A vendor issues prepayment invoices to require a deposit on the purchase before the purchase order fulfills. For example, some vendors require a prepayment for custom goods or services. If a vendor issues an invoice that requests prepayment, you can use the prepayment invoicing feature. You can define a prepayment value on the purchase order, record and pay a prepayment invoice, and then apply the prepayment invoice to the final invoice. Follow these steps to create a prepayment.

1. The purchasing agent creates, confirms, and then submits a purchase order that the vendor requested prepayment for. The prepayment value is defined on the purchase order as part of the agreement.
1. The vendor submits a prepayment invoice.
1. The Accounts payable coordinator records the prepayment invoice against the purchase order, and then pays the prepayment invoice.
1. The vendor sends a request for payment, referred to as a standard vendor invoice. After the vendor delivers the goods or services, and the related standard vendor invoices are received, the Accounts payable coordinator applies the prepayment amount that was already paid against the standard invoice.
1. The Accounts payable coordinator pays and settles the remaining amount of the standard invoice.

## Set up parameters to enable the prepayment invoicing process

Define a prepayment account on the **Purchase order** tab of the **Inventory posting** page (**Inventory management \> Setup \> Posting \> Posting**). The prepayment account is usually debited when you post the prepayment invoice. Reverse the balance in the prepayment account when you post the standard invoice that applies to the prepayment invoice. If you don't settle the prepayment invoice to a payment before applying the prepayment invoice to the standard invoice, the accounting entries from the posted prepayment invoice are reversed when you post the standard invoice.

Define the offsetting summary accounts payable account on the **Vendor posting** profile. To define the default posting profile, go to **Accounts payable \>Setup \> Accounts payable parameters \>Ledger and sales tax tab \> Posting profile with prepayment vendor invoice**.

The **Prepayment application policy** indicates whether settled prepayment invoices are automatically applied to the final invoice that you created manually. Invoices that are created using a data entity don't refer to the **Prepayment application policy**. You need to manually apply settled prepayment invoices to invoices that were created using a data entity. To define the policy, go to **Accounts payable \>Setup \> Accounts payable parameters \> Ledger and sales tax tab \> Prepayment application policy**. If you set the **Prepayment application policy** field to **Automatic**, the prepayment invoice is  automatically marked for settlement with the final invoice. If you set the field to **Notification**, a visual indication that a prepayment invoice is available for application displays when the final invoice is created.

## Create a purchase order that contains prepayment invoice information

When a vendor tells you that they require prepayment for goods and services contained on a purchase order, define the prepayment value for the associated purchase order. Go to **Accounts payable \> Common \> Purchase orders \> All purchase orders** and find the vendor’s purchase order. On the Action pane, select the **Purchase** tab, and then select **Prepayment**. Enter information for the prepayment, including a description, the value of the prepayment, whether the prepayment is a fixed amount or a percentage, and a prepayment category ID.

> [!NOTE]
> You can't define multiple prepayments on a purchase order. If you need to allow multiple prepayments on a purchase order, post the payments by using the payment journal instead of a prepayment invoice.

You can remove the prepayment from the purchase order unless you already settled a payment against the posted prepayment invoice or posted the standard invoice. To remove prepayment information from the purchase order, go to **Accounts payable \> Common \> Purchase orders \> All purchase orders** and find the vendor’s purchase order. On the Action Pane, select the **Purchase** tab, and then select **Remove prepayment**.

## Create and post a prepayment invoice

To record the vendor’s prepayment invoice, go to the **Vendor invoice** page. Select **Prepayment invoice** on the **Purchase orders** page (**Accounts payable \> Common \> Purchase orders \> All purchase orders \> Invoice tab \> Prepayment invoice**). Enter information for the prepayment invoice, including the invoice number. You can't change quantities for a prepayment invoice. If the vendor invoices a partial amount of the prepayment value that's defined on the purchase order, update the unit price to reflect the partial value.

When you post the prepayment invoice, the vendor balance and prepayment account are updated. The **Prepayment application** value on the prepayment definition contained on the purchase order is updated. The default financial dimension entries for the posted prepayment voucher are taken from the header information on the purchase order.

If you turn on the **Lock financial dimensions on invoice lines on vendor prepayment invoice** feature on the **Feature management** page, you can't update the dimensions in the prepayment header or lines.

## Post and settle payments for the prepayment invoice

Next, pay the prepayment invoice from the **Payment journal** page. To access payment journals, select **Accounts payable > Journals > Payments > Payment journal**. After you post the settlement of the payment to the prepayment invoice, the purchase order’s **Prepayment application remaining** value updates.

Before you post the standard invoice for the prepayment invoice, you can reverse the settlement of the payment from the prepayment invoice. However, after you apply a standard invoice to the prepayment invoice, you can't reverse the payment settlement from the prepayment invoice.

## Post the standard vendor invoice for the purchase order and apply the prepayment invoice to the standard invoice

Record the standard invoice received from the vendor. As part of this process, you can apply the settled prepayment invoice to the vendor invoice so that the value of the invoice is reduced by the amount that's already paid. When you apply the prepayment invoice to the vendor invoice, you reverse the accounting entries from the prepayment invoice.

## Application of the prepayment invoice after posting the standard invoice

If you forget to apply the prepayment to the standard vendor invoice at the time of posting the vendor invoice, you can apply the settled prepayment to other invoices from this vendor from the **Vendors** page (**Accounts payable > Common > Vendors > All vendors > Invoice tab > Apply**).

## Reversal of the prepayment application process

If you need to unsettle or reverse the application of a prepayment invoice from a standard invoice, select the **Reverse** action from the **Vendors** page (**Accounts payable > Common > Vendors > All vendors > Invoice tab > Reverse**). After you reverse the prepayment application, you can apply the prepayment to another standard invoice.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
