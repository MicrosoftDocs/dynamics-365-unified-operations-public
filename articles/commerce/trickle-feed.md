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

Starting with version 10.0.5 it is recommended that all statement posting processes transition to the trickle feed-based statement posting processes. There are significant performance and business benefits when using the trickle feed functionality. Sales transactions are processed throughout the day. Only financial reconciliation of tenders and cash management transactions are processed at the end of the day. This feature enables continuous processing of sales orders, invoices, and payments allowing for inventory, revenue, and payments to be updated and recognized in near real time.

## How to use trickle feed-based posting

> [!IMPORTANT]
> Before enabling this feature, you must ensure that there are no calculated and unposted statements. Post all statements before enabling. Check for open statements in the 
**Store financials** workspace.

1. To enable trickle feed-based posting of retail transactions, enable the feature named **Retail statements - Trickle feed** using Feature management.
2. Statements will be split into two types: **Transactional statements** and **Financial statements**.

## Transactional statements
  **Transactional statement** processing is intended to be run at a high frequency throughout the day.
  - Transactions are loaded from the stores to Retail HQ when the P-Job executes.
  - The **Validate store transactions** job must run and validate transactions for the transactional statement to pick them up. 
  - The **Calculate transactional statements in batch** job will pick up all unposted and validated transactions and add them to a new **Transactional statement**.
  - The **Post transactional statements in batch** job will execute the posting process and create sales orders, sales invoices, payment journals, discount journals, and income-expense transactions for unposted statements that do not contain any errors.
  - These processes are intended to run at a high frequency so that documents are created when the transactions are uploaded into Headquarters through the P-job.

## Financial statements
  **Financial statement** processing is intended to be an end of day process.
  - Only supports closing method of Shift and will only pick up closed shifts. 
  - This statement is limited to financial reconciliation and will only create the journals for the difference amounts between counted amount and transaction amount for tenders as well as journals for other cash management transactions.
 - The **Calculate financial statements in batch** will collect all unposted financial transactions and add them to a new Financial statement.
 - The **Post financial statements in batch** job will execute the posting process of the financial transactions.
 
 ## Statement Calculation and Posting jobs
  - To calculate the transactional statement, go to **Retail and Commerce > Retail and Commerce IT > POS Posting > Calculate transactional statements in batch**. 
  - To post the transactional statements in batch, go to **Retail and Commerce > Retail and Commerce IT > POS Posting > Post transactional statements in batch**.
  - To calculate the financial statement, go to **Retail and Commerce > Retail and Commerce IT > POS Posting > Calculate financial statements in batch**. 
  - To post the financial statements in batch, go to **Retail and Commerce > Retail and Commerce IT > POS Posting > Post financial statements in batch**.

Transactional and financial statement types can be created manually. Navigate to **Retail and Commerce > Channels > Stores** and click **Statements**. Click **New** and then choose the type of statement that you want to create. Fields on the **Statements** page and actions under the **Statement group** of the page will show relevant data and actions based on the selected statement type.

## Periodic process changes
With this feature enabled, the following menu items are added. These should be scheduled to run at a high frequency for transactional statements, the timing of the financial statements should be determined to start and end based on the timing of expected end of day.
  - **Retail and Commerce > Retail and Commerce IT > POS Posting > Calculate transactional statements in batch**
  - **Retail and Commerce > Retail and Commerce IT > POS Posting > Post transactional statements in batch**
  - **Retail and Commerce > Retail and Commerce IT > POS Posting > Calculate financial statements in batch**
  - **Retail and Commerce > Retail and Commerce IT > POS Posting > Post financial statements in batch**

With the feature enabled, the following menu items are removed.
  - **Retail and Commerce > Retail and Commerce IT > POS Posting > Calculate statements in batch**
  - **Retail and Commerce > Retail and Commerce IT > POS Posting > Post statements in batch**
  - **Retail and Commerce > Retail and Commerce IT > POS Posting > Post inventory**


[!INCLUDE[footer-include](../includes/footer-banner.md)]
