---
title: e-Ledger (preview)
description: Learn how to use e-Ledger in the Republic of Türkiye. 
author: v-omerorhan 
ms.author: v-omerorhan 
ms.topic: overview 
ms.date: 05/23/2025 
ms.reviewer: johnmichalak
ms.search.region: Türkiye 
ms.search.validFrom: 2020-02-03 
ms.search.form: ELedger 
ms.dyn365.ops.version: 10.0.9 
ms.assetid: b2b22868-de68-439f-914c-78c6930b7340
---

# e-Ledger (preview)

[!INCLUDE[banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article provides detailed instructions on how to configure various parameters for the e-Ledger, including document type mapping, payment methods to main accounts, exclusion of posting layers, dimensions to main accounts, and chart of accounts, and how to create the e-Ledger file and reports.

The e-Ledger is a legal and technical framework that collects general ledger records in a journal book and helps to prepare mandatory books in an electronic format in Türkiye. These books must adhere to the specified formats and standards, guaranteeing their immutability, integrity, and source accuracy, and can be used as evidence before authorities. The framework utilizes the internationally adopted XBRL (eXtensible Business Reporting Language) standard for electronic preparation. 

## Configuring e-Ledger

This section explains how to configure e-Ledger to create e-Ledger files and statutory reports in Microsoft Dynamics 365 Finance.

### Configuring electronic reporting for e-Ledger

Generating e-ledger books in electronic formats utilizes **[Electronic reporting (ER)](../../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md)**.
The e-Ledger configurations extend the **Standard Audit File (SAF-T)** configuration:

| Number | ER configuration name | Type | Description |
|---|---|---|---|
| 1 | e-Ledger Model (TR) | Model | It is an abstract, application-independent data structure that defines business concepts used to map Dynamics 365 data for generating reports.  |
| 2 | e-Ledger Model Mapping (TR) | Model mapping | The configuration sets the structure and data mapping for Türkiye's electronic ledger system, ensuring data is correctly formatted for electronic reporting.|
| 3 | Statutory General Journal (TR) (Excel) | Format (exporting) | It is an electronic format that defines the structure and establishes how data is organized and mapped for the General Journal report. |
| 4 | Statutory Ledger Book (TR) (Excel) | Format (exporting) | It is an electronic format that defines the structure and establishes how data is organized and mapped for the Ledger Book report.​ |
| 5 | XBRL GL (TR) (XML) | Format (exporting) | It is an electronic format that implements the XBRL taxonomy that standardizes financial and business information in Türkiye.  |
| 6 | General ledger data model mapping | Model mapping | It is used to extract and structure financial data from Dynamics 365 for generating regulatory and statutory reports such as e-Ledger and SAF-T.  |

You must import the latest versions of the following ER configurations:

- e-Ledger Model (TR)
  - e-Ledger Model mapping (TR)
  - Statutory General Journal (TR) (Excel)
  - Statutory Ledger Book (TR) (Excel)
  - XBRL GL (TR) (XML)
- General ledger data model mapping

To do this, go to the **Electronic reporting** workspace, and import the ER configurations to generate e-Ledger files and reports for Türkiye. 
For more information about how to import the electronic reporting formats, see [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

To configure application-specific parameters of the **XBRL GL (TR) (XML)** format, follow these steps: 

1. Go to **Workspaces > Electronic reporting**, and select **Reporting configurations**.
2. Select the **XBRL GL (TR) (XML)** configuration, and then select **Setup** in **Configurations > Application specific parameters**.
3. On the **Application specific parameters** page, on the **Lookups** FastTab, select **ELedgerSetup_Lookup**  in the **Name** field.
4. On the **Conditions** FastTab, set the following fields:

| Field         | Description  |
|---------------|--------------|
| Lookup result | Select the _lines_. |
| Lines         | Set the number of XML nodes in a branch file. This field is used to define the maximum file size allowed by the integrator. Based on the value specified here, the number of vouchers to be included in each generated XML file is determined. You can update this field as needed according to the applicable limits.|

### e-Ledger parameters

The e-Ledger parameters need to be configured before generating the e-Ledger, including document type mapping, payment methods to main accounts, posting layers exclusion, dimensions to main accounts, and the chart of accounts. 
This setup ensures that the e-Ledger records are generated correctly for multiple or single branches.
e-Ledger parameters page can be accessed from **General ledger > Ledger setup > e-Ledger parameters**.

Here are the details for each Tab: 

- **General**

This Tab is used for defining single and multiple branch structures and configuring **Batch thread** definitions within the e-Ledger. Additionally, it allows setting up format mappings to generate e-Ledger files and reports efficiently.
Before selecting format mappings, please check the [Configuring electronic reporting for e-Ledger](#configuring-electronic-reporting-for-e-ledger). These mappings should be defined beforehand.

Microsoft Dynamics 365 Finance supports the generation of e-Ledger files and reports on a branch basis.
Branch IDs can be defined as financial dimension values, and each branch ID can be mapped to a corresponding financial dimension value.
e-Ledger files and reports can be generated for each branch, and the necessary configurations can be set up accordingly.

> [!NOTE]
> The financial dimension that includes the branch IDs must be selected in the account structures. Additionally, the journal entries required for the e-Ledger must contain the branch ID value.
To generate e-Ledger files on a multi-branch basis, you must first enable the **Enable reporting per branch** parameter.
The financial dimension containing the branch IDs should be selected in the **Dimension name** field.
In the **Branch mapping** FastTab, each branch must be defined with its branch ID and branch name.
Each branch ID should be mapped by selecting the relevant financial dimension value in the **Dimension value** field.
The worker responsible for generating e-Ledger files and reports for the branches must also be specified.

If the e-Ledger will be generated for a single branch only, the parameters in the **Branch** FastTab, located in the **Branch information** group, should be used.

| **Field** | **Description** |
| --- | --- |
| Single journal number per voucher | Provides to combine the journals and get one journal item number in case of a voucher has multiple journals. |
| Format mapping | Provides to set the structure and data mapping for e-Ledger, currently **XBRL GL (TR) (XML)** option is available based on XBRL-GL format. |
| Maximum batch threads when sending to e-Ledger pool | Specify the number of values entered in the batch chain when sending to the e-Ledger pool. |
| Format mapping for ledger book | Select the electronic reporting format to be used to generate the Ledger Book report. |
| Format mapping for general journal | Select the electronic reporting format to be used to generate the General Journal report. |
| e-Ledger branch ID | Specify the e-Ledger branch ID. |
| Branch name | Specify the e-Ledger branch name. |
| Document creator | Specify the creator of the e-Ledger file. |
| Enable reporting per branch | Enables to create reports and e-Ledger file per branch. |
| Dimension value | Specify the dimension name in order to map to relevant branch. |

- **Document type mapping**

This Tab is used to configure and update e-Ledger records, including transaction types, document types and descriptions, and payment method details, based on voucher filters.
Voucher filter must be defined and fulfilled in order to find relevant transactions to map and update e-Ledger records.

<table><tbody><tr><th><p><strong>Field</strong></p></th><th><p><strong>Description</strong></p></th></tr><tr><td><p>Transaction type</p></td><td><p>Provides the ability to find the relevant voucher transactions according to the transaction type and the voucher filter.</p></td></tr><tr><td><p>Voucher filter</p></td><td><p>The voucher filter is also defined in order to find the relevant voucher transactions. Here, definition should be done by defining the prefix part of the voucher series and adding “*” at the end.</p><p>For example, if the voucher is "MH00001" and the transaction type is "General journal," the definition should be as follows:</p><ul><li><strong>Transaction Type:</strong> General journal</li><li><strong>Voucher Query Filter:</strong> MH*</li></ul><p>If the query filter includes more than one transaction type, the same voucher query filter can be applied to each transaction type. For example, if vouchers starting with "MH*" contain both the "General journal" transaction type and an empty transaction type, the configuration would be as follows:</p><ul><li><strong>1st line:</strong><ul><li><strong>Transaction Type:</strong> General journal</li><li><strong>Voucher Query Filter:</strong> MH*</li></ul></li><li><strong>2nd line:</strong><ul><li><strong>Transaction Type:</strong> (empty)</li><li><strong>Voucher Query Filter:</strong> MH*</li></ul></li></ul><p>This ensures that the relevant transactions are properly filtered and identified based on their voucher series and transaction type.</p></td></tr><tr><td><p>e-Ledger document type</p></td><td><p>This field is used to select the <strong>Document type</strong>, which enables the automatic generation of document numbers for voucher transactions. The <strong>Document type</strong> should be chosen from the predefined prefix values listed below.</p><ul><li>Check</li><li>Invoice</li><li>Order-customer</li><li>Order-vendor</li><li>Voucher</li><li>Freight</li><li>Receipt</li><li>Other</li></ul></td></tr><tr><td><p>Document type description</p></td><td><p>If the <strong>e-Ledger document type</strong> is <strong>Other</strong>, depending on the legislations, the system allows you to enter a manual description in order to explain the type of the document type.</p></td></tr><tr><td><p>e-Ledger method of payment</p></td><td><p>The system enables the automatic assignment of payment methods to the relevant main accounts in the e-Ledger items, based on the <strong>Payment method mapping</strong> assigned to the main accounts.</p></td></tr><tr><td><p>Use payment method mapping</p></td><td><p>If a <strong>Payment method mapping</strong> will be used, the <strong>Use payment method mapping</strong> field must be marked. When it is marked, e-Ledger items is updated according to the definition in the <strong>Payment method mapping</strong> Tab.</p></td></tr><tr><td><p>Worker</p></td><td><p>e-Ledger must include information about the worker who created each voucher. If this field is left empty, the worker information of the worker who created the voucher will be automatically assigned. However, if a selection is made in this field, the selected worker information will be used when generating the e-Ledger.</p></td></tr></tbody></table>

- **Payment method mapping**

This Tab is used to define method of payment based on main account filters. 

Payment methods must be reported in the e-Ledger for vouchers created for payment and collection transactions. 
In the system, payment and collection vouchers are defined on a main account basis, enabling the automatic assignment of payment methods in the e-Ledger items.

| **Field** | **Description** |
| --- | --- |
| e-Ledger method of payment | It is the field where each method of payment is defined as text in order to map payment types for vouchers. |
| Main account filter | It is the field where ledger account filter is defined. Here, definition should be done by defining the prefix part of the main accounts with adding “\*” at the end. |

- **Posting layer mapping**

This Tab allows you to select specific layers to be excluded from the e-Ledger reports and e-Ledger file. This ensures that when generating the e-Ledger, vouchers from the excluded layers are not included in the e-Ledger.

| **Field** | **Description** |
| --- | --- |
| Posting Layer | This field is used to categorize different types of financial transactions into distinct layers. |
| Exclude | This function allows to select which posting layers should be included in the e-Ledger. The **Current** posting layer is used to generate the e-Ledger. |

- **Dimension mapping**

This Tab is used to display the names of financial dimensions instead of the main account names in the **General journal account entry** FastTab in the **Ledger item number** page.

| **Field** | **Description** |
| --- | --- |
| Append dimension value to main account | This parameter is used to add a dimension value to the main account based on the defined parameters in the dimension mapping table. |
| Main account | The main account to which the name of the financial dimension value should be assigned is selected. |
| Dimension name | In the **General journal account entry** FastTab, in the **Account name** field, the financial dimension value whose name is to be displayed instead of the selected main account name is chosen. |

- **e-Ledger chart of accounts**

This Tab is used to define the e-Ledger chart of accounts for e-Ledger files and reports.

e-Ledger files and reports can be generated using a chart of accounts that differs from the one used by the legal entity (for example, the Turkish Uniform Chart of Accounts).
The e-Ledger chart of accounts allows you to map the main accounts required for e-Ledger reporting to financial dimension values. 
For each financial dimension value, a main account code and main account name are defined to complete the mapping. 

e-Ledger files and reports are then generated based on this mapping.
When e-Ledger journal entries are created, the information related to the Turkish chart of accounts, manually mapped with the financial dimension value, is written into the relevant fields in the **Ledger item number** page in the **General journal account entry** FastTab.

To configure this, select the appropriate financial dimension in the **Dimension name** field. You can then define the corresponding e-Ledger main accounts for each dimension value. The resulting e-Ledger files and reports will be created using these defined mappings.

| **Field** | **Description** |
| --- | --- |
| Enable e-Ledger chart of account | If this parameter is enabled, the defined account, account description, account group code, and group description will be shown instead of the financial dimension value in the journal ledger and the e-Ledger. |
| Dimension value | The financial dimension used to track the main accounts of the Turkish chart of accounts is selected. |
| e-Ledger main account | The main account value that should appear instead of the dimension value is defined. |
| e-Ledger main account description | The name of the main account that should appear instead of the financial dimension description is defined. |
| e-Ledger account group code | The 3-digits total account code to which the account defined in the e-Ledger main account field belongs is defined |
| e-Ledger account group description | The description of the total account code defined in the e-Ledger account group code field is entered. |

## e-Ledger process

This section provides detailed information about the steps to be followed, the relevant pages, and the fields on those pages for generating the e-Ledger file and statutory reports.

In Microsoft Dynamics 365 Finance to generate the e-Ledger file and statutory reports, the steps explained as below must be followed:

1. **Updating period status**: The status of the relevant ledger calendar period must be changed to **On hold**.
1. **Journal item numbering**: This process involves enumerating journal entries from the beginning of the year. It is necessary to perform journal item numbering after the period is on hold or closed.
1. **Ledger item number**: After journal item numbering, the journal lines page displays the data. This screen allows for the manual or automatic filling of necessary fields before sending the e-Ledger.
1. **e-Ledger pool**: Once the journal lines are updated, the records are sent to the e-Ledger pool. This step involves creating files on a branch basis and exporting them as XML or zip files to be uploaded to the Turkish Revenue Administration (GIB).
1. **Reporting e-Ledger**: This step involves creating files on a branch basis and exporting them as XML or zip files to be uploaded to the Turkish Revenue Administration (GIB). The statuory reports also covers how to inquire about statutory ledgers and e-Ledger records, including voucher transactions and ledger items.

After the status of the relevant fiscal period is updated, the necessary e-Ledger processes are carried out on the **General ledger > Period close > e-Ledger and statutory** page.
This page displays the e-Ledger periods and their statuses, the debit and credit totals for each branch for the relevant periods, the last assigned journal item numbers, and the e-Ledger file status.

  - **Statutory ledgers** 

This FastTab provides an overview of the e-Ledger files and reports generated for each branch ID.
It allows for comparing the total debit and credit amounts after journal entries are created with the totals after those entries are sent to the e-Ledger pool.
It also enables tracking of the periods and branches for which e-Ledger files have been generated.

| **Field** | **Descriptions** |
| --- | --- |
| e-Ledger branch ID | Displays the branch ID. Ensures that e-Ledger records are shown based on the branch ID. |
| Journal item numbered | Specifies whether journal item numbering has been performed for the relevant branch. |
| Last journal item number | After the journal item numbering process is completed, the last item number assigned for that period is updated in this field. |
| Journal debit total | After the journal item numbering is completed, this field displays the total debit amount for the relevant branch. |
| e-Ledger debit | After the ledger items are sent to the e-Ledger pool, this field displays the total debit amount of the journal entries for the relevant branch. |
| Journal credit total | After the journal item numbering is completed, this field displays the total credit amount for the relevant branch. |
| e-Ledger credit | After the ledger items are sent to the e-Ledger pool, this field displays the total credit amount of the journal entries for the relevant branch. |
| Debit balanced | If the **Journal debit total** matches the **e-Ledger debit amount** for the relevant branch, this field will be marked. |
| Credit balanced | If the **Journal credit total** matches the **e-Ledger credit amount** for the relevant branch, this field will be marked. |
| Sent | On the **e-Ledger pool** page, this field is marked after the e-Ledger file is generated. Once the file is created, no further changes are allowed on the e-Ledger for the relevant branch. |

### Changing status of a Ledger calendar period

This section explains how to change the status of a ledger period to create an e-Ledger file.
To generate an e-Ledger file, the related period status must be changed first. To do this, navigate to the **Ledger calendar** page and set the legal entity period status to **On hold**.

You can access the **Ledger calendar** page via **General ledger > Calendars > Ledger calendars**. In the **Ledger calendars** page;

1. Select **Calendar**.
2. Select **Fiscal year**.
3. Select the period that you want to create e-Ledger file.
4. In the **Legal entities** FastTab, select **Legal entity**.
5. Select **On hold** in the **Period status** field.
6. Click **Save**.

The system automatically generates the ledger calendar with a total of 14 periods, including each month, an **Opening** and a **Closing** period. The status of the **Opening** period is set to **Permanently closed**, while the **Closing** period status is set to **On hold** until the entire ledger calendar is closed.
The e-Ledger can only be generated for the periods in between; it cannot be created independently for the **Opening** or **Closing** periods. The **Opening** period is combined with **Period 1** and the **Closing** period is combined with **Period 12** when generating the e-Ledger.

### Assigning journal item numbers

This section explains how to assign journal item numbers to the voucher transactions in e-Ledger.

Each journal item must have a unique number which should be assigned according to dates.
The journal item numbering process is managed from **e-Ledger and statutory ledger** page. To apply the process, the journal item numbering must be completed for all periods starting from the beginning of the year. 
Journal item numbering should also be done for Period 0 (the Opening period), with the first item number assigned to the opening voucher. 
If the e-Ledger is generated based on branches, journal item numbering must be applied separately for each branch.

In order to assign the journal item numbers, first need to navigate the **e-Ledger and statutory ledger** page in **General ledger > Period close > e-Ledger and statutory ledger**. 
Then, click the **Assign journal item numbers** in **Ledger item number** group in **Statutory ledger** Tab. 
This will create the ledger items and will assign a unique number to each voucher transaction in the e-Ledger.

To generate ledger items and assign journal item numbers for the e-Ledger of the next period, the current period must be properly closed and the e-Ledger must be finalized. 
Even if there are no transactions in the relevant period, the **Assign journal item numbers** process must still be completed to enable the generation of the e-Ledger for the following period.

The following table explains the parameters available on the dialog page that appears when you click **Assign journal item numbers**.

| **Field** | **Description** |
| --- | --- |
| Reference | This parameter indicates the period to which the ledger item numbers are to be assigned. |
| Exclude for zero value voucher in all rows | During the journal item numbering process, if all lines of a voucher have a total value of zero, no journal item number is assigned to those lines. If one line in the voucher has a value of zero, a journal item number will be assigned to that line, but the line will not be created in the e-Ledger. |

### Removing journal item numbers

If the journal item numbering has been performed and the e-Ledger file has not yet been created, the numbering process can be reverted using this button.
When the numbering is reverted, the e-Ledger records will be deleted both from the **Ledger item number** page and from the **e-Ledger pool**. If the e-Ledger records have already been created, the numbering process cannot be reverted.

### Ledger item number

The **Ledger item number** button is used to access the journal entry lines which will be recorded in the e-Ledger file after journal item numbering has been performed.
You can access the **Ledger item number** for the relevant period in **Statutory ledgers** tab in **e-Ledger** group in **General ledger > Period close > e-Ledger and statutory ledger** page.
After clicking **Assign journal item numbers**, the relevant fields are automatically populated based on e-Ledger parameters, and the corresponding e-Ledger items are generated.

| **Button** | **Descriptions** |
| --- | --- |
| Send to e-Ledger pool | This button sends created e-Ledger items to the pool in order to fix related records in the e-Ledger file to be created. It will also allows you to change beginning number of voucher line numbering . |
| e-Ledger pool | This button redirects to the e-Ledger pool containing the submitted records. |

 - **Overview**

This FastTab allows you to manage and review ledger items for e-Ledger. 
It includes options to refresh fields, automatically populate required information, or manually update these fields.

Before creating the e-Ledger file and statutory reports, the required fields must be populated. 
The **Overview** FastTab contains key information related to the journal items that will be displayed in the e-Ledger.
For the selected period and branch, it includes mandatory e-Ledger fields such as the journal item number, document type, document type description, document date, method of payment, and the worker who created the voucher.

After assigning journal item numbers for the e-Ledger, the journal entries for the period are generated. Based on the definitions made in the parameter page, the required fields for the e-Ledger are automatically populated.
Using the **Manual** button, the **Document type**, **Document type description**, and **Payment method** fields can be updated manually.
The **Automatic** button allows these fields to be refreshed automatically, based on the parameter configurations.
To view the voucher transactions for a journal, click the **Voucher transactions** button.

Once the necessary updates are completed in the **Overview** FastTab, the records are sent to the **e-Ledger pool** by clicking for e-Ledger file and report generation.

For detailed information about the buttons and fields, see the following section:

| **Button** | **Descriptions** |
| --- | --- |
| Refresh | This function refreshes the fields on the e-Ledger summary page. |
| Automatic | It automatically fills the necessary fields before sending the e-Ledger based on the pre-configured e-Ledger parameters. Automatic option will update all records sync with the latest e-Ledger parameters once its clicked. |
| Manual | This funtion enable to fulfill necessary fields manually per record before sending the e-Ledger. The e-Ledger document type, document type descriptions, payment method can be updated according to the branch. |
| Voucher transactions | It allows access to journal entry for the relevant ledger item.|

| **Field** | **Description** |
| --- | --- |
| Ledger item number | Displays the journal item number. |
| e-Ledger branch ID | Defines the branch ID. |
| Document date | Displays the document date. |
| Voucher | Shows voucher numbers for the ledger item. |
| Document number | Displays the document number type, which can be selected as an invoice, check, or other options. |
| Document type description | Provides an explanation based on the document type. For example, if _Other_ is selected, the document type description can be defined as manually.|
| e-Ledger method of payment | Displays payment method information. |
| Total debit | Shows the total debit amount of the voucher. |
| e-Ledger document type | Displays the document type for the e-Ledger. |
| Total credit | Shows the total credit amount of the voucher. |
| Worker | Defines the document recorder for e-Ledger declarations. |
| Journal item description | Allows the definition of journal item descriptions. |
| Description | Displays the voucher description. |
| Dimension value | Shows the dimension value of the branch. |

  - **General journal account entry**

This FastTab provides a breakdown of e-Ledger transactions, including account details, debit/credit classifications, and categorized dimension values. 
Each entry consists of an e-Ledger account group code, main account details, voucher amount and description, ensuring structured financial tracking. 
This section helps maintain organized journal entries and supports financial reconciliation processes efficiently.

| **Field** | **Description** |
| --- | --- |
| e-Ledger account group code | The three-digit group code required for inclusion in the e-Ledger.|
| e-Ledger main account | The account that will be replaced by the selected dimension value. |
| Main account | Displays the main account field. _Example: 100.20.001, 656.01.001, 320.01.001, etc._|
| Account name | Displays the description of the main account.|
| Debit or credit | Indicates whether the voucher is a debit (D) or credit (C) record.|
| Amount | Displays the voucher amount.|
| Description | Displays the description of the voucher.|
| Dimension value | Shows the dimension value of the branch.|

Once the necessary updates are completed in the **Overview** FastTab, click the **Send to e-Ledger pool** button to send the ledger items to the **e-Ledger pool** for e-Ledger file and report generation.
For detailed information about the buttons and fields, see the following section:

| **Button** | **Descriptions** |
| --- | --- |
| Send to e-Ledger pool | This function is used to send the ledger items to the **e-Ledger pool** based on branch.|
| e-Ledger pool | It provides to access the **e-Ledger pool** page. |


### e-Ledger pool

This page is used to perform all necessary checks related to the e-Ledger before generating the e-Ledger files and reports.

The **e-Ledger pool**page can be accessed both through the **Ledger item number** page and via **General ledger > Inquiries and reports > Period end reports > E-ledger pool**. However, the **E-ledger pool** page in **Period end reports** is only used for querying the e-Ledger and retrieving statutory reports.

The **e-Ledger pool** is a centralized location where e-Ledger records are stored before submission. 
It contains detailed transaction data, including fiscal year, period, branch ID, document details, and ledger item numbers.
You can also use the **Voucher transactions** button to access the voucher details of any journal entry.
It allows a final review of the e-Ledger for the selected period. If any errors are identified, all records can be deleted from the **e-Ledger pool**.

In addition, the e-Ledger file and statutory reports can be generated on this page.
You can generate the statutory ledger books and general journals in Excel format.​ 

**Statutory ledgers** Tab will help you to select which statutory report you want to generate.

  - **Overview**

This FastTab provides information about the parameters and fields of the ledger items. 

| **Parameters** | **Description** |
| --- | --- |
| Fiscal year | Displays the year information. |
| Period name | Displays the relevant month of the e-Ledger file. |
| e-Ledger branch ID | Displays the branch ID. |

You can review voucher entries, check total debit and credit amounts, and verify payment methods in the **Overview** FastTab. 
Each record includes the required informations for e-Ledger such as ledger item number, document type, document type description and method of payment. 

The **e-Ledger pool** ensures that all e-Ledger data is correctly structured before final submission.

| **Field** | **Description** |
| --- | --- |
| Fiscal calendar period reference | Defines the fiscal year and month information used for generating the e-Ledger file and reports.|
| e-Ledger branch ID | Defines the branch ID. |
| Name | Defines the branch name. |
| Ledger item number | Displays the journal item number. It must be same with the number that is the result of the **Assign journal item numbers** function.|
| Document reference | Indicates the voucher of the ledger item. |
| Document date | Displays the document date. |
| e-Ledger document type | Displays the document type for the e-Ledger. |
| Document type description | Provides an explanation based on the document type. For example, if _Other_ is selected, the document type description can be manually defined the type of the document. |
| Document number | Displays the document number type, which can be selected as an invoice, check, or other options. |
| e-Ledger method of payment | Displays payment method information. |
| Total debit | Shows the total debit amount of the voucher. |
| Total credit | Shows the total credit amount of the voucher. |
| Worker | Defines the document recorder for e-Ledger declarations. |
| Journal item description | Allows the definition of journal item descriptions. |
| Created date and time | Represents the date and time in the UTC timezone when the relevant voucher is sent to the pool. |

  - **Lines**

This FastTab displays detailed voucher line information in the **e-Ledger pool** . 
Each line includes a unique **Voucher line number**, main and sub-account details, ledger date, debit/credit status, amount, and a description.

This section allows you to track and review individual transaction lines, ensuring accuracy before finalizing e-Ledger submissions. 
It helps in identifying specific entries within a voucher and verifying compliance with financial regulations.

| **Field** | **Description** |
| --- | --- |
| Voucher line number | The voucher line number after being sent to the pool. |
| Main account code | The three-digit group code required for inclusion in the e-book. |
| Main account name | Displays the description of the main account. |
| Sub account code | Displays the main account field. Example: _100.20.001_, _656.01.001_, _320.01.001_, etc. |
| Sub account name | Displays the description of the sub-account. |
| Ledger date | The date when the related voucher line was created. |
| Debit or credit | Indicates whether the voucher is a debit (D) or credit (C) record. |
| Amount | Displays the voucher amount. |
| Ledger detail comment | Displays the description of the voucher (default text). |

If any updates are required after reviewing all records in the **e-Ledger pool**, all records must first be deleted from the **e-Ledger pool**, and the necessary changes should be made on the **Ledger item number** page.

Here are the explanations of the buttons;

| **Button** | **Descriptions** |
| --- | --- |
| Create e-Ledger file | This function is used to generate e-Ledger file in XBRL format. |
| Delete all | This function is used to delete the ledger items from the **e-Ledger pool**.  |
| Voucher transactions | It provides access to voucher transactions.  |


### e-Ledger file creation

This section provides information about generating e-Ledger files and reports.

Once all vouchers have been submitted and the data for the relevant period is confirmed, **Statutory ledger book** and **Statutory general journal** reports will be available to generate. 
These reports allow you to compare the e-Ledger records and the total debit and credit amounts of the e-Ledger with the Trial balance before generating the e-Ledger file.

The e-Ledger file can be generated once the relevant period is permanently closed. To generate the e-Ledger file; 

1. Go to **General ledger > Calendars > Ledger calendars**.
2. Update the status of the specific period from **On hold** to **Permanently closed** for the relevant legal entity.  
3. Return to the **e-Ledger pool** page.
4. Once the period is marked as **Permanently closed**, the **Create e-Ledger file** button will become active in the **e-Ledger pool** page.
5. Click **Create e-Ledger file**.
6. Click **OK** to generate the file.

>[!NOTE]
> To generate the e-Ledger file, the relevant period must be permanently closed.
> Therefore, before closing the period, the records that will be included in the e-Ledger file should be reviewed using the **Statutory ledger Book** and **Statutory general journal** reports.
> If no issues are found in the e-Ledger records, the period can be permanently closed and the e-Ledger file can be generated.
[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
