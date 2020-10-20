---
# required metadata

title: Edit & audit of online orders & async customer orders transactions
description: This topic describes the feature to edit & audit online orders and async customer order transactions in Dynamics 365 Commerce.
author: josaw1
manager: AnnBe
ms.date: 10/20/2020
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
# Edit & audit of online orders & async customer orders transactions

[!include [banner](includes/banner.md)]

# Details
Between Retail version 10.0.5 & 10.0.6, support to edit cash and carry transactions like sales and returns along with editing cash management transactions like Float entry, Tender removal etc. was introduced. With the 10.0.7 version, support to edit async customer order transactions and online order transactions is also being introduced. The below points describe the process to do the same.  
1.	Install the Dynamics Excel Add-in.
2.	Specify a Hold code in the field **Hold code for order synchronization errors** under **Retail parameters > Customer orders > Order** fast tab 
3.	Go to the **Retail store financials** workspace. The **Online order synchronization** errors tile and **Customer order synchronization errors** tile provides a pre-filtered view of the retail transaction form with the transaction records that has failed synchronization for each of those types. 
4.	Open the from. Click a record to see the synchronization error details for it which is available in the **Synchronization status** fast tab. The fast tab provides the following error details:
    - Pending order status
    - Order error details
    - Modified date and time
    - Retry count
5.	Based on the error details, if the record needs a data fix, click **Office Add in**, and then click **Edit selected transaction** 
6.	If the transaction being edited is an online order transaction, then an Excel file with the details of the selected transaction opens, with the following worksheets:
    - Transaction: This worksheet has the header details for the transaction.
    - Sales transaction: This worksheet has the line details for the transaction.
    - Payment transactions: This worksheet has the details of the payment lines for the transaction.
    - Discount transactions: This worksheet has the discount-related details for the transaction.
    - Tax transactions: This worksheet has the tax-related details for the transaction.
    - Charges transactions: This worksheet has the charges-related data for the transaction.
7.	If the transaction being edited is an async customer order transaction, then an Excel file with the details of the selected transaction opens, with the following worksheets:
    - Lines: This worksheet has the header and line details for the transaction.
    - Payments: This worksheet has the details of the payment lines for the transaction.
    - Discounts: This worksheet has the discount-related details for the transaction.
    - Taxes: This worksheet has the tax-related details for the transaction.
    - Charges: This worksheet has the charges-related data for the transaction
8.	In the Excel file, first set the **Pending order status** field to **Editing** and publish the change. This will prevent the **Synchronize order** job that is running in batch to skip this record from processing. 
9.	In the Excel file, you modify the appropriate fields and then upload the data back into Retail Headquarters using the Dynamics Excel Add-in publish functionality. Once published, the changes will be reflected in the system. During publish, no validation is done on changes that users make.
10.	A complete audit trail of the changes can be viewed by clicking **View audit trail** in the **Retail transaction** header for the header-level changes and in the relevant section and record on the appropriate transaction page. For example, all changes relating to sales lines will be visible on the **Sales transactions** page, changes relating to payments will be visible on the **Payment transactions** page, etc. The audit details that are maintained for the changes are as follows.
    - Modified date and time
    - Field
    - Old value
    - New value
    - Modified by
11.	After your changes are made and published, click on the **Synchronize order** button to immediately start the synchronization process. Alternatively, the user can wait for the synchronization process that is being run in batch to process the transaction.
12.	 Once the orders are synchronized successfully, these orders by default are placed in a Hold status using the Hold code as defined in the Retail parameters. The Hold on the orders needs to be removed before the order can be processed further for fulfillment or other operations.  
