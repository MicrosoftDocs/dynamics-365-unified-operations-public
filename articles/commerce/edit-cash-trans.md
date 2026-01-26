---
title: Edit and audit cash and carry and cash management transactions
description: Learn how to edit and audit cash and carry and cash management transactions in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 01/22/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: global
ms.author: josaw
ms.search.validFrom: 2018-11-15
ms.dyn365.ops.version: 
ms.custom: 
ms.assetid: ed0f77f7-3609-4330-bebd-ca3134575216
ms.search.industry: Retail
---
# Edit and audit cash and carry and cash management transactions

[!include [banner](../includes/banner.md)]

This article describes how to edit and audit cash and carry and cash management transactions in Microsoft Dynamics 365 Commerce.

Dynamics 365 Commerce customers use both a first-party point of sale (POS) application and partner POS applications. For the first-party application, a batch process pulls store transactions from the channels into Commerce headquarters. For partner applications, integration pulls transactions into Commerce headquarters. In both cases, you must perform a consistency check process after pulling transactions into Commerce headquarters. This process runs multiple validations on the transactions. Only transactions that pass validation are included in the statement for posting in Commerce headquarters.

Various reasons can cause Commerce transactions to fail validation. A bug in the integration code or in the POS application might cause inconsistent data. Alternatively, a user error might cause inconsistent data. For example, a user deletes a product after it was synced to the channel, or a user closes a fiscal period without posting transactions for that period. Although the system flags these transactions and excludes them from the statements, they can disrupt a customer's daily process of posting daily sales to the financials. In Commerce, you can edit the transactions that fail validation while you also maintain an audit of all the changes.

## Edit transactions

In Commerce version 10.0.5, you can only edit cash and carry transactions, such as sales and returns. You can't edit customer orders or online orders. In Commerce version 10.0.6 and later, you can also edit cash management transactions.

To edit transactions in Commerce headquarters, follow these steps:

1. Install the [Microsoft Dynamics Office Add-in](https://marketplace.microsoft.com/product/office/WA104379629?tab=Overview).
1. In Commerce headquarters, open the **Store financials** workspace. The **Transaction validation failures** tile provides a prefiltered view of the transaction page that failed one or more validation rules.
1. Open the transaction page, select the record that failed validation, select **Office Add in**, and then select **Edit selected transaction**. An Excel file that shows the details of the selected transaction is opened. This file contains the following worksheets:

    - **Lines** – This worksheet has the header and product lines for the transaction, and related data for the transaction.
    - **Payments** – This worksheet has the details of the payment lines for the transaction.
    - **Discounts** – This worksheet has the discount-related details for the transaction.
    - **Taxes** – This worksheet has the tax-related details for the transaction.
    - **Charges** – This worksheet has the charges-related data for the transaction.

1. In the Excel file, modify the appropriate fields, and then upload the data back into Commerce headquarters by using the publishing functionality of the Dynamics Excel Add-in. After the data is published, the changes appear in the system. During publication, no validation is done for changes that users make.
1. You can view a complete audit trail of the changes by selecting **View audit trail** in the **Retail transaction** header for the header-level changes, and in the relevant section and record on the appropriate transaction page. For example, all changes related to sales lines are shown on the **Sales transactions** page, and all changes related to payments are shown on the **Payment transactions** page. The following audit details are maintained for the changes:

    - Modified date and time
    - Field
    - Old value
    - New value
    - Modified by

1. After you make and publish your changes, run **Validate store transactions** to validate that those changes are consistent and valid.

> [!NOTE]
> You can edit only transactions that failed validation. If you want to edit a transaction that passed validation, change the validation status of the transaction to **Error** or **None**, and then publish the change. You can then edit the data on the header or in any other child records of the transaction, and publish the header or records.

## Bulk-edit transactions that are linked to a statement

Commerce version 10.0.6 and later support the option to bulk edit transactions at the statement level.

To bulk edit transactions that link to a statement in Commerce headquarters, follow these steps:

1. Open the **Statements** page, and select the statement that contains the transactions you want to edit.
1. Select the **Open in Microsoft Office** button.
1. Depending on what you need to edit, select one of the following options:

    - **Edit cash and carry transactions** – This option lets you edit all the cash and carry transactions that the statement includes. The following Excel worksheets are available:

        - **Transaction** – This worksheet has all the header-level information for the sales transactions.
        - **Sales transaction** – This worksheet has all the line-level information for the sales transactions.
        - **Payment transactions** – This worksheet has all the payment line information for the sales transactions.
        - **Discount transactions** – This worksheet has all the discount line information for the sales transactions.
        - **Tax transactions** – This worksheet has all the tax line information for the sales transactions.
        - **Charge transactions** – This worksheet has all the charge line information for the sales transactions.

    - **Edit cash management transactions** – This option lets you edit all the cash management transactions that the statement includes. The following Excel worksheets are available:

        - **Transaction** – This worksheet has all the header-level information for the cash management transactions.
        - **Bank tender transactions** – This worksheet has all the bank drop transaction details.
        - **Safe tender transactions** – This worksheet has all the safe drop transaction details.
        - **Tender declaration** – This worksheet has all the tender declaration transaction details.
        - **Income-expense transaction** – This worksheet has all the income-expense transaction line details.
        - **Payment transactions** – This worksheet has all the payment-related information for the **Pay invoice** operation and the income-expense transaction.

1. Edit the required transactions.

    > [!NOTE]
    > Validations aren't done when you publish bulk-edited transactions. You must make sure that all your edits are accurate, and that the fidelity of data across the worksheets is maintained. For example, if you want to change the transaction date, so that you can manage scenarios where the fiscal or inventory period for the open transactions is closed, you must change the date on all the Excel worksheets that have the **Business date** column. To validate transactions after you edit them, you can select **Revalidate transactions** on the **Statements** page. Wait for the validation job to finish running before you post the statement.

1. If the aggregation is already generated, open the **Aggregated transactions** page, and select **Regenerate sales order xml**.

## Bulk-edit transactions that aren't linked to a statement

Commerce version 10.0.10 and later support the option to bulk-edit transactions that fail validation but aren't linked to a statement.

To bulk-edit transactions that aren't linked to a statement in Commerce headquarters, follow these steps:

1. Open the **All stores** page, and select the store that you need to edit transactions for.
1. Select the **Open in Microsoft Office** button, and then select **Edit cash and carry transactions**.
1. Edit the required transactions, and then publish them.

## Additional resources

[Edit and audit online order and asynchronous customer order transactions](edit-order-trans.md)

[Edit financial dimensions for retail transactions](edit-financial-dim.md)

[Create an Excel workbook to edit retail transactions](create-excel-edit.md)

[Add fields to an Excel workbook to edit retail transactions](add-fields-excel.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
