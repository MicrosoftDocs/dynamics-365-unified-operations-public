---
title: Advance holder transactions
description: Learn how to work with advance holder transactions in Microsoft Dynamics 365 Finance, including an outline on creating purchase orders with advance holder details.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/06/2026
ms.reviewer: johnmichalak
ms.search.region: Czech Republic, Estonia, Hungary, Latvia, Lithuania, Poland, Russia
ms.search.validFrom: 2016-11-30
ms.search.form: HcmWorkerAdvHolderTableListPage_RU
---

# Advance holder transactions

[!include [banner](../../includes/banner.md)]

You can post transactions for workers who are advance holders by using advance holder accounts. You can track all advance holder transactions by using the worker ID specified for each advance holder. This number is retrieved as an account number for advance holder transactions in the **General journals** and **Advance holder transactions** pages.

## Create and post a purchase order with advance holder details

For more general information about purchase orders, see [Purchase order overview](../../../supply-chain/procurement/purchase-order-overview.md). If you create and post a vendor invoice with advance holder details, the advance holder’s balances are posted to the employee balance account instead of the vendor balance account. To add advance holder details to a purchase order, follow these steps:

1. In the **Terms of payment** field in the **Price and discount** section, select the payment term. <!---For more information about **Terms of payment**, see [Define vendor payment terms](../../accounts-payable/tasks/define-vendor-payment-terms.md).--> Select a payment term that has the **From advance holder** option selected on the **Terms of payment** page. For more information about setting up terms of payment for advance holders, see [Advance holders overview](emea-advance-holders.md).
1. In the **Advance holder** field on the **Price and discount** FastTab, select the advance holder for the purchase order.

The purchase order posting process creates two vendor transactions with opposite amounts and one advance holder transaction. Without advance holder details, it creates only one vendor transaction.

## Settle advance holder balances via a bank

When you settle advance holder balances via a bank, you create journal entries for closing the advance holder balances in the general journal. You can set up the code for the journal and the bank in the **Advance holders** section on the **Accounts payable parameters** page. For more information, see [Advance holders overview](emea-advance-holders.md). To close an advance holder’s balance via a bank, open **Accounts payable** &gt; **Advance holders** &gt; **Advance holders**. Select the **Balance** button on the action pane, and then select **Close via bank**. Enter the following information on the **Close via bank** page.

| Field                    | Description |
|------------------------------|-------------------|
| **Date of payment**          | Enter the date that the payment should be posted.|
| **Amount to be transferred** | Enter the balance amount while closing. The amount that is indicated in the **Amount** field in the **Balance** form is displayed by default. |
| **Automatic**                | Select the **Automatic** check box to create and post a journal that is preset on the **Accounts payable parameters** page.|

## Settle advance holder balances via cash

When you settle advance holder balances via cash, you create journal entries for closing the advance holder balances in a slip journal. You can set up the code for the journal and the cash in the **Advance holders** tab on the **Accounts payable parameters** page. For more information, see [Advance holders overview](emea-advance-holders.md). To close an advance holder’s balance via cash, open **Accounts payable** > **Advance holders** > **Advance holders**. Select the **Balance** button on the Action Pane, and then select **Close via cash**. Enter the following information on the **Close via cash** page.

| Field                    | Description
|------------------------------|-----------------|
| **Date of payment**          | Enter the date that the payment should be posted.|
| **Amount to be transferred** | Enter the balance amount while closing. The amount that is indicated in the **Amount** field in the **Balance** form is displayed by default. |
| **Automatic**                | Select the **Automatic** check box to create and post automatically a journal that is preset on the **Accounts payable parameters** page.     |

After the slip journal is processed, if the amount in the **Amount to be transferred** field is negative, the system generates a disbursement slip for the advance holder when you close the balances. If the amount in the **Amount to be transferred** field is positive, the system generates a reimbursement slip.

## Additional resources

[Advance payment to an employee (Eastern Europe)](advance-payment-employee.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
