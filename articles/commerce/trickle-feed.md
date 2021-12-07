---
# required metadata

title: Trickle feed-based order creation for retail store transactions
description: This topic describes the trickle feed-based order creation for store transactions in Microsoft Dynamics 365 Commerce.
author: analpert
ms.date: 12/08/2021
ms.topic: index-page
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2019-09-30
ms.dyn365.ops.version: 

---
# Trickle feed-based order creation for retail store transactions

[!include [banner](includes/banner.md)]

In Dynamics 365 Commerce version 10.0.5 and later, it is recommended that all statement posting processes transition to the trickle feed-based statement posting processes. There are significant performance and business benefits associated with using the trickle feed functionality. Sales transactions are processed throughout the day. Only financial reconciliation of tenders and cash management transactions are processed at the end of the day. Trickle feed functionality enables the continuous processing of sales orders, invoices, and payments. This allows inventory, revenue, and payments to be updated and recognized in near real time.

## Use trickle feed-based posting

> [!IMPORTANT]
> Before enabling trickle feed-based posting, you must ensure that there are no calculated and unposted statements. Post all statements before you enable the feature. You can check for open statements in the **Store financials** workspace.

To enable trickle feed-based posting of retail transactions, go to the **Feature management** workspace and enable **Retail statements - Trickle feed**. Statements will be split into two types: **Transactional statements** and **Financial statements**.

### Transactional statements
Transactional statement processing is intended to be run at a high frequency throughout the day so that documents are created when  transactions are uploaded into Commerce HQ. Transactions are loaded from the stores to Commerce HQ when you run the **P-Job**. You must also run the **Validate store transactions** job to validate transactions so that the transactional statement picks them up.

Schedule the jobs listed below to run at a high frequency.
- To calculate a transactional statement, run **Retail and Commerce > Retail and Commerce IT > POS Posting > Calculate transactional statements in batch**. This job will pick up all unposted and validated transactions and add them to a new transactional statement.
- To post transactional statements in batch, run **Retail and Commerce > Retail and Commerce IT > POS Posting > Post transactional statements in batch**. This job will execute the posting process and create sales orders, sales invoices, payment journals, discount journals, and income-expense transactions for unposted statements that do not contain any errors. 


### Financial statements
Financial statement processing is intended to be an end-of-day process. This type of statement processing only supports the closing method of shift and will only pick up closed shifts. Statements are limited to financial reconciliation and will only create the journals for the difference amounts between counted amount and transaction amount for tenders, and journals for other cash management transactions.

Time the financial statements jobs to start and end based on the timing of expected end of day.
- To calculate a financial statement, run **Retail and Commerce > Retail and Commerce IT > POS Posting > Calculate financial statements in batch**. This job will collect all unposted financial transactions and add them to a new financial statement.
- To post financial statements in batch, run **Retail and Commerce > Retail and Commerce IT > POS Posting > Post financial statements in batch**.


### Manual create statements
Transactional and financial statement types can also be created manually. 

1. Go to **Retail and Commerce > Channels > Stores** and select **Statements**. 
2. Select **New** and then choose the type of statement that you want to create. Fields on the **Statements** page and actions under the **Statement group** on the page will show relevant data and actions based on the statement type you select.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
