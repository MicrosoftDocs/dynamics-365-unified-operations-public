---
# required metadata

title: Edit and audit retail store transactions
description: This topic describes the functionality for editing and auditing store transactions. 
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
ms.assetid: ed0f77f7-3609-4330-bebd-ca3134575216
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2019-09-29
ms.dyn365.ops.version: 

---

# Edit and audit retail store transactions

[!include [banner](includes/banner.md)]



Dynamics 365 Commerce customers use first-party as well as third-party point of sale (POS) applications. With the first-party POS application, store transactions are pulled into Headquarters from the channels through a batch process. With third-party applications, transactions are pulled into Headquarters through integration. In both cases, after transactions are pulled into Headquarters, a consistency check process needs to be executed that runs multiple validations on the transactions so that only successfully validated transactions are pulled into the statement to be posted in Headquarters. 

Commerce transactions fail validation for various reasons. For example, a bug in the integration code or a bug in the POS application may cause inconsistent data, or a user error, such as deleting a product after it was synchronized to the channel or closing a fiscal period without posting transactions for that period, can cause inconsistent data.

While these transactions get flagged and are excluded from the statements, the transactions can disrupt a customer’s daily process of posting daily sales to the financials.

In Commerce, you can edit the specific transactions that fail validation while maintaining audit of all the changes. 

## Edit and audit transactions

In Retail version 10.0.5, cash and carry transactions like sales and returns are the only transactions that can be edited. Editing customer orders or online orders is not supported. In Retail version 10.0.6 and higher, editing cash management transactions is also supported.

1. Install the Dynamics Excel Add-in.

2. Go to the **Store financials** workspace. The **Transaction validation failures** tile provides a pre-filtered view of the transaction form that failed one or more of the validation rules.
 
3. Open the form. Click the record that failed validation, click **Office Add in**, and then click **Edit selected transaction**. An Excel file with the details of the selected transaction opens, with the following worksheets:

    - Lines: This worksheet has the header and product lines and related data for the transaction.
    - Payments: This worksheet has the details of the payment lines for the transaction.
    - Discounts: This worksheet has the discount-related details for the transaction.
    - Taxes: This worksheet has the tax-related details for the transaction.
    - Charges: This worksheet has the charges-related data for the transaction.

4. In the Excel file, you modify the appropriate fields and then upload the data back into Headquarters using the Dynamics Excel Add-in publish functionality. Once published, the changes will be reflected in the system. During publish, no validation is done on changes that users make.

5. A complete audit trail of the changes can be viewed by clicking **View audit trail** in the **Retail transaction** header for the header-level changes and in the relevant section and record on the appropriate transaction page. For example, all changes relating to sales lines will be visible on the **Sales transactions** page, changes relating to payments will be visible on the **Payment transactions** page, etc. The audit details that are maintained for the changes are as follows.

   - Modified date and time
   - Field 
   - Old value
   - New value
   - Modified by

6. After your changes are made and published, run the **Validate store transactions** option again to validate that the changes you made are consistent and valid.

> [!NOTE]
> You can only edit transactions that failed validation. If you want to edit transactions that passed validation, change the validation status of the transaction you want to change to **Error** or **None** and then you will be able to edit it. 


## Bulk edit transactions

In Retail version 10.0.6 and higher, the option to bulk edit transactions at a statement level is supported. 

1. Use the Excel Add-in to open a statement that has transactions you want to modify using steps 1-3 above.

2. Choose one of the options below.

    - **Edit cash and carry transactions**. This option enables you to edit all the cash and carry transactions included in the statement. The following Excel worksheets are available.
    
       - **Transaction**: This worksheet has all the header-level information for the sales transactions.
       - **Sales transaction**: This worksheet has all the lines-level information for the sales transactions.
       - **Payment transactions**: This worksheet has all the payment lines information for the sales transactions.
       - **Discount transactions**: This worksheet has all the discount lines information for the sales transactions.
       - **Tax transactions**: This worksheet has all the tax lines information for the sales transactions.
       - **Charge transactions**: This worksheet has all the charge lines information for the sales transactions.

    - **Edit cash management transactions**. This option enables you to edit all the cash management transactions included in the statement. The following Excel worksheets are available.
     
       - **Transaction**: This worksheet has all the header-level information for the cash management transactions.
       - **Bank tender transactions**: This worksheet has all the bank drop transaction details.
       - **Safe tender transactions**: This worksheet has all the safe drop transaction details.
       - **Tender declaration**: This worksheet has all the tender declaration transaction details.
       - **Income-expense transaction**: This worksheet has all the income-expense transaction line details.
       - **Payment transactions**: This worksheet has all the payment-related information for the **Pay invoice** operation as well as the income-expense transaction.

3.	Validations are not performed when you publish bulk edited transactions. You must ensure that all your edits are accurate and the fidelity of data across the worksheets is maintained. For example, if you want to change the transaction date to manage the scenarios where the fiscal or inventory period for the open transactions is closed, you need to change the date on all the Excel worksheets that have the **Business date** column. To validate transactions after they have been edited, you can use **Revalidate transactions** on the **Statements** page.
