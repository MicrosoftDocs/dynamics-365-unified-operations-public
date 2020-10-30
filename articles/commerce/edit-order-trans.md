---
# required metadata

title: Edit and audit online order and asynchronous customer order transactions
description: This topic describes how to edit and audit online order and asynchronous customer order transactions in Microsoft Dynamics 365 Commerce.
author: josaw1
manager: AnnBe
ms.date: 10/30/2020
ms.topic: index-page
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
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
# Edit and audit online order and asynchronous customer order transactions

[!include [banner](../includes/banner.md)]

This topic describes how to edit and audit online order and asynchronous customer order transactions in Microsoft Dynamics 365 Commerce.

## Overview

Between Commerce versions 10.0.5 and 10.0.6, support was added to edit cash and carry transactions (such as sales and returns) and cash management transactions (such as float entry and tender removal). With Commerce version 10.0.7, support was added to edit asynchronous customer order transactions and online order transactions. 

## Edit and audit order transactions

To edit and audit order transactions in Commerce headquarters, follow these steps. 

1. Install the [Microsoft Dynamics Office Add-in](https://appsource.microsoft.com/en-us/product/office/WA104379629?tab=Overview).
1. Under the **Retail parameters \> Customer orders \> Order** FastTab, specify a hold code for **Hold code for order synchronization errors**.
1. Go **Store financials**. The **Online order synchronization errors** and **Customer order synchronization errors** tiles provide a prefiltered view of the retail transaction form with the transaction records that have failed synchronization for each of those types. 
1. Open either the **Online order synchronization errors** or **Customer order synchronization errors** form. Select a record to see the synchronization error details. The **Synchronization status** FastTab provides the following error details:
    - **Pending order status**
    - **Order error details**
    - **Modified date and time**
    - **Retry count**
1. Based on the error details, if the record needs a data fix, select **Office Add in**, and then select **Edit selected transaction**. 
1. If the transaction being edited is an online order transaction, then an Excel file with the details of the selected transaction opens, with the following worksheets:
    - **Transaction**: This worksheet has the header details for the transaction.
    - **Sales transaction**: This worksheet has the line details for the transaction.
    - **Payment transactions**: This worksheet has the details of the payment lines for the transaction.
    - **Discount transactions**: This worksheet has the discount-related details for the transaction.
    - **Tax transactions**: This worksheet has the tax-related details for the transaction.
    - **Charges transactions**: This worksheet has the charges-related data for the transaction.
1. If the transaction being edited is an asynchronous customer order transaction, then an Excel file with the details of the selected transaction opens, with the following worksheets:
    - **Lines**: This worksheet has the header and line details for the transaction.
    - **Payments**: This worksheet has the details of the payment lines for the transaction.
    - **Discounts**: This worksheet has the discount-related details for the transaction.
    - **Taxes**: This worksheet has the tax-related details for the transaction.
    - **Charges**: This worksheet has the charges-related data for the transaction
1. In the Excel file, enter **Editing** for **Pending order status**, and then publish the change. This will prevent the **Synchronize order** job that is running in batch to skip this record from processing. 
1. In the Excel file, modify the appropriate fields and then upload the data back into Commerce headquarters using the Dynamics Excel Add-in publish functionality. Once published, the changes will be reflected in the system. During publish, no validation is done on changes that users make.
1. A complete audit trail of the changes can be viewed by selecting **View audit trail** in the **Retail transaction** header for the header-level changes, and in the relevant section and record on the appropriate transaction page. For example, all changes relating to sales lines will be visible on the **Sales transactions** page, and changes relating to payments will be visible on the **Payment transactions** page. The audit details that are maintained for the changes are as follows.
    - Modified date and time
    - Field
    - Old value
    - New value
    - Modified by
1. After your changes are made and published, select **Synchronize order** to immediately start the synchronization process. Alternatively, you can wait for the synchronization process that is being run in batch to process the transaction.
1. Once the orders are synchronized successfully, these orders are by default placed in a hold status using the hold code as defined in the Commerce parameters. The hold on the orders needs to be removed before the order can be processed further for fulfillment or other operations.  

## Additional resources

[Edit and audit cash and carry and cash management transactions](edit-cash-trans.md)

[Edit financial dimensions for retail transactions](edit-financial-dim.md)

[Create an Excel spreadsheet to edit retail transactions](create-excel-edit.md)

[Add fields to an Excel spreadsheet to edit retail transactions](add-fields-excel.md)
