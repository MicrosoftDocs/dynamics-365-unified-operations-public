---
# required metadata

title: Edit and audit retail store transactions
description: This topic describes the functionality for editing and auditing retail store transactions. 
author: josaw1
manager: AnnBe
ms.date: 09/29/2019
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

Dynamics 365 for Retail customers use first-party as well as third-party point of sale (POS) applications. With first-party POS application, retail store transactions are pulled into headquarters (HQ) from the channels through a batch process. With third-party applications, transactions are pulled into HQ through integration. In both cases, after transactions are pulled into HQ, a consistency check process needs to be executed that runs multiple validations on the transactions so that only successfully validated transactions are pulled into the statement to be posted in HQ. 

Sometimes, retail transactions fail validation for various reasons. For example, a bug in the integration code or a bug in the POS application may cause inconsistent data, or a user error, such as deleting a product after it was synchronized to the channel or closing a fiscal period without posting retail transactions for that period, can cause inconsistent data.

While these transactions get flagged and are excluded from the statements, the transactions can disrupt a customer’s daily process of posting daily retail sales to the financials.

In Retail, you can edit the specific retail transactions that fail validation while maintaining audit of all the changes. 

To edit and audit transactions, do the following.

1. Install the Dynamics Excel Add-in.
<!--- stopped here --->

2. A new tile has been introduced on the **Retail store financials** workspace called **Transaction validation failures** which provides a pre-filtered view of the Retail transaction form that failed one or more of the validation rules.
 
3. On the Retail transaction form, for the record that failed validation, the user can modify the concerned record by clicking on the record and clicking on the **Office Add in** button and clicking on the option **Edit selected transaction**. This will open an Excel file with the details of the selected transaction in multiple excel worksheet as per below:

    1. Lines: This has the header and product lines related data for the transaction
    2. Payments: This has the details of the payment lines for the transaction
    3. Discounts: This has the discount related details for the transaction
    4. Taxes: This has the tax related details for the transaction
    5. Charges: This has the charges related data for the transaction

   In the Excel worksheet, the user can modify the required fields and upload it back into the system using the standard Dynamics Excel    Add in publish capability.

4. Once published, the changes made by the user are reflected in the system. During the publishing process, no validation is performed on the changes made by the user.

5. The system maintains a complete audit trail of the change made by the user and the same can be viewed using the **View audit trail** button in the **Retail transaction** header for the header level changes and in the relevant section and record under the **Transactions** form. For e.g.; all sales line related changes will be visible under the **Sales transactions** form under the **Transaction** button, payment related changes will be visible under the **Payment transactions** form under the **Transaction** button and so on. The details of the audit that are maintained for the changes are as below:

     1. Modified date and time
     2. Field 
     3. Old value
     4. New value
     5. Modified by

6. After changes are made and published for retail transactions, the **Validate store transactions** option must be run again to validate that the changes made are all consistent & as per expectations.

7. By default, the system would only allow to edit the retail transactions that has failed validation. If the customer wants to edit records that has passed validation, they can flip the status of the validation status of the transaction to **Error** or **None**. This would allow the transaction to be edited. 

8. As of the version 10.0.5, only cash & carry transactions like sales, returns etc. can be edited using this feature. Editing of Customer order or Online order is not supported. Starting the 10.0.6 release, support to edit cash management transactions has also been introduced in this feature.

9. In version 10.0.6 the option to bulk edit retail transactions at a statement level has been introduced. When the Excel Add-in is opened in the context of a Retail statement for which transactions must be modified, the user is presented with the following options:

     1. **Edit cash and carry transactions** – This option allows you to edit all the cash & carry transactions included in the statement and it opens the following Excel worksheets:
        1. **Transaction** – This worksheet has all the header level information for the sales transactions
        2. **Sales transaction** – This worksheet has all the lines level information for the sales transactions
        3. **Payment transactions** – This worksheet has all the payment lines information for the sales transactions
        4. **Discount transactions** – This worksheet has all the discount lines information for the sales transactions
        5. **Tax transactions** - This worksheet has all the tax lines information for the sales transactions
        6. **Charge transactions** - This worksheet has all the charge lines information for the sales transactions

     2. **Edit cash management transactions** - This option allows you to edit all the cash management transactions included in the statement and it opens the following Excel worksheets: 
        1. **Transaction** – This worksheet has all the header level information for the cash management transactions
        2. **Bank tender transactions** - This worksheet has all the bank drop transaction details
        3. **Safe tender transactions** - This worksheet has all the safe drop transaction details
        4. **Tender declaration** - This worksheet has all the tender declaration transaction details
        5. **Income-Expense Transaction** - This worksheet has all the Income-Expense transaction line details
        6. **Payment transactions** - This worksheet has all the payment related information for the **Pay invoice** operation as well 
             as the Income-Expense transaction

10)	As with option to **Edit selected transactions**, there is no validation performed even during the publishing of transactions edited in bulk. The user must ensure that all the edits performed is accurate and the fidelity of data across the worksheets is maintained. For e.g.: If the user wants to change the date of transaction to handle the scenarios where the fiscal or inventory period for the open retail transactions is closed, the user needs to change the date on all Excel worksheets that has the Business date column. Changing in one worksheet will not be enough.

11)	The user can validate the retail store transactions for a statement after it has been edited by using the new action introduced on **Retail statements** called as **Revalidate transactions**.
