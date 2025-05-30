---
title: Payments to self-employed persons RF-1321 for Norway
description: Learn how to set up and generate the Payments to self-employed persons RF-1321 for legal entities that have their primary address in Norway.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 03/17/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: Norway
---

# Payments to self-employed persons - RF-1321

[!include [banner](../../includes/banner.md)]

In Norway, all business employers who have made payments to self-employed persons without a fixed place of business in the income year must submit information on this in form RF-1321.

This article includes country/region-specific information about how to set up the **Payments to self-employed persons (RF-1321)** for legal entities that have their primary address in Norway.

## Set up Payments to self-employed persons RF-1321 for Norway

To use the **Payments to self-employed persons RF-1321** report in Dynamics 365 Finance, complete the following setup tasks:

1. [Import Electronic reporting (ER) configurations](#import).
2. [Import a package of data entities that includes a predefined Electronic messaging (EM) setup](#em-setup)
3. [Set up number sequences for Electronic messages functionality](#number-sequences)
4. [Set up document management parameters](#document-management-parameters)
5. [Set up security roles for electronic message processing](#em-security-roles)
6. [Set up ER format for RF-1321](#setup-format)
7. [Save the executable class parameters for Electronic messaging](#executable-class-parameters).
8. [Set up the organization number](#organization-number)

### <a name="import"></a> Import ER configurations

In Finance, import the following ER configurations.

| ER configuration name                                       | Configuration type |
|-------------------------------------------------------------|--------------------|
| Statistics on invoices                                      | Model              |
| Statistics on invoices model mapping                        | Model mapping      |
| Statistics on invoices for RF-1321 model mapping            | Model mapping      |
| RF-1321 Payments to self-employed persons (NO)              | Format (exporting) |
| RF-1321 Payments to self-employed persons (NO) - Per Vendor | Format (exporting) |

Learn more about how to import ER configurations in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

Import the most recent versions of the configurations. The version description usually includes the number of the Microsoft Knowledge Base (KB) article that explains the changes that were introduced in the configuration version.

> [!NOTE]
> After you import all the ER configurations from the preceding table, set the **Default for model mapping** option to **Yes** for the **Statistics on invoices for RF-1321 model mapping** configuration.

### <a id="em-setup"></a>Import a package of data entities that includes a predefined EM setup

The process of setting up the [Electronic messages](../../general-ledger/electronic-messaging-setup.md) (EM) functionality for **Payments to self-employed persons RF-1321** report has many steps. 
Because the names of some predefined entities are used in the ER configurations, it's important that you use a set of predefined values that are delivered in a package of data entities for the related tables. 
Some records in the data entities package include a link to ER configurations. Before you start to import the data entities package, import ER configurations into Finance.

1. In [Lifecycle Services](https://lcs.dynamics.com/v2), go to the **Shared asset library**, and select **Data package** as the asset type. 
2. In the list of data package files, find **NO RF-1321 EM setup v.N** package (where "N" is the version of the package), and download it to your computer. We recommend that you download the latest available version of the package.
3. In Finance, go to **Workspaces** \> **Data management**.
4. Before you import setup data from the data entities package, make sure that the data entities in your application are refreshed and synced. In the **Data management** workspace, go to **Framework parameters** \> **Entity settings**, and then select **Refresh entity list**. Wait for confirmation that the refresh has been completed. For more information about how to refresh the entity list, see [Entity list refresh](../../../fin-ops-core/dev-itpro/data-entities/data-entities.md#entity-list-refresh).
5. Validate that the source data and target data are correctly mapped. For more information, see [Validate that the source data and target data are mapped correctly](../../../fin-ops-core/fin-ops/data-entities/data-import-export-job.md#validate-that-the-source-data-and-target-data-are-mapped-correctly).
6. In the **Data management** workspace, select **Import**, and then, on the **Import** FastTab, set the **Group name** field.
7. On the **Selected entities** FastTab, select **Add file**.
8. In the **Source data format** field, select **Package**, and then select **Upload and add**. 
9. Find and select the **NO RF-1321 EM setup v.N** setup file that you previously downloaded.
10. Wait until the data entities from the file are listed in the grid on the **Selected entities** FastTab, and then select **Close**.
11. Before the data entities are used for the first time to import the data from the package, sync the mapping of the source data and the target data. In the list for the package, select a data entity, and then, on the Action Pane, select **Modify target mapping**. 
12. Above the grid for the package, select **Generate mapping** to create a mapping from scratch. Then save the mapping.
13. Repeat steps 11 and 12 for every data entity in the package before you start the import.
14. You can now import data from the **NO RF-1321 EM setup v.N** setup file into the selected company. On the Action Pane, select **Import** to start the import.

For more information, see [Data management overview](../../../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages.md).

### <a id="number-sequences"></a>Set up number sequences for Electronic messages functionality

To work with the Electronic messages functionality, you must define the related number sequences.

1. Go to **Tax** \> **Setup** \> **General ledger parameters**.
2. On the **Number sequences** tab, set up number sequences for **Message**

### <a id="document-management-parameters"></a>Set up document management parameters

The following file types must be defined on the **File types** tab of the **Document management parameters** page (**Organization administration** \> **Document management** \> **Document management parameters**):

- **XML** – eXtensible Markup Language
- **ZIP** – Compressed file
 
If any of these file types aren't defined on the **File types** tab, add them.

### <a id="em-security-roles"></a>Set up security roles for electronic message processing

Different groups of users might require access to different electronic message processing. You can limit access to each type of processing, based on security groups that are defined in the system.

Follow these steps to define which security roles have access to the **RF-1321** processing.

1. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Electronic message processing**.
2. Select the **RF-1321** processing, and add the security groups that must work with this processing. 

If security roles aren't defined for electronic message processing, only a system admin can view the electronic message processing by going to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**.

### <a id="setup-format"></a>Set up ER format for **RF-1321**

There are two Electronic Reporting (ER) formats supported for **RF-1321**:

- RF-1321 Payments to self-employed persons (NO)
- RF-1321 Payments to self-employed persons (NO) - Per Vendor
  
To specify which ER format will be used in **RF-1321** processing, follow these steps.

1. Go to **Tax** > **Setup** > **Electronic messages** > **Message processing actions**.
2. In the list of message processing actions select **Generate file**.
3. In the **Format mapping** field, select **RF-1321 Payments to self-employed persons (NO)** or **RF-1321 Payments to self-employed persons (NO) - Per Vendor**.

### <a id="executable-class-parameters"></a>Save the executable class parameters for Electronic messaging

The **RF-1321** processing uses the **EMRF1321PayToSelfEmployedVendorController_NO** executable class to initiate data collection for the report data provider and further report generation. 
Before you use this class for the first time, you must save its parameters.

1. Go to **Tax** \> **Setup** \> **Electronic messaging** \> **Executable class settings**.
2. Select the **Generating RF-1321** executable class (which is set to call **EMRF1321PayToSelfEmployedVendorController_NO**), and then, on the Action Pane, select **Parameters**.
3. In the **RF-1321 Payments to self-employed vendors without fixed place of business** dialog box, select **Posting profile** is necessary and click **OK**.

### <a name="organization-number"></a> Set up the organization number

To set up the organization number that is reported in `<organisasjonsnummer>` field, follow these steps.

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
2. Expand **Bank account information** FastTab.
3. In the **Routing number** specify the organization number that is reported in `<organisasjonsnummer>` field.

## Payments to self-employed persons RF-1321 reporting

In Finance, you can generate the RF-1321 using Electronic Messages (EM).

### Create an electronic message for RF-1321 reporting

1. Go to **Tax** > **Inquiries and reports** > **Electronic messages** > **Electronic messages**.
2. Select **RF-1321**, and then, on the **Messages** FastTab, select **New**.
3. In the **Run processing** dialog box, select **OK**.
4. A new electronic message is created. Enter a description, and specify the start and end dates of the period that you want to generate the RF-1321 report for.

### Generate an XML file in RF-1321 format

1. On the **Electronic messages** page, on the **Messages** FastTab, select **Generate report**.
2. In the **Run processing** dialog box, in the **Action** field, select **Generate file**.
3. To run report generation in a batch, enable the **Batch processing** ckeckbox on the **Run in the background** FastTab and specify the batch parameters.
5. In the interactive mode (the **Batch processing** ckeckbox is **Off**), the report parameters are available on the next report dialog. You can select a **Posting profile** or specify other filters using **Records to include**.
6. Select **OK** to start the report generation.
6. When the report is generated, it's attached to the electronic message as a file. To view the file, select the electronic message, and then select the **Attachments** button (paper clip symbol) in the upper-right corner of the page.

The action log is related to the electronic message log information about the user who generated the RF-1321 and performed other actions with the electronic message.
