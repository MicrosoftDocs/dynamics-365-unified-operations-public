---
title: Edit and audit online order and asynchronous customer order transactions
description: This article describes how to edit and audit online order and asynchronous customer order transactions in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 10/21/2022
ms.topic: index-page
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: v-chgriffin
ms.search.region: global
ms.author: josaw
ms.search.validFrom: 2018-11-15
ms.dyn365.ops.version: 
ms.custom: 
ms.assetid: ed0f77f7-3609-4330-bebd-ca3134575216
ms.search.industry: Retail
---
# Edit and audit online order and asynchronous customer order transactions

[!include [banner](../includes/banner.md)]

This article describes how to edit and audit online order and asynchronous customer order transactions in Microsoft Dynamics 365 Commerce.

## Overview

Between Commerce versions 10.0.5 and 10.0.6, support was added for editing cash and carry transactions (such as sales and returns) and cash management transactions (such as float entry and tender removal). In Commerce version 10.0.7, support was added for editing online order transactions and asynchronous customer order transactions.

## Edit and audit order transactions

To edit and audit order transactions in Commerce headquarters, follow these steps.

1. Install the [Microsoft Dynamics Office Add-in](https://appsource.microsoft.com/product/office/WA104379629?tab=Overview).
1. On the **Commerce parameters** page, on the **Customer orders** tab, on the **Order** FastTab, specify a hold code for **Hold code for order synchronization errors**.
1. Open the **Store financials** workspace. The **Online order synchronization errors** and **Customer order synchronization errors** tiles provide a prefiltered view of the retail transaction page. Each shows the transaction records that have failed synchronization for the corresponding order type.
1. Open either the **Online order synchronization errors** page or the **Customer order synchronization errors** page. Select a record to view the synchronization error details. The **Synchronization status** FastTab provides the following error details:

    - Pending order status
    - Order error details
    - Modified date and time
    - Retry count

1. If the error details indicate that the record must be fixed, select **Office Add in**, and then select **Edit selected transaction**. An Excel file that shows the details of the selected transaction is opened.

    - If the transaction that is being edited is an online order transaction, the Excel file contains the following worksheets:

        - **Transaction** – This worksheet has the header details for the transaction.
        - **Sales transaction** – This worksheet has the line details for the transaction.
        - **Payment transactions** – This worksheet has the details of the payment lines for the transaction.
        - **Discount transactions** – This worksheet has the discount-related details for the transaction.
        - **Tax transactions** – This worksheet has the tax-related details for the transaction.
        - **Charges transactions** – This worksheet has the charges-related data for the transaction.

    - If the transaction that is being edited is an asynchronous customer order transaction, the Excel file contains the following worksheets:

        - **Lines** – This worksheet has the header and line details for the transaction.
        - **Payments** – This worksheet has the details of the payment lines for the transaction.
        - **Discounts** – This worksheet has the discount-related details for the transaction.
        - **Taxes** – This worksheet has the tax-related details for the transaction.
        - **Charges** – This worksheet has the charges-related data for the transaction.

1. In the Excel file, in the **Pending order status** field, enter **Editing**, and then publish the change. In this way, you prevent the **Synchronize order** job that is running in batch mode from skipping this record during processing.
1. In the Excel file, modify the appropriate fields, and then upload the data back into Commerce headquarters by using the publishing functionality of the Dynamics Excel Add-in. After the data is published, the changes will be reflected in the system. During publication, no validation is done for changes that users make.
    > [!NOTE]
    > If you can't find the field that that you need to edit, follow the steps below to add the missing field in the worksheet.
    >   1. Select **Design** in Data Connector.
    >   1. Select the pencil icon next to the table in which you want to add a field.
    >   1. Select the field in the **Available fields** section and then select **Add**.
    >   1. Add as many fields as you need and then select **Update**.
    >   1. When the update is complete, you may need to select **Refresh** to update the values.

3. You can view a complete audit trail of the changes by selecting **View audit trail** in the **Retail transaction** header for the header-level changes, and in the relevant section and record on the appropriate transaction page. For example, all changes that are related to sales lines will be shown on the **Sales transactions** page, and all changes that are related to payments will be shown on the **Payment transactions** page. The following audit details are maintained for the changes:

    - Modified date and time
    - Field
    - Old value
    - New value
    - Modified by

1. After you've made and published your changes, select **Synchronize order** to immediately start the synchronization process. Alternatively, you can wait for the synchronization process that is running in batch mode to process the transaction.

By default, after the orders are successfully synced, they are put in a hold status, based on the hold code that is defined in the Commerce parameters. The hold on the orders must be removed before the orders can be processed further for fulfillment or other operations.

## Additional resources

[Edit and audit cash and carry and cash management transactions](edit-cash-trans.md)

[Edit financial dimensions for retail transactions](edit-financial-dim.md)

[Create an Excel workbook to edit retail transactions](create-excel-edit.md)

[Add fields to an Excel workbook to edit retail transactions](add-fields-excel.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
