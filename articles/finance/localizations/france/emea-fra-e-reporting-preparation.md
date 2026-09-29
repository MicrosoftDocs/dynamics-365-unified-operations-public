--- 
title: France e-reporting (electronic reporting of transactions) preparation
description: Learn how to set up e-reporting in France. 
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 09/28/2026
ms.custom:
  - bap-template
ms.reviewer: johnmichalak 
ms.search.region: France
ms.search.validFrom: 2026-06-30
ms.search.form: CustTable, VendTable, OMLegalEntity
ms.dyn365.ops.version: Version 7.0.0 
---

# How to prepare your Dynamics 365 Finance for French e-reporting

[!INCLUDE [banner](../../includes/banner.md)]

To enable France e-reporting, complete the following steps:

- [Import and configure ER configurations](#configurations)
- [Configure application-specific parameters for the ER format](#configure-asp)
- [Import a package of data entities that includes a predefined EM setup](#data-entities)
- [Set up EM parameters for the France e-reporting](#set-up-em-parameters)
- [Configure sales tax codes for the France e-reporting](#configure-sales-tax-codes)
- [Configure VAT exemption reason codes for the France e-reporting](#configure-vat-exemption-reason-codes)
- [Configure units of measure for the France e-reporting](#configure-units-of-measure)

Optionally, you can [set up France e-reporting to report in multiple VAT registrations legal entity](#set-up-multi-tax) if applicable.

Optionally, if you want to submit reports directly to the tax authorities through EDICOM from Finance, see [Set up and use the EDICOM integration for France e-Reporting](emea-fra-e-reporting-edicom-integration-guide.md).

## <a id="configurations"></a>Import and configure ER configurations

To prepare Finance for France e-reporting, import the following ER configurations.

| ER configuration name | Type | Description |
| --------------------- | ---- | ----------- |
| Invoices Communication Model | Model | A generic data model that standardizes how invoice-related information is structured and processed across electronic reporting scenarios based on Electronic Messages (EM) functionality. |
| e-Reporting Model mapping | Model mapping | A generic model mapping that provides model mapping for e-reporting based on Electronic Messaging (EM). |
| e-Reporting XML (FR) | Format (exporting) | XML format for France e-reporting. |

Import the latest versions of these configurations. The version description usually includes the number of the Microsoft Knowledge Base (KB) article that explains the changes that were introduced in the configuration version.

Use the number of the KB in the [Dynamics 365 Lifecycle Services Issue search portal](https://lcs.dynamics.com/v2) to learn more about the changes introduced.
If the latest configuration version contains references to the objects that aren't available in your Finance version, the import process locks for that configuration version. In this case, import the latest version of the configuration that's available for your Finance version.

> [!NOTE]
> After you import all the ER configurations from the preceding table, set the **Default for model mapping** option to **Yes** for the **e-Reporting Model mapping** configuration.

Learn more about how to import ER configurations in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

> [!NOTE]
> The ER configurations listed earlier cover the base France e-reporting file generation. If you want to submit reports directly to the tax authorities through EDICOM from Finance, you must import an additional set of ER configurations that the direct submission channel relies on. For the full list of the additional ER configurations and their minimum versions, see [Set up and use the EDICOM integration for France e-Reporting](emea-fra-e-reporting-edicom-integration-guide.md#er-configurations).

## <a id="configure-asp"></a>Configure application-specific parameters for the e-Reporting XML (FR) format

To correctly populate the `TransactionReportType > Transaction > CategoryCode` field in the France e-reporting XML output, configure application-specific parameters for the format.

The `CategoryCode` identifies the type of reported transaction according to the French regulatory classification. Derive the correct value based on the transaction characteristics in your system.

Use the **TransCategoryCodeLookup** application-specific parameter to flexibly determine the `CategoryCode` in the report. Configure this lookup to align your business data with the required reporting classifications.

The following values are supported:

- **TLB1**: Transactions – Goods (B2C aggregated or sales of goods)
- **TPS1**: Transactions – Services
- **TNT1**: Transactions – Non-territorial or outside VAT scope
- **TMA1**: Transactions – Mixed or aggregated categories

To configure the **TransCategoryCodeLookup**, follow these steps:

1. In the configuration tree, under the **Invoices Communication Model**, select the **e-Reporting XML (FR)** format.
1. On the **Action** pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, select the latest version of the format that you want to define conditions for.
1. On the **Lookups** FastTab, select the **TransCategoryCodeLookup** lookup, and define the appropriate conditions.
1. On the **Conditions** FastTab, define which combination of **Tax code**, **Sales tax group**, and **Item sales tax group** must correspond to a specific lookup result.
1. Assign the appropriate **TransactionCategoryCode** value for each combination.
1. After you finish setting up conditions, in the **State** field, select **Completed**. Then save the configuration.

## <a id="data-entities"></a>Import a package of data entities that includes a predefined EM setup

Setting up the [Electronic messages](../../general-ledger/electronic-messaging-setup.md) (EM) functionality for France e-reporting involves many steps.
Because the ER configurations use the names of some predefined entities, use a set of predefined values that the package of data entities delivers for the related tables. Some records in the data entities in the package include a link to ER configurations. Before you start to import the data entities package, [import ER configurations](#configurations) into Finance.

To import a package of data entities, follow these steps:

1. In [Lifecycle Services](https://lcs.dynamics.com/v2), go to the **Shared asset library**, and select **Data package** as the asset type. Then find and download to your computer one of the following packages:
   - `FR eReporting EM setup v.3 ID1175852.zip` (or a later version) – the base package. It delivers the **FR e-Reporting** processing that collects data and generates the reporting files. Download this package if you generate the reporting files in Finance and transmit them by your own means.
   - `FR eReporting submission EDICOM EM setup v.1 ID1173584.zip` (or a later version) – the extended package for direct submission to EDICOM. In addition to the base data collection and file generation, it contains the actions that submit the reports directly to the tax authorities through EDICOM and retrieve their processing status. Download this package instead if you want to submit reports to EDICOM directly from Finance.
1. After the data package file is downloaded, in Finance, select the company that you want to work with France e-reporting, and then go to **Workspaces** \> **Data management**.
1. Before you import setup data from the package of data entities, make sure that the data entities in your application are refreshed and synced. In the **Data management** workspace, go to **Framework parameters** \> **Entity settings**, and then select **Refresh entity list**. Wait for confirmation that the refresh is complete. For more information about how to refresh the entity list, see [Entity list refresh](../../../fin-ops-core/dev-itpro/data-entities/data-entities.md#entity-list-refresh).
1. Validate that the source data and target data are correctly mapped. For more information, see [Validate that the source data and target data are mapped correctly](../../../fin-ops-core/fin-ops/data-entities/data-import-export-job.md#validate-that-the-source-data-and-target-data-are-mapped-correctly).
1. Import data from the data package file into the selected company. In the **Data management** workspace, select **Import**, and then, on the **Import** FastTab, in the **Group name** field, select a value.
1. On the **Selected entities** FastTab, select **Add file**.
1. In the **Source data format** field, select **Package**, and then select **Upload and add**.
1. Find and select the data package file that you downloaded in step 1.
1. Wait until the data entities from the file are listed in the grid on the **Selected entities** FastTab, and then select **Close**.
1. On the Action Pane, select **Import** or **Import now** to start the import.

For more information, see [Data management](../../../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages.md?toc=%2ffin-and-ops%2ftoc.json).

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

To enable France e-reporting processing, configure the Electronic Messages (EM) parameters. This setup defines how the system collects data, structures messages, enriches them with extra data, and processes them during report generation.

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

   - **FR-eRep SenderId**: specifies the identifier of the reporting entity.
   - **FR-eRep SenderName**: specifies company name of the issuer of the transmission document.
   - **FR-eRep TypeCode**: specifies the type of report. The following values are available: IN - Initiale (default value), RE - Rectificative.

Enter the appropriate default values based on your reporting requirements. The system uses these values as header-level information in the generated report.

### Set up message item additional fields

Message item additional fields define values at the transaction level (message item level).

To set up message item additional fields, follow these steps:

1. In the same processing setup, go to the **Message item additional fields** section.
1. Set fields for each relevant message item type. The default configuration defines the following values:

   | Message item type | Field name | Default value |
   | ----- | ----- | ----- |
   | **FR-eRep Transactions B2C** | FR-eRep TaxDueDateTypeCode | 3 |
   | **FR-eRep Transactions Invoice** | FR-eRep TaxDueDateTypeCode | 3 |

The **FR e-Reporting** processing supports the following values for **FR-eRep TaxDueDateTypeCode**:

- **3**: Invoice issue date
- **432**: Payment date (VAT on cash receipts)

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

Select **OK** to save the parameters of the selected action.

### Security roles for the electronic message processing

Different groups of users might require access to different electronic message processing. You can limit access to each type of processing, based on security groups that you define in the system.

To limit access to the **FR e-reporting** processing, follow these steps:

1. In Finance, go to **Tax** > **Setup** > **Electronic messages** > **Electronic message processing**.
1. Select the **FR e-reporting** processing.
1. On the **Security roles** FastTab, add the security groups that must work with this processing for testing purposes. If you don't define a security group for the processing, only a system administrator can see the processing on the **Electronic messages** page.

> [!NOTE]
> If you don't define security roles for electronic message processing, only a system admin can see the electronic message processing by going to **Tax** > **Inquiries and reports** > **Electronic messages** > **Electronic messages**.

### Set up executable class settings

Executable class settings define how the system executes processing logic during EM actions.

The following executable classes are involved in **FR e-reporting** processing:

| Executable class | Description | Executable class name | Action type |
|------------------|-------------|-----------------------|-------------|
| **FR-eRep PopulateMessageItems** | Generate message elements for e-reporting | `EReportingEMCreateItemsController_FR` | Populate records |
| **FR-eRep GenerateReportFile** | Generate a message for e-reporting | `EReportingEMExportController_FR` | Electronic reporting export |
| **FR-eRep RegenerateReportFile** | Regenerate a previously generated e-reporting message | `EReportingEMReExportController_FR` | Electronic reporting export |

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
  - **FR‑eRep Transactions Invoice** – Invoice-based transactions subject to reporting
  - **FR‑eRep Transactions B2C** – Aggregated B2C transactions
  - **FR‑eRep Payments Invoice** – Payments related to invoices
  - **FR‑eRep Payments B2C** – Payments related to B2C transactions

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

To set up **FR-eRep PopulateMessageItems** executable class parameters, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** > **Setup** > **Electronic messaging** > **Executable class settings**.
1. Select the **FR-eRep PopulateMessageItems** executable class, and then, on the Action Pane, select **Parameters** and define parameters:

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

1. Use **Records to include** for each report section to configure company-specific filters for data collection. To learn more about how the **FR-eRep Populate Report Data** action collects source data for the French e-reporting report, how it filters each source transaction, and which section of the report the transaction is classified under, see [Data collection and classification for the French e-reporting](emea-fra-e-reporting-details.md). Filters are available for the four sections of France e-report:

   - Payments report type – Invoice
   - Transactions report type – Transaction
   - Transactions report type – Invoice
   - Payments report type – Transaction

1. In the **Populate new message items for French e‑Reporting** report dialog box, select **OK** to save parameters.

When the process runs, it evaluates the filters specified in **Records to include** of the **FR‑eRep PopulateMessageItems** executable class parameters for each report section and retrieves only records that meet the filter conditions. The process assigns these records to the appropriate message item type.

#### Set up **FR-eRep GenerateReportFile** executable class parameters

The **FR‑eRep GenerateReportFile** executable class generates the e‑reporting XML output based on the data collected in electronic message items.
This class performs the report generation step of the process:

- Reads electronic message items created during the data collection step (**FR-eRep Populate Report Data** action).
- Organizes the data according to the reporting structure.
- Produces a structured output file that represents the electronic message in XML format.

During execution, the **FR‑eRep GenerateReportFile** class:

- Retrieves the electronic message items to process.
- Applies the reporting structure and mappings.
- Generates a structured XML output file.

The **FR-eRep GenerateReportFile** class generates one or several electronic messages with attached output files, depending on the data that's being reported. Message items are split into separate electronic messages by the following criteria:

- **Data type** – transaction data and payment data are reported in separate files.
- **Document direction** – outgoing documents (customer sales) and incoming documents (vendor reverse charge) are reported in separate files.
- **Reporting period** – items are split by the reporting period that's derived from the **VAT regime** parameter, the operation date (transaction data) or collection date (payment data) and report generation date. Each file covers a single reporting period.

As a result, each electronic message and generated file represents one reporting document for a single combination of data type, direction, and reporting period. A period that was already submitted and later changed is regenerated as a rectifying (RE) transmission is new message items are found relevant to that period.

Within the **FR e-reporting** processing:

- The generate report action triggers the class.
- It transforms message items into a consumable report format.
- It attaches the output file for further submission.

After this class executes:

- A structured XML output file is generated and attached for the electronic message.
- The file contains all relevant transactions or payment data.

The settings of this class control the execution of logic that drives data collection, processing, and output generation.

1. In Dynamics 365 Finance, go to **Tax** > **Setup** > **Electronic messaging** > **Executable class settings**.
1. Select the **FR-eRep GenerateReportFile** executable class, and then, on the Action Pane, select **Parameters** and define parameters:

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

##### Reporting period and VAT regime

The **FR-eRep GenerateReportFile** executable class groups message items into separate reports by reporting period, in addition to the invoice direction (incoming/outgoing) and data type (transaction/payment). Each generated report (electronic message) covers exactly one reporting period. Items that belong to different periods are never combined into the same report.

The reporting period comes from the declarant's VAT regime together with the date of the operation (for transaction data) or the collection date (for payment data), as required by the French e-reporting regulation. Configure the following parameters.

| Parameter name | Value | Description |
|----------------|----------|----------|
| **VAT regime** | <li>Standard VAT regime - Monthly, </br> <li>Simplified VAT regime - Quarterly, </br> <li>Franchise in base VAT regime | Specifies the VAT regime of the declarant. This value drives the reporting-period granularity that's applied when the file is generated. |

The **VAT regime** value determines the reporting period as follows.

| VAT regime | Transaction data period | Payment data period |
| ------------- | ------------------------ | --------------------- |
| Standard VAT regime - Monthly | Ten-day periods (1–10, 11–20, 21–end of month) | Monthly |
| Simplified VAT regime - Quarterly | Monthly | Monthly |
| Franchise in base VAT regime | Bimonthly civil periods (Jan–Feb, Mar–Apr, May–Jun, Jul–Aug, Sep–Oct, Nov–Dec) | Same bimonthly period |

When you regenerate a report for a reporting period that you already submitted and subsequently changed, you must issue the transmission as a rectifying transmission (RE – Rectificative) rather than a new initial transmission (IN – Initiale). In the generated file, the transmission type is represented by a single report tag whose value the system populates from the **FR-eRep TypeCode** additional field of the electronic message. Accordingly, the **FR-eRep TypeCode** additional field must hold the rectifying value (RE) before the report is regenerated; otherwise, the system populates the report tag with the initial value and regenerates an initial transmission. If you transmit reports outside Dynamics 365 Finance, you are responsible for setting the **FR-eRep TypeCode** additional field to **RE** after a reporting period is successfully submitted. If you use the EDICOM integration provided by Microsoft, this step is performed automatically: the system sets the **FR-eRep TypeCode** additional field to **RE** upon receipt of the authority's confirmation of a successful submission. Together with per-period reporting, the correct transmission type ensures that reports meet the platform's period-consistency requirements and aren't rejected with a period-control error (`REJ_PER`).

After you configure the parameters for the **FR-eRep GenerateReportFile** executable class, select **OK** in the **French e-Reporting generation** report dialog box to save the parameters.

#### Set up **FR-eRep RegenerateReportFile** executable class parameters

The **FR‑eRep RegenerateReportFile** executable class regenerates the e‑reporting XML output for an electronic message that was already generated. It performs the regeneration step of the process in place, on the selected electronic message:

- Links the newly created message items to the selected electronic message.
- Reads the electronic message items and organizes the data according to the reporting structure.
- Regenerates the structured output file, and takes the output file name from the selected ER configuration, in the same way as the other e-reporting generation actions.

During execution, the **FR‑eRep RegenerateReportFile** class:

- Retrieves the electronic message items to process for the selected message.
- Applies the reporting structure and mappings.
- Regenerates the structured XML output file and attaches it to the electronic message.
- Sets the message items that fail regeneration to the **FR-eRep Entry Report Failed** status.

Within the **FR e-reporting** processing:

- The regenerate report action triggers the class.
- It links the new message items that are relevant to the selected message.

After this class executes:

- A regenerated XML output file is attached to the electronic message.
- The file contains all relevant transactions or payment data for the reporting period.
- The e-reporting file is regenerated as initial (IN) or a rectifying (RE) transmission, based on the **FR-eRep TypeCode** additional field of the electronic message.

To set up **FR-eRep RegenerateReportFile** executable class parameters, follow these steps.

1. In Dynamics 365 Finance, go to **Tax** > **Setup** > **Electronic messaging** > **Executable class settings**.
1. Select the **FR‑eRep RegenerateReportFile** executable class, and then, on the Action Pane, select **Parameters** and define parameters:

| Report type | Parameter name | Parameter value |
| --- | --- | --- |
| Transactions report type | Invoice | FR-eRep Transactions Invoice |
| Transactions report type | Transaction | FR-eRep Transactions B2C |
| Transactions report type | Status to Pending | FR-eRep Transaction Entry Pending |
| Transactions report type | Status to Excluded | FR-eRep Transaction Entry Excluded |
| Payments report type | Status to Pending | FR-eRep Payment Entry Pending |
| Payments report type | Status to Excluded | FR-eRep Payment Entry Excluded |

1. In the **French e-Reporting regeneration** report dialog box, select **OK** to save parameters.

## <a id="configure-sales-tax-codes"></a>Configure sales tax codes

The `/TransactionsReport/Invoice/TaxSubTotal/TaxCategory/Code` element identifies the VAT category that applies to the reported tax subtotal. 
Specify the value by using the UNTDID 5305 (Duty, tax, or fee category code) code list, which is the code list referenced by EN 16931 for VAT category classification. 
In Dynamics 365 Finance, this value comes from the sales tax information that you post for the invoice. 
You maintain the mapping between internal sales tax codes and the required UNTDID 5305 values through **External codes** that are associated with the tax setup to ensure that the code reported in the electronic report complies with the target format requirements.

1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax codes**.
1. Select a sales tax code. On the **Action** pane, on the **Sales tax code** tab, in the **Sales tax code** group, select **External codes**.
1. In the **Overview** section, create a line for the selected sales tax code. Enter **UNTDID5305** in the **Code** field.
1. In the **Value** section, enter an external code according to the [Duty or tax or fee category code (Subset of UNCL5305)](https://docs.peppol.eu/poacc/billing/3.0/codelist/UNCL5305/) in the **Value** field.

>[!TIP]
> When you generate the report, the system resolves the value for the `TaxCategory/Code` element from the **External codes** that you set up for the sales tax code, in the following order:
>
>1. It first looks for an external code entry whose **Code** is **UNTDID5305**, and uses the **Value** from the first matching line.
>1. If no **UNTDID5305** entry is found, it uses the **Code** with name of the **Sales tax codes** selected on step 2 with the **Standard code** checkbox selected, and uses the value corresponding to that line instead.
>1. If neither lookup returns a value, the system resolves the value for the `TaxCategory/Code` element based on the tax characteristics of the line: if the tax transaction was posted with an exemption, **E** (Exempt from tax) is reported; otherwise, if the tax rate is 0 (zero), **Z** (Zero rated goods) is reported; otherwise, **S** (Standard rate) is reported.
>   
>To guarantee a compliant value, ensure that every sales tax code that can appear in the report has a **UNTDID5305** external code defined.

## <a id="configure-vat-exemption-reason-codes"></a>Configure VAT exemption reason codes

The `/TransactionsReport/Invoice/TaxSubTotal/TaxCategory/TaxExemptionReasonCode` element identifies the reason why the reported tax subtotal is exempt from VAT. 
Specify the value by using the VATEX (VAT exemption reason code) code list, which is the code list referenced by EN 16931 for VAT exemption reason classification. 
In Dynamics 365 Finance, this value comes from the sales tax information that you post for the invoice. 
You maintain the mapping between internal sales tax codes and the required `VATEX` values through **External codes** that are associated with the tax setup. This setup ensures that the code reported in the electronic report complies with the target format requirements.

1. Go to **Tax** \> **Setup** \> **Sales tax** \> **Sales tax exempt codes**.
1. Select a sales tax exempt code. On the **Action** pane, select **External codes**.
1. In the **Overview** section, create a line for the selected **Sales tax exempt code**. Enter **VATEX** in the **Code** field.
1. In the **Value** section, enter an external code according to the [VAT exemption reason code (VATEX)](https://docs.peppol.eu/poacc/billing/3.0/codelist/vatex/) in the **Value** field, such as *VATEX-FR-298SEXDECIESA*.

>[!TIP]
> When you generate the report, the system resolves the value for the `TaxExemptionReasonCode` element from the **External codes** that you set up for the sales tax code, in the following order:
>
>1. It first looks for an external code entry whose **External code** is **VATEX**, and uses the value from the first matching line.
>1. If no **VATEX** entry is found, the system resolves the value for the `TaxExemptionReasonCode` element from the internal **Sales tax exempt code** value.
>   
>To guarantee a compliant value, ensure that every sales tax exempt code that can appear on a reported exempt invoice has a **VATEX** external code defined.

## <a id="configure-units-of-measure"></a>Configure units of measure

The `/TransactionsReport/Invoice/Line/BilledQuantity/@UnitCode` attribute identifies the unit of measure for the billed quantity reported in the invoice line. 
Specify the value by using the UN/ECE Recommendation 20 (Codes for units of measure used in international trade) code list, which is the code [list referenced by EN 16931 for unit of measure classification](https://docs.peppol.eu/poacc/billing/3.0/codelist/UNECERec20/). 
In Dynamics 365 Finance, you derive this value from the unit of measure that you post for the invoice line. 
Maintain the mapping between internal units of measure and the required UN/ECE Recommendation 20 values through **External codes** that are associated with the unit setup to ensure that the code reported in the electronic report complies with the target format requirements.

1. Go to **Organization administration** > **Setup** > **Units** > **Units**.
1. Select a unit ID, and then select **External codes**.
1. On **External codes**, create a line for the selected unit on the **Overview** FastTab and enter **UNECEREC20** in the **Code** column.
1. On the **Value** FastTab, enter the external code from the [UNECE Recommendation 20 code list](https://docs.peppol.eu/poacc/billing/3.0/codelist/UNECERec20/) in the **Value** field.

>[!TIP]
> When you generate the report, the system resolves the value for the `BilledQuantity/@UnitCode` attribute from the **External codes** that you set up for the unit of measure, in the following order:
>
>1. It first looks for an external code entry whose **Code** is **UNECEREC20**, and uses the **Value** from the first matching line.
>1. If no **UNECEREC20** entry is found, it uses the **Code** with the name of the **Units** selected in step 2 with the **Standard code** checkbox selected, and uses the value corresponding to that line instead.
>1. If neither lookup returns a value, the system resolves the value for the `BilledQuantity/@UnitCode` attribute from default value **EA** (each).
>   
>To guarantee a compliant value, ensure that every unit of measure that can appear in the report has a **UNECEREC20** external code defined.

## <a id="set-up-multi-tax"></a>Set up FR e-Reporting to report in multiple VAT registrations legal entity

The multiple VAT registrations legal entity scenario applies to organizations that operate with multiple VAT registration numbers within the same legal entity.
You support this scenario when you use the [Tax Calculation](../global/global-tax-calcuation-service-overview.md) functionality and enable the [Support multiple VAT registration numbers](../global/emea-multiple-vat-registration-numbers.md) parameter in the **Tax calculation parameters** page.

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
