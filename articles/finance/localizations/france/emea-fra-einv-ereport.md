---
title: Electronic invoicing for France
description: Learn how to work with Electronic invoicing for France in Microsoft Dynamics 365 Finance.
author: ilikond
ms.author: ikondratenko
ms.topic: how-to
ms.date: 04/24/2026
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: France
ms.search.validFrom: 2026-04-24
ms.dyn365.ops.version: AX 10.0.48
---

# Electronic invoicing for France

This article helps you get started with electronic invoicing for France. Set up the system to generate, submit, and receive electronic invoices and other related documents in the required format in Microsoft Dynamics 365 Finance via a certified service provider acting as an Approved Platform (*Platform Agréée* - **PA**).

:::image type="content" source="emea-fra-einvoices-flow.jpg" alt-text="Screenshot of the e-invoicing and e-reporting flow for France.":::

> [!NOTE]
> This electronic invoicing approach uses an invoicing service that's applicable only to cloud deployments of Microsoft Dynamics 365 Finance.

Watch the overview of the French electronic invoicing implementation in Finance.

> [!VIDEO 45223d9e-5e49-42dc-895c-7d9ccb08b17a]

## Prerequisites

Before you start, make sure these prerequisites are in place:

- The company is a registered taxpayer in France.
- The company has a signed agreement with the selected Approved Platform and obtained the credentials required for establishing a secure connection to the Approved Platform's infrastructure.
  > [!NOTE]
  > This implementation assumes [Edicom](https://edicomgroup.com/electronic-invoicing) is the selected certified Approved Platform (PA). For more information, see [Edicom integration with Microsoft Dynamics 365](https://edicomgroup.com/connectors/microsoft).
  
  > Watch the overview of the Edicom credentials configuration in Finance. More details are provided in the [next](#EdCred) chapters.
  > [!VIDEO 70723008-ac71-4514-9b12-af8b7e792890]

- Install the **Electronic invoicing add-in** as described in [Install the add-in for Electronic invoicing microservices](../global/gs-e-invoicing-set-up-overview.md#install-the-add-in-for-electronic-invoicing-microservices).
- Activate **Electronic invoicing integration** with Finance or Supply Chain Management as described in [Enable Electronic invoicing integration](../global/gs-e-invoicing-set-up-overview.md#enable-electronic-invoicing-integration).
- Configure the common part of the [**Electronic document parameters**](../global/gs-e-invoicing-set-up-parameters.md#set-up-electronic-document-parameters).

  > [!NOTE]
  > You need to configure the service environment only if you previously used the Regulatory Configuration Service (RCS) experience to configure the Electronic Invoicing service. Otherwise, keep the **Environment** parameter empty. The system assigns it automatically and makes it read-only. For more information, see [Service environment configuration](../global/gs-e-invoicing-set-up-overview.md#service-environment-configuration).

- In the **Feature management** workspace, on the **All** tab, enable the following features. If these features don't appear on the page, select **Check for updates**. Select the features, and then select **Enable now** for each of them. For more information, see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
  - **E-Invoice Document Status Lifecycle Management**
  - **E-Invoice Document Response Submission**
  - **Export channels for electronic invoicing integration**
  - **Execute update actions for submitted documents**

  And **disable** the following feature.
  - **Simultaneous globalization features completion and deployment** (*to activate the possibility of the **Application setup** copying*).

## <a id="EdCred"></a>Create the Azure Key Vault configuration

Configure the common part of the Azure resources required for Electronic invoicing functioning. For more information, see [Configure Azure resources for Electronic invoicing](../global/gs-e-invoicing-set-up-azure-resources.md).

Add the following element to the key vault:

- Add the secret for the **token** that authorizes access to Edicom services.

## Set up electronic invoicing Key Vault parameters

Set up electronic invoicing Key Vault parameters.

1. Go to **Organization administration** > **Setup** > **Electronic document parameters**.
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

1. In Dynamics 365 Finance, go to **Organization administration** > **Setup** > **Electronic document parameters**.
1. Select the **Electronic invoicing** tab and select the **Save** menu button.
1. If the configuration is correct, the system shows the *Synchronization with the e-invoicing service was successful* information message. You can continue with the next chapters.
1. If there are synchronization errors, address the errors to achieve successful synchronization.

## Import the electronic invoicing feature

1. Go to **Globalization Studio** and select the **Electronic invoicing** tile. Import the latest versions of the following globalization features as described in [Import features from the repository](../global/gs-e-invoicing-import-feature-global-repository.md).
   - **French electronic invoice (FR)**
   - **French electronic invoice status (FR)**
  
1. All the required Electronic Reporting configurations are automatically imported as a result of the globalization features import. You can review imported Electronic Reporting configurations in the **Electronic reporting** workspace, on the **Reporting configurations** tile. The full list of the required Electronic Reporting configurations can be found in the **[List of Electronic Reporting configurations](#ERconfigs)** section of the **Appendix** chapter.

> [!NOTE]
> If some of the configurations aren't imported, import them manually as described in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

> [!IMPORTANT]
> Make sure that the **Vendor invoice Mapping to destination** and **Response message model mapping to destination (FR)** Electronic Reporting configurations are marked as **Default for model mapping**.

## Configure the electronic invoicing features

The **French electronic invoice (FR)** and **French electronic invoice status (FR)** features publish some parameters with default values. Before you deploy the features, review the default values and update them so they reflect your business operations.

Review and update the **French electronic invoice (FR)** feature configuration:

1. Go to **Globalization Studio** and select the **Electronic invoicing** tile. Import the globalization feature as described in [Import features from the repository](../global/gs-e-invoicing-import-feature-global-repository.md).
1. Copy the imported **French electronic invoice (FR)** globalization feature and select your configuration provider, as described in [Create a Globalization feature](../global/gs-e-invoicing-create-new-globalization-feature.md).
1. On the **Versions** tab, check that the **Draft** version is selected.
1. On the **Feature parameters** tab, specify these required **Edicom** connection and integration parameters:

    - **Domain** – Use the domain number (can be also referred as **Service ID**) from Edicom to identify the company.
    - **Group** – Use the group code for internal routing within the Edicom infrastructure.
    - **Destination** – Construct the destination by appending **_EDIWIN** to the Domain/Service ID number. For example, if the Domain number is **123456**, enter **123456_EDIWIN**.
    - **Token** – Select the name of the [token](#Tok) you created earlier.

1. Each copy starts as a **Draft** version. Complete and deploy the feature as described in [Complete and deploy a Globalization feature](../global/gs-e-invoicing-complete-publish-deploy-globalization-feature.md).

   > [!NOTE]
   > While deploying the feature, toggle the **Activate application setup** checkbox in the **APPLICATION** section. In this case, the system automatically preconfigures the significant part of the **Electronic document parameters** in Finance. You can review and change the preconfigured parameters, as described in the next chapter.

1. Repeat steps 2 through 5 for the **French electronic invoice status (FR)** feature.

## Configure electronic document parameters

The system preconfigures electronic documents when you deploy the globalization features to the service and select the **Activate application setup** option during deployment. This section provides information about the setup, or if you decide to amend the standard system setup. If no amendment is required, go to the **Configure integration channels** chapter.

1. Go to **Organization administration** > **Setup** > **Electronic document parameters**.
1. On the **Electronic document** tab, add records for the following views.
   - **Customer invoice journal - Domestic B2B transactions (France)**
   - **Project invoice journal - Domestic B2B transactions (France)**
   - **Customer invoice response**
   - **Pending vendor invoice response**
1. For each electronic document, set the **Document context** and **Electronic document model mapping** fields as described in [Set up electronic invoicing parameters](../global/gs-e-invoicing-set-up-parameters.md#set-up-electronic-document-parameters).

> [!NOTE]
> To minimize the risk of accidental massive submissions, the system implements default filtering by document dates. In the **Date filed to filter** column, specify the exact selected table's field for filtering. In the **Days to look back** column, define the number of days to subtract from the current date to determine the earliest date for document processing. If you don't configure the **Date filed to filter** and **Days to look back** columns, the **Invoice date** equal to the current date is used by default.

1. For the **Customer invoice journal - Domestic B2B transactions (France)** and **Project invoice journal - Domestic B2B transactions (France)** electronic documents, select **Response types**.
1. Select **New** to create a new response type.
1. In the **Response type** column, enter **LifeCycleStatus**. Enter the value exactly as shown.
1. In the **Submission status** column, select the **Completed** value.
1. In the **Data entity name** column, select the **Electronic document submission log** entity.
1. In the **Model mapping** column, select the **Edicom life cycle status format (FR)** configuration.
1. Repeat steps 2 through 6 for the following values in the **Submission status** column.
   - **Failed**
   - **Pending**
   - **Pending update actions execution**
1. Select **New** to create a new response type.
1. In the **Response type** column, enter **ValidationStatus**. Enter the value exactly as shown.
1. In the **Submission status** column, select the **Completed** value.
1. In the **Data entity name** column, select the **Electronic document submission log** entity.
1. In the **Model mapping** column, select the **Edicom Response Processing (FR)** configuration and the **Invoice status** mapping name.
1. Repeat steps 8 through 12 for the following values in the **Submission status** column.
   - **Failed**
   - **Pending update actions execution**

:::image type="content" source="e-invoice-fra-parameters.jpg" alt-text="Screenshot of the setup on the Electronic document tab of the Electronic document parameters page.":::

1. For the **Customer invoice response** electronic document, select **Response types**.
1. Select **New** to create a new response type.
1. In the **Response type** column, enter **Response**. Enter the value exactly as shown.
1. In the **Submission status** column, select the **Completed** value.
1. In the **Data entity name** column, select the **Electronic document submission log** entity.
1. In the **Model mapping** column, select the **Edicom Cust App Response Processing** configuration.
1. Repeat steps 2 through 6 for the **Pending** value in the **Submission status** column.
1. Select **Save**, and then close the page.
1. For the **Pending vendor invoice response** electronic document, select **Response types**.
1. Select **New** to create a new response type.
1. In the **Response type** column, enter **Response**. Enter the value exactly as shown.
1. In the **Submission status** column, select the **Completed** value.
1. In the **Data entity name** column, select the **Electronic document submission log** entity.
1. In the **Model mapping** column, select the **Edicom Vend App Response Processing** configuration.
1. Repeat steps 10 through 14 for the **Pending** value in the **Submission status** column.  
1. Select **Save**, and then close the page.

> [!NOTE]
> If you created derived equivalents of the earlier Electronic Reporting configurations, use them instead of the standard configurations.

## Configure integration channels

1. <a id="ExChannel"></a>On the **Integration channels** tab, in the **Channels** section, select **Add** to create a new channel.
1. In the **Channel** field, enter **EdiStatus**. Enter the value exactly as shown. The system uses it to submit outgoing electronic invoices.
1. In the **Company** field, select the legal entity.
1. In the **Document context** field, select the **Data channel context** mapping from the **Customer invoice context model** configuration.
1. In the **Channel type** field, select **Export**.
1. In the **Channels** section, select **Add** to create another channel.
1. In the **Channel** field, enter **InvStatus**. Enter the value exactly as shown. The system uses it to update lifecycle statuses for previously submitted invoices.
1. In the **Company** field, select the legal entity.
1. In the **Document context** field, select the **Data channel context** mapping from the **Import response context** configuration.
1. In the **Channel type** field, select **Export**.
1. In the **Channels** section, select **Add** to create another channel.
1. In the **Channel** field, enter **EdiImport**. Enter the value exactly as shown. The system uses it to import incoming electronic invoices.
1. In the **Company** field, select a required legal entity.
1. In the **Document context** field, select the **Data channel context** mapping from the **Import invoice context model** configuration.
1. In the **Channel type** field, select **Import**.
1. In the **Import sources** section, select **Add** to create an import source.
1. In the **Name** field, enter **ResponseXml**. Enter the value exactly as shown.
1. In the **Data entity name** field, select the **Vendor invoice header** entity.
1. In the **Model mapping** field, select the **Import vendor invoice** mapping from the **Vendor invoice import Edicom (FR)** configuration.
1. Select **Save**, and then close the page.

:::image type="content" source="e-invoice-fra-channels.jpg" alt-text="Screenshot of the configuration on the Integration channels tab of the Electronic document parameters page.":::

> [!NOTE]
> If you use integration channels names other than **InvStatus**, **EdiStatus**, and **EdiImport**, or import source name other than **ResponseXml**, you need to make related changes in the involved context configurations and invoicing feature setups' applicability rules and variables.

## Set up registration numbers

If these registration types and categories already exist and are configured accordingly, skip this procedure.

### <a id="SIREN"></a>Set up SIREN number

> [!NOTE]
> When you generate the output files for electronic invoices, the system uses registration numbers from the **Enterprise ID (COID)** category as *Système d'identification du répertoire des entreprises* numbers (**SIREN**). If the **Enterprise ID (COID)** registration category already exists and is assigned to a registration type, skip this procedure.

To configure the **SIREN** registration number, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration** > **Global address book** > **Registration types** > **Registration types**.
1. Create a registration type.
1. In the **Country/region** field, select **FRA - France**.
1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration categories**.
1. Create a registration category.
1. In the **Registration types** field, select the registration type that you created in step 2.
1. In the **Registration categories** field, select **Enterprise ID (COID)**.

### <a id="SIRET"></a>Set up SIRET number

To configure the *Système d’identification du répertoire des établissements* (**SIRET**) registration number, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** > **Global address book** > **Registration types** > **Registration types**.
1. Create a registration type.
1. In the **Country/region** field, select **FRA - France**.
1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration categories**.
1. Create a registration category.
1. In the **Registration types** field, select the registration type that you created in step 2.
1. In the **Registration categories** field, select **SIRET**.

### <a id="VAT"></a>Set up VAT number

Optionally, to configure the tax-exempt number, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** > **Global address book** > **Registration types** > **Registration types**.
1. Create a registration type.
1. In the **Country/region** field, select **FRA - France**.
1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration categories**.
1. Create a registration category.
1. In the **Registration types** field, select the registration type that you created in step 2.
1. In the **Registration categories** field, select **VAT ID**.

### <a id="Branch"></a>Set up Branch ID

If you configure Branch IDs, the system uses them as electronic addresses for routing documents. To configure the Branch ID, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** > **Global address book** > **Registration types** > **Registration types**.
1. Create a registration type.
1. In the **Country/region** field, select **FRA - France**.
1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration categories**.
1. Create a registration category.
1. In the **Registration types** field, select the registration type that you created in step 2.
1. In the **Registration categories** field, select **Branch ID**.

> [!NOTE]
> If you can't use branches as electronic addresses, you can alternatively configure electronic addresses through electronic document properties as described in the [Configure electronic addresses](#ElAddr) chapter. In this case, only one electronic address per invoice party is supported.

### Additional configuration of registration numbers

To support scenarios when companies have multiple subsidiaries with their own registration numbers such as SIREN, SIRET, VAT ID, and Branch ID as an electronic address, you need to activate and configure the **Establishments** functionality. For more information, see the following articles:

- [Invoice party applicability rules for registration categories](../../../fin-ops-core/dev-itpro/organization-administration/invoice-party-applicability-rules.md)
- [Establishments in France](emea-fra-establishments-for-france.md)
- [Registration numbers setup for France](emea-fra-registration-numbers-setup-for-france.md)

> [!NOTE]
> In the current implementation of Electronic invoicing, multiple registration numbers are supported only for Buyers.

## Set up address structure

Set up the postal address structure.

1. Go to **Organization administration** > **Global address book** > **Addresses** > **Address setup**.
1. Ensure that at least the **Country code** element is configured.

## Configure legal entity data

### Enter the address

Add the primary address.

1. Go to **Organization administration** > **Organizations** > **Legal entities**, and select a legal entity.
1. On the **Addresses** FastTab, add the primary address for the legal entity.

### Seller identification

Add the registration numbers.

1. Go to **Organization administration** > **Organizations** > **Legal entities**.
1. On the Action Pane, select **Registration IDs**.
1. On the **Registration ID** FastTab, select **Add**, set **Registration type** to the [SIREN](#SIREN) type you created earlier, and enter the SIREN number in the **Registration number** column.
1. Select **Add**, set **Registration type** to the [SIRET](#SIRET) type you created earlier, and enter the SIRET number in the **Registration number** column.
1. Define the Tax exempt ([VAT](#VAT)) number whatever way is used in your company.

> [!NOTE]
> If you don't define the registration number with the **VAT** registration category, the value from **Organization administration** > **Organizations** > **Legal entities** > **Foreign trade and statistics** > **INTRASTAT** > **VAT exempt number export** is used.

## Configure customer data

### Enter the address

To enter the address, follow these steps:

1. Go to **Accounts receivable** > **Customers** > **All customers**.
1. Select a customer.
1. On the **Addresses** FastTab, add a valid address for the selected customer.

### Buyer identification

To enter the registration numbers, follow these steps:

1. Go to **Accounts receivable** > **Customers** > **All customers**.
1. On the Action Pane, on the **Customer** tab, in the **Registration** group, select **Registration IDs**.
1. Select the **Address** that the registration numbers belong to. Make sure that the **Purpose** of the selected address contains the **Delivery** and **Invoice** values.
1. On the **Registration ID** FastTab, select **Add** to create a registration ID.
1. In the **Registration type** field, select the [SIREN](#SIREN) registration type that you created earlier.
1. Select **Add**, and in the **Registration type** field, select the [SIRET](#SIRET) registration type that you created earlier.
1. Select **Add** to create another registration ID, if necessary.
1. In the **Registration number** field, enter a valid [Branch ID](#Branch) for the specific address of the selected customer.
1. Select **Add** to create another registration ID, if necessary.
1. In the **Registration number** field, enter a valid [VAT](#VAT) number for the selected customer.

> [!NOTE]
> If you don't define the registration number with the **VAT** registration category, the value from **Accounts receivable** > **Customers** > **All customers** > **Invoice and delivery** > **SALES TAX** > **Tax exempt number** is used.

## <a id="ElAddr"></a>Configure electronic addresses

> [!NOTE]
> Follow the steps in this section only if you don't use registration numbers of the **Branch ID** category. Electronic addresses that you configure through electronic document properties take priority and overwrite registration numbers of the **Branch ID** category when generating e-invoices XML files.

Follow these steps to configure electronic addresses for sellers or buyers that you use as **EndpointIDs** for document routing.

### Configure electronic document properties

Set up electronic document properties.

1. Go to **Accounts receivable** > **Setup** > **Electronic document property types**, and select **New**.
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

   :::image type="content" source="emea-fra-e-invoices-addresses.jpg" alt-text="Screenshot of the property type added on the Electronic document property types page.":::

### Enter the seller electronic address

To enter the Seller schema code, follow these steps:

1. Go to **Organization administration** > **Organizations** > **Legal entities** and select a legal entity.
1. Select **Electronic document properties** from the Action Pane.
1. In the **Value** column, enter the required seller electronic address.

### Enter the buyer electronic address

To enter the Buyer schema codes, follow these steps:

1. Go to **Accounts receivable** > **Customers** > **All customers**.
1. Select a specific customer in the list. On the Action Pane, on the **Customer** tab, in the **Properties** group, select **Electronic document properties**.
1. In the **Value** column, enter the required buyer electronic address.

> [!NOTE]
> For both Seller and Buyer identification, the system uses the electronic address you define as the **EndpointID** value with the **schemeID** attribute set to **0225** (FRCTC ELECTRONIC ADDRESS) by default, according to the [Electronic Address Scheme (EAS)](https://docs.peppol.eu/poacc/billing/3.0/codelist/eas/).

If you don't define the electronic addresses, the system uses the following Endpoint determination algorithm:

- The system uses the **SIRET** number with the **0009** value as the *schemeID* attribute.
- If the system doesn't find a **SIRET** number, it uses the **SIREN** number with the **0002** value as the *schemeID* attribute.
- If the system doesn't find a **SIREN** number, it uses the Global Location Number (GLN), also known as the European article numbering (EAN) number, with the **0088** value as the *schemeID* attribute.

  > [!NOTE]
  > The system assumes that the dedicated registration number of the **EAN** registration category is already defined.
- If the system doesn't find an **EAN** number, it uses the VAT number with the **9957** value as the *schemeID* attribute.

## Configure mandatory notes

According to French requirements, each individual electronic invoice must contain three mandatory **Note** elements in the header with the **following** predefined prefixes:

- **#PMD#** *the text of the first note*
- **#PMT#** *the text of the second note*
- **#AAB#** *the text of the third note*

### Configure mandatory notes for Sales and Free text invoices

To automate the creation of notes, see [Advanced notes management](../italy/emea-ita-exil-structured-notes.md).
Configure at least three external header-level notes with the mandatory prefixes for the required documents, for all or selected customers. When you configure these notes, the system automatically adds them to the applicable documents upon creation.

:::image type="content" source="emea-fra-advanced-notes.jpg" alt-text="Screenshot of the advance notes configuration.":::

### Configure mandatory notes for Project invoices

For Project invoices, the functionality of Advanced notes doesn't apply. Follow the steps described in this section to configure the mandatory notes for Project invoices.

1. Go to **Accounts receivable** > **Setup** > **Electronic document property types**, and select **New**.
1. In the **Type** field, enter the required notes codes at least, **#PMD#**, **#PMT#**, and **#AAB#**.
1. In the **Group description** field, enter **FReInvNotes**. Enter the value exactly as shown.
1. Select **Applicability** to add an applicable table.
1. On the **Electronic document property type applicability setup** page, in the **Table name** field, select **Legal entities**, **Customers**, and **Project invoices**.
1. Save your changes and return to the **Electronic document property types** page.
1. Save your changes, and close the page.

:::image type="content" source="e-invoice-fra-properties.jpg" alt-text="Screenshot of the properties types configuration.":::

#### Enter the Legal Entity mandatory notes

To enter the Legal Entity mandatory notes, follow these steps.

1. Go to **Organization administration** > **Organizations** > **Legal entities** and select a legal entity.
1. Select **Electronic document properties** from the Action Pane.
1. In the **Value** column, enter the required note text for each of the mandatory notes.

#### Enter the Customers mandatory notes

To enter the Customers mandatory notes, follow these steps.

1. Go to **Accounts receivable** > **Customers** > **All customers**.
1. Select a specific customer in the list. On the Action Pane, on the **Customer** tab, in the **Properties** group, select **Electronic document properties**.
1. In the **Value** column, enter the required note text for each of the mandatory notes.

#### Enter the Invoices mandatory notes

To enter the Invoices mandatory notes, follow these steps.

1. Go to **Project management and accounting** > **Project invoices** > **Project invoices**.
1. Select a specific project invoice in the list, and then, on the Action Pane, on the **Project invoice** tab, in the **Properties** group, select **Electronic document properties**.
1. In the **Value** column, enter the required note text for each of the mandatory notes.

> [!NOTE]
> Invoice-level notes have higher priority than Customer-level notes and Legal Entity-level notes. Use them if you need to enter specific notes for a particular invoice.  Customer-level notes have higher priority than Legal Entity-level notes. Use them when you need to have similar notes for all invoices issued to a specific customer. Use Legal Entity-level notes for the same notes for all invoices issued from the Legal Entity for all customers.

## Set up units of measure

Set up units of measure.

1. Go to **Organization administration** > **Setup** > **Units** > **Units**.
1. Select a unit ID, and then select **External codes**.
1. On **External codes** page, in **Overview**, enter the unit ID in the **Code** column.
1. In the **Standard code** column, select the checkbox.
1. In the **Value** section, enter the external code from the [UNECE Recommendation 20 code list](https://docs.peppol.eu/poacc/billing/3.0/codelist/UNECERec20/) in the **Value** field.

   > [!NOTE]
   > If no specific unit of measure applies, the system uses the default value **EA**.

## Configure sales tax codes

1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax codes**.
1. Select a sales tax code. On the Action Pane, on the **Sales tax code** tab, in the **Sales tax code** group, select **External codes**.
1. In the **Overview** section, create a line for the selected unit. Enter the sales tax code from step 2 in the **External code** field.
1. In the **Value** section, enter an external code according to the [Duty or tax or fee category code (Subset of UNCL5305)](https://docs.peppol.eu/poacc/billing/3.0/codelist/UNCL5305/) in the **Value** field.
1. Go to **Tax** \> **Setup** \> **Sales tax** \> **Sales tax exempt codes**.
1. Define exempt codes that you use for nontaxable, zero-rated, or exempted operations.

> [!NOTE]
> The exempt codes can have any value that your company uses internally, but the **Description** field must contain the standardized tax exemption code according to the official categorization introduced in France, such as *VATEX-FR-298SEXDECIESA*. The value from the **Description** field is used as **Tax Exemption Reason** when generating the output XML files for electronic invoices.

## Issue electronic invoices

> [!IMPORTANT]
> **Electronic invoicing scope**
>
>The following types of documents are *excluded* from **E-Invoicing** individual submissions and are *included* in the scope of **E-Reporting**.
>
>- **Non-domestic Business-to-Business (B2B) invoices** - the invoices issued to buyers whose **Delivery** address is outside France.
>- **All Business-to-Consumer (B2C) invoices** - the invoices issued for the customers that don't have the **SIREN** registration number defined.

After you complete the required configuration steps, generate and submit electronic invoices for posted invoices. The submission process consists of three major steps.

- **Submission of e-invoices to Edicom** - at this stage, the system generates the XMLs of e-invoices and submits them to Edicom.
- **Inquiring statuses of submitted e-invoices** - at this stage, the system inquires the initial status of submitted e-invoices from Edicom. The submission status can be **Failed** if the submitted invoice is **Rejected** by Edicom due to various reasons, or **Pending update actions execution** if the submitted invoice is successfully validated by Edicom and the system is ready for further processing.
- **Update statuses of submitted e-invoices** - at this stage, Dynamics 365 and Edicom can intercommunicate exchanging different e-invoices statuses until the concluding status is reached or due to preconfigured timeout.

:::image type="content" source="e-invoice-lifecycle.jpg" alt-text="Screenshot of outgoing electronic documents lifecycle.":::

### Submission of e-invoices to Edicom

To start the electronic invoice submission process, go to **Organization administration** > **Periodic** > **Electronic documents** > **Submit electronic documents**. For more information, see [Submit electronic documents](../global/e-invoicing-submit-electronic-documents.md).

> [!NOTE]
> During this stage, the system performs the first two actions from the **French electronic invoice (FR)** feature for the related invoice: it generates the XML file of the electronic invoice in the required format and, if the first action is successful, submits the generated XML file to Edicom.

Check the submission results at **Organization administration** > **Periodic** > **Electronic documents** > **Electronic document submission log**. For more information, see [Work with Electronic document submission log](../global/e-invoicing-submission-log.md). The documents can have either **Failed** submission status, if there were either Electronic Reporting run-time errors or Edicom portal is unreachable, or **Pending service response** submission status, when ready for further processing.

The following types of invoices are processed during the submission.

- Invoices based on Sales orders - electronic invoices of **380** type are generated.
- Credit notes based on Sales orders - electronic invoices of **381** type are generated.
- Free text invoices - electronic invoices of **380** type are generated.
- Free text credit notes - electronic invoices of **381** type are generated.
- Project invoices - electronic invoices of **380** type are generated.
- Project credit notes - electronic invoices of **381** type are generated.
- Customer prepayment invoices created using [Customer prepayment invoices](../../accounts-receivable/customer-prepayment-invoice.md) functionality - electronic invoices of **386** type are generated.

### Inquiring statuses of submitted e-invoices

To check the initial status of the submitted electronic invoices from Edicom, follow these steps:

1. Go to **Organization administration** > **Periodic** > **Electronic documents** > **Run submission process in export channels**.
1. In the **Channel** field, select the **EdiStatus** export channel or the channel you [created](#ExChannel) for invoices, and then select **OK**.

Check the results at **Organization administration** > **Periodic** > **Electronic documents** > **Electronic document submission log**. The documents can be in either **Failed** status if Edicom rejects them due to syntactical, or other validation errors, or **Pending update actions execution** if Edicom successfully validates them and they're ready for further processing.

> [!NOTE]
> You can also view submitted electronic invoices in the [Ediwin](https://ediwin.edicomgroup.com/) portal in the **Outbound** folder and its subfolders, where you can monitor further processing.

### Update statuses of submitted e-invoices

As part of the document lifecycle, some buyer responses for successfully submitted invoices might come later. These responses can affect the statuses of submitted documents. To keep document statuses up to date, run the following procedure.

1. Go to **Organization administration** > **Periodic** > **Electronic documents** > **Electronic document submission log**.
1. Select any document and run **Functions** > **Execute update actions** from the menu.
1. The procedure runs for all documents in the **Pending update actions execution** submission status. If necessary, define additional filtering, and then select **OK**.

> [!NOTE]
> You can also configure periodic running of this procedure in the background to avoid manual intervention.

You can run the procedure multiple times to retrieve various lifecycle document statuses from Edicom until it reaches a **termination** status code or a predefined **timeout**.

If the procedure reaches any termination document status code, it updates the related document's submission status to **Completed** - this status concludes the lifecycle of the document. All other, nontermination, document statuses are for information only and keep the **Pending update actions execution** submission status intact.

:::image type="content" source="e-invoice-fra-update-status.jpg" alt-text="Screenshot of submission log statuses.":::

You can configure the status codes for successful or unsuccessful termination and the timeout period in days in the related feature setup parameters.
To configure the parameters, follow these steps.

1. In the **Globalization Studio** workspace, the **Electronic invoicing** tile, select the **French electronic invoice (FR)** globalization feature.
1. On the **Versions** tab, check that the **Draft** version is selected. Create a new draft version of the feature if necessary.
1. On the **Setups** tab, select the feature setup for a required document.
1. In the **Processing pipeline** section, select the last, **Terminate pipeline with optional condition and date** action.
1. In the **Parameters** grid, select the **Success status values** parameter. In the **Value** column, enter status codes separated by comma. These statuses are used for the pipeline processing termination when reached. To learn more about the available statuses, see the **[List of lifecycle status codes](#StatusCodes)** section of the **Appendix** chapter.
1. Select the **Number of days** parameter. In the **Value** column, enter the number of days after which the pipeline terminates regardless of the processing document status.
1. Complete and deploy the feature.

:::image type="content" source="e-invoice-fra-termination.jpg" alt-text="Screenshot of termination parameters configuration.":::

## Receive incoming electronic invoices

Set more parameters in Microsoft Dynamics 365 Finance to import incoming invoices.

Configure these master data types to match incoming electronic invoices:

- vendors
- products
- units

Follow the steps in [Import vendor electronic invoices](../europe/emea-peppol-import.md), starting at [Configure vendor data](../europe/emea-peppol-import.md#configure-vendor-data).

### Receive electronic invoices

After you complete the configuration, receive incoming electronic invoices in the French-specific UBL-based format.

> [!NOTE]
> Review incoming electronic invoices in the **Inbound** folder and its subfolders in your [Ediwin](https://ediwin.edicomgroup.com/) portal.

Receive electronic invoices:

1. Go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Receive electronic documents**.
1. Select **OK**, and then close the page.

View receipt logs for processed electronic invoices: go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Electronic document receipt log**.

View successfully received invoices: go to **Accounts payable** \> **Invoices** \> **Pending vendor invoices**.

## Send electronic invoices responses

Some business scenarios assume sending responses for either incoming or outgoing electronic invoices. The responses result in assigning mandatory document statuses that conclude electronic invoices lifecycle.

### Send responses for Customer and Project invoices

Current implementation allows sending only *payment reception confirmation* responses to your Buyers. To enter responses, follow these steps.

1. Go to **Accounts receivable** > **Inquires and reports** > **Invoices** > **Invoice journal** for Sales and Free text invoices or to **Project management and accounting** > **Project invoices** > **Project invoices**.
1. Select a specific invoice in the list, and then, on the Action Pane, on the **Invoice** / **Project invoice** tab, in the **Document** group, select **Add response**.
1. In the **Response code** field, select the required value from the list. The **Amount paid** field is automatically populated based on payments settled against this invoice.
1. Select **OK**, and then close the page.
1. Go to **Organization administration** > **Periodic** > **Electronic documents** > **Submit electronic documents**.
1. In the **Record to include** section, make sure that the required **Customer invoice response** records are selected.
1. Select **OK** to start the responses submission process.
   > [!NOTE]
   > At this stage, the **French electronic invoice status (FR)** globalization feature, **Send AR response** feature setup is being run for responses processing.
1. Go to **Organization administration** > **Periodic** > **Electronic documents** > **Run submission process in export channels**.
1. In the **Channel** field, select the **InvStatus** export channel or the channel you [created](#ExChannel) for responses, and then select **OK**.
1. Check the responses submission results at **Organization administration** > **Periodic** > **Electronic documents** > **Electronic document submission log**, select **Customer invoice response** document type.  

### Send responses for pending vendor invoices

The current implementation only supports sending *refusal* responses to your sellers. To enter responses, follow these steps:

1. Go to **Accounts payable** > **Invoices** > **Pending vendor invoice**.
1. Select a specific invoice in the list. On the Action Pane, on the **Vendor invoice** tab, in the **Actions** group, select **Add response**.
1. In the **Response code** field, select the required value from the list.
1. In the **Reason code** field, select the required value from the list.
1. Select **OK**, and then close the page.
1. Go to **Organization administration** > **Periodic** > **Electronic documents** > **Submit electronic documents**.
1. In the **Record to include** section, make sure that the required **Pending vendor invoice response** records are selected.
1. Select **OK** to start the responses submission process.
   > [!NOTE]
   > At this stage, the **French electronic invoice status (FR)** globalization feature, **Send AP response** feature setup runs for responses processing.
1. Go to **Organization administration** > **Periodic** > **Electronic documents** > **Run submission process in export channels**.
1. In the **Channel** field, select the **InvStatus** export channel or the channel you [created](#ExChannel) for responses, and then select **OK**.
1. Check the responses submission results at **Organization administration** > **Periodic** > **Electronic documents** > **Electronic document submission log**. Select **Pending vendor invoice response** document type.  

## Appendix

### <a id="StatusCodes"></a>List of lifecycle status codes

The list of mandatory status codes supported in electronic invoicing for Microsoft Dynamics 365 Finance.

| Code | Status | Requirement | Description |
|------------|------------------|-----------------------------------|---------------------------------|
| 200 | Deposited | **Mandatory** | An e-invoice is transmitted to the PA, which certifies that the invoice is validated and compliant. |
| 210 | Refused | **Mandatory** | The recipient refuses the invoice. |
| 212 | Payment received | **Mandatory** | The invoice is fully paid by the recipient. |
| 213 | Rejected | **Mandatory** | The invoice is rejected by either issuer's or receiver's PA. |

> [!NOTE]
> The electronic invoicing functionality in Microsoft Dynamics 365 Finance isn't limited to the statuses listed in the preceding table. The system can receive any valid status from your buyers' PAs through Edicom. At the same time, the current implementation supports sending only refusal responses to your sellers and payment reception confirmation responses to your buyers.
> You can find the full list of statuses in the [Specifications and standards for electronic invoicing](https://www.impots.gouv.fr/specifications-externes-b2b).

### <a id="ERconfigs"></a>List of Electronic Reporting configurations

- Invoice model
  - Invoice model mapping
  - Invoice model mapping (FR)
  - UBL Sales e-invoice (FR)
  - UBL Sales e-credit note (FR)
  - UBL Project e-invoice (FR)
  - UBL Project e-credit note (FR)
  - Vendor invoice import
  - Vendor invoice import Edicom (FR)
  - Vendor invoice Mapping to destination
  - Invoice status model mapping
  - Edicom invoice status format
  - Edicom invoice status payment confirmation format
  - Edicom invoice status reject format
- Customer invoice context model
  - Import invoice context model
  - Import invoice context model (FR)
  - Import response context
  - AP response context
  - AR response context
- Response message model
  - Response message model mapping to destination
  - Response message model mapping to destination (FR)
  - Edicom life cycle status format (FR)
  - Edicom Response status parsing format(FR)
  - Edicom Response Invoice Status (FR)
  - Edicom Response Processing (FR)
  - Edicom response error log import
  - Edicom Response message status format

## More information

- [Electronic invoicing coverage by country and region](../global/e-invoicing-coverage.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
