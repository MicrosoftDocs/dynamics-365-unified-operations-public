---
# required metadata

title: Edit and audit retail store transactions
description: This topic describes the functionality for editing and auditing retail store transactions. 
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
ms.assetid: ed0f77f7-3609-4330-bebd-ca3134575216
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2019-09-29
ms.dyn365.ops.version: 

---
# Edit and audit retail store transactions

Microsoft Dynamics 365 Retail customers use both a first-party point of sale (POS) application and third-party POS applications. In the first-party POS application, a batch process is used to pull retail store transactions into headquarters (HQ) from the channels. In third-party applications, transactions are pulled into HQ through integration. In both cases, after transactions are pulled into HQ, a consistency check must be run. This consistency check does multiple validations on the transactions, and only transactions that are successfully validated are pulled into the statement that will be posted in HQ.

Retail transactions might fail validation for various reasons. For example, a bug in the integration code or in the POS application might cause inconsistent data. User errors can also cause inconsistent data. For example, a user might delete a product after it was synced to the channel or close a fiscal period without posting retail transactions for that period.

Although retail transactions that fail validation are flagged and excluded from the statements, they can disrupt a customer's daily process of posting daily retail sales to the financials.

In Retail, you can edit the retail transactions that fail validation, and maintain an audit of all the changes.

## Edit and audit transactions

In Dynamics 365 Retail version 10.0.5, cash-and-carry transactions, such as sales and returns, are the only transactions that can be edited. Customer orders and online orders can't be edited. In Dynamics 365 Retail version 10.0.6 and later, cash management transactions can also be edited.

1. Install the Dynamics Excel Add-in.
2. In the **Retail store financials** workspace, select the **Transaction validation failures** tile to open a prefiltered view of the retail transactions that failed one or more validation rules.
3. Select a record that failed validation, select **Office Add in**, and then select **Edit selected transaction**. A Microsoft Excel file that contains the details of the selected transaction is opened. This file has the following worksheets:

    - **Lines** – This worksheet has the header and product lines, and related data for the transaction.
    - **Payments** – This worksheet has the details of the payment lines for the transaction.
    - **Discounts** – This worksheet has the discount-related details for the transaction.
    - **Taxes** – This worksheet has the tax-related details for the transaction.
    - **Charges** – This worksheet has the charge-related details for the transaction.

4. Edit the appropriate fields in the Excel file, and then upload the data back to HQ by using the Publish functionality of the Dynamics Excel Add-in. After the file is published, the system will reflect your changes. No validation is done on changes that users make during publishing.
5. To view a complete audit trail of the changes, select **View audit trail** in the **Retail transaction** header (for header-level changes) and the relevant section and record on the **Transactions** page. For example, all changes that are related to sales lines are shown on the **Sales transactions** page, and all changes that are related to payments are shown on the **Payment transactions** page. The following audit details are maintained for the changes:

    - The date and time when the change was made
    - The field that was changed
    - The old value
    - The new value
    - The person who made the change

6. After you've published your changes, select **Validate store transactions** again to validate that they are consistent and valid.

> [!NOTE]
> You can edit only transactions that failed validation. To edit a transaction that passed validation, you must first change the validation status of the transaction to **Error** or **None**.

## Edit transactions in bulk

In Retail version 10.0.6 and later, you can edit retail transactions in bulk at the statement level.

1. Use the Dynamics Excel Add-in to open the statement that has the transactions that you want to edit. For instructions, see steps 1 through 3 of the previous procedure.
2. Select one of the following options:

    - **Edit cash and carry transactions** – Edit all the cash-and-carry transactions that are included in the statement. The following Excel worksheets are available:

        - **Transaction** – This worksheet has all the header-level information for the sales transactions.
        - **Sales transaction** – This worksheet has all the line-level information for the sales transactions.
        - **Payment transactions** – This worksheet has all the payment line information for the sales transactions.
        - **Discount transactions** – This worksheet has all the discount line information for the sales transactions.
        - **Tax transactions** – This worksheet has all the tax line information for the sales transactions.
        - **Charge transactions** – This worksheet has all the charge line information for the sales transactions.

    - **Edit cash management transactions** – Edit all the cash management transactions that are included in the statement. The following Excel worksheets are available:

        - **Transaction** – This worksheet has all the header-level information for the cash management transactions.
        - **Bank tender transactions** – This worksheet has all the details of bank drop transactions.
        - **Safe tender transactions** – This worksheet has all the details of safe drop transactions.
        - **Tender declaration** – This worksheet has all the details of tender declaration transactions.
        - **Income-expense transaction** – This worksheet has all the details of income expense transaction lines.
        - **Payment transactions** – This worksheet has all the payment-related information for the **Pay invoice** operation and the income expense transaction.

Validations aren't done when you publish edited transactions in bulk. You must make sure that all your changes are accurate, and that they maintain the fidelity of data across the worksheets. For example, if you want to change the transaction date to manage scenarios where the fiscal or inventory period for open retail transactions is closed, you must change the date on all the Excel worksheets that have the **Business date** column. To validate transactions after they have been edited, select **Revalidate transactions** on the **Retail statements** page.
