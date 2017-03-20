---
# required metadata

title: Advance holder transactions
description: Learn how to work with advance holder transactions in Microsoft Dynamics 365 for Operations.
author: ShylaThompson
manager: AnnBe
ms.date: 2016-12-12 21 - 45 - 33
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: HcmWorkerAdvHolderTableListPage_RU
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 81
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 262554
ms.assetid: 84ff97bb-ae21-4d6d-8160-9325f64134ce
ms.search.region: Czech Republic, Estonia, Hungary, Latvia, Lithuania, Poland, Russia
# ms.search.industry: 
ms.author: v-elgolu
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Advance holder transactions

Learn how to work with advance holder transactions in Microsoft Dynamics 365 for Operations.

Transactions for these workers who are advance holders can be posted by using advance holder accounts. The worker ID that is specified for each advance holder can be used to track all advance holder transactions. This number is retrieved as an account number for advance holder transactions in the **General journals** and **Advance holder transactions** pages.

## Create and post a purchase order with advance holder details
For more general information about purchase orders, see [Purchase order overview](/manufacturing/procurement-sourcing/purchase-order-overview). If a vendor invoice is created and posted with advance holder details, the advance holder’s balances will be posted to the employee balance account instead of the vendor balance account. To add advance holder details to a purchase order, do the following:

-   In the **Terms of payment** field in the **Price and discount** section, select the payment term. <!---For more information about **Terms of payment**, see [Define vendor payment terms](http://ax.help.dynamics.com/en/wiki/define-vendor-payment-terms/).--> Select a payment term that has the **From advance holder** option selected on the **Terms of payment** page. For more information about setting up terms of payment for advance holders, see [Advance holders](advance-holders.md).
-   In the **Advance holder** field on the **Price and discount** FastTab, select the advance holder for the purchase order.

The purchase order posting process creates two vendor transactions with opposite amounts and one advance holder transaction. Without advance holder details, only one vendor transaction is created.

## Settle advance holder balances via a bank
When you settle advance holder balances via a bank, journal entries for closing the advance holder balances are created in the general journal. You can set up the code for the journal and the bank in the **Advance holders** section on the **Accounts payable parameters** page. For more information, see [Advance holders](advance-holders.md). To close an advance holder’s balance via a bank, open **Accounts payable** &gt; **Advance holders** &gt; **Advance holders**. Click the **Balance** button on the Action Pane, and then click **Close via bank**. Enter the following information on the **Close via bank** page.

| Field                    | Description |
|------------------------------|-------------------|
| **Date of payment**          | Enter the date that the payment should be posted.|
| **Amount to be transferred** | Enter the balance amount while closing. The amount that is indicated in the **Amount** field in the **Balance** form is displayed by default. |
| **Automatic**                | Select the **Automatic** check box to create and post a journal that is preset on the **Accounts payable parameters** page.|

## Settle advance holder balances via cash
When you settle advance holder balances via cash, journal entries for closing the advance holder balances are created in a slip journal. You can set up the code for the journal and the cash in the **Advance holders** tab on the **Accounts payable parameters** page. For more information, see [Advance holders](advance-holders.md). To close an advance holder’s balance via cash, open **Accounts payable** &gt; **Advance holders** &gt; **Advance holders**. Click the **Balance** button on the Action Pane, and then click **Close via cash**. Enter the following information on the **Close via cash** page.

| Field                    | Description
|------------------------------|-----------------|
| **Date of payment**          | Enter the date that the payment should be posted.|
| **Amount to be transferred** | Enter the balance amount while closing. The amount that is indicated in the **Amount** field in the **Balance** form is displayed by default. |
| **Automatic**                | Select the **Automatic** check box to create and post automatically a journal that is preset on the **Accounts payable parameters** page.     |

After the slip journal is processed, if the amount in the **Amount to be transferred** field was negative, a disbursement slip is generated for the advance holder when the balances are closed. If the amount in the **Amount to be transferred** field was positive, a reimbursement slip is generated.

