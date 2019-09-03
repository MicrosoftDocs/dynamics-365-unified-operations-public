---
# required metadata

title: Trickle feed-based order creation for retail store transactions
description: This topic describes the trickle feed-based order creation for retail store transactions functionality in Microsoft Dynamics 365 for Retail.
author: josaw1
manager: AnnBe
ms.date: 08/29/2019
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
ms.assetid: ed0f77f7-3609-4330-bebd-ca3134575216
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2018-11-15
ms.dyn365.ops.version: 

---
# Trickle feed-based order creation for retail store transactions

> [!NOTE]
> This feature is currently in Public preview. Please do reach out to the Dynamics 365 Retail team to enable this feature in production.

Currently Retail statement posting is an end of day operation and all the transactions are posted in the books only at the end of the day. The current posting process is as described below: 
  1. Based on the data synchronized to the HQ, the **Post inventory** job reserves the inventory for products at a defined recurring schedule.

  2. At the end of the day, when the stores are closed and the end-of-day operations are performed in the store, the remaining data is synchronized to the HQ. Retail transactions are then validated for accuracy using the **Validate store transactions** job. Subsequently, based on the **Calculate statements in batch** process, the system creates a statement document for every store and the **Post statements in batch** process removes the already created inventory reservation, creates sales orders for the retail transactions which in turn creates new inventory reservation and then sales orders are invoiced, payment journals are created & posted along with other related vouchers in the system.
As evident from the above points, only temporary inventory reservations are created during the day. These inventory reservations are then removed at the end of the day and all transactions are processed as sales orders, new inventory transactions are created along with other transactions at the end of the day. There is no processing of these transactions happening during the day and all of them are back loaded to the end of the day. This creates a situation where large transactions must be processed in a limited time window and results in phenomenal load and locks, which results in statement posting failures. This lends to a situation where retailers cannot recognize revenue, payments in their books on a timely manner. 

This feature aims to create a statement posting model where retail stores transactions are processed through a trickle feed mechanism throughout the day and only the financial reconciliation of tenders & other cash mgmt. transactions are processed at the end of the day. This model will split the load of creating Sales orders , invoices & payments throughout the day which will provide much better perceived performance to the end user and also fulfill the business objective of recognizing revenue, payments etc. in the books in a close to real time mode. This will also do away with the **all or nothing** nature of current statement posting process.


# Details
  
  1. To enable the trickle feed based posting of retail transactions, a new license key called **Retail statements (trickle feed) – Preview** needs to be enabled from the menu path **System administration > Set up > License configuration**. Customers will have to disable the **Retail statements** key before this can be enabled. At the time of enabling the key, there should not be any pending statements to be posted. Customers can switch between the keys if there are no pending statements when the keys are being switched.

  2. This feature will split the current statement document into two different types:
      1. Transactional statement
      2. Financial statement

      The Transactional statement will pick up all unposted & validated retail transactions and create Sales order, sales invoices,           payment & discount journals, Income/ Expense transactions at a cadence as configured by the customer. The expectation is that           customers configures this process to run at much higher frequency so that documents are created as and when the retail                   transactions are uploaded into HQ through the P-job. With this process, the **Post inventory** batch job becomes redundant and           should not be used with this feature
   
      The Financial statement is designed to be created at the end of the day and **will only support the Closing method of Shift**.           This document will be limited to financial reconciliation and will only create the journals for the difference amounts between           counted amount and transaction amount for the different tenders along with journals for other cash mgmt. transactions.   

3)	The Transactional statement can be calculated in batch using the new menu item **Calculate transactional statements in batch** and the same can be posted in batch using the new menu item **Post transactional statements** in a batch

4)	The Financial statement can be calculated in batch using the new menu item **Calculate financial statements in batch** and the same can be posted in batch using the new menu item **Post financial statements in batch**.

5)	Both statement types can also be created manually, using the **Retail statements** menu item available under **Retail > Channels > Retail stores**. On clicking **New** on this form, the user will be prompted to choose the type of statement that needs to be created.

6)	The batch jobs **Calculate statements in batch** and **Post statements in batch** will also be redundant with this feature and should not be used.

7)	All unposted statements of either types can be seen using the **Retail statements** form with type identifier available as column on the form. The same is true for the **Posted statements** form as well.  

8)	Fields on the **Retail statements** form along with actions available under the **Statement** group of the form will only show relevant data & actions based on the selected statement type.
