---
# required metadata

title: Trickle feed-based order creation for retail store transactions
description: This topic describes the trickle feed-based order creation for retail store transactions in Microsoft Dynamics 365 Commerce.
author: josaw1
manager: AnnBe
ms.date: 10/14/2019
ms.topic: index-page
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2019-09-30
ms.dyn365.ops.version: 

---
# Trickle feed-based order creation for retail store transactions (Public preview)

[!include [banner](includes/banner.md)]



In Dynamics 365 Retail versions 10.0.4 and earlier, statement posting is an end-of-day operation and all transactions are posted in the books at the end of the day. Large transactions must then be processed in a limited time window, sometimes resulting in load and locks and statement posting failures. Retailers also can't recognize revenue and payments in their books throughout the day.

With the public preview of trickle feed-based order creation introduced in Retail version 10.0.5, transactions are processed throughout the day, and only the financial reconciliation of tenders and other cash management transactions are processed at the end of the day. This functionality splits the load of creating sales orders, invoices, and payments throughout the day, providing better perceived performance and the ability to recognize revenue and payments in the books in near real-time. 


## How to use trickle feed-based posting
  
1. To enable trickle feed-based posting of transactions, go to **System administration > Set up > License configuration** and disable the the **Statements** key.

2. On the same page, enable the **Statements (trickle feed) – Preview** license key. When you enable this key, make sure there are no pending statements waiting to be posted. 

    > [!Important]
    > Before you enable the **Statements (trickle feed) – Preview** license key, make sure that no pending statements are waiting to be posted.

3. The current statement document will be split into two different types; transactional statement and financial statement.

      - The transactional statement will pick up all unposted and validated transactions and create sales orders, sales invoices, payment and discount journals, and income-expense transactions at the cadence that you configure. You should configure this process to run at a high frequency so that documents are created when the transactions are uploaded into Headquarters through the P-job. With the transactional statement that already creates sales orders and sales invoices, there is no real need to configure the **Post inventory** batch job. However, you can still use it to meet specific business requirements that you may have.  
      
     - The financial statement is designed to be created at the end of the day and only supports the closing method of **Shift**. This statement will be limited to financial reconciliation and will only create the journals for the difference amounts between counted amount and transaction amount for the different tenders, along with journals for other cash management transactions.   

4. To calculate the transactional statement, click **Retail and Commerce > Retail and Commerce IT > POS Posting > Calculate transactional statements in batch**. To post the transactional statement statements in batch, click **Retail and Commerce > Retail and Commerce IT > POS Posting > Post transactional statements in batch**.

5. To calculate the financial statement, click **Retail and Commerce > Retail and Commerce IT > POS Posting > Calculate financial statements in batch**. To post the financial statements in batch, click **Retail and Commerce > Retail and Commerce IT > POS Posting > Post financial statements in batch**.

> [!NOTE]
> The menu items **Retail and Commerce > Retail and Commerce IT > POS Posting > Calculate statements in batch** and **Retail and Commerce > Retail and Commerce IT > POS Posting > Post statements in batch** are removed with this new feature.

Alternately, transactional and financial statement types can be created manually. Go to **Retail and Commerce > Channels > Stores** and click **Statements**. Click **New** and then choose the type of statement that you want to create. Fields on the **Statements** page and actions under the **Statement group** of the page will show relevant data and actions based on the selected statement type.
