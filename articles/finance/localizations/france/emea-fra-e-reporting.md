--- 
title: France e-reporting (electronic reporting of transactions)
description: Learn how to set up and report electronically transaction in France. 
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 06/07/2026
ms.custom:
ms.reviewer: johnmichalak 
audience: Application User
ms.search.region: France
ms.search.validFrom: 2026-06-30
ms.search.form: CustTable, VendTable, OMLegalEntity
ms.dyn365.ops.version: Version 7.0.0 
---

# France e-reporting (electronic reporting of transactions)

## Overview

France e-reporting (transmission des données de transaction) is part of the French continuous transaction control (Réforme de la facturation électronique) reform that requires companies to report specific business transactions to the French tax authorities through an approved intermediary platform.
In Dynamics 365 Finance, the France e-reporting feature enables organizations to:

- Collect required transaction data from Finance documents
- Transform data into the French-compliant formats by using Electronic reporting (ER)

This feature complements [electronic invoicing (e-invoicing)](emea-fra-einv-ereport.md) requirements and relies on the same core concepts, including registration identifiers and establishment-based reporting.

## Scope of e-reporting

France e-reporting applies to the electronic transmission of data for transactions that are outside the scope of mandatory e-invoicing.
This includes:

- B2C (business-to-consumer) transactions
- Cross-border B2B and B2C transactions
- Payment data for transactions where VAT is due upon payment

E-reporting complements e-invoicing by ensuring that the tax authorities receive data for all VAT-relevant transactions.

## Registration IDs and establishments

Accurate identification of legal entities and their establishments is required for compliant reporting.

Before you configure e-reporting:

- Set up registration IDs (for example, VAT ID, SIREN and SIRET numbers)
- Configure the establishment structure
- Ensure that transactions are associated with the correct establishment

For more information, see [Registration IDs set up for France](emea-fra-registration-numbers-setup-for-france.md) and [Use establishments in France](emea-fra-establishments-for-france.md).

## Setup overview

To enable France e-reporting, complete the following steps:

- [Import and configure ER configurations](#configurations)
- [Configure application-specific parameters for the ER format]()
- [Import a package of data entities that includes a predefined EM setup](#data-entities)
- [Set up EM parameters for the France e-reporting](#set-up-em-parameters)

### <a id="configurations"></a>Import and configure ER configurations

To prepare Finance to France e-reporting, import the following ER configurations.

|	ER configuration name |	Type |	Description|
|-----------------------|------|-------------|
| Invoices Communication Model	| Model	| A generic data model that standardizes how invoice-related information is structured and processed across electronic reporting scenarios based on Electronic Messages (EM) functionality. |
| e-Reporting Model mapping |	Model mapping	| A generic model mapping that provides model mapping for e-reporting based on Electronic Messaging (EM). |
|	e-Reporting XML (FR)	|Format (exporting) |	XML format for France e-reporting. |

Import the latest versions of these configurations. 
The version description usually includes the number of the Microsoft Knowledge Base (KB) article that explains the changes that were introduced in the configuration version. 
Use the number of the KB in the [LCS Issue search portal](https://lcs.dynamics.com/v2) to learn more about the changes introduced. 
If the latest configuration version contains references to the objects that aren't available in your Finance version, the import process locks for that configuration version. 
In this case, import the latest version of the configuration that's available for your Finance version.

> [!NOTE]
> After you import all the ER configurations from the preceding table, set the **Default for model mapping** option to **Yes** for the **e-Reporting Model mapping** configuration.

Learn more about how to import ER configurations in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

### <a id="configure-asp"></a>Configure application-specific parameters for the e-Reporting XML (FR) format

To correctly populate the `TransactionReportType > Transaction > CategoryCode` field in the France e-reporting XML output, you must configure application-specific parameters for the format.

The `CategoryCode` identifies the type of reported transaction according to the French regulatory classification. The correct value must be derived based on the transaction characteristics in your system.

The **TransCategoryCodeLookup** application-specific parameter is provided to enable flexible determination of the `CategoryCode` in the report. You can configure this lookup to align your business data with the required reporting classifications.

The following values are supported:
- TL: Transactions – Goods (B2C aggregated / sales of goods)
- TPS1: Transactions – Services
- TNT1: Transactions – Non-territorial / outside VAT scope
- TMA1: Transactions – Mixed / aggregated categories

Configure the **TransCategoryCodeLookup**:
1. In the configuration tree, under the **Invoices Communication Model**, select the **e-Reporting XML (FR)** format.
1. On the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
2. On the **Application specific parameters** page, select the latest version of the format that you want to define conditions for.
3. On the **Lookups** FastTab, select the **TransCategoryCodeLookup** lookup, and define the appropriate conditions.
4. On the **Conditions** FastTab, define which combination of **Tax code**, **Sales tax group**, **Item sales tax group** must correspond to a specific lookup result.
5. Assign the appropriate **TransactionCategoryCode** value for each combination.
6. After you finish setting up conditions, in the **State** field, select **Completed**. Then save the configuration.

### <a id="data-entities"></a>Import a package of data entities that includes a predefined EM setup

Setting up the [Electronic messages](../../general-ledger/electronic-messaging-setup.md) (EM) functionality for France e-reporting involves many steps. 
Because the ER configurations use the names of some predefined entities, use a set of predefined values that are delivered in a package of data entities for the related tables. 
Some records in the data entities in the package include a link to ER configurations. Before you start to import the data entities package, [import ER configurations](#configurations) into Finance.

To import a package of data entities, follow these steps:

1. In [LCS](https://lcs.dynamics.com/v2), go to the **Shared asset library**, and select **Data package** as the asset type. Then find `FR eReporting EM setup v.1 ID1103856.zip` in the list of data package files, and download it to your computer.
1. After the `FR eReporting EM setup v.1 ID1103856.zip` file is downloaded, in Finance, select the company that you want to work with France e-reporting, and then go to **Workspaces** \> **Data management**.
1. Before you import setup data from the package of data entities, make sure that the data entities in your application are refreshed and synced. In the **Data management** workspace, go to **Framework parameters** \> **Entity settings**, and then select **Refresh entity list**. Wait for confirmation that the refresh is complete. For more information about how to refresh the entity list, see [Entity list refresh](../../../fin-ops-core/dev-itpro/data-entities/data-entities.md#entity-list-refresh).
1. Validate that the source data and target data are correctly mapped. For more information, see [Validate that the source data and target data are mapped correctly](../../../fin-ops-core/fin-ops/data-entities/data-import-export-job.md#validate-that-the-source-data-and-target-data-are-mapped-correctly).
1. Import data from the `FR eReporting EM setup v.1 ID1103856.zip` file into the selected company. In the **Data management** workspace, select **Import**, and then, on the **Import** FastTab, in the **Group name** field, select a value.
1. On the **Selected entities** FastTab, select **Add file**.
1. In the **Source data format** field, select **Package**, and then select **Upload and add**.
1. Find and select the `FR eReporting EM setup v.1 ID1103856.zip` file that you downloaded in step 1.
1. Wait until the data entities from the file are listed in the grid on the **Selected entities** FastTab, and then select **Close**.
1. On the Action Pane, select **Import** or **Import now** to start the import.

For more information, see [Data management](../../../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages.md?toc=%2ffin-and-ops%2ftoc.json).

The `FR eReporting EM setup v.1 ID1103856.zip` package provides a setup for the **FR e-Reporting** electronic messages processing that you can use.

#### Electronic message definitions in France e-reporting

In the context of France e-reporting processing, an electronic message represents a single generated reporting document for a defined reporting period.

Each electronic message:
- Corresponds to one structured XML report
- Contains a collection of transactions and/or payment data
- Is generated based on the selected reporting scope and period
- Serves as the unit of processing within the **Electronic Messages** framework

Within the system:
- The electronic message acts as a container for reporting data
- Individual transactions and payment records are represented as message items
- All message items are aggregated into one output file during report generation

This structure allows you to:
- Group transactions into a single report
- Track processing status at the report level
- Maintain traceability between source transactions and the generated reporting output

### <a id="set-up-em-parameters"></a>Set up EM parameters for the France e-reporting

To enable France e-reporting processing, you must configure Electronic Messages (EM) parameters. This setup defines how the data is collected, messages are structured, enriched with additional data, and processed during report generation.

The configuration includes:
- Message additional fields
- Message item additional fields
- Action parameters
- Executable class settings

#### Set up message additional fields

Message additional fields define values that apply to the entire electronic message and are included in the generated output.

1. Open the **Electronic messages processing** setup
2. Select the **FR e-Reporting** rocessing
3. Go to the **Message additional fields** section
4. Configure the default values for the following additional fields:
- FR-eRep SenderId: specifies the identifier of the reporting entity
- FR-eRep SenderName: specifies company name of the issuer of the transmission document
- FR-eRep TypeCode: – specifies the type of report. Following values are available: IN - Initiale (default value), RE - Rectificative.

Enter the appropriate default values based on your reporting requirements. These values are used as header-level information in the generated report.

#### Set up message item additional fields

Message item additional fields define values at the transaction level (message item level).

1. In the same processing setup, go to the **Message item additional fields** section.
2. Configure fields for each relevant message item type. Default configuration define the following:

| Message item type| Field name | Default value |
|-----|-----|-----|
| FR-eRep Transactions B2C | FR-eRep TaxDueDateTypeCode | 3 |
| FR-eRep Transactions Invoice | FR-eRep TaxDueDateTypeCode | 3 |

The following values of **FR-eRep TaxDueDateTypeCode** are supported by **FR e-Reporting** rocessing:
- 3: Invoice issue date
- 432: Payment date (VAT on cash receipts)

These fields are used to populate transaction-level attributes in the generated output.

#### Set up parameters for actions

Electronic Messages uses processing actions that require parameter configuration.

1. Open the **Electronic message processing** page and select the **FR e-reporting** processing.
2. Select **Action parameters button** to configure parameters for the following Actions:
- FR-eRep Generate Full Report
- FR-eRep Generate Payments Report
- FR-eRep Generate Transactions Report
- FR-eRep Regenerate Report File

| Parameter name                         | Parameter value                 |
|----------------------------------------|---------------------------------|
| Additional field for Sender Id         | FR-eRep SenderId               |
| Additional field for Sender name       | FR-eRep SenderName             |
| Additional field for VAT payment type  | FR-eRep TaxDueDateTypeCode     |
| Additional field for Type code         | FR-eRep TypeCode               |
| Message item type for Payments report type - Invoice  | FR-eRep Payments Invoice       |
| Message item type for Payments report type - Transactions | FR-eRep Payments B2C           |
| Message item type for Transactions report type - Invoice  | FR-eRep Transactions Invoice   |
| Message item type for Transactions report type - Transactions | FR-eRep Transactions B2C       |

Proper configuration ensures that the system correctly collects and processes data during report generation.

#### Set up executable class settings

Executable class settings define how the system executes processing logic during EM actions.

1. Open the **Executable class settings** page and locate the **FR-eRep PopulateMessageItems** executable class.

These settings control the execution of logic that drives data collection, processing, and output generation.

## Use EM functionality to report to the France e-reporting

## Report to the France e-reporting for multiple VAT registrations
