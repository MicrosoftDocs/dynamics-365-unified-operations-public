--- 
title: France e-reporting (electronic reporting of transactions) preparation
description: Learn how to set up e-reporting in France. 
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 07/28/2026
ms.custom:
  - bap-template
ms.reviewer: johnmichalak 
ms.search.region: France
ms.search.validFrom: 2026-06-30
ms.search.form: CustTable, VendTable, OMLegalEntity
ms.dyn365.ops.version: Version 7.0.0 
---

# How to prepare your Dynamics 365 Finance for French e-Reporting

[!include [banner](../../includes/banner.md)]

To enable France e-reporting, complete the following steps:

- [Import and configure ER configurations](#configurations)
- [Configure application-specific parameters for the ER format](#configure-asp)
- [Import a package of data entities that includes a predefined EM setup](#data-entities)
- [Set up EM parameters for the France e-reporting](#set-up-em-parameters)

Optionally, you can [set up France e-Reporting to report in multiple VAT registrations legal entity](#set-up-multi-tax) if applicable.

## <a id="configurations"></a>Import and configure ER configurations

To prepare Finance for France e-reporting, import the following ER configurations.

| ER configuration name | Type | Description|
|-----------------------|------|-------------|
| Invoices Communication Model | Model | A generic data model that standardizes how invoice-related information is structured and processed across electronic reporting scenarios based on Electronic Messages (EM) functionality. |
| e-Reporting Model mapping | Model mapping | A generic model mapping that provides model mapping for e-reporting based on Electronic Messaging (EM). |
| e-Reporting XML (FR) |Format (exporting) | XML format for France e-reporting. |

Import the latest versions of these configurations. The version description usually includes the number of the Microsoft Knowledge Base (KB) article that explains the changes that were introduced in the configuration version.

Use the number of the KB in the [Dynamics 365 Lifecycle Services Issue search portal](https://lcs.dynamics.com/v2) to learn more about the changes introduced.
If the latest configuration version contains references to the objects that aren't available in your Finance version, the import process locks for that configuration version. In this case, import the latest version of the configuration that's available for your Finance version.

> [!NOTE]
> After you import all the ER configurations from the preceding table, set the **Default for model mapping** option to **Yes** for the **e-Reporting Model mapping** configuration.

Learn more about how to import ER configurations in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

## <a id="configure-asp"></a>Configure application-specific parameters for the e-Reporting XML (FR) format

To correctly populate the `TransactionReportType > Transaction > CategoryCode` field in the France e-reporting XML output, you must configure application-specific parameters for the format.

The `CategoryCode` identifies the type of reported transaction according to the French regulatory classification. The correct value must be derived based on the transaction characteristics in your system.

The **TransCategoryCodeLookup** application-specific parameter enables flexible determination of the `CategoryCode` in the report. You can configure this lookup to align your business data with the required reporting classifications.

The following values are supported:

- TLB1: Transactions – Goods (B2C aggregated / sales of goods)
- TPS1: Transactions – Services
- TNT1: Transactions – Non-territorial / outside VAT scope
- TMA1: Transactions – Mixed / aggregated categories

To configure the **TransCategoryCodeLookup**, follow these steps:

1. In the configuration tree, under the **Invoices Communication Model**, select the **e-Reporting XML (FR)** format.
1. On the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, select the latest version of the format that you want to define conditions for.
1. On the **Lookups** FastTab, select the **TransCategoryCodeLookup** lookup, and define the appropriate conditions.
1. On the **Conditions** FastTab, define which combination of **Tax code**, **Sales tax group**, **Item sales tax group** must correspond to a specific lookup result.
1. Assign the appropriate **TransactionCategoryCode** value for each combination.
1. After you finish setting up conditions, in the **State** field, select **Completed**. Then save the configuration.

## <a id="data-entities"></a>Import a package of data entities that includes a predefined EM setup

Setting up the [Electronic messages](../../general-ledger/electronic-messaging-setup.md) (EM) functionality for France e-reporting involves many steps.
Because the ER configurations use the names of some predefined entities, use a set of predefined values that the package of data entities delivers for the related tables. Some records in the data entities in the package include a link to ER configurations. Before you start to import the data entities package, [import ER configurations](#configurations) into Finance.

To import a package of data entities, follow these steps:

1. In [Lifecycle Services](https://lcs.dynamics.com/v2), go to the **Shared asset library**, and select **Data package** as the asset type. Then find `FR eReporting EM setup v.1 ID1103856.zip` in the list of data package files, and download it to your computer.
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

### Electronic message definitions in France e-reporting

In the context of France e-reporting processing, an electronic message represents a single generated reporting document for a defined reporting period.

Each electronic message:

- Corresponds to one structured XML report.
- Contains a collection of transactions and payment data.
- Is generated based on the selected reporting scope and period.
- Serves as the unit of processing within the **Electronic Messages** framework.

Within the system:

- The electronic message acts as a container for reporting data.
- Individual transactions and payment records are represented as message items.
- All message items are aggregated into one output file during report generation.

This structure allows you to:

- Group transactions into a single report.
- Track processing status at the report level.
- Maintain traceability between source transactions and the generated reporting output.

## <a id="set-up-em-parameters"></a>Set up EM parameters for the France e-reporting

To enable France e-reporting processing, you must configure Electronic Messages (EM) parameters. This setup defines how the system collects data, structures messages, enriches them with extra data, and processes them during report generation.

The configuration includes:

- Message additional fields
- Message item additional fields
- Action parameters
- Security roles for the electronic message processing
- Executable class settings

### Set up message additional fields

Message additional fields define values that apply to the entire electronic message and are included in the generated output.

To set up message additional fields, follow these steps:

1. Open the **Electronic messages processing** setup.
1. Select the **FR e-Reporting** processing.
1. Go to the **Message additional fields** section.
1. Set the default values for the following additional fields:

   - FR-eRep SenderId: specifies the identifier of the reporting entity.
   - FR-eRep SenderName: specifies company name of the issuer of the transmission document.
   - FR-eRep TypeCode: specifies the type of report. The following values are available: IN - Initiale (default value), RE - Rectificative.

Enter the appropriate default values based on your reporting requirements. The system uses these values as header-level information in the generated report.

### Set up message item additional fields

Message item additional fields define values at the transaction level (message item level).

To set up message item additional fields, follow these steps:

1. In the same processing setup, go to the **Message item additional fields** section.
1. Set fields for each relevant message item type. The default configuration defines the following values:

   | Message item type| Field name | Default value |
   | ----- | ----- | ----- |
   | FR-eRep Transactions B2C | FR-eRep TaxDueDateTypeCode | 3 |
   | FR-eRep Transactions Invoice | FR-eRep TaxDueDateTypeCode | 3 |

The **FR e-Reporting** processing supports the following values for **FR-eRep TaxDueDateTypeCode**:

- 3: Invoice issue date
- 432: Payment date (VAT on cash receipts)

These fields populate transaction-level attributes in the generated output.

### Set up parameters for actions

Electronic Messages uses processing actions that require parameter configuration.

To set up parameters for actions, follow these steps:

1. Open the **Electronic message processing** page and select the **FR e-reporting** processing.
1. Select **Action parameters** to configure parameters for the following actions:

   - FR-eRep Generate Full Report
   - FR-eRep Generate Payments Report
   - FR-eRep Generate Transactions Report
   - FR-eRep Regenerate Report File

| Parameter name                         | Parameter value                |
| -------------------------------------- | ------------------------------ |
| Additional field for Sender ID         | FR-eRep SenderId               |
| Additional field for Sender name       | FR-eRep SenderName             |
| Additional field for VAT payment type  | FR-eRep TaxDueDateTypeCode     |
| Additional field for Type code         | FR-eRep TypeCode               |
| Message item type for Payments report type - Invoice  | FR-eRep Payments Invoice           |
| Message item type for Payments report type - Transactions | FR-eRep Payments B2C           |
| Message item type for Transactions report type - Invoice  | FR-eRep Transactions Invoice   |
| Message item type for Transactions report type - Transactions | FR-eRep Transactions B2C   |

Proper configuration ensures that the system correctly collects and processes data during report generation.

### Security roles for the electronic message processing

Different groups of users might require access to different electronic message processing. You can limit access to each type of processing, based on security groups that you define in the system.

To limit access to the **FR e-reporting** processing, follow these steps:

1. In Finance, go to **Tax** \> **Setup** \> **Electronic messages** \> **Electronic message processing**.
1. Select the **FR e-reporting** processing.
1. On the **Security roles** FastTab, add the security groups that must work with this processing for testing purposes. If you don't define a security group for the processing, only a system administrator can see the processing on the **Electronic messages** page.

> [!NOTE]
> If you don't define security roles for electronic message processing, only a system admin can see the electronic message processing by going to **Tax** > **Inquiries and reports** > **Electronic messages** > **Electronic messages**.

### Set up executable class settings

Executable class settings define how the system executes processing logic during EM actions.

Two executable classes are involved in **FR e-reporting** processing:

| Executable class | Description | Executable class name | Action type |
|------------------|-------------|-----------------------|-------------|
| FR-eRep PopulateMessageItems | Generate message elements for e-reporting | EReportingEMCreateItemsController_FR | Populate records |
| FR-eRep GenerateReportFile | Generate a message for e-reporting | EReportingEMExportController_FR | Electronic reporting export |

#### Set up **FR-eRep PopulateMessageItems** executable class parameters

The **FR‑eRep PopulateMessageItems** executable class performs the data collection and preparation step of the process. It:

- Retrieves transaction and payment data from multiple data sources in Finance.
- Aggregates and organizes the data according to reporting requirements.
- Creates and populates electronic message items based on the collected data.
- Defines relevant values of additional fields for created message items.

During execution, the class:

- Reads data from multiple tables and transaction sources, including:
  - Customer invoices
  - Vendor invoices
  - Payment transactions
  - Tax transactions
- Applies selection criteria based on the executable class parameters
- Calculates and assigns relevant values to the message item additional fields
- Assigns to electronic message items types:
  - FR‑eRep Transactions Invoice – Invoice-based transactions subject to reporting
  - FR‑eRep Transactions B2C – Aggregated B2C transactions
  - FR‑eRep Payments Invoice – Payments related to invoices
  - FR‑eRep Payments B2C – Payments related to B2C transactions

Each message item type represents a specific reporting scenario and determines how the system processes and includes the data in the final report.

Within the **FR e-reporting** processing:

- The system triggers the **FR‑eRep PopulateMessageItems** executable class during the data collection action.
- It produces the message items that serve as the input for report generation.
- The generated message items are later used to produce the structured output.

After this class executes:

- The system creates electronic message items in the **Electronic message items** table based on the **FR‑eRep PopulateMessageItems** executable class parameters.
- Each message item represents a transaction or aggregated data set.
- The system calculates all relevant values for message item additional fields for the created message items.
- The system is ready to proceed to the report generation step.

To set up **FR-eRep PopulateMessageItems** executable class parameters, select the **Parameters** button on the Action pane.

| Report type              | Parameter name                   | Parameter value                  |
|--------------------------|----------------------------------|----------------------------------|
| Transactions report type | Invoice                          | FR-eRep Transactions Invoice     |
| Transactions report type | Transaction                      | FR-eRep Transactions B2C         |
| Transactions report type | Status to Created                | FR-eRep Transaction Entry Created|
| Transactions report type | Additional field for VAT payment | FR-eRep TaxDueDateTypeCode       |
| Transactions report type | Paid to date value               | 432                              |
| Payments report type     | Invoice                          | FR-eRep Payments Invoice         |
| Payments report type     | Transaction                      | FR-eRep Payments B2C             |
| Payments report type     | Status to Created                | FR-eRep Payment Entry Created    |

During execution of the **FR‑eRep PopulateMessageItems** executable class, filters define which records are selected and included in electronic message items.
Configure these filters in the **Records to include** sections to control how the system retrieves data from source tables.

Filters are available for the four sections of France e-report:

- Payments report type – Invoice
- Transactions report type – Transaction
- Transactions report type – Invoice
- Payments report type – Transaction

When the process runs, it evaluates the filters during data selection and retrieves only records that meet all filter conditions. The process assigns these records to the appropriate message item type.

#### Set up **FR-eRep GenerateReportFile** executable class parameters

The **FR‑eRep GenerateReportFile** executable class generates the e‑reporting XML output based on the data collected in electronic message items.
This class performs the report generation step of the process. It:

- Reads electronic message items created during the data collection step.
- Organizes the data according to the reporting structure.
- Produces a structured output file that represents the electronic message in XML format.

During execution, the **FR‑eRep GenerateReportFile** class:

- Retrieves the electronic message items to process.
- Applies the reporting structure and mappings.
- Generates a structured XML output file.

The generated file represents:

- One reporting document for the reporting period.
- A collection of transactions and payment data.

Within the **FR e-reporting** processing:

- The generate report action triggers the class.
- It transforms message items into a consumable report format.
- It prepares the output file for further processing outside the system.

After this class executes:

- A structured XML output file is generated for the electronic message.
- The file contains all relevant transactions and payment data.

The settings of this class control the execution of logic that drives data collection, processing, and output generation.

| Report type              | Parameter name                   | Parameter value                  |
|--------------------------|----------------------------------|----------------------------------|
| Transactions report type | Invoice                          | FR-eRep Transactions Invoice     |
| Transactions report type | Transaction                      | FR-eRep Transactions B2C         |
| Transactions report type | Status to Pending                | FR-eRep Transaction Entry Pending|
| Transactions report type | Status to Excluded               | FR-eRep Transaction Entry Excluded|
| Payments report type     | Invoice                          | FR-eRep Payments Invoice         |
| Payments report type     | Transaction                      | FR-eRep Payments B2C             |
| Payments report type     | Status to Pending                | FR-eRep Payment Entry Pending  |
| Payments report type     | Status to Excluded                | FR-eRep Payment Entry Excluded    |

## <a id="set-up-multi-tax"></a>Set up FR e-Reporting to report in multiple VAT registrations legal entity

The multiple VAT registrations legal entity scenario applies to organizations that operate with multiple VAT registration numbers within the same legal entity.
This scenario is supported if you're using the [Tax Calculation](../global/global-tax-calcuation-service-overview.md) functionality and enabled the [Support multiple VAT registration numbers](../global/emea-multiple-vat-registration-numbers.md) parameter in the **Tax calculation parameters** page.

In this scenario, you must group and report transactions per VAT registration, rather than for the whole legal entity. When you enable multiple VAT registrations, you assign each transaction (for example, customer invoice, vendor invoice, or tax transaction) a tax registration number.

As a result:

- All reporting-relevant records contain the VAT registration context.
- The system can distinguish transactions belonging to different registrations.

To report data for a specific VAT registration, configure filters in the **FR‑eRep PopulateMessageItems** executable class parameters.
For example, apply a filter on fields that contain the VAT registration identifier or use conditions that correspond to your tax registration setup.

Only records that match the filter criteria are:

- Retrieved from source tables.
- Converted into electronic message items.
- Included in the generated report.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
