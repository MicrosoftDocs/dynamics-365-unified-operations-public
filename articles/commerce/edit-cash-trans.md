---
# required metadata

title: Edit and audit cash and carry and cash management transactions
description: This topic describes how to edit and audit cash and carry and cash management transactions in Microsoft Dynamics 365 Commerce.
author: josaw1
manager: AnnBe
ms.date: 10/29/2020
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
# Edit and audit cash and carry and cash management transactions

[!include [banner](../includes/banner.md)]

This topic describes how to edit and audit cash and carry and cash management transactions in Microsoft Dynamics 365 Commerce.

## Overview

Dynamics 365 Commerce customers use first-party as well as third-party point of sale (POS) applications. With the first-party POS application, store transactions are pulled into Commerce headquarters from the channels through a batch process. With third-party applications, transactions are pulled into headquarters through integration. In both cases, after transactions are pulled into headquarters a consistency check process needs to be executed that runs multiple validations on the transactions so that only successfully validated transactions are pulled into the statement to be posted in headquarters.

Commerce transactions fail validation for various reasons. For example, a bug in the integration code or a bug in the POS application may cause inconsistent data, or a user error (such as deleting a product after it was synchronized to the channel, or closing a fiscal period without posting transactions for that period) can cause inconsistent data. While these transactions get flagged and are excluded from the statements, the transactions can disrupt a customer's daily process of posting daily sales to the financials. In Commerce, you can edit the specific transactions that fail validation while maintaining an audit of all the changes.

## Edit transactions

In Commerce version 10.0.5, cash and carry transactions like sales and returns are the only transactions that can be edited. Editing customer orders or online orders is not supported in 10.0.5. In Commerce version 10.0.6 and higher, editing cash management transactions is also supported.

To edit transactions in Commerce headquarters, follow these steps.

1. Install the [Microsoft Dynamics Office Add-in](https://appsource.microsoft.com/en-us/product/office/WA104379629?tab=Overview). 
1. In Commerce headquarters, go to **Store financials**. The **Transaction validation failures** tile provides a pre-filtered view of the transaction form that failed one or more of the validation rules.
1. Open the form. Select the record that failed validation, select **Office Add in**, and then select **Edit selected transaction**. A Microsoft Excel file with the details of the selected transaction opens, with the following worksheets:
    - Lines: This worksheet has the header and product lines and related data for the transaction.
    - Payments: This worksheet has the details of the payment lines for the transaction.
    - Discounts: This worksheet has the discount-related details for the transaction.
    - Taxes: This worksheet has the tax-related details for the transaction.
    - Charges: This worksheet has the charges-related data for the transaction.
1. In the Excel file, modify the appropriate fields and then upload the data back into headquarters using the Dynamics Office Add-in publish functionality. Once published, the changes will be reflected in the system. During publish, no validation is done on changes that users make.
1. A complete audit trail of the changes can be viewed by selecting **View audit trail** in the **Retail transaction** header for the header-level changes, and in the relevant section and record on the appropriate transaction page. For example, all changes relating to sales lines will be visible on the **Sales transactions** page, and changes relating to payments will be visible on the **Payment transactions** page. The audit details that are maintained for the changes are as follows.
    - Modified date and time
    - Field
    - Old value
    - New value
    - Modified by
1. After your changes are made and published, run **Validate store transactions** to validate that the changes you made are consistent and valid.

> [!NOTE]
> You can only edit transactions that failed validation. If you want to edit transactions that passed validation, change the validation status of the transaction you want to change to Error or None and publish the same. Now you will be able to edit the data in the header or any other child records of the transaction and publish them successfully. 
  
## Bulk edit transactions linked to a statement

In Commerce version 10.0.6 and higher, the option to bulk edit transactions at a statement level is supported.

To bulk edit transactions linked to a statement, follow these steps.

1. Navigate to the **Statements** form, and then select the statement that contains the transactions that needs to be changed.
1. Select the Microsoft Office logo.
1. Depending on what needs to be edited, choose one of the options below.
    - **Edit cash and carry transactions** - This option enables you to edit all the cash and carry transactions included in the statement. The following Excel worksheets are available.
      - Transaction: This worksheet has all the header-level information for the sales transactions.
      - Sales transaction: This worksheet has all the lines-level information for the sales transactions.
      - Payment transactions: This worksheet has all the payment lines information for the sales transactions.
      - Discount transactions: This worksheet has all the discount lines information for the sales transactions.
      - Tax transactions: This worksheet has all the tax lines information for the sales transactions.
      - Charge transactions: This worksheet has all the charge lines information for the sales transactions.
    - **Edit cash management transactions** - This option enables you to edit all the cash management transactions included in the statement. The following Excel worksheets are available.
      - Transaction: This worksheet has all the header-level information for the cash management transactions.
      - Bank tender transactions: This worksheet has all the bank drop transaction details.
      - Safe tender transactions: This worksheet has all the safe drop transaction details.
      - Tender declaration: This worksheet has all the tender declaration transaction details.
      - Income-expense transaction: This worksheet has all the income-expense transaction line details.
      - Payment transactions: This worksheet has all the payment-related information for the **Pay invoice** operation as well as the income-expense transaction.
1. Edit the required transactions.
    > [!NOTE]
    > Validations are not performed when you publish bulk edited transactions. You must ensure that all your edits are accurate and the fidelity of data across the worksheets is maintained. For example, if you want to change the transaction date to manage the scenarios where the fiscal or inventory period for the open transactions is closed, you must change the date on all the Excel worksheets that have the **Business date** column. To validate transactions after they have been edited, you can use **Revalidate transactions** on the **Statements** page. Wait for the validation job to complete before posting the statement.
1. If the aggregation has already been generated, navigate to **Aggregated transactions**, and then select **Regenerate sales order xml**.

## Bulk edit transactions not linked to a statement

In Commerce version 10.0.10 and higher, the option to bulk edit transactions that are failing validations and not linked to a statement is supported.

To bulk edit transactions not linked to a statement, follow these steps.

1. Navigate to **All stores** and select the store for which transactions must edited.
1. Select the Microsoft Office logo, and then select **Edit cash and carry transactions**.
1. Edit the required transactions and then publish them.

## Additional resources

[Edit and audit online order and asynchronous customer order transactions](edit-order-trans.md)

[Edit financial dimensions for retail transactions](edit-financial-dim.md)

[Create an Excel spreadsheet to edit retail transactions](create-excel-edit.md)

[Add fields to an Excel spreadsheet to edit retail transactions](add-fields-excel.md)
