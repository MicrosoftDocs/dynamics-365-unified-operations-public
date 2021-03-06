---
# required metadata

title: Standard Audit File for Tax (SAF-T) for Lithuania
description: This topic explains how to set up and generate the Standard Audit File for Tax (SAF-T) for legal entities that have their primary address in Lithuania. 
author: liza-golub
ms.author: elgolu
ms.date: 06/03/2021
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

According to Article 16 of the Law on Accounting of the Republic of Lithuania,
companies in Lithuania are legally required to provide a report in the format
Standard Audit File for Tax (SAF-T). This article describes how Dynamics 365
Finance supports the SAF-T requirements.

Find more related information on [SAF-T -
VMI](https://www.vmi.lt/cms/web/guest/saf-t)

## Setup

This document provides information about how to prepare Dynamics 365 Finance to
work with **SAF-T for Lithuania starting from 10.0.18**.

To start working with Lithuania SAF-T report follow the next steps:

1.  When your Finance application version is suitable, import the following versions or later of these Electronic reporting (ER) 
configurations from Global repository:

| **ER configuration name**       | **Type**      | **Version** | **Description**                                                                         |
|---------------------------------|---------------|-------------|-----------------------------------------------------------------------------------------|
| **Standard Audit File (SAF-T)** | **Model**     | **128**     | Common data model for different audit reports                                           |
| SAF-T General model mapping     | Model mapping | 128.251     | Model mapping that provides general data sources mapping                                |
| SAF-T Format (LT)               | Format        | 128.198     | The XML format that represents SAF-T in accordance with requirements for Lithuania.     |

SAF-T General model mapping provides general data sources mapping for the following master data:

<ul>
  <li>GeneralLedgerAccounts - General ledger.</li>
  <li>Customers - Purchasers (customers), other debtors (available in the file).</li>
  <li>Suppliers - Suppliers, other creditors (available in the file).</li>
  <li>TaxTable - Tax type table data. All tax type tables used in the accounting system of the entity are specified, e.g. VAT, Corporate Income Tax, excise taxes, etc.</li>
  <li>UOMTable - Type table of units of measurement.</li>
  <li>AnalysisTypeTable - Data of type tables of analytical accounting. Used for further detailing of transaction data, e.g. unit costs, additional costs (or a centre of costs), project.</li>
  <li>MovementTypeTable - Stock movement types.</li>
  <li>Products - Products / services.</li>
  <li>PhysicalStock - Stock (data of the stock contained in the file).</li>
</ul>

And following transactional data:

<ul>
  <li>GeneralLedgerEntries - General Ledger Entries.</li>
  <li>Sales invoices - Initial sales documents.</li>
  <li>PurchaseInvoices - Accounting documents of purchases (acquisitions).</li>
  <li>Payments - Payments.</li>
  <li>MovementOfGoods - Information on movement of goods, e.g. recording of goods, write-off after sale of goods or after use thereof in production, recording of finished products, loss determined, defective goods, etc.</li>
  <li>AssetTransactions - Economic transactions or economic asset (tangible, intangible and financial assets) events.</li>
</ul>

Be sure to import the most recent versions of these configurations. The version
description usually includes the number of the Microsoft Knowledge Base (KB)
article that explains the changes that were introduced in the configuration
version.

**Note:** After all the ER configurations from the preceding table are imported,
set the **Default for model mapping** option to **Yes** for the **SAF-T General
model mapping** configuration.

For more information about how to download ER configurations, see [Download ER
configurations from the Global
repository](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo).

2. Set up **Application specific parameters** for **SAF-T Format (LT)**. Open
**Electronic Reporting**, select **SAF-T Format (LT)** under **Standard Audit
File (SAF-T)** model, click **Configurations** \> **Application-specific
parameters** \> **Setup** on the Action pane and select the last version of the
configuration in the list on the left. Provide mapping for all the lookup
fields:

-   **StandardMainAccount_Lookup** - define mapping of the Main accounts used by
    the company and Standard main accounts of Lithuania

-   **ReportTaxCodes_LOOKUP** - define mapping of the Sales tax codes used by
    the company and Standard tax codes of Lithuania

-   **StandardAnalysisType_LOOKUP** - define mapping of the Dimensions used by
    the company and Standard Analysis of Lithuania

-   **AddressType_LOOKUP** - define mapping of the address’s types used by the
    company and the address types used in the Lithuanian SAF-T

When setup of lookup fields is done, in the **State** field, select
**Completed**, and then save the configuration.

3. Set up SAF-T format in **General ledger** \> **Setup** \> **General ledger
parameters**, **Standard Audit File for Tax** fast tab, **Standard Audit File
for Tax (SAF-T)** field.
