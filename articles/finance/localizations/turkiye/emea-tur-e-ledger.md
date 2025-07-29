---
title: Generate e-Ledger
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

# Generate e-Ledger
[!INCLUDE[banner](../../includes/banner.md)]

This article provides detailed instructions for configuring various parameters for e-Ledger, including parameters for the document type mapping, payment methods for main accounts, exclusion of posting layers, dimensions for main accounts, and the chart of accounts. The article also provides instructions for generating the e-Ledger file and reports.

E-Ledger is a legal and technical framework that collects general ledger records in a journal book and helps prepare mandatory books in electronic format in the Republic of Türkiye. These books must adhere to the specified formats and standards to ensure their immutability, integrity, and source accuracy, and to ensure that they can be used as evidence before authorities. The framework uses the internationally adopted eXtensible Business Reporting Language (XBRL) standard for electronic preparation.

## Configure e-Ledger

This section explains how to configure e-Ledger so that you can generate the e-Ledger file and statutory reports in Microsoft Dynamics 365 Finance.

### Configure electronic reporting for e-Ledger

The [Electronic reporting (ER)](../../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md) framework is used to generate e-Ledger books in electronic format. The e-Ledger configurations extend the **Standard Audit File (SAF-T)** configuration.

To generate the e-Ledger file and reports for Türkiye, you must open the **Electronic reporting** workspace (**Workspaces** \> **Electronic reporting**) and import the latest versions of the following ER configurations:

- e-Ledger Model (TR)

    - e-Ledger Model Mapping (TR)
    - Statutory General Journal (TR) (Excel)
    - Statutory Ledger Book (TR) (Excel)
    - XBRL GL (TR) (XML)

- General ledger data model mapping

Learn more about how to import the ER formats in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

The following table describes the e-Ledger ER configurations.

| Number | ER configuration name | Type | Description |
|---|---|---|---|
| 1 | e-Ledger Model (TR) | Model | This model is an abstract, application-independent data structure. It defines business concepts that are used to map Dynamics 365 data for the generation of reports. |
| 2 | e-Ledger Model Mapping (TR) | Model mapping | This model mapping sets the structure and data mapping for Türkiye's electronic ledger system. In this way, it ensures that data is correctly formatted for electronic reporting.|
| 3 | Statutory General Journal (TR) (Excel) | Format (exporting) | This electronic format defines the structure and establishes how data is organized and mapped for the **General Journal** report. |
| 4 | Statutory Ledger Book (TR) (Excel) | Format (exporting) | This electronic format defines the structure and establishes how data is organized and mapped for the **Ledger Book** report.​ |
| 5 | XBRL GL (TR) (XML) | Format (exporting) | This electronic format implements the XBRL taxonomy that standardizes financial and business information in Türkiye. |
| 6 | General ledger data model mapping | Model mapping | This model mapping is used to extract and structure financial data from Dynamics 365 for the generation of regulatory and statutory reports such as e-Ledger and SAF-T. |

For the **XBRL GL (TR) (XML)** format, you must follow these steps to configure application-specific parameters.

1. In the **Electronic reporting** workspace, select **Reporting configurations**.
1. Select the **XBRL GL (TR) (XML)** configuration, and then, on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** FastTab, in the **Name** field, select **ELedgerSetup_Lookup**.
1. On the **Conditions** FastTab, set the following fields.

    | Field | Description |
    |---|---|
    | Lookup result | Select the lines. |
    | Lines | Set the number of XML nodes in a branch file. This field is used to define the maximum file size that the integrator allows. The value that you specify determines the number of vouchers that are included in each generated XML file. You can update this field as required, according to the applicable limits. |

### Configure e-Ledger parameters

Before you can generate the e-Ledger file and reports, you must configure e-Ledger parameters on the **e-Ledger parameters** page (**General ledger** \> **Ledger setup** \> **e-Ledger parameters**). These parameters include parameters for the document type mapping, payment methods for main accounts, exclusion of posting layers, dimensions for main accounts, and the chart of accounts. This configuration ensures that e-Ledger records are correctly generated for multiple or single branches.

The following sections provide information about the parameters on each tab of the **e-Ledger parameters** page.

#### The General tab

Use the **General** tab to define single and multiple branch structures, and to configure batch thread definitions in e-Ledger. In addition, use this tab to set up format mappings so that the e-Ledger file and reports can be generated efficiently. Before you select format mappings, review the [Configure electronic reporting for e-Ledger](#configure-electronic-reporting-for-e-ledger) section of this article. The mappings should be defined beforehand.

Dynamics 365 Finance supports the generation of the e-Ledger file and reports on a branch basis. Branch IDs can be defined as financial dimension values, and each branch ID can be mapped to a corresponding financial dimension value. The e-Ledger file and reports can be generated for each branch, and the required configurations can be set up accordingly.

> [!NOTE]
> The financial dimension that includes the branch IDs must be selected in the account structures. Additionally, the journal entries that are required for the e-Ledger file and reports must contain the branch ID value.

To generate e-Ledger files for multiple branches, you must first enable the **Enable reporting per branch** parameter. The financial dimension that contains the branch IDs should be selected in the **Dimension name** field. On the **Branch mapping** FastTab, each branch must be defined through a branch ID and branch name. Map each branch ID by selecting the relevant financial dimension value in the **Dimension value** field. In addition, the worker who is responsible for generating the e-Ledger file and reports for the branches must be specified.

To generate e-Ledger files for a single branch only, set the fields in the **Branch information** section of the **Branch** FastTab.

| Field | Description |
|---|---|
| Single journal number per voucher | When this option is enabled, if a voucher has multiple journals, the journals are combined, and you get one journal item number. |
| Format mapping | Set the structure and data mapping for e-Ledger. Currently, the **XBRL GL (TR) (XML)** option is available, based on XBRL-GL format. |
| Maximum batch threads when sending to e-Ledger pool | Specify the number of values that should be entered in the batch chain when it's sent to the e-Ledger pool. |
| Format mapping for ledger book | Select the ER format to use to generate the **Ledger Book** report. |
| Format mapping for general journal | Select the ER format to use to generate the **General Journal** report. |
| e-Ledger branch ID | Specify the e-Ledger branch ID. |
| Branch name | Specify the e-Ledger branch name. |
| Document creator | Specify the creator of the e-Ledger file. |
| Enable reporting per branch | Generate the e-Ledger file and reports per branch. |
| Dimension value | Specify the dimension name to map to the relevant branch. |

#### The Document type mapping tab

Use the **Document type mapping** tab to configure and update e-Ledger records based on voucher filters. The information includes transaction types, document types and descriptions, and payment method details. To find relevant transactions to map and update e-Ledger records, you must define a voucher filter.

<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Transaction type</td>
<td>Select a transaction type. This field is used together with the <b>Voucher filter</b> field to find the relevant voucher transactions.</td>
</tr>
<tr>
<td>Voucher filter</td>
<td><p>Specify the prefix part of the voucher series, and add an asterisk (*) at the end. This field is used together with the <b>Transaction type</b> field to find the relevant voucher transactions.</p><p>For example, the voucher number is MH00001, and the transaction type is <b>General journal</b>. In this case, you should set the fields in the following way:</p><ul><li><b>Transaction type:</b> General journal</li><li><b>Voucher filter:</b> MH*</li></ul><p>If the query filter includes more than one transaction type, the same voucher query filter can be applied to each transaction type. For example, vouchers that have a voucher number that starts with "MH" include both transactions of the <b>General journal</b> type and transactions where the transaction type is blank. In this case, you should set the fields in the following way:</p><ul><li>First line:<ul><li><b>Transaction type:</b> General journal</li><li><b>Voucher filter:</b> MH*</li></ul></li><li>Second line:<ul><li><b>Transaction type:</b> (Blank)</li><li><b>Voucher filter:</b> MH*</li></ul></li></ul><p>This configuration ensures that the relevant transactions are correctly filtered and identified, based on their voucher series and transaction type.</p></td>
</tr>
<tr>
<td>e-Ledger document type</td>
<td><p>This field is used to specify the document type, so that document numbers can be automatically generated for voucher transactions. To specify the document type, select among the following predefined prefix values:</p><ul><li>Check</li><li>Invoice</li><li>Order-customer</li><li>Order-vendor</li><li>Voucher</li><li>Freight</li><li>Receipt</li><li>Other</li></ul></td>
</tr>
<tr>
<td>Document type description</td>
<td>If you set the <b>e-Ledger document type</b> field to <b>Other</b>, depending on the legislation, you can manually enter a description to explain the type of document.</td>
</tr>
<tr>
<td>e-Ledger method of payment</td>
<td>The system enables the automatic assignment of payment methods to the relevant main accounts in the e-Ledger items, based on the payment method mapping that is assigned to the main accounts.</td>
</tr>
<tr>
<td>Use payment method mapping</td>
<td>If a payment method mapping will be used, you must select this option. E-Ledger items are then updated according to the definition on the <b>Payment method mapping</b> tab.</td>
</tr>
<tr>
<td>Worker</td>
<td>The e-Ledger must include information about the worker who created each voucher. If you select a worker in this field, the worker information of that worker is assigned. If you leave this field blank, the worker information of the worker who created the voucher is automatically assigned when the e-Ledger is generated.</td>
</tr>
</tbody>
</table>

#### The Payment method mapping tab

Use the **Payment method mapping** tab to define methods of payment, based on main account filters.

Payment methods must be reported in the e-Ledger for vouchers that are created for payment and collection transactions. In the system, payment and collection vouchers are defined on a main account basis. In this way, payment methods can automatically be assigned in the e-Ledger items.

| Field | Description |
|---|---|
| e-Ledger method of payment | Define each method of payment as text, to enable mapping of payment types for vouchers. |
| Main account filter | Define the ledger account filter by specifying the prefix part of the main accounts and adding an asterisk (\*) at the end. |

#### The Posting layer mapping tab

Use the **Posting layer mapping** tab to select specific layers that should be excluded from the e-Ledger file and reports. In this way, you ensure that vouchers from the excluded layers aren't included in the e-Ledger when it's generated.

| Field | Description |
|---|---|
| Posting Layer | Use this field to categorize different types of financial transactions into distinct layers. |
| Exclude | Select which posting layers should be excluded from the e-Ledger. The **Current** posting layer is used to generate the e-Ledger. |

#### The Dimension mapping tab

Use the **Dimension mapping** tab to view the names of financial dimensions instead of the main account names on the **General journal account entry** FastTab of the **Ledger item number** page.

| Field | Description |
|---|---|
| Append dimension value to main account | Use this field to add a dimension value to the main account, based on the defined parameters in the dimension mapping table. |
| Main account | Select the main account that the name of the financial dimension value should be assigned to. |
| Dimension name | If the name of a financial dimension value should be shown instead of the name of the selected main account, select the financial dimension value in the **Account name** field on the **General journal account entry** FastTab of the **Ledger item number** page. |

#### The e-Ledger chart of accounts tab

Use the **e-Ledger chart of accounts** tab to define the e-Ledger chart of accounts for the e-Ledger file and reports.

The chart of accounts that is used to generate the e-Ledger file and reports can differ from the chart of accounts that the legal entity uses (for example, the Turkish Uniform Chart of Accounts). The e-Ledger chart of accounts can be used to map the main accounts that are required for e-Ledger reporting to financial dimension values. For each financial dimension value, a main account code and main account name are defined to complete the mapping.

Based on this mapping, the e-Ledger file and reports are then generated. When e-Ledger journal entries are created, the information that is related to the Turkish chart of accounts that is manually mapped to the financial dimension value is entered in the relevant fields on the **General journal account entry** FastTab of the **Ledger item number** page.

To configure this mapping, select the appropriate financial dimension in the **Dimension name** field. Then define the corresponding e-Ledger main accounts for each dimension value. The configured mapping will then be used to generate the e-Ledger file and reports.

| Field | Description |
|---|---|
| Enable e-Ledger chart of account | When this option is enabled, the defined account, account description, account group code, and group description are shown instead of the financial dimension value in the journal ledger and the e-Ledger. |
| Dimension value | Select the financial dimension to use to track the main accounts of the Turkish chart of accounts. |
| e-Ledger main account | Specify the main account value that should appear instead of the dimension value. |
| e-Ledger main account description | Specify the name of the main account that should appear instead of the financial dimension description. |
| e-Ledger account group code | Specify the three-digit total account code that the account that is specified in the **e-Ledger main account** field belongs to. |
| e-Ledger account group description | Enter a description of the total account code that is specified in the **e-Ledger account group code** field. |

## Generate the e-Ledger file and reports

This section provides detailed information about the steps that are used to generate the e-Ledger file and statutory reports in Dynamics 365 Finance.

Here is an overview of the steps:

1. **Update the period status.** The status of the relevant ledger calendar period must be changed to **On hold**.
1. **Assign journal item numbers.** This step involves enumerating journal entries from the beginning of the year. Journal item numbering must be done after the period is on hold or closed.
1. **Review and manage journal entry lines.** After journal item numbering is done, the journal lines page shows the data. On the **Ledger item number** page, required fields can be manually or automatically populated before the e-Ledger is sent.
1. **Review the e-Ledger pool.** After the journal lines are updated, the records are sent to the e-Ledger pool. This step involves creating files on a branch basis and exporting them as XML or zip files, so that they can be uploaded to the Turkish Revenue Administration (GIB).
1. **Generate the e-Ledger file and reports.** This step involves creating files on a branch basis and exporting them as XML or zip files, so that they can be uploaded to the GIB. The statutory reports also cover how to inquire about statutory ledgers and e-Ledger records, including voucher transactions and ledger items.

After the status of the relevant fiscal period is updated, the necessary e-Ledger processes are performed on the **e-Ledger and statutory** page (**General ledger** \> **Period close** \> **e-Ledger and statutory**). This page shows the e-Ledger periods and their statuses, the debit and credit totals for each branch for the relevant periods, the last assigned journal item numbers, and the e-Ledger file status.

### The Statutory ledgers FastTab

The **Statutory ledgers** FastTab on the **e-Ledger and statutory** page provides an overview of the e-Ledger file and reports that are generated for each branch ID. You can use it to compare the total debit and credit amounts after journal entries are created with the totals after those entries are sent to the e-Ledger pool. You can also use it to track the periods and branches that e-Ledger files were generated for.

| Field | Description |
|---|---|
| e-Ledger branch ID | The branch ID. This field ensures that e-Ledger records are shown based on the branch ID. |
| Journal item numbered | A value that indicates whether journal item numbering was done for the relevant branch. |
| Last journal item number | After journal item numbering is completed, this field is updated with the last item number that was assigned for the period. |
| Journal debit total | After journal item numbering is completed, this field shows the total debit amount for the relevant branch. |
| e-Ledger debit | After the ledger items are sent to the e-Ledger pool, this field shows the total debit amount of the journal entries for the relevant branch. |
| Journal credit total | After journal item numbering is completed, this field shows the total credit amount for the relevant branch. |
| e-Ledger credit | After the ledger items are sent to the e-Ledger pool, this field shows the total credit amount of the journal entries for the relevant branch. |
| Debit balanced | If the **Journal debit total** value matches the **e-Ledger debit amount** value for the relevant branch, this field is marked. |
| Credit balanced | If the **Journal credit total** value matches the **e-Ledger credit amount** value for the relevant branch, this field is marked. |
| Sent | After the e-Ledger file is generated, this field is marked on the **e-Ledger pool** page. After the file is generated, no further changes are allowed in the e-Ledger for the relevant branch. |

### Change the status of the ledger calendar period

Before an e-Ledger file can be generated, the status of the related ledger calendar period must be changed to **On hold**.

1. Go to **General ledger** \> **Calendars** \> **Ledger calendars**.
1. Select **Calendar**.
1. Select **Fiscal year**.
1. Select the period that you want to generate an e-Ledger file for.
1. On the **Legal entities** FastTab, select **Legal entity**.
1. In the **Period status** field, select **On hold**.
1. Select **Save**.

The system automatically generates the ledger calendar so that it has a total of 14 periods: one period for each month, an **Opening** period, and a **Closing** period. The status of the **Opening** period is set to **Permanently closed**. The status of the **Closing** period is set to **On hold** until the whole ledger calendar is closed.

The e-Ledger can be generated only for the periods between the **Opening** and **Closing** periods. It can't be generated independently for the **Opening** period or the **Closing** period. When the e-Ledger is generated, the **Opening** period is combined with period 1, and the **Closing** period is combined with period 12.

### Assign journal item numbers

This section explains how to assign journal item numbers to the voucher transactions in the e-Ledger.

Each journal item must have a unique number that is assigned according to dates. The journal item numbering process is managed on the **e-Ledger and statutory ledger** page. Application of the process requires that journal item numbering is completed for all periods, starting from the beginning of the year. Journal item numbering should also be done for period 0 (the **Opening** period), and the first item number should be assigned to the opening voucher. If the e-Ledger is generated based on branches, journal item numbering must be applied separately for each branch.

1. Go to **General ledger** \> **Period close** \> **e-Ledger and statutory ledger**.
1. On the Action Pane, on the **Statutory ledger** tab, in the **Ledger item number** group, select **Assign journal item numbers** to create the ledger items and assign a unique number to each voucher transaction in the e-Ledger.

The following table describes the fields in the dialog that appears when you select **Assign journal item numbers**.

| Field | Description |
|---|---|
| Reference | The period that the ledger item numbers will be assigned to. |
| Exclude for zero value voucher in all rows | When this option is enabled, if all lines of a voucher have a total value of 0 (zero), no journal item number is assigned to them during the journal item numbering process. If one line in the voucher has a value of 0 (zero), a journal item number is assigned to that line, but the line isn't created in the e-Ledger. |

> [!IMPORTANT]
> Before ledger items can be generated and journal item numbers can be assigned for the e-Ledger of the next period, the current period must be correctly closed, and the e-Ledger must be finalized. Even if there are no transactions in the relevant period, the **Assign journal item numbers** process must be completed to enable the generation of the e-Ledger for the next period.

### Remove journal item numbers

If journal item numbering was completed, but the e-Ledger file hasn't yet been generated, you can use the **Remove journal item numbers** button to reverse the numbering process. When the numbering process is reversed, the e-Ledger records are deleted from both the **Ledger item number** page and the **e-Ledger pool** page.

If e-Ledger records have already been created, the numbering process can't be reversed.

### Review and manage journal entry lines

Use the **Ledger item number** button to access the journal entry lines that will be recorded in the e-Ledger file after journal item numbering is done. You can find the **Ledger item number** button for the relevant period in the **e-Ledger** group on the **Statutory ledgers** tab of Action Pane on the **e-Ledger and statutory ledger** page.

After you select **Assign journal item numbers**, the relevant fields are automatically populated based on e-Ledger parameters, and the corresponding e-Ledger items are generated.

The following table describes the buttons on the **Ledger item number** page.

| Button | Description |
|---|---|
| Send to e-Ledger pool | Send created e-Ledger items to the pool, so that related records in the e-Ledger file that will be generated can be fixed. You can also change that start number of voucher line numbering. |
| e-Ledger pool | Open the e-Ledger pool that contains the submitted records. |

The following sections provide information about each FastTab on the **Ledger item number** page.

#### The Overview FastTab

Use the **Overview** FastTab to manage and review ledger items for the e-Ledger. This FastTab includes buttons for refreshing fields, automatically populating required information, or manually updating fields.

Before you generate the e-Ledger file and statutory reports, the required fields must be populated. The **Overview** FastTab contains key information that is related to the journal items that will be shown in the e-Ledger. For the selected period and branch, it includes mandatory e-Ledger fields, such as fields for the journal item number, the document type, the document type description, the document date, the method of payment, and the worker who created the voucher.

After you assign journal item numbers for the e-Ledger, the journal entries for the period are generated. The required fields for the e-Ledger are automatically populated based on the configurations on the parameter page. If you select the **Manual** button, you can manually update the **Document type**, **Document type description**, and **Payment method** fields. If you select the **Automatic** button, those fields ca be refreshed automatically, based on the parameter configurations. To view the voucher transactions for a journal, select the **Voucher transactions** button.

After you complete the required updates on the **Overview** FastTab, the records are sent to the e-Ledger pool for e-Ledger file and report generation.

| Button | Description |
|---|---|
| Refresh | Refresh the fields on the e-Ledger summary page. |
| Automatic | Automatically populate the required fields before the e-Ledger is sent, based on the preconfigured e-Ledger parameters. When you select this button, all records are updated so that they are synchronized with the latest e-Ledger parameters. |
| Manual | Manually set required fields for each record before the e-Ledger is sent. Depending on the branch, the e-Ledger document type, document type description, and payment method can be updated. |
| Voucher transactions | Access the journal entry for the relevant ledger item.|

| Field | Description |
|---|---|
| Ledger item number | The journal item number. |
| e-Ledger branch ID | The branch ID. |
| Document date | The document date. |
| Voucher | Voucher numbers for the ledger item. |
| Document number | The document number type (**Invoice**, **Check**, or **Other**). |
| Document type description | An explanation of the document type. For example, if the document type is **Other**, the document type description can be manually defined. |
| e-Ledger method of payment | Payment method information. |
| Total debit | The total debit amount of the voucher. |
| e-Ledger document type | The document type for the e-Ledger. |
| Total credit | The total credit amount of the voucher. |
| Worker | The document recorder for e-Ledger declarations. |
| Journal item description | This field allows for the definition of journal item descriptions. |
| Description | The voucher description. |
| Dimension value | The dimension value of the branch. |

#### The General journal account entry FastTab

The **General journal account entry** FastTab provides a breakdown of e-Ledger transactions. The information includes account details, debit/credit classifications, and categorized dimension values. Each entry consists of an e-Ledger account group code, main account details, a voucher amount, and a description to ensure structured financial tracking. This FastTab efficiently helps maintain organized journal entries and supports financial reconciliation processes.

| Field | Description |
|---|---|
| e-Ledger account group code | The three-digit group code that is required for inclusion in the e-Ledger.|
| e-Ledger main account | The account that will be replaced by the selected dimension value. |
| Main account | The main account field (for example, **100.20.001**, **656.01.001**, or **320.01.001**). |
| Account name | A description of the main account.|
| Debit or credit | A value that indicates whether the voucher is a debit (**D**) record or a credit (**C**) record.|
| Amount | The voucher amount.|
| Description | A description of the voucher.|
| Dimension value | The dimension value of the branch.|

After you complete the required updates on the **Overview** FastTab, select the **Send to e-Ledger pool** button to send the ledger items to the e-Ledger pool for e-Ledger file and report generation.

| Button | Descriptions |
|---|---|
| Send to e-Ledger pool | Send the ledger items to the e-Ledger pool, based on the branch.|
| e-Ledger pool | Open the **e-Ledger pool** page. |

### Review the e-Ledger pool

Use the **e-Ledger pool** page to perform all required checks that are related to the e-Ledger before the e-Ledger file and reports are generated.

You can open the **e-Ledger pool** page by using the **e-Ledger pool** button on the **Ledger item number** page or by going to **General ledger** \> **Inquiries and reports** \> **Period end reports** \> **E-ledger pool**. However, the version of the **E-ledger pool** page that is opened from **Period end reports** can be used only to query the e-Ledger and retrieve statutory reports.

The e-Ledger pool is a centralized location where e-Ledger records are stored before they are submitted. It contains detailed transaction data, including the fiscal year, the period, the branch ID, document details, and ledger item numbers. You can use the **Voucher transactions** button to access the voucher details of any journal entry.

The e-Ledger pool lets you do a final review of the e-Ledger for the selected period. If you find any errors, you can delete all records from the e-Ledger pool.

In addition, you can generate the e-Ledger file and statutory reports from the **e-Ledger pool** page. You can generate the statutory ledger books and general journals in Excel format.​ The **Statutory ledgers** tab helps you select which statutory report you want to generate.

The following sections provide information about each FastTab on the **e-Ledger pool** page.

#### The Overview FastTab

The **Overview** FastTab provides information about the ledger items.

| Field | Description |
|---|---|
| Fiscal year | The year information. |
| Period name | The relevant month of the e-Ledger file. |
| e-Ledger branch ID | The branch ID. |

On the **Overview** FastTab, you can review voucher entries, check total debit and credit amounts, and verify payment methods. Each record includes the required information for e-Ledger, such as the ledger item number, document type, document type description, and method of payment. The e-Ledger pool helps ensure that all e-Ledger data is correctly structured before final submission.

| Field | Description |
|---|---|
| Fiscal calendar period reference | The fiscal year and month information that is used to generate the e-Ledger file and reports. |
| e-Ledger branch ID | The branch ID. |
| Name | The branch name. |
| Ledger item number | The journal item number. This number must match the result of the **Assign journal item numbers** function. |
| Document reference | The voucher of the ledger item. |
| Document date | The document date. |
| e-Ledger document type | The document type for the e-Ledger. |
| Document type description | An explanation of the document type. For example, if the document type is **Other**, the document type description can be manually defined. |
| Document number | The document number type (**Invoice**, **Check**, or **Other**). |
| e-Ledger method of payment | Payment method information. |
| Total debit | The total debit amount of the voucher. |
| Total credit | The total credit amount of the voucher. |
| Worker | The document recorder for e-Ledger declarations. |
| Journal item description | This field allows for the definition of journal item descriptions. |
| Created date and time | The date and time when the relevant voucher was sent to the pool, in Coordinated Universal Time. |

#### The Lines FastTab

The **Lines** FastTab shows detailed information for voucher lines in the e-Ledger pool. Each line has a unique voucher line number, main account and sub-account details, a ledger date, a debit/credit status, an amount, and a description.

Use this FastTab to track and review individual transaction lines, so that you can ensure accuracy before you finalize e-Ledger submissions. It helps you identify specific entries in a voucher and verify compliance with financial regulations.

| Field | Description |
|---|---|
| Voucher line number | The voucher line number after it's sent to the pool. |
| Main account code | The three-digit group code that is required for inclusion in the e-book. |
| Main account name | A description of the main account. |
| Sub account code | The main account field (for example, **100.20.001**, **656.01.001**, or **320.01.001**). |
| Sub account name | A description of the sub-account. |
| Ledger date | The date when the related voucher line was created. |
| Debit or credit | A value that indicates whether the voucher is a debit record (**D**) or a credit (**C**) record. |
| Amount | The voucher amount. |
| Ledger detail comment | A description of the voucher (default text). |

If any updates are required after you review all the records in the e-Ledger pool, you must first delete all records from the e-Ledger pool. Then make the required changes on the **Ledger item number** page.

The following table describes the buttons that are available.

| Button | Descriptions |
|---|---|
| Create e-Ledger file | Generate an e-Ledger file in XBRL format. |
| Delete all | Delete the ledger items from the e-Ledger pool. |
| Voucher transactions | Go to the voucher transactions. |

### Generate the e-Ledger file and reports

This section explains how to generate the e-Ledger file and reports.

After all vouchers are submitted, and the data for the relevant period is confirmed, you can generate the **Statutory ledger book** and **Statutory general journal** reports. You can use these reports to compare the e-Ledger records and the total debit and credit amounts of the e-Ledger with the trial balance before you generate the e-Ledger file.

> [!NOTE]
> You can generate the e-Ledger file only after the relevant period is permanently closed. Before you close the period, you should use the **Statutory ledger book** and **Statutory general journal** reports to review the records that will be included in the e-Ledger file. If you find no issues in the e-Ledger records, you can permanently close the period and generate the e-Ledger file.

To generate the e-Ledger file, follow these steps.

1. Go to **General ledger** \> **Calendars** \> **Ledger calendars**.
1. Update the status of the specific period from **On hold** to **Permanently closed** for the relevant legal entity.
1. Return to the **e-Ledger pool** page. After the period is marked as **Permanently closed**, the **Create e-Ledger file** button becomes active.
1. Select **Create e-Ledger file**.
1. Select **OK** to generate the file.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
