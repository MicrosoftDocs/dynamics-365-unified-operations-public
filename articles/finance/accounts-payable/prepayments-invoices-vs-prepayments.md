---
# required metadata

title: Prepayment invoices vs. prepayments
description: This article describes and contrasts the two methods that organizations can use for advance payments (prepayments). 
author: abruer
ms.date: 10/24/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LedgerJournalTransVendPaym, PurchTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: a0bb5220-73d4-48ae-84d0-46a171c224fa
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Prepayment invoices vs. prepayments

[!include [banner](../includes/banner.md)]

This article describes and contrasts the two methods that organizations can use for advance payments (prepayments). One method creates a prepayment invoice that's associated with a purchase order. The other method creates prepayment journal vouchers by creating journal entries and marking them as prepayment journal vouchers.

Organizations might issue prepayments (advance payments) to vendors for goods or services before those goods or services are fulfilled. Two methods can be used to issue prepayments to vendors. To minimize risk, you can track prepayments by defining the prepayment on a purchase order. For this method, you must create a prepayment invoice that is associated with a purchase order. This method is referred to as prepayment invoicing. Organizations that don't want to track prepayments as closely or don't receive a prepayment invoice from their vendor can use prepayment journal vouchers instead of the prepayment invoicing method. You can create prepayment journal vouchers by creating journal entries and marking them as prepayment journal vouchers. For this method, you can't track which prepayments to a vendor are made against which purchase orders. However, you can mark a posted prepayment for settlement against a purchase order.

## When to use prepayment invoicing vs. prepayments

| Prepayment invoicing                                                                | Prepayments                                                              |
|-------------------------------------------------------------------------------------|--------------------------------------------------------------------------|
| Define a prepayment value on the purchase order.                                    | No prepayment value is defined on the purchase order.                    |
| A prepayment invoice and a final invoice must be posted.                       | No prepayment invoice must be posted.                                    |
| Liability for the prepayment is held in the prepayment account, not the AP account. | Liability for the prepayment is held in the AP account.                  |
| The vendor balance doesn’t reflect the prepayment value throughout the process.     | The vendor balance reflects the prepayment value throughout the process. |
| Prepayment invoicing is available in Accounts payable only.                         | Prepayments are available in Account payable and Accounts receivable.    |

## Overview of the prepayment process
Accounting practices in many countries/regions require that prepayments from a customer or to a vendor not be posted to the usual summary accounts for the customer or vendor. Instead, these prepayments are posted to special ledger accounts for prepayments. When a sales order or purchase order is created, an invoice is issued to the customer or from the vendor. When the invoice is paid, the prepayment and sales tax prepayment voucher on the prepayment ledger accounts are reversed, and the invoice amounts are automatically posted to the usual summary accounts. Follow these steps to create a prepayment.

1.  Set up a posting profiles for prepayments.
2.  In Accounts receivable parameters and Accounts payable parameters, under **Ledger and sales tax**, select the new posting profile by using the **Posting profile for payment journal with prepayment** parameter.
3.  Create a payment journal, and then create the new payment.
4.  You can flag the payment as a prepayment. If a payment is flagged as a prepayment, the payment is posted to the ledger accounts that are defined on the posting profile that you set up in steps 1 and 2. Additionally, if the payment is flagged as a prepayment, taxes are calculated. Some government require that taxes be paid when a prepayment is recorded, even if there isn't an invoice.
5.  Post the prepayment.
6.  Optional: You can settle the prepayment against the purchase order or sales order before you create the invoice. On the sales order or purchase order page, on the Action Pane, use **Settle transactions**.
7.  After the vendor delivers the goods or services, record the invoice. If you settled the prepayment against the purchase order or sale order in step 6, the prepayment is automatically settled against the invoice that you created. If you didn't settle the prepayment against the purchase order or sales order, you can manually settle it against the invoice by using **Settle transactions** on the customer or vendor page. The prepayment amount is then reversed out of the temporarily AP/AR ledger account. Additionally, if taxes were calculated, they are reversed, because the invoice has the actual taxes.

## Overview of the prepayment invoicing process
Prepayment invoices are a common business practice. A vendor issues prepayment invoices to require a deposit on the purchase before the purchase order is fulfilled. For example, some vendors require a prepayment for custom goods or services. If a vendor issues an invoice that requests prepayment, you can use the prepayment invoicing feature. A prepayment value can be defined on the purchase order, a prepayment invoice is recorded and paid, and then the prepayment invoice is applied to the final invoice. Follow these steps to create a prepayment.

1.  The purchasing agent creates, confirms, and then submits a purchase order that the vendor has requested prepayment for. The prepayment value is defined on the purchase order as part of the agreement.
2.  The vendor submits a prepayment invoice.
3.  The Accounts payable coordinator records the prepayment invoice against the purchase order, and then the prepayment invoice is paid.
4.  The vendor sends a request for payment, referred to as a standard vendor invoice. After the vendor delivers the goods or services, and the related standard vendor invoices have been received, the Accounts payable coordinator applies the prepayment amount that was already paid against the standard invoice.
5.  The Accounts payable coordinator pays and settles the remaining amount of the standard invoice.

## Set up parameters to enable the prepayment invoicing process
A prepayment account must be defined on the **Purchase order** tab of the **Inventory posting** page (**Inventory management \> Setup \> Posting \> Posting**). The prepayment account will be updated, usually debited, when the prepayment invoice is posted. The balance in the prepayment account will be reversed when the standard invoice that's applied to the prepayment invoice is posted. If you do not settle the prepayment invoice to a payment prior to applying the prepayment invoice to the standard invoice, the accounting entries from the posted prepayment invoice will be reversed when the standard invoice is posted.

The offsetting summary accounts payable account is defined on the **Vendor posting** profile. To define the default posting profile, click **Accounts payable \>Setup \> Accounts payable parameters \>Ledger and sales tax tab \> Posting profile with prepayment vendor invoice**.

The **Prepayment application policy** indicates whether settled prepayment invoices will be automatically applied to the final invoice that was created manually. Invoices that are created using a data entity won't refer to the **Prepayment application policy**. You will need to manually apply settled prepayment invoices to invoices that were created using a data entity. To define the policy, go to **Accounts payable \>Setup \> Accounts payable parameters \> Ledger and sales tax tab \> Prepayment application policy**. If the **Prepayment application policy** field is set to **Automatic**, the prepayment invoice will be automatically marked for settlement with the final invoice. If the field is set to **Notification**, a visual indication that a prepayment invoice is available for application will display when the final invoice is created.

## Create a purchase order that contains prepayment invoice information
When a vendor tells you that they require prepayment for goods and services contained on a purchase order, you must define the prepayment value for the associated purchase order. Go to **Accounts payable \> Common \> Purchase orders \> All purchase orders** and find the vendor’s purchase order. On the Action pane, select the **Purchase** tab, and then select **Prepayment**. Enter information for the prepayment, including a description, the value of the prepayment, whether the prepayment is a fixed amount or a percentage, and a prepayment category ID. 

> [!Note] 
> Multiple prepayments definitions on a purchase order are not allowed. If you need to allow multiple prepayments on a purchase order, post the payments using the payment journal instead of a prepayment invoice.

The prepayment may be removed from the purchase order unless you have already settled a payment against the posted prepayment invoice or posted the standard invoice. To remove a prepayment information from the purchase order, select **Accounts payable \> Common \> Purchase orders \> All purchase orders** and find the vendor’s purchase order. On the Action Pane, select the **Purchase** tab, and then select **Remove prepayment**.

## Create and post a prepayment invoice
To record the vendor’s prepayment invoice, go to the **Vendor invoice** page by selecting the **Prepayment invoice** option on the **Purchase orders** page (**Accounts payable \> Common \> Purchase orders \> All purchase orders \> Invoice tab \> Prepayment invoice**). Enter information for the prepayment invoice, including the invoice number. You cannot change quantities for a prepayment invoice. If the vendor has invoiced a partial amount of the prepayment value that's defined on the purchase order, you can update the unit price to reflect the partial value.

When the prepayment invoice is posted, the vendor balance and prepayment account will be updated. The **Prepayment application** value on the prepayment definition contained on the purchase order will also be updated. The default financial dimension entries for the posted prepayment voucher will be taken from the header information on the purchase order.

If the **Lock financial dimensions on invoice lines on vendor prepayment invoice** feature on the **Feature management** page is turned on, the dimensions in the prepayment header or lines can't be updated. 

## Post and settle payments for the prepayment invoice
Next, the prepayment invoice will be paid from the **Payment journal** page. To access payment journals, click **Accounts payable \> Journals \> Payments \> Payment journal**. After posting the settlement of the payment to the prepayment invoice, the purchase order’s **Prepayment application remaining** value will be updated.

Before posting the standard invoice for the prepayment invoice, you can reverse the settlement of the payment from the prepayment invoice. However, after a standard invoice is applied to the prepayment invoice, the payment settlement can't be reversed from the prepayment invoice.

## Post the standard vendor invoice for the purchase order and apply the prepayment invoice to the standard invoice
Record the standard invoice received from the vendor. As part of this process, you can apply the settled prepayment invoice to the vendor invoice so that the value of the invoice is reduced by the amount that's already been paid. Applying the prepayment invoice to the vendor invoice will ensure that accounting entries from the prepayment invoice will be reversed.

## Application of the prepayment invoice after posting the standard invoice
If you forget to apply the prepayment to the standard vendor invoice at the time of posting the vendor invoice, the settled prepayment will be available to apply to other invoices from this vendor from the **Vendors** page (**Accounts payable \> Common \> Vendors \> All vendors \> Invoice tab \> Apply**).

## Reversal of the prepayment application process
If you need to unsettle or reverse the application of a prepayment invoice from a standard invoice, select the **Reverse** action from the **Vendors** page (**Accounts payable \> Common \> Vendors \> All vendors \> Invoice tab \> Reverse**). After the prepayment application is reversed, you can apply the prepayment to another standard invoice. 



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
