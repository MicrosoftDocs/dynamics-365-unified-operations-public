---
title: Standard Audit File for Tax (SAF-T) for Denmark
description: This article explains how to set up and generate the Standard Audit File for Tax (SAF-T) for legal entities that have a primary address in Denmark.
author: liza-golub
ms.date: 05/22/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Denmark
ms.author: egolub
ms.search.validFrom: 
ms.dyn365.ops.version: 
---

# Standard Audit File for Tax (SAF-T) for Denmark

[!include [banner](../includes/banner.md)]

This article describes how to prepare Microsoft Dynamics 365 Finance to work with the Standard Audit File for Tax (SAF-T) report and generate the file in XML format according to the requirements for SAF-T in Denmark.

> [!NOTE]
> The [One voucher](../general-ledger/one-voucher.md) functionality introduces a limitation on further SAF-T reporting for some scenarios that are subject to SAF-T. Specifically, a bank statement scenario must be posted by using different vouchers for transactions that have different counteragent accounts. We recommend that you set the **Allow multiple transactions within one voucher** option on the **General ledger parameters** page to **No** in your legal entity if you post transactions that are part of the SAF-T report. For information about One voucher functionality, see [One voucher](../general-ledger/one-voucher.md).

## Setup

To start to work with the SAF-T report for Denmark, complete the following steps.

1. [Turn on features in Feature management.](#features)
2. [Import Electronic reporting configurations.](#import)
3. [Set up application-specific parameters for the **SAF-T Format (DK)** configuration.](#application)
4. [Select the SAT-T format in General ledger parameters.](#satt)
5. [Create a contact person for your company.](#contact)
6. [Configure the Registration number of the legal entity.](#registration-id)
7. [Configure Standard chart of accounts.](#coa)

### <a name="features"></a>Turn on features in Feature management

1. In the **Feature management** workspace, on the **All** tab, find and select the following features in the feature list:

    - [Standard Audit File for Tax (SAF-T) electronic report](../general-ledger/standard-audit-file.md)
    - Optimize datasets memory consumption at ER reports runtime

2. Select **Enable now**.

### <a name="import"></a>Import Electronic reporting configurations

In Finance, import the following versions or later of these Electronic reporting (ER) configurations from the Global repository.

For more information about how to download ER configurations, see [Download ER configurations from the Global repository](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

| ER configuration name       | Type          | Version | Description |
|-----------------------------|---------------|---------|-------------|
| Standard Audit File (SAF-T) | Model         | 164     | The common data model for different audit reports. |
| SAF-T General model mapping | Model mapping | 164.354 | The model mapping that provides general data source mapping. |
| SAF-T Format (DK)           | Format        | 164.21  | The XML format that represents the SAF-T report in accordance with the requirements for Denmark. |

Import the most recent versions of the configurations. The version description usually includes the number of the Microsoft Knowledge Base (KB) article that explains the changes that were introduced in the configuration version.

> [!IMPORTANT]
> After all the ER configurations from the previous table are imported, set the **Default for model mapping** option to **Yes** for the **SAF-T General model mapping** configuration.
>
> ![Default for model mapping option set to Yes for the SAF-T General model mapping configuration.](media/dk-saf-t-default-model-mapping.png)

The **SAF-T General model mapping** configuration provides general data source mapping for the following master data:

- **GeneralLedgerAccounts** – General ledger.
- **Customers** – Purchasers and other debtors.
- **Suppliers** – Suppliers and other creditors.
- **TaxTable** – Tax type tables that are used in the legal entity's accounting system. Examples include value-added tax (VAT), corporate income tax, and excise taxes.
- **UOMTable** – Table for units of measurement.
- **AnalysisTypeTable** – Data tables for analytical accounting. This data is used to provide details of transaction data. Examples include unit costs, additional costs, a cost center, or a project.
- **MovementTypeTable** – Stock movement types.
- **Products** – Products and services.
- **PhysicalStock** – Data about the stock that is contained in the file.

The **SAF-T General model mapping** configuration also provides general data source mapping for the following transactional data:

- **GeneralLedgerEntries** – General ledger entries.
- **Sales invoices** – Initial sales documents.
- **PurchaseInvoices** – Accounting documents for purchases and acquisitions.
- **Payments** – Payments.
- **MovementOfGoods** – Information about the movement of goods. For example, movement occurs when goods are recorded, when goods are written off after they are sold or used in production, and when finished products, determined loss, and defective goods are recorded.
- **AssetTransactions** – Economic transactions or events for tangible or intangible economic assets, and for financial assets.

### <a name="application"></a>Set up application-specific parameters for the SAF-T Format (DK) configuration

We recommend that you enable the **Use application specific parameters from previous versions of ER formats** feature in the **Feature management** workspace. When this feature is enabled, parameters that are configured for the earlier version of an ER format automatically become applicable for the later version of the same format. If this feature isn't enabled, explicitly configure the application-specific parameters for each format version. The **Use application specific parameters from previous versions of ER formats** feature is available in the **Feature management** workspace starting in Finance version 10.0.23. For more information about how to set up the parameters of an ER format for each legal entity, see [Set up the parameters of an ER format per legal entity](../../fin-ops-core/dev-itpro/analytics/er-app-specific-parameters-set-up.md).

We also recommend that you enable the **Accelerate the ER labels storage** feature in the **Feature management** workspace. This feature helps improve network bandwidth utilization and overall system performance because, in most cases, ER labels of a single language are used when you work with a single ER configuration. The **Accelerate the ER labels storage** feature is available in the **Feature management** workspace as of Finance version 10.0.25. For more information about how to set up the parameters of an ER format for each legal entity, see [Performance](../../fin-ops-core/dev-itpro/analytics/er-design-multilingual-reports.md#performance).

1. In the **Electronic reporting** workspace, open the **Configurations** page.
2. In the configuration tree, under **Standard Audit File (SAF-T)**, select **SAF-T Format (DK)**.
3. Make sure that you're working in the company that you want to set up the application-specific parameters for.
4. Select **Configurations** \> **Application-specific parameters**, and then, on the Action Pane, select **Setup**.
5. In the list on the left, select the last version of the configuration.
6. Provide the mapping for the **ReportTaxCodes\_LOOKUP** lookup field. Define the mapping between the sales tax codes that are used by the company and the standard tax codes of Denmark.
7. Select the value **Other** as the last condition in the list. The **Tax Code** column must be set to **\*Not blank\***.
8. In the **Line** column, verify that **Other** is the last condition in the table. At least one line that has **\*Not blank\*** values must be set up.
9. When you've finished setting up the lookup fields, in the **State** field select **Completed**, and then save the configuration.

### <a name="satt"></a>Select the SAT-T format in General ledger parameters

1. Go to **General ledger** \> **Setup** \> **General ledger parameters**.
2. On the **Standard Audit File for Tax** FastTab, in the **Standard Audit File for Tax (SAF-T)** field, select **SAF-T Format (DK)**.

### <a name="contact"></a>Create a contact person for your company

The **Company** node of the SAF-T report must include information for a contact. This node is located under the **Header** node. To set up contact information that will be reported to SAF-T, follow these steps.

1. Go to **Sales and marketing** \> **Relationships** \> **Contacts** \> **All contacts**.
2. Select **New** to create a new contact for your legal entity. Be sure to select **Legal entity** in the **Contact for** field.
3. Check the **Party ID** value to make sure that you select the legal entity that SAF-T will be reported from.

![ER configurations for the SAF-T report for Lithuania.](media/lt-saf-t-contact-person.png)

### <a name="registration-id"></a> Configure the registration number of the legal entity

To generate a SAF-T, you must configure the registration number.

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
2. Select the legal entity, and then select **Registration IDs**.
3. Select or create the address in Denmark, and then, on the **Registration ID** FastTab, select **Add**.
4. In the **Registration type** field, select the registration type that is dedicated to Denmark, and that uses the **VAT Id** registration category.
5. In the **Registration number** field, enter the tax number.
6. On the **General** tab, in the **Effective** field, enter the date when the number becomes effective.

For more information about how to set up registration categories and registration types, see [Registration IDs](emea-registration-ids.md).

### <a name="coa"></a> Configure a standard chart of accounts (Standardkontoplan)

In the Danish SAF-T report, main accounts that are used in Finance must be associated with Danish standard accounts. Use the [consolidation account groups and additional consolidation accounts](../budgeting/consolidation-account-groups-consolidation-accounts.md) functionality to create this association.

1. Create a [consolidation account group](../general-ledger/tasks/create-consolidation-groups.md#create-a-consolidation-account-group). For example, create a group that is named **Standardkontoplan**.
2. [Add accounts to the consolidation account group](../general-ledger/tasks/create-consolidation-groups.md#add-accounts-to-consolidation-account-group). In the **Consolidation account** field, specify a standard account. This value is reported in the **StandardAccountID** element of SAF-T under the **Master data** \> **GeneralLedgerAccounts** \> **Account** node. In the **Consolidation account name** field, optionally specify the standard account name or description. This value isn't used in SAF-T.

## Generate the SAF-T report

1. Go to **General ledger** \> **Inquiries and reports** \> **Standard Audit File for Tax (SAF-T)** \> **Standard Audit File for Tax (SAF-T)**.
2. In the **Electronic report parameters** dialog box, set the following fields.

    | Field name | Description |
    |------------|-------------|
    | **From date** and **To date** | Specify the start and end dates of the period that the report should include data for. The start date is reflected in the **Header** \> **SelectionCriteria** \> **PeriodStart** node of the SAF-T. The end date is reflected in the **Header** \> **SelectionCriteria** \> **PeriodEnd** node. The period for one file or one part of a file can't be shorter than one month or longer than a reporting period. |
    | **Print zero balance** | This checkbox affects the data that is reported in the **MasterFiles** \> **GeneralLedgerAccounts** node of the SAF-T. Select this checkbox to include all the main accounts of your company, including main accounts that have a zero balance during the specified period. Clear the checkbox to include only main accounts that have a non-zero balance or transactions during the specified period. |
    | **Export all Customers** | This checkbox affects the data that is reported in the **MasterFiles** \> **Customers** node of the SAF-T. Select this checkbox to include all the customers of your company, including customers that have a zero balance during the specified period. Clear the checkbox to include only customers that have a non-zero balance or transactions during the specified period. |
    | **Export all Suppliers** | This checkbox affects the data that is reported in the **MasterFiles** \> **Suppliers** node of the SAF-T. Select this checkbox to include all the suppliers of your company, including suppliers that have a zero balance during the specified period. Clear the checkbox to include only suppliers that have a non-zero balance or transactions during the specified period. |
    | **Export all Analysis types** | This checkbox affects the data that is reported in the **MasterFiles** \> **AnalysisTypeTable** node of the SAF-T. Select this checkbox to include all the dimensions of your company. Clear the checkbox to include only dimensions that are used in transactions that are reported during the specified period. |
    | **Export all Products** | This checkbox affects the data that is reported in the **MasterFiles** \> **Products** node of the SAF-T. Select this checkbox to include all the products of your company, including products that have zero physical stock during the specified period. Clear the checkbox to include only products that have non-zero physical stock or transactions during the specified period. |
    | **Export all Sales tax codes** | This checkbox affects the data that is reported in the **MasterFiles** \> **TaxTable** node of the SAF-T. Select this checkbox to include all the sales tax codes of your company. Clear the checkbox to include only sales tax codes that are used in transactions that are reported during the specified period. |
    | **Consolidation account group** | Select the consolidation account group that you [set up earlier](#coa) to configure the standard chart of accounts (**Standardkontoplan**). |
    | **Header Comment** | Specify your comment to SAF-T. The value of this field is reported in the **HeaderComment** element of SAF-T under the **AuditFile** \> **Header** node. The element can contain any additional generic comments about the audit file. The maximum length is 256 characters. |
    | **Tax Accounting Basis** | <p>The value of this field is reported in the **TaxAccountingBasis** element of SAF-T under the **AuditFile** \> **Header** node. Select one of the following values:</p><ul><li>Invoice Accounting</li><li>Cash Accounting</li><li>Delivery</li><li>Other</li></ul> |
    | **Tax Entity** | <p>The value of this field is reported in the **TaxEntity** element of SAF-T under **AuditFile** \> **Header** node. Select one of the following values:</p><ul><li>Company</li><li>Division</li><li>Branch reference</li></ul> |

3. On the **Run in the background** FastTab, you can specify parameters of the batch job and run the report in batch mode.

    When an electronic report is generated in batch mode, you can find related batch information and the generated output file as an attachment by going to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**. For more information about how to configure a destination for each ER format configuration and its output component, see [Electronic reporting (ER) destinations](../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).

4. Select **OK** to generate the report.
