---
# required metadata

title: View transactions on settlement for Eastern Europe
description: This topic provides information about the Transactions on settlement page for customers and vendors.
author: ShylaThompson
manager: AnnBe
ms.date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: CustVendTransPostingLog_RU
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 81
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 270544
ms.assetid: 3d0de195-183b-4b0c-b432-074b411200e2
ms.search.region: Czech Republic, Estonia, Hungary, Latvia, Lithuania, Poland
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# View transactions on settlement for Eastern Europe

This topic provides information about the Transactions on settlement page for customers and vendors.

Use the **Transactions on settlement** page to view information about complex settlement transactions for a customer or a vendor. This feature is available only for legal entities that have their primary address in Lithuania, Latvia, Estonia, Czech Republic, Hungary, or Poland. You can find the **Transactions on settlement** page at the following locations:

-   **Accounts payable** &gt; **Vendors** &gt; **All vendors**. On the Action Pane, on the **Vendor** tab, click **Transactions** &gt; **Transactions**. On the **Vendor transactions** page, select a transaction, and then click **Transactions on settlement**.
-   **Accounts receivable** &gt; **Customers** &gt; **All customers**. On the Action Pane, on the **Customer** tab, click **Transactions**. On the **Customer transactions** page, select a transaction, and then click **Transactions on settlement**.

Settlement-related information is captured and can be shown on the **Transactions on settlement** page for transactions that were created in the following scenarios:

-   **Exchange adjustment** – Settlement of an invoice and a payment generates a realized or unrealized exchange rate difference.
-   **Posting profile change** – Two entries, such as an invoice and a credit memo, that have different posting profiles are settled.
-   A prepayment is converted to a payment, or a payment is converted to a prepayment.
-   **Cash discount** – An invoice is settled with a payment that a discount amount has been deducted from.
-   **Penny difference** – An invoice is settled with a payment that has a slightly different amount than the invoice.
-   **Conditional tax posting** – An invoice is settled with a payment that conditional tax has been applied to.
-   **Cross-company settlement** – Intercompany functionality is used to settle an invoice with a payment from an organization.


