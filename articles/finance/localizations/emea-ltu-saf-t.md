---
# required metadata

title: Standard Audit File for Tax (SAF-T) for Lithuania
description: This topic explains how to set up and generate the Standard Audit File for Tax (SAF-T) for legal entities with a primary address in Lithuania. 
author: liza-golub
ms.author: elgolu
ms.date: 03/08/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

manager: 
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

This document provides information about how to prepare Dynamics 365 Finance to work with **SAF-T** report for Lithuania.

According to Article 16 of the Law on Accounting of the Republic of Lithuania, companies in Lithuania are legally required to provide a report in the format Standard Audit File for Tax (SAF-T). This article describes how Dynamics 365 Finance supports the SAF-T requirements.

For more information, see [SAF-T - VMI](https://www.vmi.lt/cms/web/guest/saf-t).

## Setup  

To start working with the **Lithuania SAF-T** report complete the following steps.

1.  In Finance, import the following or later versions of these Electronic reporting (ER) configurations from the Global repository:

    | **ER configuration name**       | **Type**      | **Version** | **Description**                                                                         |
    |---------------------------------|---------------|-------------|-----------------------------------------------------------------------------------------|
    | **Standard Audit File (SAF-T)** | **Model**     | **128**     | Common data model for different audit reports                                           |
    | SAF-T General model mapping     | Model mapping | 128.251     | Model mapping that provides general data sources mapping                                |
    | SAF-T Format (LT)               | Format        | 128.198     | The XML format that represents SAF-T in accordance with requirements for Lithuania.     |

    ![ER configurations for Standard Audit File for Tax (SAF-T) for Lithuania](media/lt-saf-t-ger-configurations.png)

    SAF-T General model mapping provides general data sources mapping for the following master data:

    <ul>
      <li>GeneralLedgerAccounts: General ledger.</li>
      <li>Customers: Purchasers (customers) and other debtors (available in the file).</li>
      <li>Suppliers: Suppliers and other creditors (available in the file).</li>
      <li>TaxTable: Tax type table data. All tax type tables used in the accounting system of the entity are specified. For example, VAT, Corporate Income Tax, and excise taxes.</li>
      <li>UOMTable: Type table of units of measurement.</li>
      <li>AnalysisTypeTable: Data of type tables of analytical accounting. Used for detailing transaction data. For example, unit costs, additional costs, a center of costs, or a project.</li>
      <li>MovementTypeTable: Stock movement types.</li>
      <li>Products: Products and services.</li>
      <li>PhysicalStock: Stock (data of the stock contained in the file).</li>
    </ul>

     SAF-T General model mapping provides general data sources mapping for the following transactional data:

    <ul>
      <li>GeneralLedgerEntries: General ledger entries.</li>
      <li>Sales invoices: Initial sales documents.</li>
      <li>PurchaseInvoices: Accounting documents of purchases and acquisitions.</li>
      <li>Payments: Payments.</li>
      <li>MovementOfGoods: Information on movement of goods. For example, recording of goods, write-off after sale of goods or after use in production, recording of finished products, loss determined, and defective goods.</li>
      <li>AssetTransactions: Economic transactions or economic asset (tangible, intangible and financial assets) events.</li>
    </ul>

    Be sure to import the most recent versions of these configurations. The version description usually includes the number of the Microsoft Knowledge Base (KB) article that explains the changes that were introduced in the configuration version.

    ![Default model mapping for Standard Audit File for Tax (SAF-T) for Lithuania](media/lt-saf-t-default-model-mapping.png)

    > [!IMPORTANT]
    > After all the ER configurations from the table above are imported, set the **Default for model mapping** option to **Yes** for the **SAF-T General model mapping** configuration.

    For more information about how to download ER configurations, see [Download ER configurations from the Global repository](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

2. Set up **Application specific parameters** for **SAF-T Format (LT)**. Go to **Electronic Reporting** and under the **Standard Audit File (SAF-T)** model, select **SAF-T Format (LT)**.
3. Select **Configurations** \> **Application-specific parameters**, and on the Action Pane, select **Setup** and then select the last version of the configuration in the list on the left. 
4. Provide mapping for all the lookup fields:

  - **StandardMainAccount_Lookup**: Define how to map the Main accounts used by the company and the Standard main accounts of Lithuania.
  - **ReportTaxCodes_LOOKUP**: Define how to map the Sales tax codes used by the company and the Standard tax codes of Lithuania.
  - **StandardAnalysisType_LOOKUP**: Define how to map the dimensions used by the company and the Standard Analysis of Lithuania.
  - **AddressType_LOOKUP**: Define how to map the address types used by the company and the address types used in the Lithuanian SAF-T.

5. When the lookup fields are set up, in the **State** field, select **Completed**, and then save the configuration.
6. Go to **General ledger** \> **Setup** \> **General ledger parameters**, and select the **Standard Audit File for Tax** FastTab.
7. In the **Standard Audit File for Tax (SAF-T)** field, set up the SAF-T format.
8. Go to **Feature management** > **All**. In the feature list, locate and select the following features:

    - **Optimization of query data source creation time during execution of ER reports**
    - **Optimize datasets memory consumption at ER reports runtime**
 
9. Select **Enable now**.

## Generate SAF-T

- To run the SAF-T report, go to **General ledger** \> **Inquires and reports** \> **Standard Audit File for Tax (SAF-T)** \> **Standard Audit File for Tax (SAF-T)**.

The following table provides a description of the report dialog fields.

| **Field name**                                   | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|--------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **SAF-T File type**                              | SAF-T supports the following types: <ul><li>**F** - Full SAF-T file. This type of SAF-T file can be split by period.</li><li>**GL** - General ledger records. This part of SAF-T file can be split by entities, periods, or parts. </li><li>**PI** - Purchase data. This part of SAF-T file can be split by entities, periods, or parts.</li><li>**PA** - Payments data. This part of SAF-T file can be split by entities, periods, or parts.</li><li>**SI** - Sales data. This part of SAF-T file can be split by entities, periods, or parts.</li><li>**MG** - Movement of goods. This part of SAF-T file can be split by entities, periods, or parts.</li><li>**AS** - Movement of fixed asset. This part of SAF-T file can be split by entities, periods or parts.</li><ul> |
| **Reporting period from** and **Reporting period to**   | Specify the date interval for which SAF-T is requested. These dates are reflected in the **Header** \> **SelectionCriteria** \> **SelectionStartDate** and **SelectionEndDate** nodes of the SAF-T respectively. These are start and end dates of the period inspected.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| **From date** and **To date** | Specify the date interval for which data will be included in the report. These dates are reflected in the **Header** \> **SelectionCriteria** \> **PeriodStart** and **PeriodEnd** nodes of the SAF-T respectively. A period of one file or a part of a file can't be shorter than one month and longer than a reporting period.                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| **Number of parts**                              | Specify in how many parts you will generate your SAF-T. This value is reflected in the **Header** \> **NumberOfParts** node of the SAF-T.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| **Part number**                                  | Specify the number of the part to generate in the current SAF-T. This value is reflected in the **Header** \> **PartNumber** node of the SAF-T.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| **Print zero balance**                           | This check box influences the data reported in **MasterFiles** \> **GeneralLedgerAccounts** node of SAF-T. Select this check box if you want to include all the main accounts of your company, even those with a zero balance in the specified period. When the **Print zero balance** check box is unmarked, only main accounts with a non-zero balance or transactions in the specified period will be included in the **MasterFiles** \> **GeneralLedgerAccounts** node of SAF-T.                                                                                                                                                                                                                                                                                                                                                                                                          |
| **Export all Customers**                         | This check box influences the data reported in **MasterFiles** \> **Customers** node of SAF-T. Select this check box if you want to include all the customers of your company, even those with zero balance in the specified period. When the **Export all Customers** check box isn't selected, only customers with a non-zero balance or transactions in the specified period will be included in the **MasterFiles** \> **Customers** node of SAF-T.                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| **Export all Suppliers**                         | This check box influences the data reported in **MasterFiles** \> **Suppliers** node of SAF-T. Select this check box if you want to include all the suppliers of your company, even with zero balance in the specified period. When the **Export all Suppliers** check box isn't selected, only suppliers with a non-zero balance or transactions in the specified period will be included in the **MasterFiles** \> **Suppliers** node of SAF-T.                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| **Export all Analysis types**                    | This check box influences the data reported in **MasterFiles** \> **AnalysisTypeTable** node of SAF-T. Select this check box if you want to include all the dimensions of your company. When the **Export all Analysis types** check box isn't selected, only the dimensions used in transactions reported in the specified period will be included in the **MasterFiles** \> **AnalysisTypeTable** node of SAF-T.                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **Export all Products**                          | This check box influences the data reported in **MasterFiles** \> **Products node of SAF-T**. Select this check box to include all the products of your company, even with zero PhysicalStock in the specified period. When the **Export all Products** check box is not selected, only products with non-zero PhysicalStock or transactions in the specified period are included in the **MasterFiles** \> **Suppliers** node of SAF-T.                                                                                                                                                                                                                                                                                                                                                                                                                                |
| **Export all Sales tax codes**                   | This check box influences the data reported in **MasterFiles** > **TaxTable** node of SAF-T. Select this check box to include all of your company's Sales tax codes. When the **Export all Sales tax codes** check box is not selected, only the Sales tax codes that are used in transactions that are reported in the specified period are included in the **MasterFiles** \> **TaxTable** node of SAF-T.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |

## SAF-T content

According to the technical documentation on SAF-T, different types of SAF-T include the following content:

| **SAF-T file part**        | **Group of elements** | **F** | **GL** | **MG** | **SI** | **PI** | **PA** | **AS** |
|----------------------------|-----------------------|-------|--------|--------|--------|--------|--------|--------|
| **Header**                 |                       |       |        |        |        |        |        |        |
|                            | Header                | X     | X      | X      | X      | X      | X      | X      |
| **Master files**           |                       |       |        |        |        |        |        |        |
|                            | GeneralLedgerAccounts | X     | X      |        |        |        |        |        |
|                            | Customers             | X     | X      | X      | X      | X      | X      |        |
|                            | Suppliers             | X     | X      | X      | X      | X      | X      | X      |
|                            | TaxTable              | X     | X      | X      | X      | X      |        |        |
|                            | UOMTable              | X     |        | X      | X      | X      |        |        |
|                            | AnalysisTypeTable     | X     | X      |        | X      | X      | X      |        |
|                            | MovementTypeTable     | X     |        | X      |        |        |        |        |
|                            | Products              | X     |        | X      | X      | X      |        |        |
|                            | PhysicalStock         | X     |        | X      | X      | X      |        |        |
|                            | Assets                | X     |        |        |        |        |        | X      |
| **General ledger entries** |                       |       |        |        |        |        |        |        |
|                            | GeneralLedgerEntries  | X     | X      |        |        |        |        |        |
| **Source documents**       |                       |       |        |        |        |        |        |        |
|                            | Sales invoices        | X     |        |        | X      |        |        |        |
|                            | PurchaseInvoices      | X     |        |        |        | X      |        |        |
|                            | Payments              | X     |        |        |        |        | X      |        |
|                            | MovementOfGoods       | X     |        | X      |        |        |        |        |
|                            | AssetTransactions     | X     |        |        |        |        |        | X      |

