---
# required metadata

title: Standard Audit File for Tax (SAF-T) for Lithuania
description: This topic explains how to set up and generate the Standard Audit File for Tax (SAF-T) for legal entities that have their primary address in Lithuania. 
author: liza-golub
ms.author: elgolu
ms.date: 03/08/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Lithuania
# ms.search.industry: 
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Standard Audit File for Tax (SAF-T) for Lithuania

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

According to Article 16 of the Law on Accounting of the Republic of Lithuania, companies in Lithuania are legally required to provide a report in Standard Audit File for Tax (SAF-T) format. This topic describes how Microsoft Dynamics 365 Finance supports the SAF-T requirements and explains how to prepare Finance to work with the SAF-T report for Lithuania.

For more information, see [SAF-T - VMI](https://www.vmi.lt/cms/web/guest/saf-t).

## Setup

To start to work with the **Lithuania SAF-T** report, follow these steps.

1. In Finance, import the following versions or later of these Electronic reporting (ER) configurations from the Global repository.

    | ER configuration name       | Type          | Version | Description |
    |-----------------------------|---------------|---------|-------------|
    | Standard Audit File (SAF-T) | Model         | 128     | The common data model for different audit reports. |
    | SAF-T General model mapping | Model mapping | 128.251 | The model mapping that provides general data source mapping. |
    | SAF-T Format (LT)           | Format        | 128.198 | The XML format that represents the SAF-T report in accordance with the requirements for Lithuania. |

    ![ER configurations for the SAF-T report for Lithuania](media/lt-saf-t-ger-configurations.png)

    The **SAF-T General model mapping** configuration provides general data source mapping for the following master data:

    - **GeneralLedgerAccounts** – General ledger.
    - **Customers** – Purchasers (customers) and other debtors (available in the file).
    - **Suppliers** – Suppliers and other creditors (available in the file).
    - **TaxTable** – Data of tax type tables. All tax type tables that are used in the legal entity's accounting system are specified. Examples include value-added tax (VAT), corporate income tax, and excise taxes.
    - **UOMTable** – Type table for units of measurement.
    - **AnalysisTypeTable** – Data of type tables for analytical accounting. This data is used to provide details of transaction data. Examples include unit costs, additional costs, a cost center, or a project.
    - **MovementTypeTable** – Stock movement types.
    - **Products** – Products and services.
    - **PhysicalStock** – Stock (data about the stock that is contained in the file).

    The **SAF-T General model mapping** configuration also provides general data source mapping for the following transactional data:

    - **GeneralLedgerEntries** – General ledger entries.
    - **Sales invoices** – Initial sales documents.
    - **PurchaseInvoices** – Accounting documents for purchases and acquisitions.
    - **Payments** – Payments.
    - **MovementOfGoods** – Information about the movement of goods. Example of movements include recording of goods, write-off of goods after they are sold or used in production, and recording of finished products, determined loss, and defective goods.
    - **AssetTransactions** – Economic transactions or events for economic assets (tangible, intangible, and financial assets).

    Be sure to import the most recent versions of the configurations. The version description usually includes the number of the Microsoft Knowledge Base (KB) article that explains the changes that were introduced in the configuration version.

    > [!IMPORTANT]
    > After all the ER configurations from the previous table are imported, set the **Default for model mapping** option to **Yes** for the **SAF-T General model mapping** configuration.
    >
    > ![Default for model mapping option set to Yes for the SAF-T General model mapping configuration](media/lt-saf-t-default-model-mapping.png)

    For more information about how to download ER configurations, see [Download ER configurations from the Global repository](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

    Next, you must set up application-specific parameters for the **SAF-T Format (LT)** configuration.
    
2. In Electronic reporting, open the **Configurations** page. In the configuration tree, under **Standard Audit File (SAF-T)**, select **SAF-T Format (LT)**.
3. Select **Configurations** \> **Application-specific parameters**, and then, on the Action Pane, select **Setup**.
4. Select the last version of the configuration in the list on the left.
5. Provide the mapping for all the lookup fields:

    - **StandardMainAccount_Lookup** – Define the mapping between the main accounts that are used by the company and the standard main accounts of Lithuania.
    - **ReportTaxCodes_LOOKUP** – Define the mapping between the sales tax codes that are used by the company and the standard tax codes of Lithuania.
    - **StandardAnalysisType_LOOKUP** – Define the mapping between the dimensions that are used by the company and the standard analysis types of Lithuania.
    - **AddressType_LOOKUP** – Define the mapping between the address types that are used by the company and the address types that are used in the SAF-T report for Lithuania.

6. When you've finished setting up the lookup fields, in the **State** field, select **Completed**. Then save the configuration.
7. Go to **General ledger** \> **Setup** \> **General ledger parameters**.
8. On the **Standard Audit File for Tax** FastTab, in the **Standard Audit File for Tax (SAF-T)** field, set up the SAF-T format.
9. Go to **Feature management** \> **All**.
10. In the feature list, find and select the following features:

    - Optimization of query data source creation time during execution of ER reports
    - Optimize datasets memory consumption at ER reports runtime

11. Select **Enable now**.

## Generate the SAF-T report

- To generate the SAF-T report, go to **General ledger** \> **Inquiries and reports** \> **Standard Audit File for Tax (SAF-T)** \> **Standard Audit File for Tax (SAF-T)**.

The following table describes the fields in the report dialog box.

| Field name | Description |
|------------|-------------|
| **SAF-T File type** | <p>The SAF-T supports the following file types:</p><ul><li>**F** – A full SAF-T file. This type of SAF-T file can be split by period.</li><li>**GL** – General ledger records. This part of the SAF-T file can be split by entities, periods, or parts. </li><li>**PI** – Purchase data. This part of the SAF-T file can be split by entities, periods, or parts.</li><li>**PA** – Payment data. This part of the SAF-T file can be split by entities, periods, or parts.</li><li>**SI** – Sales data. This part of the SAF-T file can be split by entities, periods, or parts.</li><li>**MG** – The movement of goods. This part of the SAF-T file can be split by entities, periods, or parts.</li><li>**AS** – The movement of fixed assets. This part of the SAF-T file can be split by entities, periods, or parts.</li><ul> |
| **Reporting period from** and **Reporting period to** | Define the start and end dates of the period that the SAF-T is requested for. The start date is reflected in the **Header** \> **SelectionCriteria** \> **SelectionStartDate** node of the SAF-T, and the end date is reflected in the **Header** \> **SelectionCriteria** \> **SelectionEndDate** node. |
| **From date** and **To date** | Specify the start and end dates of the period that the report should include data for. The start date is reflected in the **Header** \> **SelectionCriteria** \> **PeriodStart** node of the SAF-T. The end date is reflected in the **Header** \> **SelectionCriteria** \> **PeriodEnd** node. The period for one file or one part of a file can't be shorter than one month and longer than a reporting period. |
| **Number of parts** | Specify the number of parts to generate the SAF-T in. This value is reflected in the **Header** \> **NumberOfParts** node of the SAF-T. |
| **Part number** | Specify the number of the part to generate in the current SAF-T. This value is reflected in the **Header** \> **PartNumber** node of the SAF-T. |
| **Print zero balance** | This check box affects the data that is reported in the **MasterFiles** \> **GeneralLedgerAccounts** node of the SAF-T. Select this check box to include all the main accounts of your company, even main accounts that have a zero balance during the specified period. Clear the check box to include only main accounts that have a non-zero balance or transactions during the specified period. |
| **Export all Customers** | This check box affects the data that is reported in the **MasterFiles** \> **Customers** node of the SAF-T. Select this check box to include all the customers of your company, even customers that have a zero balance during the specified period. Clear the check box to include only customers that have a non-zero balance or transactions during the specified period. |
| **Export all Suppliers** | This check box affects the data that is reported in the **MasterFiles** \> **Suppliers** node of the SAF-T. Select this check box to include all the suppliers of your company, even suppliers that have a zero balance during the specified period. Clear the check box to include only suppliers that have a non-zero balance or transactions during the specified period. |
| **Export all Analysis types** | This check box affects the data that is reported in the **MasterFiles** \> **AnalysisTypeTable** node of the SAF-T. Select this check box to include all the dimensions of your company. Clear the check box to include only dimensions that are used in transactions that are reported during the specified period. |
| **Export all Products** | This check box affects the data that is reported in the **MasterFiles** \> **Products** node of the SAF-T. Select this check box to include all the products of your company, even products that have zero physical stock during the specified period. Clear the check box to include only products that have non-zero physical stock or transactions during the specified period. |
| **Export all Sales tax codes** | This check box affects the data that is reported in the  **MasterFiles** \> **TaxTable** node of the SAF-T. Select this check box to include all the sales tax codes of your company. Clear the check box to include only sales tax codes that are used in transactions that are reported during the specified period. |

## SAF-T content

According to the SAFT-T technical documentation, different types of SAF-T include different content, as shown in the following table.

| SAF-T file part        | Group of elements     | F | GL | MG | SI | PI | PA | AS |
|------------------------|-----------------------|---|----|----|----|----|----|----|
| Header                 |                       |   |    |    |    |    |    |    |
|                        | Header                | X | X  | X  | X  | X  | X  | X  |
| Master files           |                       |   |    |    |    |    |    |    |
|                        | GeneralLedgerAccounts | X | X  |    |    |    |    |    |
|                        | Customers             | X | X  | X  | X  | X  | X  |    |
|                        | Suppliers             | X | X  | X  | X  | X  | X  | X  |
|                        | TaxTable              | X | X  | X  | X  | X  |    |    |
|                        | UOMTable              | X |    | X  | X  | X  |    |    |
|                        | AnalysisTypeTable     | X | X  |    | X  | X  | X  |    |
|                        | MovementTypeTable     | X |    | X  |    |    |    |    |
|                        | Products              | X |    | X  | X  | X  |    |    |
|                        | PhysicalStock         | X |    | X  | X  | X  |    |    |
|                        | Assets                | X |    |    |    |    |    | X  |
| General ledger entries |                       |   |    |    |    |    |    |    |
|                        | GeneralLedgerEntries  | X | X  |    |    |    |    |    |
| Source documents       |                       |   |    |    |    |    |    |    |
|                        | Sales invoices        | X |    |    | X  |    |    |    |
|                        | PurchaseInvoices      | X |    |    |    | X  |    |    |
|                        | Payments              | X |    |    |    |    | X  |    |
|                        | MovementOfGoods       | X |    | X  |    |    |    |    |
|                        | AssetTransactions     | X |    |    |    |    |    | X  |
