---
title: Make payments to self-employed persons - RF-1321 for Norway
description: Learn how to set up and generate payments to self-employed persons using the RF-1321 report for legal entities in Norway with Microsoft Dynamics 365 Finance.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 06/12/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: Norway
---

# Make payments to self-employed persons - RF-1321 for Norway

[!include [banner](../../includes/banner.md)]

This article explains how to set up and generate payments to self-employed persons using the RF-1321 report for legal entities in Norway with Microsoft Dynamics 365 Finance.

In Norway, all business employers who made payments to self-employed persons who did not have a fixed place of business during the income year must submit information about those payments in form RF-1321.

## Set up the Payments to self-employed persons RF-1321 report for Norway

To use the **Payments to self-employed persons RF-1321** report in Microsoft Dynamics 365 Finance, complete the following setup tasks:

1. [Import Electronic reporting (ER) configurations](#import).
1. [Import a package of data entities that includes a predefined Electronic messaging (EM) setup](#em-setup).
1. [Set up number sequences for the Electronic messages functionality](#number-sequences).
1. [Set up document management parameters](#document-management-parameters).
1. [Set up security roles for electronic message processing](#em-security-roles).
1. [Set up the ER format for the RF-1321 processing](#setup-format).
1. [Save the executable class parameters for EM](#executable-class-parameters).
1. [Set up the organization number](#organization-number).

### <a name="import"></a>Import ER configurations

In Finance, import the following ER configurations.

| ER configuration name                                       | Configuration type |
|-------------------------------------------------------------|--------------------|
| Statistics on invoices                                      | Model              |
| Statistics on invoices model mapping                        | Model mapping      |
| Statistics on invoices for RF-1321 model mapping            | Model mapping      |
| RF-1321 Payments to self-employed persons (NO)              | Format (exporting) |
| RF-1321 Payments to self-employed persons (NO) - Per Vendor | Format (exporting) |

Learn more about how to import ER configurations in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

Import the most recent versions of the configurations. The version description usually includes the number of the Knowledge Base (KB) article that explains the changes that were introduced in the configuration version.

> [!NOTE]
> After you import all the ER configurations from the preceding table, set the **Default for model mapping** option to **Yes** for the **Statistics on invoices for RF-1321 model mapping** configuration.

### <a id="em-setup"></a>Import a package of data entities that includes a predefined EM setup

The process of setting up the [Electronic messages](../../general-ledger/electronic-messaging-setup.md) functionality for the **Payments to self-employed persons RF-1321** report has many steps.

Because the names of some predefined entities are used in the ER configurations, it's important that you use a set of predefined values that are delivered in a package of data entities for the related tables.

Some records in the data entities package include a link to ER configurations. Before you start to import the data entities package, import ER configurations into Finance.

To import ER configurations into Finance, follow these steps.

1. In [Dynamics 365 Lifecycle Services](https://lcs.dynamics.com/v2), go to the **Shared asset library**, and select **Data package** as the asset type.
1. In the list of data package files, find the package that is named **NO RF-1321 EM setup v.*N***, where *N* is the version number of the package. Download the package to your computer. We recommend that you download the latest available version of the package.
1. In Finance, go to **Workspaces** \> **Data management**.
1. Before you import setup data from the data entities package, make sure that the data entities in your application are refreshed and synced. In the **Data management** workspace, go to **Framework parameters** \> **Entity settings**, and then select **Refresh entity list**. Wait for confirmation that the refresh was completed. Learn more about how to refresh the entity list in [Entity list refresh](../../../fin-ops-core/dev-itpro/data-entities/data-entities.md#entity-list-refresh).
1. Validate that the source data and target data are correctly mapped. Learn more in [Validate that the source data and target data are mapped correctly](../../../fin-ops-core/fin-ops/data-entities/data-import-export-job.md#validate-that-the-source-data-and-target-data-are-mapped-correctly).
1. In the **Data management** workspace, select **Import**.
1. On the **Import** FastTab, set the **Group name** field.
1. On the **Selected entities** FastTab, select **Add file**.
1. In the **Source data format** field, select **Package**.
1. Select **Upload and add**.
1. Find and select the **NO RF-1321 EM setup v.*N*** package file that you downloaded.
1. Wait until the data entities from the file are listed in the grid on the **Selected entities** FastTab, and then select **Close**.
1. Before the data entities are used for the first time to import the data from the package, sync the mapping of the source data and the target data. For each data entity in the package, follow these steps:

    1. In the list for the package, select a data entity, and then, on the Action Pane, select **Modify target mapping**.
    1. Above the grid for the package, select **Generate mapping** to create a mapping from scratch.
    1. Save the mapping.

1. You can now import data from the **NO RF-1321 EM setup v.*N*** setup file into the selected company. To start the import, select **Import** on the Action Pane.

Learn more in [Data management overview](../../../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages.md).

### <a id="number-sequences"></a>Set up number sequences for the electronic messages functionality

To work with the Electronic messages functionality, you must define the related number sequences.

To set up number sequences, follow these steps.

1. In Dynamics 365 Finance, go to **Tax** \> **Setup** \> **General ledger parameters**.
1. On the **Number sequences** tab, set up number sequences for **Message**.

### <a id="document-management-parameters"></a>Set up document management parameters

The following file types must be defined on the **File types** tab of the **Document management parameters** page (**Organization administration** \> **Document management** \> **Document management parameters**):

- **XML** – eXtensible Markup Language
- **ZIP** – Compressed file

If any of these file types aren't defined on the **File types** tab, add them.

### <a id="em-security-roles"></a>Set up security roles for electronic message processing

Different groups of users might require access to different electronic message processing. You can limit access to each type of processing, based on security groups that are defined in the system.

To define which security roles have access to the **RF-1321** processing, follow these steps.

1. In Dynamics 365 Finance, go to **Tax** \> **Setup** \> **Electronic messages** \> **Electronic message processing**.
1. Select the **RF-1321** processing, and add the security groups that must work with this processing.

If security roles aren't defined for electronic message processing, only a system admin can view the electronic message processing by going to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**.

### <a id="setup-format"></a>Set up the ER format for the RF-1321 processing

Two ER formats are supported for the **RF-1321** processing:

- RF-1321 Payments to self-employed persons (NO)
- RF-1321 Payments to self-employed persons (NO) - Per Vendor

To specify which ER format is used in the **RF-1321** processing, follow these steps.

1. In Dynamics 365 Finance, go to **Tax** \> **Setup** \> **Electronic messages** >\ **Message processing actions**.
1. In the list of message processing actions, select **Generate file**.
1. In the **Format mapping** field, select **RF-1321 Payments to self-employed persons (NO)** or **RF-1321 Payments to self-employed persons (NO) - Per Vendor**.

### <a id="executable-class-parameters"></a>Save the executable class parameters for Electronic messaging

The **RF-1321** processing uses the **EMRF1321PayToSelfEmployedVendorController_NO** executable class to initiate data collection for the report data provider and further report generation. Before you use this class for the first time, you must save its parameters.

1. In Dynamics 365 Finance, go to **Tax** \> **Setup** \> **Electronic messaging** \> **Executable class settings**.
1. Select the **Generating RF-1321** executable class, and then, on the Action Pane, select **Parameters**. (The **Generating RF-1321** executable class is set to call **EMRF1321PayToSelfEmployedVendorController_NO**.)
1. In the **RF-1321 Payments to self-employed vendors without fixed place of business** dialog, select a posting profile as required, and then select **OK**.

### <a name="organization-number"></a>Set up the organization number

To set up the organization number that is reported in the `<organisasjonsnummer>` field, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration** \> **Organizations** \> **Legal entities**.
1. On the **Bank account information** FastTab, in the **Routing number** field, specify the organization number that is reported in the `<organisasjonsnummer>` field.

## Payments to self-employed persons RF-1321 reporting

In Finance, you can use the Electronic messages functionality to generate the **Payments to self-employed persons RF-1321** report.

### Create an electronic message for RF-1321 reporting

1. In Dynamics 365 Finance, go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**.
1. Select **RF-1321**, and then, on the **Messages** FastTab, select **New**.
1. In the **Run processing** dialog, select **OK**.
1. A new electronic message is created. Enter a description, and specify the start and end dates of the period that you want to generate the report for.

### Generate an XML file in RF-1321 format

1. On the **Electronic messages** page, on the **Messages** FastTab, select **Generate report**.
1. In the **Run processing** dialog, in the **Action** field, select **Generate file**.
1. On the **Run in the background** FastTab, use the **Batch processing** checkbox to specify the mode that report generation runs in:

    - To run report generation in a batch, select the **Batch processing** checkbox. Then specify the batch parameters.
    - To run report generation in interactive mode, clear the **Batch processing** checkbox. The report parameters are available in the next report dialog. You can select a posting profile or specify other filters on the **Records to include** FastTab.

1. Select **OK** to generate the report.
1. When the report is generated, it's attached to the electronic message as a file. To view the file, select the electronic message, and then select the **Attachments** button (paper clip symbol) in the upper-right corner of the page.

The action log is related to the electronic message log information about the user who generated the **Payments to self-employed persons RF-1321** report and performed other actions with the electronic message.
