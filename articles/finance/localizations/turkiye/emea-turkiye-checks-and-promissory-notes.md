---
title: Use checks and promissory notes
description: Learn how to use checks and promissory notes in the Republic of Türkiye. 
author: v-omerorhan 
ms.author: v-omerorhan 
ms.topic: how-to 
ms.date: 09/08/2025
ms.reviewer: johnmichalak
ms.search.region: Türkiye 
ms.search.validFrom: 2020-02-03 
ms.search.form: ChecksAndPromissoryNotes 
ms.dyn365.ops.version: 10.0.9 
ms.assetid: b2b22868-de68-439f-914c-78c6930b7340
---

# Use checks and promissory notes
[!INCLUDE[banner](../../includes/banner.md)]

In Türkiye, checks and promissory notes are widely used commercial payment instruments that require careful tracking and accounting to comply with regulations. 
The **Cash and bank management** module in Dynamics 365 Finance provides functionality to manage checks and promissory notes, including their receipt, issuance, transfer, collection, endorsement, return, and rediscounting.

The **Check and promissory note operations** feature in Finance helps businesses manage all steps related to checks and promissory notes. 
Create, record, transfer, and track these documents throughout their lifecycle.

This feature lets you use automated processes like transaction codes and rediscount calculations. Quickly see the status of each document and ensure records are accurate.

This module ensures compliance with requirements by offering specialized configuration options, automated journal entries, portfolio tracking, and rediscount calculations.

Key capabilities of the **Check and promissory note operations** feature include:

- Define and manage check and promissory note transaction codes.
- Group documents using portfolio codes (received or issued).
- Record and track the lifecycle of commercial papers.
- Generate and reverse rediscount entries.
- Integrate with customer and vendor payments, bank transactions, and posting profiles.

## Configure checks and promissory note parameters

This section provides general information about the parameters for the **Check and promissory note operations** feature for Türkiye.

The **Check and promissory note parameters** page defines company-wide settings for managing the lifecycle of checks and promissory notes. 
These parameters determine how documents behave in journals, which default accounts are used, and how legal requirements apply.

Access the **Check and promissory note parameters** page by going to **Cash and bank management > Setup > Check and promissory note operations > Check and promissory note parameters**.

Here are the details for the fields:

### General Tab

| Field | Description |
|------------|-------------|
| Settlement status | Defines the default settlement behavior for checks and promissory notes. If set to **None**, the system doesn't apply automatic settlement when transactions are posted. |
| Customer method of payment | Specifies the default method of payment to use for customers when recording check or promissory note transactions. |
| Vendor method of payment | Specifies the default method of payment to use for vendors during check or promissory note operations. |
| Portfolio account type | Indicates the type of account used to represent portfolios in accounting entries. Typically set to **Bank** but can vary depending on how portfolios are configured. |
| Use due date | Controls due dates on check and promissory note documents. When turned on, the system tracks and validates due dates during operations. |
| The Printed number field is mandatory | If enabled, the check or note number must be entered before posting a transaction. This ensures traceability of printed documents. |
| Control of out date for check | When enabled, prevents entering an issue (out) date later than the check's due date. This ensures compliance with date logic. |
| Is reverse date | If enabled, the system supports reversal postings to use the original transaction’s date, which is important for maintaining accurate historical records. |

### Rediscount Tab

#### Overview Tab

| Field name | Description |
|------------|-------------|
| Journal name | Specifies the default journal used when posting rediscount transactions. This journal must already exist and be set up under **General ledger > Journal names**. |
| Exchange rate type | Defines which exchange rate type used for rediscount calculations involving foreign currency checks or promissory notes. For example, **Forex Buying** or **Banknote Buying**. |
| Detail level | Determines the level of detail shown in the rediscount journal lines. Options typically include **Details** (per check/note) or **Summary** (per portfolio or account). |
| Interest calculation type | Selects the basis on which interest is calculated. The option **Calculated period date** means the interest is calculated based on the actual number of days between the posting date and maturity date. |
| Automatic posting | If you enable it, the system automatically posts rediscount entries after generation. If disabled, the entries must be reviewed and posted manually. |

#### Accounts receivable Tab

| Field  | Description  |
| ------ | ------- |
| Rediscount account of notes receivable | Specifies the general ledger account used to post rediscounted notes receivable. |
| Rediscount interest expense account    | Specifies the general ledger account for posting interest expenses from rediscount operations. |
	
#### Accounts payable Tab

| Field  | Description |
| ------- | -------- |
| Rediscount account of notes payable | Specifies the general ledger account used to post rediscounted notes receivable. |
| Rediscount interest income account | Specifies the general ledger account for posting interest expenses from rediscount operations. |

### Check dimensions Tab

| Field | Description |
|----|----|
| COA dimension | Calculates coding rediscount at the chart of accounts level. |
| Portfolio dimension | Links system check numbers to portfolio account dimensions (for example, 101, 103, etc.). |
| Customer dimension | Applies if vendor (320*) or customer (120*) accounts track check numbers. |
| Vendor dimension | Applies if vendor (320*) or customer (120*) accounts track check numbers. |
| Bank dimension | Applies if bank accounts (102*) use check dimension tracking. |

### Number sequences Tab

| Field  | Description  |
| ------- | -------- |
| System number of check | Automatically generates a unique identifier for each check or promissory note entered into the system. |
| Check payroll number   | Number sequences assigned to identify check payroll batches. |
| Check movement number  | Sequence number used to identify each transaction line for check or promissory note entries (journal transaction number). |
| Last refreshed on    | System-generated reference indicating the last refresh or update point for check sequences. |
| Expiration date   | Number sequence to track the expiration date-related operations, used for validity tracking or aging of checks. |

> [!NOTE]  
> Rediscount accounting is typically used at the end of the month or year to reflect accrued interest income or expenses related to postdated checks or promissory notes.

## Define portfolio codes for check and promissory note operations

This section provides an overview of the key features and functionalities available on the **Check and promissory notes portfolio codes** page in Finance. 

By following the steps outlined, you can effectively manage check and promissory note processes within your organization.

Portfolio codes let organizations define and manage financial instruments, like checks and promissory notes, used in Turkish commercial transactions.

In Türkiye, it's a legal and operational requirement to group these instruments under portfolios for tracking, processing, and reporting. These portfolios help classify received and issued commercial papers and facilitate proper accounting, endorsement, and reconciliation processes.

Use this page to:

- Set up portfolio codes with descriptive names.
- Optionally assign default ledger accounts for accounting.
- Categorize portfolios by instrument type (check or promissory note).
- Support financial and legal workflows that rely on portfolio tracking, including customer/vendor payments, protests, collections, and commercial paper reporting.

Here are the details for each field:

| **Field** | **Description** |
| --- | --- |
| Portfolio code | Specifies a unique identifier for each portfolio. |
| Portfolio name | Specifies a descriptive label for the portfolio. |
| Account type | Specifies the type of account associated with the portfolio. |
| Account number | Specifies the account number linked to the portfolio. In the **Account type** field: |
| Portfolio type | Indicates the type of portfolio (for example, check portfolio, promissory note portfolio). |
| Currency | Specifies the currency in which the portfolio transactions are conducted. |
| Bank account for collection | Specifies the bank account used for collecting checks or promissory notes. |

> [!NOTE]
> Each portfolio must be defined with a specific currency. A portfolio can only be used for transactions in the currency assigned to it.

To create a new portfolio, follow these steps:

1. Go to **Cash and bank management > Setup > Check and promissory note operations > Check and promissory note portfolio codes**.
1. Select **New**.
1. In the **Portfolio code** field, type a unique code.
1. In the **Portfolio name** field, enter a name for the portfolio.
1. Select an account type in the **Account type** field.
1. Select an account number in the **Account number** field.
   - If **Bank** is selected, select a bank account for accounting. 
   - If **Ledger** is selected, select a main account for accounting.
1. Select a portfolio type from the **Portfolio type** field.
    - **Check received**: Use this option for portfolios that track checks received from customers.
    - **Check given**: Use this option for portfolios that track checks issued by the company.
    - **Promissory note received**: Use this option for portfolios that manage promissory notes received from customers.
    - **Promissory note given**: Use this option for portfolios that track promissory notes issued by the company.
1. Select a currency in the **Currency** field.
1. Select a bank account for the collection in the **Bank account for collection** field. Select the bank account used as the offset account during check collection transactions for the portfolio.

## Define transaction codes for check and promissory note operations

This section explains how to define transaction codes to create a check and promissory note transaction in Finance.

The **Check or promissory note transaction codes** page is used to define standardized transaction codes for managing checks and promissory notes in Finance. 
These codes represent actions such as endorsement, collection, return, protest, or cancellation, and are essential for tracking the legal and financial status of commercial paper. 

Transaction codes are central to managing check and promissory note operations in Türkiye. 
Each type of check or promissory note movement, such as receipt, issue, transfer, collection, return, or bounce, is represented by a unique transaction code.

This page lets users configure these codes to support financial and legal processes, including automated posting, matching, and categorization. 
These codes are then used in the **Check and promissory note journal** to determine how each document is recorded and processed.

The page is used to:

  - Create codes that represent different types of financial movements for checks and promissory notes.
  - Assign behavior parameters to each code, such as whether it's a receipt, issue, collection, or return.
  - Link transaction codes with appropriate journal names and accounts to ensure correct ledger postings.
  - Enable automatic matching (settlement) of customer/vendor balances based on the selected transaction.

Here are the details for each field:

| Field                     | Description                                                                                                   |
|---------------------------|---------------------------------------------------------------------------------------------------------------|
| Transaction code          | Specifies a unique identifier (up to 10 characters) for the transaction.                                      |
| Against transaction code  | Used for transfer operations where two linked transactions are needed (receipt + issue).                      |
| Transaction code description | Specifies a descriptive name that explains the purpose of the transaction.                              |
| Journal name              | Specifies the journal name used when the check and promissory note journal is posted.                        |
| Receipt                   | Specifies that this code is used to receive a check/promissory note into a portfolio.                        |
| Issue                     | Specifies that this code is used to issue a check/promissory note from a portfolio.                          |
| Collection                | Specifies the transaction as a collection event for issued or received documents.                            |
| Return                    | Specifies the transaction as a return of a previously issued or received check/promissory note.              |
| Bounce check              | Specifies the transaction as a bounced check.                                                                |
| New check                 | Used when entering a new check or promissory note into the system.                                           |
| Against transaction code  | Specifies the related transaction code used in transfer transactions between portfolios.                     |
| Account type              | Specifies the offset account type: Customer, Vendor, Ledger, Bank, Portfolio, or COA.                         |
| Account number            | Specifies the default account to use when this transaction code is selected.                                 |
| Auto settlement           | Enables automatic matching of open customer/vendor balances when posting.                                   |
| Matching type             | Determines how matching is done (by due date, transaction date, etc.).                                       |
| Bank transaction type     | Optional field to classify bank-related check movements.                                                     |

To create a transaction code for the check and promissory note process:

1. Go to **Cash and bank management > Setup > Check and promissory note operations > Check or promissory note transaction codes**.
1. Select **New**.
1. In the **Transaction code** field, enter a unique code.
1. In the **Transaction code description** field, enter a name for the transaction code.
1. Select **Against transaction code**. This field specifies the related transaction code that is automatically triggered when the selected transaction code is used in a journal.
For example, when transferring a check between two portfolios, you can define an against transaction code to automatically generate both the outgoing and incoming movements within the same journal.
1. Assign a **Journal name** to specify which journal is used for posting.
1. Set the appropriate flags to define the behavior of the transaction in the relevant field:
   -  Select **Receipt** if the transaction represents the receipt of a check or promissory note.
   -  Select **Issue** if the transaction represents issuing a document.
   -  Select **Collection**, **Return**, or **Bounce check** as needed.
   -  Enable **New check** if this is the first entry of the document into the system.
1. In the **Account type** field, choose the type of account to post against (for example, Customer, Vendor, Ledger).
1. Select or enter the **Account number** if a default is required.
1. Select **Against transaction code** to link the outgoing and incoming movements if the transaction is part of a transfer (for example, between two portfolios).
1. Select **Auto settlement** if you want the system to automatically settle open transactions.
1. Choose a **Matching type** to define how settlements are matched (for example, by due date or transaction date).
1. Select or enter a **Bank transaction type** to track the check or promissory note in bank transactions.
1. Select **Save**.

The transaction code is now available for use in the **Check and promissory note journal** and related processes.

> [!NOTE]
> Select only the relevant flags for a single type of transaction. For example, don't select both **Receipt** and **Return**.

## Define bank branch names for check and promissory note operations

This section explains how to select bank and branch information for bank check records.
The **Bank branch name** defines and manages the relationship between banks and their branches in Türkiye. This information is essential for processes that require accurate identification of bank and branch codes, such as bank check transactions.
The **Bank branch name** supports users to configure and reference standardized bank and branch information based on the official registry used in the Turkish banking system. Each bank and its associated branches are uniquely identified by a combination of codes.

The following table explains each field.

| **Field** | **Description** |
| --- | --- |
| Bank groups | A unique numeric code representing the bank. |
| Branch code | A unique code representing the specific branch of the bank. |
| Bank branches | The name of the bank branch. |

Follow these steps to create a bank branch.

1. Go to **Cash and bank management > Setup > Check and promissory note operations > Bank branch name**.
1. Select **New**.
1. In the **Bank group** field, enter or select the bank group code.
1. In the **Branch code** field, type the branch code.
1. In the **Bank branches** field, type the branch name.
1. Select **Save**.

## Create a new check and promissory note journal

This article provides a detailed overview of the **Check and promissory note journal** in Finance. 

This feature enables organizations operating in Türkiye to manage and track financial transactions related to commercial papers—such as checks and promissory notes—in compliance with Turkish commercial law and local accounting standards.
You can use this journal for:

- Issuance or acceptance of a check or promissory note.
- Receipt or return of a check or promissory note.
- Endorsement checks to third parties.
- Collection or settlement of amounts in check or promissory note.

Each journal line is associated with predefined portfolios, transaction codes, and ledger posting profiles, which support accurate financial categorization and integration with the general ledger. 
This setup ensures that financial movements are posted automatically and in accordance with statutory requirements.

When you use this functionality, organizations benefit from:

- Automated posting processes for commercial paper transactions
- Full auditability and compliance with local financial regulations
- Maturity and rediscount tracking capabilities for checks and promissory notes
- Transparent and standardized journal entries for internal and external reporting

Each field is explained in the following table.

| Field  | Description  |
|-------------|----------|
| Check payroll number  | Specifies the unique, system-generated identifier for each journal line.         |
| Transaction code      | Indicates the type of transaction (for example, CK10 for receipt, CK20 for issue).     |
| Date                  | Specifies the transaction date for the check or promissory note.                 |
| Portfolio code        | Indicates the portfolio assigned to the document for classification and tracking.|
| Description           | Describes the purpose or nature of the transaction.                             |
| Reversal date         | Specifies the date when the transaction should be reversed, if applicable.       |
| Account type          | Indicates the account category involved (for example, Customer, Vendor, Bank).         |
| Account number        | Specifies the relevant account number for the transaction.                       |
| Posting profile      | Specifies the posting profile used to generate ledger entries.                   |
| Average maturity      | Indicates the calculated maturity date based on the document’s due date.        |
| Average maturity day  | Specifies the number of days from the transaction date to the maturity date.     |
| Journal batch number  | Specifies the system-generated identifier for the posting batch.                 |
| Posted                | Indicates the journal was posted to the ledger.                    |
| Reversal journal ID   | Specifies the ID of the journal created when reversing the transaction.          |
| Against transaction ID| Indicates the linked transaction (if part of a transfer or offset pair).        |
| Total                 | Specifies the monetary amount of the check or promissory note.                   |

Use these functions to create a journal.

Each button on the **Check and promissory note journal** is explained in the following table. 

| Button | Description   |
|---------|----------|
| New check             | Creates a new check or promissory note that will be manually registered.         |
| Select check          | Indicate that an existing check or note should be selected for processing.       |
| Post                  | Indicate that the journal will be submitted for financial posting.               |
| Journals              | Provides access to the source journal for a check and promissory note journal that has been posted to the ledger. |
| Check reversal journal| Describe the reversal of a previously posted journal for audit compliance.       |
| Transactions          | Indicate that the transaction history of the selected document will be displayed.|
| Check journal list    | Specify that a list of all check journal entries will be displayed for review.   |

To create a **Check and promissory note journal**, select **New** and go to the details page.

The **Check and promissory note journal – Header** view is used to enter the main details of a check or promissory note transaction. 
It helps users define how the document is processed by setting values like the transaction type, account information, portfolio, and dates. 
You can also enter additional information such as payment references or exchange rate settings if needed. 
These details ensure the transaction is recorded correctly, linked to the right accounts, and ready for posting or reversal.

Each field is explained in the following table.

| Field                      | Description                                                                                     |
|--------------------------------|---------------------------------------------------------------------------------------------|
| Check payroll number       | Specify the system-generated number that uniquely identifies the journal header.                |
| Transaction code           | Specify the movement type (for example, receipt, issue, return) using a predefined code.               |
| Journal batch number       | Specify the journal batch number that groups the transactions for posting.                      |
| Portfolio code             | Specify the portfolio in which the check or note is tracked (for example, PA10101).                    |
| Account type               | Indicate the type of related account: Customer, Vendor, Bank, Ledger, or Portfolio.             |
| Account number             | Specify the associated account number for the selected account type.                            |
| Against transaction code   | Indicate the linked transaction code in case of offset (for example, transfer between portfolios).     |
| Reversal date              | Indicate the date the reversal should occur, if applicable.                                     |
| Reversal journal number    | Indicate the ID of the reversal journal, if this transaction has been reversed.                 |
| Posted                     | Specify whether the transaction has already been posted to the general ledger.                  |
| Description                | Describe the purpose or context of the check/promissory note transaction.                       |
| Date                       | Specify the transaction date of the document.                                                   |
| Bank transaction type        | Specify the nature of the bank movement (optional).                                           |
| Payment reference            | Indicate the reference value associated with the payment.                                     |
| Payment ID                   | Specify an optional identifier for the payment.                                               |
| Activate fixed exchange rate | Indicate whether a fixed exchange rate should be applied to the transaction.                  |
| Fixed exchange rate type     | Specify the rate type used if fixed exchange rate is enabled.                                 |
| Exchange rate                | Specify the applicable fixed exchange rate.                                                   |
| Exchange rate type (Reporting Currency) | Specify the exchange rate type for the reporting currency context.                 |
| Exchange rate (Reporting Currency)       | Specify the exchange rate used for reporting purposes.                            |

## Create a received check or promissory note in Check and promissory journal

This section explains how to create a new check or promissory note entry using the **New check** page in the **Check and promissory note journal**. 

Use this form to manually register a new check or note, such as when a check is received from a customer or issued to a vendor.
Define the document’s identity, financial values, due dates, associated accounts, and ownership information. 
This structured data ensures accurate posting to the general ledger and full lifecycle tracking of the processes.

Each field on the **Summary** FastTab **Check definition** page is explained in the following table.   

| Field                    | Description                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| Currency                 | Indicates the currency of the check or promissory note.                     |
| Check due date           | Indicates the maturity date on which the check or note is payable.          |
| Check printing number    | Specifies the physical number printed on the check or promissory note.      |
| Amount                   | Specifies the monetary value stated on the check or note.                   |
| Portfolio type           | Specifies the portfolio where the check or note will be tracked.            |
| Account type             | Specifies the type of offset account (for example, Customer, Vendor, Ledger, Bank).|
| Account number           | Specifies the actual account number based on the selected type.             |
| Posting profile          | Indicates the posting profile to be used when creating ledger entries.      |
| Own check                | Specifies if the document is the company’s own check.                       |

Each field on the **General** FastTab **Check definition** page is explained in the following table.  

| Field                        | Description                                                         |
|------------------------------|---------------------------------------------------------------------|
| Drawer                       | Enter the name of the person or company who wrote the check.        |
| Date drawn                   | Specify the date on which the check was written.                    |
| Guarantor                    | Specify the guarantor (used for promissory notes).                  |
| Signed                       | Enter the name of the signer of the document.                       |
| Bank groups                  | Select the bank issuing or receiving the document.                  |
| Branch code                  | Specify the branch code of the bank associated with the transaction.|
| Bank account for collection  | Specify the related bank account number stated on the check.        |
| Bank branches                | Specify the bank branch name issuing or receiving the document.     |
| Bank transaction type        | Indicate the nature of the related bank transaction (optional).     |
| Payment reference            | Optionally enter a payment reference code.                          |
| Payment ID                   | Specify an identifier for payment transactions.                     |
| Activate fixed exchange rate | Enable this field if a fixed exchange rate is to be used.           |
| Fixed exchange rate type     | Specify the type of exchange rate if the fixed rate is activated.   |
| Exchange rate                | Specify the actual exchange rate value if fixed rate is used.       |
| Exchange rate type (Reporting Currency) | Specify the exchange rate used when reporting in different currencies. |

After selecting all relevant fields and values for the check or promissory note, select **Save**, and then select **Check transfer journal** in the ActionPane. 
You see the check or promissory record in the **Lines** tab in the **Check and promissory note journal**. 
The **Lines** Tab displays all transactions associated with selected checks and promissory notes. 

This section provides guidance on using the **Transactions** FastTab in the **Lines** Tab of the **Check and promissory note journal**. 
The **Transactions** FastTab offers you the ability to review the details of the selected line, access open, or settled transactions, and manage matching and cancellation activities directly from within the journal.

Add new lines from **New check** if needed, or delete existing lines using **Delete rows**. 

The following table explains each function in the **Transaction** FastTab. 

| Action   | Description  |
|------|--------|
| Delete rows            | Deletes the selected lines. |
| Open transactions      | Displays the open transactions for the account associated with the selected journal line. You can mark the transactions to be settled. Once marked, the matching is completed automatically during posting. |
| Settle transactions    | Displays the transactions for the accounts         |
| Transactions           | View all posted financial transactions associated with a specific customer or vendor account. It provides a detailed ledger view of each transaction, including invoices, payments, credit notes, settlements, and adjustments. |

## Settle check and promissory note with open transactions

This section explains the **Open Transactions** page, which you access from the **Lines** tab of the **Check and promissory note journal**. 
Use this page to settle checks and promissory note payments with open transactions in customer or vendor accounts.

To settle a transaction using a received check or promissory note, manually enter an amount to perform a partial settlement to apply only a portion of the check or note's value to the open transaction.

The following table explains each field in the **Open transactions** page. 

| Field  | Description |
|--------------------------|----------------|
| Marked                   | Indicates the open transaction to be settled by marking its checkbox. |
| Customer or vendor       | Indicates whether it's a customer or vendor transaction. |
| Account Number           | Specifies the account number associated with this transaction. |
| Name                     | Enter or display the name associated with this account number, typically a customer, or vendor name.  |
| Currency                 | Indicates the currency used for this transaction, such as TRY or EUR. |
| Amount                   | Specifies the total amount involved in this transaction in its respective currency value. |
| Open amount              | Specifies any remaining open amount that isn't settled for this transaction.|
| Remaining amount         | Indicates any remaining balance after partial settlements have been made on this transaction. |
| Amount to settle         | Specifies how much of this amount is intended to be settled during current processing. |
| Amount of manual settlement | Indicates any manually entered settlement amounts applied towards clearing balances. |
| Date                     | Specifies the date when action was taken on transactions such as settlement entries. |
| Due date                 | Specifies the due date by which the transaction is expected to be settled. |
| Invoice                     | Specifies the invoice number related to the customer or vendor transaction.  |
| Voucher                | Specifies the voucher number associated with the customer or vendor transaction. |

After marking an open transaction, select **Save**, and close the page. 
To transfer checks or promissory notes between portfolios for collection or payment, select the portfolio that contains the relevant check or promissory note. 
To do this, select **Select check**. 

## Send check or promissory note to portfolio account

This section provides an overview of the **Select check** page, which lets users retrieve and transfer previously registered check or promissory note records into the journal for further processing. 
The form shows eligible documents based on the selected portfolio and currency, ensuring accurate classification and compliance with Turkish financial processes.

This form lets users select commercial paper documents to transfer into the journal for processing. 
The list of records is filtered depending on the document type and its most recent transaction status:

- **Received checks and promissory notes:** The page displays documents that belong to the selected portfolio and have a last transaction code of type receipt.
- **Given checks and promissory notes:** Only documents that have been written but not yet collected are listed.

Each field in **Overview** FastTab is explained in the following table.

| Field   | Description    |
| ------------ | ----------------- |
| Currency                | Specifies the currency in which the check is issued.   |
| Check due date          | Specifies the date on which the check is due to be paid.  |
| Check printing number   | Specifies the number physically printed on the check.  |
| Amount                  | Specifies the monetary value of the check.  |
| Portfolio type          | Indicates whether the check is received or issued.  |
| Check payroll number    | Specifies the system-generated identifier for the payroll check.  |
| Account type            | Indicates whether the check is associated with a **Customer** or **Vendor** account. |
| Account number          | Specifies the relevant account number linked to the transaction. |
| Posting profile         | Specifies the posting profile to be used for generating ledger entries related to this transaction. |
| Own check | Specifies that the check is issued by the organization. |

Each field in **Receipt checks** FastTab is explained in the following table. 

| Field      | Description  |
| --------- | ----------|
| Drawer     | Specifies the name of the person or company that issued the check. |
| Date drawn | Indicates the date when the check was issued or drawn. |
| Guarantor  | Specifies the name of the guarantor, if applicable, responsible for the check payment. |
| Signed     | Indicates if the check was signed.  |
| Bank groups | Specifies the group of the bank where the check was drawn.  |
| Branch code | Specifies the bank branch code where the check was drawn. |
| Bank branches | Specifies the name of the bank branch name that issued the check.  |

To send the check or promissory note to the portfolio, select **Check transfer journal**, and close the page.
Then, select **Post** to generate a voucher.

After posting the journal to access the ledger journal and the voucher, select **Journals** in the **Daily** group. 

## Reverse check and promissory note journal

This section explains how to reverse a posted check and promissory note journal.
When you select the **Reverse journal** button on a posted check and promissory note journal, the system automatically creates a reversal journal that mirrors the original journal. 
The reversal is posted to the ledger and is linked to the original journal header to ensure full traceability.

To reverse the journal, follow these steps:

1. Go to **Cash and bank management > Check and promissory note operations > Check and promissory note journal**.
2. Select a posted journal that you want to reverse.
3. Select **Check reversal journal** in the **Cancel** group.
4. Select **OK** in the dialog page.
5. Enter or select a date in the **Date** field.
6. Select **OK** to post the reversal journal.

The reversal check journal links to the original check journal.
Access the related reverse transaction through the **Reversal journal ID** field in the **Check and promissory journal** list page.

## Maintain checks and promissory notes

This section explains how to view, filter, and manage check and promissory note records, and create company checks and promissory notes for payments using the **Check and promissory note definitions** page in Finance. 

This page offers a centralized view where all received or given checks and promissory notes are listed with key attributes such as type, amount, due date, portfolio, account, and transaction codes. 
It ensures accurate document tracking, supports financial transparency in the check lifecycle, and lets you create company checks or promissory notes for payments in Türkiye.

The **Check and promissory note definitions** page is used to:

- View and manage all previously defined check and promissory note documents.
- Filter checks based on attributes such as transaction type, due date, portfolio, account, or currency.
- Track the lifecycle of each check or promissory note including status, portfolio assignment, and associated transactions.
- Access related information such as printing number, account details, and movement records.
- Create and update company checks or promissory notes for payments. 

You can use the following filtering parameters to easily track all check and promissory note documents registered in the system:

| Parameter        | Description                                                           |
| ---------------- | ----------------------------------------------------------------------|
| Check type       | Specifies whether to view received or issued checks.                  |
| Receipt or issue | Specifies whether the last transaction was a receipt or issuance.     |
| Return           | Specifies whether the check has been returned.                        |
| Collection       | Specifies whether the check is in the collection process.             |
| Bounce check     | Specifies if the check has been marked as bounced.                    |
| Transaction code | Specifies the last transaction code used on the check.                |
| Portfolio code   | Filter checks based on their assigned portfolio.                     |
| Account type     | Specifies whether the related account is a customer, vendor, or bank. |
| Bank groups      | Filters by associated bank group.                                     |
| Account number   | Specifies the related customer/vendor/bank account.                   |

Select **Apply filter** to refresh the list based on the selected parameters and view details about the checks and promissory notes. 

Each field of the **Check and promissory note definitions** page is explained in the following table. 

| Field                  | Description                                                          |
|------------------------|----------------------------------------------------------------------|
| System number of check | Displays the internal unique number of the check or promissory note. |
| Check type             | Indicates whether the document is a received or company (given) check. |
| Check printing number  | Specify the number physically printed on the check.                   |
| Due date               | Displays the check’s maturity date.                                  |
| Due days               | Displays the number of days between the entry date and the due date. |
| Currency               | Displays the transaction currency (for example, TRY, EUR).                  |
| Amount                 | Displays the value of the check or promissory note.                  |
| Cancel                 | Indicates whether the check has been canceled.                      |
| Portfolio code         | Displays the assigned portfolio to which the check belongs.          |
| Transaction code       | Shows the last applied transaction code on the check.                |
| Portfolio entry date   | Indicates the date when the check was entered into the portfolio.    |
| Own check              | Specifies if this is an internally issued check (owned by the company).  |
| Account type           | Displays the type of account related to the check (for example, Customer, Bank).|
| Account number         | Shows the related customer/vendor/bank account.                      |
| Name                   | Displays the name of the related customer/vendor/bank.               |
| Check payroll number   | Shows the payroll reference number to which the check is assigned.   |
| Check movement number  | Shows the last movement document number associated with this check.  |
| Is in use              | Indicates whether the check is currently being used in a transaction. |

### Create company checks or promissory notes for operations

This section provides guidance for creating new check or promissory note records using the **Create a new document** pane on the **Check and promissory note definitions** page in Finance. 
This feature is part of the Turkish localization and supports generating blank checks in bulk with predefined structures and numbering logic.

The form enables users to define portfolio ownership, numbering format, and bank association. 
Once completed, the new check documents are created and automatically added to the system, ready for operational use in payment or collection processes.

Each field on the **Create a new document** page is explained in the following table. 
    
| Field                       | Description                                                                                      |
| --------------------------- | ------------------------------------------------------------------------------------------------ |
| Portfolio code              | Specifies the portfolio where the newly created checks or notes are recorded.                |
| Bank groups                 | Specifies the bank group to which the checks belong.                                             |
| Bank account for collection | Indicates the bank account that is associated with the collection of these checks.          |
| Bank branches               | Specifies the relevant branch of the bank where the checks are held.                             |
| Starting number             | Specifies the starting numeric value to be used when generating the check numbers.               |
| Number of digits            | Defines how many digits will be included in the numeric part of the check number (for example, 3 → 001).|
| Check printing number       | Specifies a prefix or format that will appear as the printed check number.                       |
| Unit to be created          | Indicates the total number of check or note records to be generated using the specified pattern. |

> [!NOTE]
> In the **Portfolio code** parameter, only the portfolio codes with a **Portfolio type** of **Check given** or **Promissory note given** from the **Check and promissory note portfolio codes** page are listed.

To create company checks and promissory notes, follow these steps. 

1. Go to **Cash and bank management > Inquiries and reports > Check and promissory note operations > Check and promissory note definitions**.
1. Select **New**.
1. Select **Create promissory note** or **Create check** options that you need.
1. In the **Create a new document** page, select the portfolio code to which the check or promissory note will be assigned in the **Portfolio code** parameter.
1. Select the bank group to which the check or promissory note belongs in the **Bank groups** parameter.
1. Select the bank branch that is associated with the collection of checks.
1. Define the **Starting number** as "1" and **Number of digits** as "3", resulting in check numbers like CHC-001, CHC-002, CHC-003 etc.
1. Type a printing number such as "CHC-", in the **Check printing number** field.
1. Type the number of units to be created as "3."
1. Select **OK** to create.

The system lists these checks or promissory notes in the **Check and promissory note definitions** page, ready for transactions in the **Check and promissory note journal**.

### Update check or promissory note information

This section provides guidance on updating existing check or promissory note records using the Update check or promissory note function in the Check and promissory note definitions page in Finance. 

This function is used when a previously registered check or promissory note needs to be corrected or updated with new values, such as changing the portfolio, amount, or due date.
To update a check or promissory note, use the **Check or promissory note update** function: 

1. Select check or promissory note that you want to update in the list.
1. Select **Check or promissory update**.
1. Update the portfolio code in Portfolio code parameter if it's needed.
1. Enter or update the amount of the check or promissory note in **Amount** field.
1. Enter or update the due date in **Due date** field.
1. Select **Update**. 

> [!NOTE]
> To use the generated company checks or promissory notes in the **Check and promissory note journal**, you must enter the **Amount** using the **Check and promissory note update** function.

**Cancel** invalidates checks or promissory notes that haven't been used in any financial transactions or that have been returned. 
You can only use this action for documents that meet the cancellation criteria based on their current status.

You can use the **Check or promissory note transactions** to access the transactions for the relevant check or promissory note. 

## Configure rediscount calculations for check and promissory note operations

This section provides guidance on performing rediscount calculations for checks and promissory notes using the Rediscount Calculation page in Finance. 

Rediscounting is a financial operation in Türkiye, typically performed at the end of the fiscal period to reflect the current value of checks and promissory notes that haven't matured yet.
The rediscount calculation feature lets organizations compute interest income or expenses for postdated commercial papers and reflect them accurately in the general ledger.

The rediscount calculation functionality helps:

  - Calculate interest income for receivable checks and promissory notes
  - Calculate interest expense for payable checks and promissory notes
  - Generate rediscount journal entries automatically
  - Reverse rediscount journals in the following fiscal period

Use the **Accounts** FastTab to define ledger accounts for receivable and payable rediscount transactions. 
The default accounts are retrieved automatically from the **Check and promissory note parameters**.

The journal numbers for the current period and the next period, including those used for reverse posting, show in the **Posting** FastTab.
View information about the check and promissory notes after rediscount calculation in the **Lines** FastTab.

Each field is explained in the following table. 

| Field                          | Description                                        |
|--------------------------------|----------------------------------------------------|
| System number of check         | Displays the unique number assigned to each check.  |
| Check printing number          | Specifies the date when the check was received. |
| Portfolio type                 | Indicate the type of portfolio associated with the check, such as received or issued. |
| Portfolio code                 | Specifies the portfolio code of the check or promissory note. |
| Transaction code               | Specifies the code that represents the type of transaction being recorded. |
| Transaction name               | Specifies the name of the transaction code. |
| Transferring customer          | Specifies the customer account that originally submitted the check or promissory note when it was first entered into the system. |
| Transferring customer name     | Specifies the customer name of transferring customer.   |
| Own check                      | Specifies if the document is the company’s own check. |
| Currency                       | Displays currency of the check or promissory note.  |
| Amount in transaction currency | Displays the amount of the check or promissory note in transaction currency.  |
| Check due date                 | Indicates the due date of the check or promissory note. |
| Due day by reference date      | Indicates the day difference between check due date and reference date. |
| Exchange rate                  | Indicates the currency exchange rate in which the check amount is due.  |
| Rediscount amount              | Specifies the rediscount amount after rediscount calculation. |

### Define interest rates for rediscount calculation

This section provides guidance on defining interest rates that will be used during rediscount calculations for checks and promissory notes in Finance. 
Rediscount interest rates apply to checks and promissory notes that haven't matured yet at the end of the fiscal period.

Defining interest rates ensures accurate rediscount value calculations and proper posting to general ledger accounts.
Define the interest rates based on currency for the check or promissory notes.

Each field on the **Interest rates** page is explained in the following table.

| Field             | Description                                             |
| ----------------- | ------------------------------------------------------- |
| Date              | Specifies the reference date of interest rate.          |
| Currency          | Specifies the currency of the interest rate.            |                          
| Interest rate (%) | Indicates the interest rate for rediscount calculation. | 

> [!NOTE]
> Make sure the legal rediscount rate is published by the Central Bank of the Republic of Türkiye (CBRT).

## Calculate rediscount amount for checks and promissory notes

This section provides an overview of the rediscount calculation logic for checks and promissory notes in Finance, specifically within the Turkish localization.

Rediscounting is a financial adjustment process for post-dated checks and promissory notes that aren't yet matured at the end of the fiscal period. 
This process reflects the time value of money by rediscounting the future receivable or payable to its present value.

In Türkiye, rediscount calculations are typically done at month-end or year-end for both customer (receivable) and vendor (payable) documents. The system calculates the rediscount amount using three key factors:
  
  - The number of remaining days until maturity
  - The applicable interest rate
  - The nominal value of the document

Automating rediscount journal postings and reversals lets organizations maintain compliant and accurate financial records while reducing manual work. 
Rediscount entries reverse in the next fiscal period, restoring the original document value after fulfilling reporting requirements.

The parameters on the **Check and promissory note rediscount calculation** page are explained in the following table.  

| Field                  | Description                                                                                |
|------------------------|-----------------------------------------------------------------------------------------------|
| Version ID             | Specifies the version code for the period in which the discount calculation will be performed. |
| Current reference date | Defines the reference date for the discount calculation. The period reference date must be the last day of the month. |
| Next reference date    | Defines the reference date for the next period's discount calculation. The next period reference date must be the first day of the month and can't be before the period reference date. The system records a reverse entry for this date. |
| Exchange rate type     | Specifies the type of currency for foreign currency checks and notes. The value defined in the check-note parameters is used as the default.     |
| Detail level           | Specifies the level of detail for the journal entry when the discount values are posted. The value defined in the check-note parameters is used as the default. |
| Journal name           | Specifies the journal that is used to post the rediscount transaction. |
| Posted                 | Indicates whether the rediscount journal has been successfully posted. |

Follow these steps to create a rediscount calculation. 

1. Go to **Cash and bank management > Inquiries and reports > Check and promissory note operations > Check and promissory note rediscount calculation**.
1. Define the interest rate for the relevant period in **Interest rates** page and select **Save** and close the page.
1. Select **New**.
1. Type a **Version ID** manually.
1. In the **Current reference date** parameter, enter or select a date.
1. In the **Next reference date** parameter, enter or select a date.
1. Select or update the exchange rate type in the **Exchange rate type** parameter if it's needed.
1. Select an option for calculation in **Detail level** parameter.
1. Select a journal name for posting the calculation results in the **Journal name** parameter.
1. Select **Save**.
1. Select **Calculate** to calculate the rediscount amounts.
1. Select **Post**. 

After posting, you see the journals in the **Journals** group in the **Postings** FastTab.
To reverse the rediscount journals, select **Reverse** in the ActionPane. The reversal journal appears in the **Reversal journals** group in the **Postings** FastTab.

## Check or promissory note transactions

This article lists all posted transactions related to checks and promissory notes. It also lets you track and monitor these financial documents.
It lets you define and manage the types of movements applied to checks and promissory notes in the system.

Each transaction code represents a financial operation, such as:

- Receiving a check/note from a customer
- Issuing a promissory note to a vendor
- Transferring a check between portfolios
- Endorsing or protesting a note
- Handling collection, return, or bounce

To access the check or promissory note transactions, go to **Cash and bank management > Inquiries and reports > Check and promissory note operations > Check and promissory note transactions**. 

Each field on the overview FastTab is explained in the following table. 

| Field | Description |
|------|-------|
| Check movement number           | System-generated number for tracking the movement of checks. |
| System number of check          | Unique identifier assigned by the system to each check.  |
| Check printing number           | Number assigned to a check when it's printed. |
| Check type                      | Specifies the type of check (for example, received, issued). |
| Portfolio code                  | Code representing the portfolio to which the check belongs. |
| Name                            | Name associated with the transaction.  |
| Transaction code                | Code representing the type of transaction.  |
| Check due date                  | Date by which the check is due. |
| Currency                        | Currency in which the check is issued. |
| Amount                          | Amount of the check. |
| Account type                    | Type of account involved in the transaction (for example, customer, vendor). |
| Account number                  | Account number associated with the transaction. |
| Posting profile                 | Profile used for posting the transaction. |
| Date                            | Date of the transaction. |
| Journal batch number            | Batch number of the journal entry. |
| Voucher                         | Voucher number associated with the transaction. |
| Posted                          | Indicates whether the transaction has been posted. |
| Is in use                       | Indicates whether the check is currently in use. |
| Check reversal transaction number | Transaction number for the reversal of the check. |

Each field on the general FastTab is explained in the following table.

| Field | Description |
|------|-------|
| Bank transaction type           | Specifies the type of bank transaction.           |
| Payment reference               | Reference number for the payment.                 |
| Payment ID                      | Unique identifier for the payment.                |
| Fixed exchange rate             | Indicates whether a fixed exchange rate is used.  |
| Activate fixed exchange rate    | Option to activate the fixed exchange rate.       |
| Fixed exchange rate type        | Type of fixed exchange rate used.                 |
| Exchange rate                   | Exchange rate applied to the transaction.         |
| Reporting currency              | Currency used for reporting purposes.             |
| Exchange rate type              | Type of exchange rate used.                       |

The buttons on the **Check or promissory note transactions** page are explained in the following table.

| Button | Description |
|------|-------|
| Reverse transaction  | Reverse a posted transaction.  |
| Check and promissory note definitions | Access the definitions and parameters set for checks and promissory notes. |
| Check and promissory note journal | Access the check and promissory note journal entries.|
| Journal | Access the posted check and promissory note journal entries related to checks and promissory notes.|


This feature improves control, ensures compliance, and makes check and promissory note operations easier and more reliable.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
