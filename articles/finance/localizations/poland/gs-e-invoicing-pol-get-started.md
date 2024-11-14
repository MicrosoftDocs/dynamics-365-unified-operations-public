---
title: Electronic invoicing for Poland
description: The article provides information that will help you get started with Electronic invoicing for Poland.
author: ikondratenko
ms.date: 05/22/2024
ms.topic: how-to
ms.collection:
  - bap-ai-copilot
audience: Application User
ms.reviewer: johnmichalak
ms.search.region: Poland
ms.author: ikondratenko
ms.search.validFrom: 2024-05-01
ms.dyn365.ops.version: AX 10.0.39
---

# Electronic invoicing for Poland

[!include [banner](../../includes/banner.md)]

This article provides information that will help you get started with Electronic invoicing for Poland. It guides you through the configuration steps that are country/region-dependent in Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management. 

After you configure electronic invoicing, you can generate, digitally sign, and submit the XML files of electronic invoices according to the current regulatory requirements in Poland.

![Diagram of the electronic invoicing workflow in Poland.](apac-mys-e-invoice-workflow.jpg)

> [!NOTE]
> The electronic invoicing approach that this article describes is implemented by using an invoicing service that's applicable only to cloud deployments of Finance or Supply Chain Management.

## Prerequisites

Before you begin the procedures in this article, complete the following prerequisites:

- The primary address of the legal entity must be in Poland.
- The legal entity must be registered as a taxpayer in Poland and must have a valid tax identification number (*Numer identyfikacji podatkowej* \[NIP\]).
- Sign in to the Polish National system for electronic invoicing ([Krajowy System e-Faktur \[KSeF\]](https://ksef.mf.gov.pl/web/)) via a trusted profile, qualified signature, or qualified seal. Obtain a non-expiring **token** that the Invoicing Service can use to securely communicate with KSeF.
- Obtain the **public key** (in PEM format) from the appropriate [KSeF environment](https://ksef.mf.gov.pl/). The environment can be of the test, pre-production, or production type.
- Become familiar with electronic invoicing as it's described in [Electronic invoicing overview](../global/gs-e-invoicing-service-overview.md).
- Do the common part of electronic invoicing service configuration as described in [Set up electronic invoicing](../global/gs-e-invoicing-set-up-overview.md).

## Create the Azure Key Vault configuration

Create an Azure key vault to store the required secrets that are issued for your company. For more information, see [Configure Azure resources for Electronic invoicing](../global/gs-e-invoicing-set-up-azure-resources.md).

Add the following required elements in the key vault:

- The secret for the obtained **token**.
- The secret for the **client ID**, which must equal the taxpayer's tax identification number (NIP).
- The secret for the obtained **public key**.

    > [!NOTE]
    > The value of the public key must be wrapped in the following commands.
    >
    > `----BEGIN PUBLIC KEY----`  
    > &hellip;  
    > `----END PUBLIC KEY----`

## Configure electronic invoicing Key Vault parameters

To configure electronic invoicing Key Vault parameters, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
1. On the **Electronic invoicing** tab, in the **Key Vault settings** section, in the **Key Vault** field, select the reference to the key vault that you created in the previous section of this article.
1. In the **SAS token secret** field, select the name of the storage account secret URL that must be used to authenticate access to the storage account.
1. Select **Key Vault parameters**.
1. On the **Key Vault parameters** page, in the **Certificates** section, select **Add** to create new elements of the appropriate type for each secret that is described in the previous section.

    - <a id="Tok"></a>The **token** element of the **Secret** type.
    - <a id="ClID"></a>The **Client ID** element of the **Secret** type.
    - <a id="PK"></a>The **Public key** element of the **Secret** type.

    > [!NOTE]
    > The values in the **Name** column should match the names of the secrets that are described in the previous section.

## Configure the electronic invoicing feature

---------Feature parameters--------------

Some of the parameters from the **Polish electronic invoice (PL)** electronic invoicing feature are published with default values. Before you deploy the electronic invoicing feature to the service, review the default values, and update them as required, so that they better reflect your business operations.

To review and update the **Polish electronic invoice (PL)** electronic invoicing feature configuration, follow these steps.

1. Go to **Globalization Studio**, and select the **Electronic invoicing** tile. Then import the latest version of the **Polish electronic invoice (PL)** Globalization feature as described in [Import features from the repository](../global/gs-e-invoicing-import-feature-global-repository.md).
1. Create a copy of the imported Globalization feature, and select your configuration provider for it, as described in [Create a Globalization feature](../global/gs-e-invoicing-create-new-globalization-feature.md).
1. On the **Versions** tab, verify that the **Draft** version is selected.
1. On the **Setups** tab, in the grid, select the **Submit customer invoice derived** feature setup. Then select **Edit**.
1. On the **Processing pipeline** tab, in the **Processing pipeline** section, select the **Submit invoice to KSeF** action.
1. In the **Parameters** section, select the **Client ID** parameter. Then, in the **Value** field, select the name of the [client ID](#ClID) that you previously created.
1. Select the **Public key** parameter, and then, in the **Value** field, select the name of the [public key](#PK) that you previously created.
1. Select the **Token** parameter, and then, in the **Value** field, select the name of the [token](#Tok) that you previously created.
1. Select the **Ksef environment** parameter, and then, in the **Value** field, select the type of the environment, depending on the implementation stage: *Test*, *Demo*, or *Prod*.

    :::image type="content" source="e-inv-pol-feature-setup.jpg" alt-text="Screenshot of the setup on the Processing pipeline tab of the Feature version setup page.":::

1. Repeat steps 5 through 9 for the **Get invoice status from KSeF** action.
1. Select **Save**, and close the page.
1. Repeat steps 4 through 11 for the **Submit project invoice derived** and **Submit advance invoice derived** feature setups, as required.
1. The copy of the feature is always created as a **Draft** version. Regardless of whether you made changes, complete and deploy the feature as described in [Complete and deploy a Globalization feature](../global/gs-e-invoicing-complete-publish-deploy-globalization-feature.md).

    > [!NOTE]
    > Before you complete and deploy the feature, check whether the import of [incoming electronic invoices](#Import) must be configured.

## Configure electronic document parameters

Some additional parameters must be configured directly in Finance.

To configure electronic document parameters, follow these steps.

1. Make sure that the country/region-specific Electronic reporting (ER) configurations that are required for Poland are imported. For more information, see [Set up electronic invoicing parameters](../global/gs-e-invoicing-set-up-parameters.md#set-up-electronic-document-parameters).
1. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
1. In the **Electronic document** section, add records for the **Customer Invoice journal**, **Project invoice**, and **Advance invoice** table names.
1. For each table name, set the **Document context** and **Electronic document model mapping** fields in accordance with step 1.

    :::image type="content" source="e-inv-pol-doc-parameters.jpg" alt-text="Screenshot of the setup on the Electronic document tab of the Electronic document parameters page."::: 

1. For the **Customer Invoice journal** table name, select **Response types**.
1. Select **New** to create a response type, and enter the following values:

    - In the **Response type** field, enter **ResponseData** (the default value).
    - In the **Submission status** field, select **Pending**.
    - In the **Model mapping** field, select **KSeF response data import format (PL)**.

    :::image type="content" source="e-inv-pol-response-type.jpg" alt-text="Screenshot of the setup of the new response type on the Electronic document tab of the Electronic document parameters page.":::

    > [!NOTE]
    > **ResponseData** is the default name of the response type. If you must change it, make sure that the new name matches the name that was defined for the related variable of the **To client** type in the corresponding feature setups. To validate the variable's value, go to **Globalization Studio**, and select the **Electronic invoicing** tile. On the **Electronic invoicing features** page, verify that the **Polish electronic invoice (PL)** electronic invoicing feature is selected. On the **Setups** tab, in the grid, select the **Submit customer invoice derived** feature setup. Then select **Edit** or **View**, depending on the status of the feature version.

1. Repeat steps 5 and 6 for the **Project invoice** and **Advance invoice** table names.
1. Save your changes, and close the page.

## Configure Finance business data

### Prerequisites

The primary address of the legal entity must be in Poland.

### Configure legal entity data

To configure the legal entity data, complete the steps in each of the following sections.

#### Enter a legal entity's address

To enter a legal entity's address, follow these steps.

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
1. Select a legal entity, and then, on the **Addresses** FastTab, add a valid primary address for the legal entity.

    > [!NOTE]
    > Make sure that the following mandatory address elements are defined: country/region code, ZIP/postal code, city, and building number.

#### Enter a legal entity's tax registration number

To enter a legal entity's tax registration number, follow these steps.

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
1. Select a legal entity, and then, on the **Tax registration** FastTab, in the **Tax registration number** field, enter a valid tax registration number for the legal entity. This number will be used as the seller's tax identification number (NIP).

### Configure customer data

To configure the customer data, complete the steps in each of the following sections.

#### Enter a customer's address

To enter a customer's address, follow these steps.

1. Go to **Accounts receivable** \> **Customers** \> **All customers**.
1. Select a customer, and then, on the **Addresses** FastTab, add a valid address for the customer.

    > [!NOTE]
    > - For addresses in Poland, make sure that the following mandatory elements are defined: country/region code, ZIP/postal code, city, and building number.
    > - For foreign addresses, make sure that at least the following mandatory elements are defined: country/region code and city.

#### Enter a customer's tax registration number

To enter a customer's tax registration number, follow these steps.

1. Go to **Accounts receivable** \> **Customers** \> **All customers**.
1. Select a customer, and then, on the **Invoice and delivery** FastTab, in the **Tax exempt number** field, enter a valid tax registration number for the customer. This number will be used as the buyer's tax identification number (NIP).

### Configure additional data

You can add any additional arbitrary data to invoices. This data will be put in a special section of electronic invoices that is named *DodatkowyOpis*.

#### Configure electronic document properties

To configure electronic document properties, follow these steps.

1. Go to **Accounts receivable** \> **Setup** \> **Electronic document property types**.
1. Select **New** to add a property type.
1. In the **Type** field, enter the value to use as an additional data key (`Klucz`) in the resulting XML file of an electronic invoice.
1. Select **Applicability** to add an applicable table.
1. On the **Electronic document property type applicability setup** page, in the **Table name** field, select **Customer invoice journal** and **Project invoice**.
1. Add as many additional document properties as you require.
1. Save your changes, and return to the **Electronic document property types** page.

#### Enter additional invoice data

To enter additional invoice data, follow these steps.

1. Go to **Accounts payable** \> **Inquiries and reports** \> **Invoice** \> **Invoice journal**.
1. Select an invoice in the list, and then, on the Action Pane, on the **Invoice** tab, in the **Properties** group, select **Electronic document properties**.
1. Enter a required value. This value will be used in the `Wartosc` field in the resulting XML file of an electronic invoice.

> [!NOTE]
> You can enter additional data for project invoices in a similar way at **Project management and accounting** \> **Project invoices** \> **Project invoice**.

## Issue electronic invoices

After you complete all the required configuration steps, you can generate and submit electronic invoices for posted invoices by going to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Submit electronic documents**. For more information about how to generate and submit electronic invoices, see [Submit electronic documents](../global/e-invoicing-submit-electronic-documents.md).

You can inquire about the results of a submission by going to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Electronic document submission log** and selecting the required document type. For more information about the submission log, see [Work with Electronic document submission log](../global/e-invoicing-submission-log.md).

## Receive incoming electronic invoices

<a id="Import"></a>Complete the following configuration steps for the same version of the **Polish electronic invoice (PL)** electronic invoicing feature that is used for outgoing invoice submission.

1. Go to **Globalization Studio**, and select the **Electronic invoicing** tile. Then select the same version of the **Polish electronic invoice (PL)** electronic invoicing feature that was configured for outgoing invoices submission.
1. On the **Setups** tab, in the grid, select **Import vendor invoice derived**. Then select **Edit**.
1. On the **Import channel** tab, in the **Parameters** section, select the **Data channel** parameter. Then, in the **Value** field, define the [name of the data channel](#ImpChn). Alternatively, leave the default value unchanged. Whatever you do, make a note of the value, because you will use it in later configuration steps.
1. Select the **Client ID** parameter, and then, in the **Value** field, select the name of the [client ID](#ClID) that you previously created.
1. Select the **Public key** parameter, and then, in the **Value** field, select the name of the [public key](#PK) that you previously created.
1. Select the **Token** parameter, and then, in the **Value** field, select the name of the [token](#Tok) that you previously created.
1. Select the **Ksef environment** parameter, and then, in the **Value** field, select the type of the environment, depending on the implementation stage: *Test*, *Demo*, or *Prod*.
1. Select the **Start date** parameter, and then define the initial date for the first receipt of invoices from KSeF. All invoices that have dates between the **Start date** value and the current receiving date will be downloaded. Each successive receiving process will start from the date of the previous process.
1. On the **Applicability rules** tab, in the **Channel** field, make sure that the **Value** column contains the same import channel name that you previously defined.
1. <a id="OutputFile"></a>On the **Variables** tab, make a note of the **OutputFile** name, because you will use it in later configuration steps.
1. Select **Save**, and close the page.
1. Complete and deploy the feature as described in [Complete and deploy a Globalization feature](../global/gs-e-invoicing-complete-publish-deploy-globalization-feature.md).

### Configure additional parameters in Finance

Some additional parameters must be configured directly in Finance.

1. Make sure that the following ER configurations are imported:

    - Vendor invoice import (PL)
    - Vendor invoice Mapping to destination (PL)

1. In the **Electronic reporting** workspace, on the **Reporting configurations** tile, select the **Customer invoice context model** configuration.
1. Select **Create configuration**, and then, in the dropdown dialog box, select **Derive from Name: Customer invoice context model, Microsoft** to create a derived configuration.
1. Open the derived configuration for editing in the designer, and then select **Map model to datasource**.
1. Open the **DataChannel** definition for editing in the designer.
1. In the **Data sources** tree, expand the **$Context\_Channel** container.
1. <a id="ImpChn"></a>In the **Value** field, select **Edit**, and then enter the name of the data channel.

    :::image type="content" source="e-inv-pol-import-config.jpg" alt-text="Screenshot of the output channel configuration in Electronic reporting.":::

1. Save your changes, and complete the derived configuration.
1. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
1. On the **Integration channels** tab, in the **Channels** section, in the **Channel** field, enter the import channel name that you previously created.
1. In the **Channels** section, in the **Company** field, select a required legal entity. In the **Document context** field, select the configuration that you previously created.
1. In the **Import sources** section, in the **Name** field, enter the **OutputFile** name that you [previously created](#OutputFile).
1. In the **Data entity name** field, select **Vendor invoice header**. In the **Model mapping** field, reference the **Vendor invoice import (PL)** configuration.

    :::image type="content" source="e-inv-pol-import-output.jpg" alt-text="Screenshot of the import channel configuration in Electronic document parameters.":::

1. Select **Save**, and close the page.

### Configure master data in Finance

You must configure the following types of master data to provide a match for incoming electronic invoices:

- Vendors
- Products
- Units

#### Configure vendors

To configure vendors, follow these steps.

1. Go to **Accounts payable** \> **Vendors** \> **All vendors**, and select a vendor.
1. On the **Invoice and delivery** FastTab, in the **Tax exempt number** field, enter a valid value. The vendor's tax exempt number is used to identify the vendor during the import process for incoming electronic invoices. If no vendor that has matching data is found in the system, the import process fails, and a related error message is shown.

#### Configure products

To configure products, follow these steps.

1. Go to **Product information management** \> **Products** \> **Released products**, and select a product.
1. On the Action Pane, on the **Purchase** tab, in the **Related information** group, select **External item description**.
1. In the **Vendor relation** field, select the vendor or vendor group that the product's external identification is being set up for.
1. In the **External item number** field, enter the identification number of the product for a specific vendor or the group of vendors. External item numbers are used to identify the product during the import process for incoming electronic invoices. If no product that has matching criteria is found in the system, the import process fails, and a related error message is shown.

#### Configure units

To configure units, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **Units** \> **Units**.
1. Select a unit, and then select **External codes**.
1. On the **External codes** page, in the **Overview** section, in the **Code** field, enter a code that corresponds to the selected unit.
1. In the **Value** section, in the **Value** field, enter the external code to match with the unit codes from incoming electronic invoices during the import process.

    > [!NOTE]
    > External unit codes make sense only if incoming electronic invoices contain explicitly defined units. If incoming electronic invoices don't contain explicitly defined units, you can skip step 4.

### Receive electronic invoices

To receive electronic invoices, follow these steps.

1. Go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Receive electronic documents**.
1. Select **OK**, and then close the page.

During the import process, the system tries to automatically match incoming electronic vendor invoices with existing confirmed purchase orders.

If no purchase order is found, the system raises a warning but continues to import the products on invoice lines as **Non-stock** items. Therefore, it expects that the products belong to an item model group where the **Stocked product** checkbox is cleared in the inventory policy.

If no related **Non-stock** products exist, the system tries to import invoice lines by referring to a default item. The default item must be configured in the system as a released product where the code is defined exactly as **DEFAULT\_ITEM**. In addition, the product must belong to an item model group where the **Stocked product** checkbox is cleared in the inventory policy. If no default item is configured in the system, the import process fails, and a related error message is shown.

To view the receipt logs for electronic invoices, go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Electronic document receipt log**. For more information about how to receive electronic invoices, see [Receive electronic documents](../global/e-invoicing-electronic-documents-receiving-log.md).

To view successfully received invoices, go to **Accounts payable** \> **Invoices** \> **Pending vendor invoices**.

## Additional resources

- [Electronic invoicing overview](../global/gs-e-invoicing-service-overview.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
