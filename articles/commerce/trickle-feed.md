---
title: Trickle feed-based order creation for retail store transactions
description: Learn about trickle feed-based order creation for store transactions in Microsoft Dynamics 365 Commerce.
author: analpert
ms.date: 12/30/2025
ms.update-cycle: 1095-days
ms.topic: how-to
audience: Application User
ms.reviewer: v-griffinc 
ms.search.region: global
ms.author: shajain
ms.search.validFrom: 2019-09-30
ms.custom: 
  - bap-template
  - evergreen
---

# Trickle feed-based order creation for retail store transactions

[!include [banner](includes/banner.md)]

This article describes trickle feed-based order creation for store transactions in Microsoft Dynamics 365 Commerce.

In Microsoft Dynamics 365 Commerce version 10.0.5 and later, we recommend that you transition all statement posting processes to the trickle feed–based statement posting processes. Significant performance and business benefits are associated with using the trickle feed functionality. Sales transactions are processed throughout the day. Tender and cash management transactions are processed on the financial statement at the end of the day. Trickle feed functionality enables the continuous processing of sales orders, invoices, and payments. Therefore, inventory, revenue, and payments are updated and recognized in near-real time.

## Use trickle feed-based posting

> [!IMPORTANT]
> - Before you enable trickle feed–based posting, you must ensure that there are no calculated and unposted statements. Post all statements before you enable the feature. You can check for open statements in the **Store financials** workspace.
> - Trickle feed-based posting can't be combined with the traditional statement posting, so ensure that all required steps are applied for all legal entities.

To enable trickle feed–based posting of retail transactions, enable the **Retail statements - Trickle feed** feature in the **Feature management** workspace. Statements are split into two types: transactional statements and financial statements.

### Transactional statements

Transactional statement processing is intended to be run at a high frequency throughout the day so that documents are created when transactions are uploaded into Commerce headquarters. Transactions are loaded from the stores to Commerce headquarters when you run the **P-Job**. You must also run the **Validate store transactions** job to validate transactions so that the transactional statement picks them up.

Schedule the following jobs to run at a high frequency:

- To calculate a transactional statement, run the **Calculate transactional statements in batch** job (**Retail and Commerce \> Retail and Commerce IT \> POS Posting \> Calculate transactional statements in batch**). This job picks up all unposted and validated transactions, and adds them to a new transactional statement.
- To post transactional statements in a batch, run the **Post transactional statements in batch** job (**Retail and Commerce \> Retail and Commerce IT \> POS Posting \> Post transactional statements in batch**). This job runs the posting process and creates sales orders, sales invoices, payment journals, discount journals, and income-expense transactions for unposted statements that don't contain any errors. 

### Financial statements

Financial statement processing is intended to be an end-of-day process. This type of statement processing only supports the **Shift** closing method, and picks up only closed shifts. Statements are limited to financial reconciliation, and only create the journals for the difference amounts between the counted amount and the transaction amount for tenders, and journals for other cash management transactions.

Financial statements also enable the review of the following transactions: tender declaration transactions, payment transactions, banked tender transactions, and safe tender transactions. The tender details page is only visible when a financial statement is selected.

![An image showing the tender details section of the posted statements form only when a financial statement is selected.](./media/Trickle-feed-posted-statements-transaction-view.png)

Schedule the start and end times of the following financial statement jobs based on the expected end of the day:

- To calculate a financial statement, run the **Calculate financial statements in batch** job (**Retail and Commerce \> Retail and Commerce IT \> POS Posting \> Calculate financial statements in batch**). This job collects all unposted financial transactions and adds them to a new financial statement.
- To post financial statements in a batch, run the **Post financial statements in batch** job (**Retail and Commerce \> Retail and Commerce IT \> POS Posting \> Post financial statements in batch**).

### Manually create statements

Transactional and financial statement types can also be manually created. 

1. Go to **Retail and Commerce \> Channels \> Stores**, and select **Statements**. 
2. Select **New**, and then select the type of statement to create. Fields on the **Statements** page show data that's relevant to the selected statement type, and actions under **Statement group** show relevant actions.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
