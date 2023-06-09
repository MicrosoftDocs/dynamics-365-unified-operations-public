---
title: Electronic invoicing for Indonesia
description: This article explains how to configure and process electronic invoice for Indonesia.
author: AdamTrukawka
ms.date: 06/10/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: 
ms.search.region: Indonesia
ms.author: atrukawk
ms.search.validFrom: 
ms.dyn365.ops.version: 10.0.23
ms.search.form: 
---

# Electronic invoicing for Indonesia

[!include [banner](../includes/banner.md)]

This article will help you get started with Electronic invoicing for Indonesia. The article provides the configuration steps that are country/region-dependent in RCS and Finance. You're also guided through the steps that you must follow in Finance to export sales invoices through the service, and to review the processing results and the status of invoices.

## Prerequisites

Before you use the invoicing functionality, the following prerequisites must be met:

- [Configure the Electronic invoicing solution in Dataverse](e-invoicing-power-platform-plug-in.md).

    > [!NOTE]
    > [Microsoft Dynamics 365 Electronic Invoicing connector for Microsoft Dataverse](https://appsource.microsoft.com/product/dynamics-crm/mscrm.electronic-invoicing) isn't currently available from AppSource. If this connector is required to obtain the Dataverse solution for Electronic invoicing, send a request to <DataverseEnvoicing@microsoft.com> to get the Dataverse solution. For general questions about electronic invoicing, go to the dedicated Yammer group, [Electronic invoicing](https://www.yammer.com/dynamicsaxfeedbackprograms/#/threads/inGroup?type=in_group&feedId=9386819584&view=all). If you need further assistance, create a support ticket. For more information about support tickets, see [Get support for finance and operations apps or Lifecycle Services](../../fin-ops-core/dev-itpro/lifecycle-services/lcs-support.md).

- Follow the steps in [Get started with Electronic invoicing](e-invoicing-get-started.md).

### RCS setup

During RCS setup, complete the following tasks.

1. Enable the **Electronic reporting Microsoft Dataverse datasources support** feature in the **Feature management** workspace.
2. Import the Electronic Invoicing feature to process invoice exports and importing vendor invoices.
3. Review the format configurations that are required to generate and export sales invoices.
4. Review or configure the actions in the processing pipeline that support the sales invoice export and import scenarios.
5. Publish the Electronic Invoicing feature for export sales invoices, and import vendor invoices.
6. Import the **Invoices communication Dataverse mapping** configuration.
7. Create a connected application to Dataverse.

#### Import the Electronic Invoicing feature

1. Sign in to your RCS account.
2. In the **Globalization features** workspace, in the **Features** section, select the **Electronic Invoicing** tile.
3. On the **Electronic Invoicing features** page, select **Import** to import, from the Global repository, the **Indonesian electronic invoice (ID)** feature that is published by the Microsoft configuration provider.

    > [!NOTE]
    > If you don't see the feature in the list, select **Synchronize**, and then repeat step 3.

When you import the **Indonesian electronic invoice (ID)** feature from the Global repository, all the feature settings are imported. These settings include the configurations and actions of the processing pipeline.

#### Create a new version of the Indonesian electronic invoice (ID) feature

You can create a new feature version by using your configuration provider.

1. In the **Globalization features** workspace, select the **Electronic Invoicing** tile.
2. On the **Electronic Invoicing features** page, on the **Versions** tab, select **New**.

#### Update the configuration version

1. In the **Globalization features** workspace, select the **Electronic Invoicing** tile.
2. On the **Electronic Invoicing features** page, on the **Configurations** tab, select **Add** or **Delete** to manage the configuration versions.

When you create a new version, all configurations are inherited from the imported version of the Electronic Invoicing feature. The following configurations are required to process invoices:

- Invoices issued (ID)
- eInvoice import (ID)

In the list, select a configuration version, and then select **Edit** or **View** to open the **Format designer** page, where you can edit or view the configuration.

You can review the configuration and customize it as you require. Use the **Format designer** page to edit and view the Electronic reporting (ER) format file configurations. For more information, see [Create electronic document configurations](../../fin-ops-core/dev-itpro/analytics/electronic-reporting-configuration.md).

#### Import the Invoices communication Dataverse mapping configuration

1. Sign in to your RCS account.
1. On the RCS home page, and select **Electronic reporting**.
2. Select **Repositories**, and then find and import the **Invoices communication Dataverse mapping** configuration.

#### Create a connected application for Dataverse

1. Sign in to your RCS account.
2. On the RCS home page, select **Electronic reporting**.
3. On the **Related links** FastTab, select **Connected application**.
4. Select **New** to create a connected application, and set the following fields:

    - **Name** – Enter the name of the Dataverse instance. For example, enter **UAT Dataverse**.
    - **Type** – Select **Dataverse**.
    - **Application** – Enter the Dataverse endpoint URL. You can find this URL on the customers Microsoft Dynamics Lifecycle Services (LCS) application page.
    - **Tenant** – Enter the customer tenant.
    - **Custom URL** – Enter the Dataverse endpoint URL followed by **api/data/v9.1/**. For example, enter `https://operations-dgxtest-uat.crm.dynamics.com/api/data/v9.1/`.

5. Select **Save**.
6. On the Action Pane, select **Check connection** to test the connection with the environment. Then close the page.

### Configure the application-specific parameters

> [!NOTE]
> When you set up application-specific parameters, check the connection on the **Connected applications** page. Go to the RCS home page, and select **Electronic reporting**. At the bottom of the page, select **Connected application** \> **Check connection**.

To enable the system to determine which sales tax code in Finance corresponds to the tax code for luxury goods (PPnBM) when invoices are exported, follow these steps to set the application-specific parameters for the luxury sales tax.

1. In the **Lookups** grid, select the row for **TaxTypeLookup**.
2. In the **Conditions** grid, on the first line, set the **Lookup result** field to **PPnBM** and the **Sales tax code (TaxCode)** field to the sales tax code that is used for luxury tax in Finance.

    > [!NOTE]
    > You can set up several sales tax codes for PPnBM and have several lines for them in the **Conditions** grid.

3. On the last line, set the **Lookup result** field to **Other** and the **Sales tax code (TaxCode)** field to **\*Not blank\***. These settings specify that all other sales tax codes should not be considered luxury tax by the system.

    ![Setting application-specific parameters for sales tax codes.](media/apac-idn-aplication-specific-parameters-tax-code.png)

To enable the system to determine which sales tax group in Finance corresponds to VAT-free reasons (transaction code 07, reasons 1 through 8) or VAT-exempt reasons (transaction code 08, reasons 1 through 5) when invoices are exported, follow these steps to set the application specific parameters for those reasons.

1. In the **Lookups** grid, select the row for **VATFreeInfoLookup**.
2. In the **Conditions** grid, on the first line, set the **Lookup result** field from **1** through **8** for transaction code **07** and from **1** through **5** for transaction code **08**.
3. Set the **Tax group (TaxGroup)** field to the sales group that is used for exemption operations in Finance.
4. On the last line, set the **Lookup result** field to **Other** and the **Tax group (TaxGroup)** field to **\*Not blank\***. These settings specify that all other sales tax groups should not be considered exemption groups by the system.

    ![Setting application-specific parameters for transaction codes.](media/apac-idn-aplication-specific-parameters-transaction-codes-07-08.png)

### Manage the Electronic Invoicing feature setup

1. In the **Globalization features** workspace, select the **Electronic Invoicing** tile.
2. On the **Electronic Invoicing features** page, on the **Setups** tab, select **Add**, **Delete**, or **Edit** to manage the Electronic Invoicing feature setup.

#### Configure the Sales invoice feature setup

To generate the comma-separated values (CSV) file for a sales invoice, you must set up the Sales invoice feature.

1. On the **Electronic Invoicing features** page, on the **Setups** tab, in the **Feature setup** column, select **Invoice issued**.
2. Select **Edit** to review or configure the actions, applicability rules, and variables.

    ![Configuring the Sales invoice feature setup.](media/apac-idn-rcs-setups.png)

#### Configure the Vendor invoice feature setup

To configure the Vendor invoice feature setup, you should already have created a draft version of the feature that you will work with for this procedure.

1. On the **Electronic Invoicing features** page, on the **Setups** tab, in the **Feature setup** column, select the **Import from share point** record.
2. Select **Edit** to review or configure the actions, applicability rules, and variables.
3. On the **Feature version setup** page, on the **Data channel** tab, in the **Parameters** list, in the **Data channel** record, in the **Value** field, enter **\$Context Channel** from the derived configuration.
4. Set the other parameters for SharePoint.
5. In the **Custom file name** record, set up a filter for the file names of vendor invoices.
6. On the **Applicability rules** tab, in the record that has a **Channel** field, in the **Value** field, enter **\$Context Channel** from the derived configuration.
7. On the **Variables** tab, create or validate the record.

    ![Configuring the Vendor invoice feature setup.](media/apac-idn-feature-version-setup-variables.png)

### Assign the draft version to an e-Invoicing environment

1. On the **Electronic Invoicing features** page, on the **Environments** tab, select **Enable**.
2. In the **Environment** field, select the environment.
3. In the **Effective from** field, select the date when the environment should become effective.
4. Select **Enable**.

### Change the version status

1. On the **Electronic Invoicing features** page, on the **Versions** tab, select the version of the Electronic Invoicing feature that has a status of **Draft**.
2. Select **Change status** \> **Complete**.
3. Select **Change status** \> **Publish**.

## Set up Electronic invoicing integration in Finance

### Import the ER data model, ER data model mapping, and context configurations for invoices

1. Sign in to your Finance environment.
2. In the **Electronic reporting** workspace, in the **Configuration providers** section, select the **Microsoft** tile. Make sure that this configuration provider is set to **Active**. For information about how to mark a provider as active, see [Create configuration providers and mark them as active](../../fin-ops-core/dev-itpro/analytics/tasks/er-configuration-provider-mark-it-active-2016-11.md).
3. Select **Repositories**.
4. Select **Global resource** \> **Open**.
5. Import the following configurations:

    - Customer invoice context model
    - Invoice model
    - Vendor invoice Mapping to destination
    - Vendor invoice import (ID), Vendor invoice import XML (ID)

### Turn on the feature for processing Indonesian electronic invoices

1. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
2. On the **Features** tab, in the row for the **Indonesian electronic invoice** feature, select the **Enable** checkbox.

### Set up the processing for Indonesian electronic sales invoices

1. Go to **Organization administration** \> **Setup**\ > **Electronic document parameters**.
2. On the **Electronic document** tab, select **Add**, and enter the customer invoice journal.
3. Optional: Select **Add** again, and enter the project invoice journal.
4. In the **Batch submission ID** section, add a number sequence. The selected number sequence should be continuous. This number sequence is used to number the invoice batches when the system exports them.
5. Select **Save**.

    ![Setting up the processing for electronic sales invoices.](media/apac-idn-rcs-electronic-document-parameters.png)

### Set up the processing for Indonesian electronic vendor invoices

1. In the **Electronic reporting** workspace, select **Reporting configurations**.
2. Select **Customer invoice context model**, and then select **Create configuration**.
3. Select **Derive from Name: Customer invoice context model, Microsoft** to create a derived configuration.
4. In the **Draft** version, select **Designer**.
5. In the **Data model** tree, select **Map model to datasource**.
6. In the **Definitions** tree, select **DataChannel**, and then select **Designer**.
7. In the **Data sources** tree, expand the **\$Context\_Channel** container.
8. In the **Value** field, select **Edit**, and enter the name of the data channel. The name should have a maximum of 10 characters. It's the name of the channel that is given in the configuration of the data channel for the Electronic Invoicing feature in RCS.
9. Select **Save**, and close the page.
10. Close the page.
11. Select the derived configuration that you just created from **Customer invoice context model**, and then, on the **Versions** FastTab, select **Change Status** \> **Completed**.

> [!NOTE] 
> You can create several derived configurations that have different **\$Context Channel** values. In this way, you can import vendor invoices from different sources. For example, you might want to import vendor invoices for different legal entities.

1. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
2. On the **External channels** tab, set up the import of vendor invoices.
3. On the **Channels** FastTab, select **Add**.
4. In the **Channel** field, enter **\$Context Channel**.
5. Enter a value in the **Description** and **Company** fields.
6. In the **Document context** field, select the new configuration that you derived from **Customer invoice context model**. The mapping description should be **Data channel context**.
7. On the **Import sources** FastTab, select **Add**.
8. In the **Name** field, enter the value from the **Variables** tab on the **Feature version setup** page.
9. Enter a value in the **Description** field.
10. In **Data entity name** field, select **Vendor Invoice register header** if you want to import vendor invoices into the Invoice register. If you want to import them into pending vendor invoices, select **Vendor invoice journal**. You can have only one import source, **Vendor Invoice register header** or **Vendor invoice journal**.
11. In the **Model mapping** field, select **Vendor invoice import (ID)** to import the invoice header into the Invoice register or pending vendor invoices. Select **Vendor invoice import XML (ID)** to import the invoice header and lines into pending vendor invoices.

    > [!NOTE]
    > Before you import vendor invoices from XML files, you must set up an external item description for vendors. The system can then match an item name in the XML file with line items in sales orders.

    ![Setting up external channels.](media/apac-idn-import-setup-external-channels.png)

If you must import vendor invoices into, for example, a different legal entity, create a new channel record that has the new document context.

## Process electronic invoices in Finance

When issued invoices or imported vendor invoices are processed through Electronic invoicing, you can complete the following tasks:

- Submit or export issued invoices, and import vendor invoices.
- View the electronic document submission and receipt logs.

### Submit or export issued invoices

1. Go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Submit electronic documents**.
2. Set the **Submit document batch** option to **Yes** to export invoices in batch. Otherwise, each invoice is exported separately. The first time that you submit a document, always set the **Resubmit documents** option to **No**. If you must resubmit a document through the service, set this option to **Yes**.
3. On the **Records to include** FastTab, select **Filter** to open the **Inquiry** dialog box, where you can build a query to select documents for export.
4. Go to **System administration** \> **Setup** \> **Business events** \> **Business events parameters**, and then select **Business events batch job**. If you set up the Business event batch processor, this job can be run in batch mode.

### View submission logs

You can view the submission logs for all exported documents.

1. Go to **Organization administration** \> **Periodic** \> **Electronic documents**\ > **Electronic document submission log**.
2. Select **Update status**. An invoice batch can have the following statuses:

    - Scheduled
    - Completed
    - Failed

3. On the Action Pane, select **Inquiries** \> **Submission details** to view the details of the submission execution logs. The information in the logs is divided among three FastTabs:

    - **Processing actions** – This FastTab shows the execution log for the actions that are configured in the feature version that was set up in RCS. The **Status** column shows whether the action was successfully run.
    - **Action files** – This FastTab shows the intermediate files that were generated during execution of the actions. Select **View** to download and view the file.
    - **Processing action log** – This FastTab shows the results of the submission of electronic invoices.

4. On the Action Pane, select **Inquiries** \> **Batch submission invoices** to view invoices that were submitted in one batch.

### Import vendor invoices and view the electronic document receipt log

1. Go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Receive electronic documents**.

    > [!NOTE]
    > For the first receipt of any document, always set the **Re-import documents** option to **No**. If you must re-import a document through the service, set this option to **Yes**. This job can be run in batch mode.

2. Go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Electronic document receipt log**.
3. On the Action Pane, select **Inquiries** \> **Submission details** to view the details of the submission execution logs.

## Privacy notice

Enabling the **Indonesian electronic invoice** feature might require that limited data be sent. This data includes the organization's tax registration ID. An administrator can enable or turn off the **Indonesian electronic invoice** feature by going to **Organization administration** \> **Setup** \> **Electronic document parameters**, and then, on the **Features** tab, selecting the rows that contain the **Indonesian electronic invoice** feature and making the appropriate selection. Data that is imported from these external systems into this Dynamics 365 online service are subject to our [privacy statement](https://go.microsoft.com/fwlink/?LinkId=512132). For more information, see the "Privacy notice" section in country/region-specific feature documentation.

## Additional resources

- [Electronic invoicing overview](e-invoicing-service-overview.md)
- [Get started with Electronic invoicing](e-invoicing-get-started.md)
- [Set up Electronic invoicing](e-invoicing-setup.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
