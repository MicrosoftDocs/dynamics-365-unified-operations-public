---
# required metadata

title: Trickle feed-based order creation for retail store transactions (Public preview)
description: This topic describes trickle feed-based order creation for retail store transactions in Microsoft Dynamics 365 Retail.
author: josaw1
manager: AnnBe
ms.date: 10/08/2019
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
# Trickle feed–based order creation for retail store transactions (Public preview)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

In Microsoft Dynamics 365 Retail version 10.0.4 and earlier, retail statement posting is an end-of-day operation. All transactions are posted in the books at the end of the day. Large transactions must then be processed in a limited time window. However, this processing sometimes causes load, locks, and statement posting failures. Retailers also can't recognize revenue and payments in their books throughout the day.

Dynamics 365 Retail version 10.0.5 introduces the public preview of functionality for trickle feed–based order creation. When this functionality is used, transactions are processed throughout the day, and only the financial reconciliation of tenders and other cash management transactions are processed at the end of the day. This functionality splits the load of creating sales orders, invoices, and payments throughout the day. Therefore, it provides better perceived performance. Revenue and payments can also be recognized in the books in near-real time.

## Do trickle feed–based posting

Before you can use the new functionality for trickle feed–based posting of retail transactions, you must turn it on.

1. Go to **System administration \> Setup \> License configuration**. 
2. Under **Retail**, clear the check box for the **Retail statements** license key.
3. Select the check box for the **Retail statements (trickle feed) – Preview** license key. When you enable this key, make sure that no pending statements are waiting to be posted.

After the new functionality is turned on, the current statement document will be split into two documents: a transactional statement and a financial statement.

- The transactional statement picks up all unposted and validated retail transactions, and creates sales orders, sales invoices, payment and discount journals, and income expense transactions at the cadence that you configure. You should configure this process to run frequently, so that documents are created when the retail transactions are uploaded into headquarters (HQ) through the P-job.

    For the transactional statement that already creates sales orders and sales invoices, you don't have to configure the **Post inventory** batch job. However, you can still use it to meet any specific business requirements that you have.

- The financial statement is intended to be created at the end of the day. It supports only the **Shift** closing method. This statement is limited to financial reconciliation. It creates the journals only for the difference amounts between the counted amount and the transaction amount for the different tenders, together with journals for other cash management transactions.

To calculate the transactional statement, select **Calculate transactional statements in batch**. To post transactional statements in a batch, select **Post transactional statements in batch**.

To calculate the financial statement, select **Calculate financial statements in batch**. To post financial statements in a batch, select **Post financial statements in batch**.

> [!NOTE]
> When the new functionality for trickle feed–based posting of retail transactions is turned on, the **Calculate statements in batch** and **Post statements in batch** menu items are removed.

Alternatively, you can manually create transactional and financial statements. Go to **Retail \> Channels \> Retail stores \> Retail statements**, select **New**, and then select the type of statement to create. The fields on the **Retail statements** page will show data that is relevant to the type of statement that you selected. Additionally, the buttons on the **Statement** tab on the Action Pane will be specific to that statement type.
