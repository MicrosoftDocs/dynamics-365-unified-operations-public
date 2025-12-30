---
title: Electronic invoicing for Singapore
description: Learn how to get started with Electronic invoicing for Singapore in Microsoft Dynamics 365 Finance.
author: ilikond
ms.author: ikondratenko
ms.topic: how-to
ms.date: 10/01/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: Singapore
ms.search.validFrom: 2025-10-01
ms.dyn365.ops.version: AX 10.0.45
---

# Electronic invoicing for Singapore

[!include [banner](../../includes/banner.md)]

This article helps you get started with electronic invoicing for Singapore. Set up the system to generate, submit, and receive electronic invoices in the Singaporean extension of the [PEPPOL International (PINT)](https://www.peppolguide.sg/billing/) format in Microsoft Dynamics 365 Finance by using the last mile connector.

:::image type="content" source="../media/apac-sgp-einoices-flow.jpg" alt-text="Screenshot of the e-invoice flow for Singapore.":::

> [!NOTE]
> This electronic invoicing approach uses an invoicing service that's applicable only to cloud deployments of Microsoft Dynamics 365 Finance.

## Prerequisites

Before you start, make sure these prerequisites are in place:

- The company is a registered taxpayer in Singapore.
- The company has a signed agreement with the electronic document delivery service provider that supports document interchange in the PEPPOL (PINT) format.
- Register the following profile ID for Microsoft Dynamics 365 Finance electronic document interchange:

    - **urn:peppol:bis:billing** – Use this profile to interchange documents in PEPPOL (PINT) format.

- Get the credentials from the service provider to integrate the Electronic Invoicing service with the [Electronic Invoicing service independent software vendor (ISV) last-mile connector](../global/e-invoicing-isv-connector.md).

   > [!NOTE]
   > This implementation assumes [Edicom](https://edicomgroup.com/electronic-invoicing) is the Electronic Invoicing ISV last-mile connection service provider. For more information, see [Edicom integration with Microsoft Dynamics 365](https://edicomgroup.com/edicom-microsoft?365).

- Learn about Electronic Invoicing in the [Electronic Invoicing service overview](../global/gs-e-invoicing-service-overview.md) and [Electronic invoicing components](../global/gs-e-invoicing-administration-integration-components.md).
- Complete the common Electronic Invoicing service configuration in [Electronic invoicing configuration](../global/gs-e-invoicing-set-up-overview.md).

## Create the Azure Key Vault configuration

Create an Azure Key Vault to store required company secrets. For more information, see [Configure Azure resources for Electronic invoicing](../global/gs-e-invoicing-set-up-azure-resources.md).

Add the following element to the key vault:

- Add the secret for the **token** that authorizes access to Edicom services. Obtain it from Edicom as described in the prerequisites.

## Set up electronic invoicing Key Vault parameters

Set up electronic invoicing Key Vault parameters.

1. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
1. On the **Electronic invoicing** tab, in **Key Vault settings**, in **Key Vault**, select the key vault reference you created earlier.
1. In **SAS token secret**, select the storage account secret URL used to authenticate access to the storage account.
1. Select **Key Vault parameters**.
1. On the **Key Vault parameters** page, in **Certificates**, select **Add** and create an element of the appropriate type for each secret described earlier.

    - <a id="Tok"></a>Add the **token** element of type **Secret**.

> [!NOTE]
> Match the value in the **Name** column to the secret name described earlier.

## Import the electronic invoicing feature

1. Go to **Globalization Studio** and select the **Electronic invoicing** tile. Import the latest version of the **Singaporean electronic invoice (SG)** globalization feature as described in [Import features from the repository](../global/gs-e-invoicing-import-feature-global-repository.md).
1. In the **Electronic reporting** workspace, on the **Reporting configurations** tile, confirm that the following Electronic reporting configurations are imported as a result of the **Singaporean electronic invoice (SG)** globalization feature import.

    - **Invoice model**
    - **Invoice model mapping**
    - **PINT Sales e-invoice** 
    - **PINT Sales e-credit note**
    - **PINT Project e-invoice**
    - **PINT Project e-credit note**
    - **Customer invoice context model**
    - **Response message model**
    - **Edicom Response Processing**
    - **Error log import Json**

    > [!NOTE]
    > If the configurations aren't imported, import them manually as described in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

1. In the **Electronic reporting** workspace, on the **Reporting configurations** tile, import the latest versions of the following Electronic reporting configurations to receive incoming vendor invoices.

    - **Vendor invoice import**
    - **Vendor invoice Mapping to destination**
    - **Import invoice context model**
    
## Configure the electronic invoicing feature

The **Singaporean electronic invoice (SG)** feature publishes some parameters with default values. Before you deploy the feature, review the default values and update them so they reflect your business operations.

Review and update the **Singaporean electronic invoice (SG)** feature configuration:

1. Go to **Globalization Studio** and select the **Electronic invoicing** tile. Import the globalization feature as described in [Import features from the repository](../global/gs-e-invoicing-import-feature-global-repository.md).
1. Copy the imported **Singaporean electronic invoice (SG)** globalization feature and select your configuration provider, as described in [Create a Globalization feature](../global/gs-e-invoicing-create-new-globalization-feature.md).
1. On the **Versions** tab, check that the **Draft** version is selected.
1. On the **Feature parameters** tab, specify these required **Edicom** connection and integration parameters:

    - **Service ID** – Use the service ID (Domain) number from Edicom to identify the company.
    - **Group** – Use the group code for internal routing within the Edicom infrastructure.
    - **Destination** – Construct the destination by appending **_EDIWIN** to the service ID number. For example, if the service ID number is **123456**, enter **123456_EDIWIN**.
    - **Token** – Select the name of the [token](#Tok) you created earlier.

    :::image type="content" source="apac-sgp-einv-feature-parameters.jpg" alt-text="Screenshot of the Feature parameters tab configured for the Globalization feature for Singapore.":::

1. Each copy starts as a **Draft** version. Complete and deploy the feature as described in [Complete and deploy a Globalization feature](../global/gs-e-invoicing-complete-publish-deploy-globalization-feature.md).

## Configure electronic document parameters

1. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
1. On the **Electronic document** tab, add records for the **Customer Invoice journal** and **Project invoice** tables.
1. For each table name, set the **Document context** and **Electronic document model mapping** fields as described in [Set up electronic invoicing parameters](../global/gs-e-invoicing-set-up-parameters.md#set-up-electronic-document-parameters).

 :::image type="content" source="../belgium/emea-bel-einoices-docs.jpg" alt-text="Screenshot of the setup on the Electronic document tab of the Electronic document parameters page.":::

> [!NOTE]
> If you created derived equivalents of the earlier Electronic Reporting configurations, use them instead of the standard configurations.
    
1. <a id="ExChannel"></a>On the **Integration channels** tab, in the **Channels** section, select **Add** to create a new channel.
1. In the **Channel** field, enter **EdiStatus**. Enter the value exactly as shown. The system uses it to submit outgoing electronic invoices.
1. In the **Company** field, select the legal entity.
1. In the **Document context** field, select the **Data channel context** mapping from the **Customer invoice context model** configuration.
1. In the **Channel type** field, select **Export**.
1. In the **Channels** section, select **Add** to create another channel.
1. In the **Channel** field, enter **EdiImport**. Enter the value exactly as shown. The system uses it to import incoming electronic invoices.
1. In the **Company** field, select a required legal entity.
1. In the **Document context** field, select the **Data channel context** mapping from the **Import invoice context model** configuration.
1. In the **Channel type** field, select **Import**.
1. In the **Import sources** section, select **Add** to create an import source.
1. In the **Name** field, enter **ResponseXml**. Enter the value exactly as shown.
1. In the **Data entity name** field, select the **Vendor invoice header** entity.
1. In the **Model mapping** field, select the **Import vendor invoice** mapping from the **Vendor invoice import** configuration.
1. Select **Save**, and then close the page.

:::image type="content" source="../belgium/emea-bel-einoices-channels.jpg" alt-text="Screenshot of the configuration on the Integration channels tab of the Electronic document parameters page.":::

> [!NOTE]
> If you use integration channels other than **EdiStatus** and **EdiImport**, do another configuration for the feature and related context configurations.

## Set up registration numbers

If these registration types and categories already exist, skip this procedure.

### <a id="UEN"></a>Set up UEN number

To set up the Unique Entity Number (UEN) registration number, see [UEN of the business user](apac-sgp-iras-audit-file.md#company-uen).

### <a id="GST"></a>Set up GST number

To set up the Goods and Services Tax (GST) registration number, see [GST Registration Number of the business user](apac-sgp-iras-audit-file.md#company-gst).

## Set up address structure

Set up the postal address structure.

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**.
1. Ensure the following required elements are configured.

    - Country code
    - Postal code
    - Street

## Configure legal entity data

### Enter the address

Add the primary address.

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**, and select a legal entity.
1. On the **Addresses** FastTab, add the primary address for the legal entity.

### Seller identification

Add the registration numbers.

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
1. On the Action Pane, select **Registration IDs**.
1. On the **Registration ID** FastTab, select **Add**, set **Registration type** to the [Unique Entity Number (UEN)](#UEN) type you created earlier, and enter the UEN value in **Registration number**.
1. Select **Add**, set **Registration type** to the [Goods and Services Tax (GST)](#GST) type you created earlier, and enter the GST value in **Registration number**.

    The system puts the **UEN** number in the **Invoice\\cac:AccountingSupplierParty\\cac:Party\\cbc:EndpointID** element and the **GST** number in the **Invoice\\cac:AccountingSupplierParty\\cac:Party\\cac:PartyTaxScheme\\cbc:CompanyID** element in the generated electronic invoice XML file. These values act as the seller's identification during submission.

## Configure customer data

### Enter the address

To enter the address, follow these steps:

1. Go to **Accounts receivable** \> **Customers** \> **All customers**.
1. Select a customer.
1. On the **Addresses** FastTab, add a valid address for the selected customer.

### Buyer identification

To enter the registration numbers, follow these steps:

1. Go to **Accounts receivable** \> **Customers** \> **All customers**.
1. On the Action Pane, on the **Customer** tab, in the **Registration** group, select **Registration IDs**.
1. On the **Registration ID** FastTab, select **Add** to create a registration ID.
1. In the **Registration type** field, select the [Unique Entity Number (UEN)](#UEN) registration type that you created earlier.
1. In the **Registration number** field, enter a valid BRN registration number for the selected customer.
1. Select **Add** to create another registration ID, if necessary.
1. In the **Registration type** field, select the [Goods and Services Tax (GST)](#GST) registration type that you created earlier.
1. In the **Registration number** field, enter a valid SST registration number for the selected customer.

   The **UEN** number is entered in the **Invoice\\cac:AccountingCustomerParty\\cac:Party\\cbc:EndpointID** element and the **GST** number is entered in the **Invoice\\cac:AccountingCustomerParty\\cac:Party\\cac:PartyTaxScheme\\cbc:CompanyID** element in the electronic invoice XML file that is generated. It's used as the buyer's identification during the submission process.

> [!NOTE]
> For both, Seller and Buyer identification, the schema **0195** (Singapore UEN identifier) is used by default according to the [Electronic Address Scheme (EAS)](https://docs.peppol.eu/poacc/billing/3.0/codelist/eas/). If there's a necessity to redefine the default schema then perform the steps described in the next section. Otherwise you can ignore the next section.

## Configure identification schemas

Follow these steps only if you need to redefine the default identification schemas for sellers or buyers.

### Configure electronic document properties

Set up electronic document properties.

1. Go to **Accounts receivable** \> **Setup** \> **Electronic document property types**, and select **New**.
1. In the **Type** field, enter **CompanyEndpointType**. Enter the value exactly as shown. It's used for the **Seller** identification schema definition.
1. Select **Applicability** to add an applicable table.
1. On the **Electronic document property type applicability setup** page, in the **Table name** field, select **Legal entities**.
1. Save your changes and return to the **Electronic document property types** page.
1. Select **New** to create another electronic document property type.
1. In the **Type** field, enter **CustomerEndpointType**. Enter the value exactly as shown. It's used for the **Buyer** identification schema definition.
1. Select **Applicability** to add an applicable table.
1. On the **Electronic document property type applicability setup** page, in the **Table name** field, select **Customers**.
1. Save your changes, and return to the **Electronic document property types** page.
1. Save your changes, and close the page.

    :::image type="content" source="../belgium/emea-bel-einoices-schemas.jpg" alt-text="Screenshot of the property type added on the Electronic document property types page.":::

### Enter the seller schema code

To enter the Seller schema code, follow these steps:

1. Go to **Organization administration** \> **Organizations** \> **Legal entities** and select a legal entity.
1. Select **Electronic document properties** from the Action Pane.
1. In the **Value** column, enter the required seller schema code.

### Enter the buyer schema codes

To enter the Buyer schema codes, follow these steps:

1. Go to **Accounts receivable** \> **Customers** \> **All customers**.
1. Select a specific customer in the list, and then, on the Action Pane, on the **Customer** tab, in the **Properties** group, select **Electronic document properties**.
1. In the **Value** column, enter the required buyer schema code.

> [!NOTE]
> Schema codes defined by electronic document property types take priority over the default **0195** schema code.

## Set up units of measure

Set up units of measure.

1. Go to **Organization administration** > **Setup** > **Units** > **Units**.
1. Select a unit ID, then select **External codes**.
1. On the **External codes** page, in **Overview**, in the **Code** column, enter the unit ID.
1. In the **Standard code** column, select the checkbox.
1. In the **Value** section, in the **Value** field, enter the external code from the [UNECE Recommendation 20 code list](https://docs.peppol.eu/poacc/billing/3.0/codelist/UNECERec20/).

   > [!NOTE]
   > If no specific unit of measure applies, the system uses the default value **EA**.

## Configure sales tax codes

1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax codes**.
1. Select a sales tax code. On the Action Pane, on the **Sales tax code** tab, in the **Sales tax code** group, select **External codes**.
1. In the **Overview** section, create a line for the selected unit. In the **External code** field, enter the sales tax code from step 2.
1. In the **Value** section, in the **Value** field, enter an external code that matches one of the Singapore-specific [Duty or tax or fee category codes](https://www.peppolguide.sg/billing/codelist/SGTaxCat/).

## Issue electronic invoices

After you complete the required configuration steps, generate and submit electronic invoices for posted invoices: go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Submit electronic documents**. Learn more in [Submit electronic documents](../global/e-invoicing-submit-electronic-documents.md).

> [!IMPORTANT]
> In current implementations, the standard submission procedure only generates electronic invoices and stores them in the service. It doesn't submit them. To submit invoices, complete these extra steps.

Follow these steps to submit the generated electronic invoices.

1. In the **Feature management** workspace, confirm that the **Export channels for electronic invoicing integration** feature is enabled. Learn more in [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
1. Go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Run submission process in export channels**.
1. In the **Channel** field, select the export channel you [created](#ExChannel), and then select **OK**.

Check the submission results at **Organization administration** \> **Periodic** \> **Electronic documents** \> **Electronic document submission log**. Learn more in [Work with Electronic document submission log](../global/e-invoicing-submission-log.md).

> [!NOTE]
> Submitted electronic invoices are also available in the [Ediwin](https://ediwin.edicomgroup.com/) portal in the **Outbound** folder and its subfolders, where you can monitor further processing.

## Receive incoming electronic invoices

Set more parameters in Microsoft Dynamics 365 Finance to import incoming invoices.

Configure these master data types to match incoming electronic invoices:

- vendors
- products
- units

Follow the steps in [Import vendor electronic invoices](../europe/emea-peppol-import.md), starting at [Configure vendor data](../europe/emea-peppol-import.md#configure-vendor-data).

### Receive electronic invoices

After you complete the configuration, receive incoming electronic invoices in the **PEPPOL** format.

> [!NOTE]
> Review incoming electronic invoices in the **Inbound** folder and its subfolders in your [Ediwin](https://ediwin.edicomgroup.com/) portal.

Receive electronic invoices:

1. Go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Receive electronic documents**.
1. Select **OK**, and then close the page.

View receipt logs for processed electronic invoices: go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Electronic document receipt log**.

View successfully received invoices: go to **Accounts payable** \> **Invoices** \> **Pending vendor invoices**.

## More information

- [Electronic invoicing coverage by country and region](../global/e-invoicing-coverage.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

