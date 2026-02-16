---
title: Electronic invoicing and Electronic reporting for France
description: Learn how to work with Electronic invoicing and Electronic reporting for France in Microsoft Dynamics 365 Finance.
author: ilikond
ms.author: ikondratenko
ms.topic: how-to
ms.date: 12/05/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: France
ms.search.validFrom: 2026-03-01
ms.dyn365.ops.version: AX 10.0.45
---

# Electronic invoicing and Electronic reporting for France

This article helps you get started with electronic invoicing and electronic reporting for France. Set up the system to generate, submit, and receive electronic invoices and other related documents in the required format in Microsoft Dynamics 365 Finance via a certified Partner Agent acting as the last mile connector.

:::image type="content" source="emea-fra-einoices-flow.jpg" alt-text="Screenshot of the e-invoicing and e-rporting flow for France.":::

> [!NOTE]
> This electronic invoicing approach uses an invoicing service that's applicable only to cloud deployments of Microsoft Dynamics 365 Finance.

Watch the overview of the French electronic invoicing and electronic reporting implementation in Finance.

> [!VIDEO 45223d9e-5e49-42dc-895c-7d9ccb08b17a]

## Prerequisites

Before you start, make sure these prerequisites are in place:

- The company is a registered taxpayer in France.
- The company has a signed agreement with the certified Partner Agent and obtained the credentials required for esablishing a secure connection to Partner Agent's infrastructure.
  > [!NOTE]
  > This implementation assumes [Edicom](https://edicomgroup.com/electronic-invoicing) is the selected certified Partner Agent. For more information, see [Edicom integration with Microsoft Dynamics 365](https://edicomgroup.com/connectors/microsoft).

- Install the **Electronic invoicing add-in** as described in [Install the add-in for Electronic invoicing microservices](../global/gs-e-invoicing-set-up-overview.md#install-the-add-in-for-electronic-invoicing-microservices).
- Activate **Electronic invoicing integration** with Finance or Supply Chain Management as it's described in [Enable Electronic invoicing integration](../global/gs-e-invoicing-set-up-overview.md#enable-electronic-invoicing-integration).
- Configure the common part of the **Electronic document parameters**.

  > [!NOTE]
  > Service environment configuration is required only if the Regulatory Configuration Service (RCS) experience was previously used to configure the Electronic Invoicing service. Otherwise, keep the **Environment** parameter empty. The system assigns it automatically and make read-only. For more information, see [Service environment configuration](../global/gs-e-invoicing-set-up-overview.md#service-environment-configuration).

- In the **Feature management** workspace, on the **All** tab, search for the **Electronic invoicing documents statuses handling** feature. If this feature doesn't appear on the page, select **Check for updates**. Select the feature, and then select **Enable now**.
  
## Create the Azure Key Vault configuration

Configure the common part of the Azure resources required for Electronic invoicing functioning. For more information, see [Configure Azure resources for Electronic invoicing](../global/gs-e-invoicing-set-up-azure-resources.md).

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

For more information, see [Create a Key Vault reference](../global/gs-e-invoicing-set-up-parameters.md#create-a-key-vault-reference).

## Synchronization of the Electronic invoicing service with Finance

After you complete all the configuration steps described in the previous chapters, validate the configuration.

1. In Dynamics 365 Finance, go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
1. Select the **Electronic invoicing** tab and select the **Save** menu button.
1. If the configuration is correct, the system shows the *Synchronization with the e-invoicing service was successful* information message. You can continue with the next chapters.
1. If there are synchronization errors, address the errors to achieve successful synchronization.


## Import the electronic invoicing feature

1. Go to **Globalization Studio** and select the **Electronic invoicing** tile. Import the latest version of the **French electronic invoice (FR)** globalization feature as described in [Import features from the repository](../global/gs-e-invoicing-import-feature-global-repository.md).
1. In the **Electronic reporting** workspace, on the **Reporting configurations** tile, confirm that the following Electronic reporting configurations are imported as a result of the **French electronic invoice (FR)** globalization feature import.

    - **Invoice model**
    - **Invoice model mapping**
    - **UBL Sales e-invoice (FR)**
    - **UBL Sales e-credit note (FR)**
    - **UBL Project e-invoice (FR)**
    - **UBL Project e-credit note (FR)**
    - **E-Reporting (FR)**
    - ...
    - ...

    > [!NOTE]
    > If the configurations aren't imported, import them manually as described in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

1. In the **Electronic reporting** workspace, on the **Reporting configurations** tile, import the latest versions of the following Electronic reporting configurations to receive incoming vendor invoices.

    - **Vendor invoice import (FR)**
    - **Vendor invoice Mapping to destination (FR)**
    - **Import invoice context model**

     > [!IMPORTANT]
    > Make sure that the **Vendor invoice Mapping to destination (FR)** Electronic Reporting configuration is marked as **Default for model mapping**.
    
## Configure the electronic invoicing feature

The **French electronic invoice (FR)** feature publishes some parameters with default values. Before you deploy the feature, review the default values and update them so they reflect your business operations.

Review and update the **French electronic invoice (FR)** feature configuration:

1. Go to **Globalization Studio** and select the **Electronic invoicing** tile. Import the globalization feature as described in [Import features from the repository](../global/gs-e-invoicing-import-feature-global-repository.md).
1. Copy the imported **French electronic invoice (FR)** globalization feature and select your configuration provider, as described in [Create a Globalization feature](../global/gs-e-invoicing-create-new-globalization-feature.md).
1. On the **Versions** tab, check that the **Draft** version is selected.
1. On the **Feature parameters** tab, specify these required **Edicom** connection and integration parameters:

    - **Service ID** – Use the service ID (Domain) number from Edicom to identify the company.
    - **Group** – Use the group code for internal routing within the Edicom infrastructure.
    - **Destination** – Construct the destination by appending **_EDIWIN** to the service ID number. For example, if the service ID number is **123456**, enter **123456_EDIWIN**.
    - **Token** – Select the name of the [token](#Tok) you created earlier.

1. Each copy starts as a **Draft** version. Complete and deploy the feature as described in [Complete and deploy a Globalization feature](../global/gs-e-invoicing-complete-publish-deploy-globalization-feature.md).

## Configure electronic document parameters

1. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
1. On the **Electronic document** tab, add records for the following tables.
   - **Customer Invoice journal**
   - **Project invoice**
   - 
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

### <a id="SIREN"></a>Set up SIREN number

> [!NOTE]
> When the output files of electronic invoices are generated, registration numbers of the **Enterprise ID (COID)** category are used as *Système d'identification du répertoire des entreprises* numbers (**SIREN**). If the **Enterprise ID (COID)** registration category already exists and has been assigned to a registration type, skip this procedure.

To configure the **SIREN** registration number, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration** \> **Global address book** \> **Registration types** \> **Registration types**.
1. Create a registration type.
1. In the **Country/region** field, select **FRA - France**.
1. Go to **Organization administration** \> **Global address book** \> **Registration types** \> **Registration categories**.
1. Create a registration category.
1. In the **Registration types** field, select the registration type that you created in step 2.
1. In the **Registration categories** field, select **Enterprise ID (COID)**.

### <a id="SIRET"></a>Set up SIRET number

To configure the *Système d’identification du répertoire des établissements* (**SIRET**) registration number, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration** \> **Global address book** \> **Registration types** \> **Registration types**.
1. Create a registration type.
1. In the **Country/region** field, select **FRA - France**.
1. Go to **Organization administration** \> **Global address book** \> **Registration types** \> **Registration categories**.
1. Create a registration category.
1. In the **Registration types** field, select the registration type that you created in step 2.
1. In the **Registration categories** field, select **SIRET**.

### <a id="VAT"></a>Set up VAT number

Optinally, to configure the Tax exempt number, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration** \> **Global address book** \> **Registration types** \> **Registration types**.
1. Create a registration type.
1. In the **Country/region** field, select **FRA - France**.
1. Go to **Organization administration** \> **Global address book** \> **Registration types** \> **Registration categories**.
1. Create a registration category.
1. In the **Registration types** field, select the registration type that you created in step 2.
1. In the **Registration categories** field, select **VAT**.

## Set up address structure

Set up the postal address structure.

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**.
1. Ensure that at least the **Country code** element is configured.
   
## Configure legal entity data

### Enter the address

Add the primary address.

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**, and select a legal entity.
1. On the **Addresses** FastTab, add the primary address for the legal entity.

### Seller identification

Add the registration numbers.

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
1. On the Action Pane, select **Registration IDs**.
1. On the **Registration ID** FastTab, select **Add**, set **Registration type** to the [SIREN](#SIREN) type you created earlier, and enter the SIREN numner in the **Registration number** column.
1. Select **Add**, set **Registration type** to the [SIRET](#SIRET) type you created earlier, and enter the SIRET numner in the **Registration number** column.
1. Define the Tax exempt ([VAT](#VAT)) number whatever way is used in your company.

> [!NOTE]
> If the registration number with the **VAT** registration category is not defined then the value from the **Organization administration** \> **Organizations** \> **Legal entities** \> **Foreign trade and statistics** \> **INTRASTAT** \> **VAT exempt number export** will be used.

## Configure customer data

### Enter the address

To enter the address, follow these steps.

1. Go to **Accounts receivable** \> **Customers** \> **All customers**.
1. Select a customer.
1. On the **Addresses** FastTab, add a valid address for the selected customer.

### Buyer identification

To enter the registration numbers, follow these steps.

1. Go to **Accounts receivable** \> **Customers** \> **All customers**.
1. On the Action Pane, on the **Customer** tab, in the **Registration** group, select **Registration IDs**.
1. On the **Registration ID** FastTab, select **Add** to create a registration ID.
1. In the **Registration type** field, select the [SIREN](#SIREN) registration type that you created earlier.
1. Select **Add**, and in the **Registration type** field, select the [SIRET](#SIRET) registration type that you created earlier.
1. Select **Add** to create another registration ID, if necessary.
1. In the **Registration number** field, enter a valid [VAT](#VAT) number for the selected customer.

> [!NOTE]
> If the registration number with the **VAT** registration category is not defined then the value from the **Accounts receivable** \> **Customers** \> **All customers** \> **Invoice and delivery** \> **SALES TAX** \> **Tax exempt number** will be used.

## Configure electronic addresses

Follow these steps electronic addresses for sellers or buyers that will be *primarily* used as **EndpointIDs** for documents routing.

### Configure electronic document properties

Set up electronic document properties.

1. Go to **Accounts receivable** \> **Setup** \> **Electronic document property types**, and select **New**.
1. In the **Type** field, enter **SellerElectronicAddress**. Enter the value exactly as shown. It's used for the **Seller** identification schema definition.
1. Select **Applicability** to add an applicable table.
1. On the **Electronic document property type applicability setup** page, in the **Table name** field, select **Legal entities**.
1. Save your changes and return to the **Electronic document property types** page.
1. Select **New** to create another electronic document property type.
1. In the **Type** field, enter **BuyerElectronicAddress**. Enter the value exactly as shown. It's used for the **Buyer** identification schema definition.
1. Select **Applicability** to add an applicable table.
1. On the **Electronic document property type applicability setup** page, in the **Table name** field, select **Customers**.
1. Save your changes, and return to the **Electronic document property types** page.
1. Save your changes, and close the page.

   :::image type="content" source="emea-fra-einoices-e-addresses.jpg" alt-text="Screenshot of the property type added on the Electronic document property types page.":::

### Enter the seller electronic address

To enter the Seller schema code, follow these steps.

1. Go to **Organization administration** \> **Organizations** \> **Legal entities** and select a legal entity.
1. Select **Electronic document properties** from the Action Pane.
1. In the **Value** column, enter the required seller electronic address.

### Enter the buyer electronic address

To enter the Buyer schema codes, follow these steps.

1. Go to **Accounts receivable** \> **Customers** \> **All customers**.
1. Select a specific customer in the list, and then, on the Action Pane, on the **Customer** tab, in the **Properties** group, select **Electronic document properties**.
1. In the **Value** column, enter the required buyer electronic address.

> [!NOTE]
> For both, Seller and Buyer identification, the defined above electronic address will be used as the **EndpointID** value with the **schemeID** attribute equal to **0225** (FRCTC ELECTRONIC ADDRESS) is used by default according to the [Electronic Address Scheme (EAS)](https://docs.peppol.eu/poacc/billing/3.0/codelist/eas/).

If the electronic addresses are not defined then the system will use the following Endpoint determination algorithm: 

- **SIRET** number is used with the **0009** value as the *schemeID* attribute.
- If **SIRET** number is not defined then **SIREN** number is used with the **0002** value as the *schemeID* attribute.
- If **SIREN** number is not defined then Global Location Number (GLN), also known as European article numbering (EAN) number is used with the **0088** value as the *schemeID* attribute.

  > [!NOTE]
  > It assumes that the dedicated Registration number of the **EAN** registration category has been defined in advance.
- If **EAN** number is not defined then VAT number is used with the **9957** value as the *schemeID* attribute.

## Configure mandatory notes

According to French requirements, each individual electronic invoice must contain 3 mandatory **Note** elements in the header with the **following** predefined prefixes:

- **#PMD#** *the text of the first note*
- **#PMT#** *the text of the second note*
- **#AAB#** *the text of the third note*

To automate the notes creation, the recommendation is to use the functionality of [Advanced notes management](../italy/emea-ita-exil-structured-notes.md).
You need to configure at least 3 external header-level notes with the mandatory prefixes for the required documents, for all or specifically selected customers. Once configured, the notes will be automatically added to the applicable documents upon creation.

:::image type="content" source="emea-fra-advanced-notes.jpg" alt-text="Screenshot of the advance notes configuration.":::

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
1. Go to **Tax** \> **Setup** \> **Sales tax** \> **Sales tax exempt codes**.
1. Define exempt codes that will be used in the event of non-taxable, zero-rated or exempted operations.

> [!NOTE]
> The exempt codes can have any value internally used in your company, but the **Description** field must contain the standardized tax exemption code according to the official categorization introduced in France, for example: *VATEX-FR-298SEXDECIESA*. Exactly the value from the Description field will be used as **Tax Exemption Reason** while generating the output XML files for electronic invoices. 

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


