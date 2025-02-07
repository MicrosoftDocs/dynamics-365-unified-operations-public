---
title: Electronic invoicing for Belgium
description: Learn how to get started with Electronic invoicing for Belgium in Microsoft Dynamics 365 Finance.
author: ilikond
ms.author: ikondratenko
ms.topic: how-to
ms.date: 05/05/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: Belgium
ms.search.validFrom: 2025-05-05
ms.dyn365.ops.version: AX 10.0.45
---

# Electronic invoicing for Belgium

[!include [banner](../../includes/banner.md)]

This article provides information to help you get started with Electronic invoicing for Belgium. It includes information about how to configure the system so that you can generate, submit, and receive electronic invoices in the [Pan-European Public Procurement Online (PEPPOL)](https://docs.peppol.eu/poacc/billing/3.0/) format in Microsoft Dynamics 365 Finance using the last-mile connector.

![Screenshot that shows e-invoices flow for Belgium.](../media/emea-bel-einoices-flow.jpg)

> [!NOTE]
> The electronic invoicing approach that this article describes is implemented by using an invoicing service that's applicable only to cloud deployments of Microsoft Dynamics 365 Finance.

## Prerequisites

Before you begin the procedures in this article, the following prerequisites must be met:

- The company must be a registered tax payer in Belgium.
- The company must have a signed agreement with the provider of electronic document delivery service that secures electronic document interchange in the PEPPOL format.
- Among the registered profile IDs, the company should have the following profile that Microsoft Dynamics 365 Finance uses for electronic document interchange:

    - **urn:fdc:peppol.eu:2017:poacc:billing:01:1.0** – This profile is used to interchange documents in PEPPOL format.

- The company must obtain, from the service provider, the required credentials to enable integration of the Electronic Invoicing service with the [Electronic Invoicing service independent software vendor (ISV) last-mile connector](../global/e-invoicing-isv-connector.md).

   > [!NOTE]
   > Current implementation assumes [Edicom](https://edicomgroup.com/electronic-invoicing) as the Electronic Invoicing ISV last-mile connection service provider. For more information refer to: [Edicom integration with Microsoft Dynamics 365](https://edicomgroup.com/edicom-microsoft?365).

- Become familiar with Electronic invoicing as it's described in [Electronic Invoicing service overview](../global/gs-e-invoicing-service-overview.md) and [Electronic invoicing components](../global/gs-e-invoicing-administration-integration-components.md).
- Do the common part of Electronic Invoicing service configuration as described in [Electronic invoicing configuration](../global/gs-e-invoicing-set-up-overview.md).

## Create the Azure Key Vault configuration

Create an Azure key vault to store the required secrets that are issued for your company. For more information, see [Configure Azure resources for Electronic invoicing](../global/gs-e-invoicing-set-up-azure-resources.md).

Add the following required elements in the key vault:

- The secret for the **token** that grants authorization to access the Edicom services. Must be preliminary obtained from Edicom as was described in the prerequisites.

## Configure electronic invoicing Key Vault parameters

To configure electronic invoicing Key Vault parameters, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
1. On the **Electronic invoicing** tab, in the **Key Vault settings** section, in the **Key Vault** field, select the reference to the key vault that you created in the previous section of this article.
1. In the **SAS token secret** field, select the name of the storage account secret URL that must be used to authenticate access to the storage account.
1. Select **Key Vault parameters**.
1. On the **Key Vault parameters** page, in the **Certificates** section, select **Add** to create new elements of the appropriate type for each secret that is described in the previous section.

    - <a id="Tok"></a>The **token** element of the **Secret** type.

> [!NOTE]
> The values in the **Name** column should match the names of the secrets that are described in the previous section.

## Import the electronic invoicing feature

1. Go to **Globalization Studio**, and select the **Electronic invoicing** tile. Then import the latest version of the **Belgian electronic invoice (BE)** Globalization feature as described in [Import features from the repository](../global/gs-e-invoicing-import-feature-global-repository.md).
1. In the **Electronic reporting** workspace, on the **Reporting configurations** tile, make sure that the following Electronic reporting configurations are successfully imported as result of the **Belgian electronic invoice (BE)** Globalization feature import.

    - **Invoice model**
    - **Invoice model mapping**
    - **PEPPOL Sales e-invoice** 
    - **PEPPOL Sales e-credit note**
    - **PEPPOL Project e-invoice**
    - **PEPPOL Project e-credit note**
    - **Customer invoice context model**
    - **Response message model**
    - **Edicom Response Processing**
    - **Error log import Json**

    > [!NOTE]
    > If due to some reason the mentioned Electronic reporting configurations were not imported then import them manually as described in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

1. In the **Electronic reporting** workspace, on the **Reporting configurations** tile, additionally import the latest versions of the following Electronic reporting configurations required for receiving incoming vendor invoices.

    - **Vendor invoice import**
    - **Vendor invoice Mapping to destination**
    - **Import invoice context model**
    
## ===========================

## Configure the electronic invoicing feature

Some of the parameters from the **Polish electronic invoice (PL)** electronic invoicing feature are published with default values. Before you deploy the electronic invoicing feature to the service, review the default values, and update them as required, so that they better reflect your business operations.

To review and update the **Polish electronic invoice (PL)** electronic invoicing feature configuration, follow these steps.

1. Go to **Globalization Studio**, and select the **Electronic invoicing** tile. Then import the latest version of the **Polish electronic invoice (PL)** Globalization feature as described in [Import features from the repository](../global/gs-e-invoicing-import-feature-global-repository.md).
1. Create a copy of the imported Globalization feature, and select your configuration provider for it, as described in [Create a Globalization feature](../global/gs-e-invoicing-create-new-globalization-feature.md).
1. On the **Versions** tab, verify that the **Draft** version is selected.
1. On the **Feature parameters** tab, specify values for the following connection and integration parameters. These parameters are required for interoperation with Polish KSEF services.

    - **EnvironmentName** – select the type of the environment, depending on the implementation stage: *Test*, *Demo*, or *Prod*.
    - **PolishClientID** – select the name of the [client ID](#ClID) that you previously created.
    - **PolishImportDataChannel** – enter the [name of the data channel](#ImpChn) that you previously defined.
    - **PolishPublicKey** – select the name of the [public key](#PK) that you previously created.
    - **PolishToken** – select the name of the [token](#Tok) that you previously created.

    ![Screenshot that shows the Feature parameters tab configured for the Globalization feature for Poland.](e-inv-pol-feature-parameters.jpg)

1. On the **Setups** tab, in the grid, select the **Import vendor invoices derived** feature setup and select **Edit**.
1. On the **Applicability rules** tab, in the **Set up applicability rule** section, in the **Value** field, enter the [name of the data channel](#ImpChn) that you previously defined.
1. <a id="OutputFile"></a>On the **Variables** tab, make a note of the **OutputFile** name, because you will use it in later configuration steps.
1. Select **Save**, and close the page.
1. The copy of the feature is always created as a **Draft** version. Complete and deploy the feature as described in [Complete and deploy a Globalization feature](../global/gs-e-invoicing-complete-publish-deploy-globalization-feature.md).

## Configure electronic document parameters

1. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
1. On the **Electronic document** tab, add records for the **Customer Invoice journal**, **Project invoice**, and **Advance invoice** table names.
1. For each table name, set the **Document context** and **Electronic document model mapping** fields in accordance with [Set up electronic invoicing parameters](../global/gs-e-invoicing-set-up-parameters.md#set-up-electronic-document-parameters).

    :::image type="content" source="e-inv-pol-doc-parameters.jpg" alt-text="Screenshot of the setup on the Electronic document tab of the Electronic document parameters page."::: 

    > [!NOTE]
    > If you have created the [derived analogues](#Context) of the mentioned above Electronic Reporting configurations then use it instead of standard ones.

1. For the **Customer Invoice journal** table name, select **Response types**.
1. Select **New** to create a response type, and enter the following values:

    - In the **Response type** field, enter **ResponseData** (the default value).
    - In the **Submission status** field, select **Pending**.
    - In the **Model mapping** field, select **KSeF response data import format (PL)**.

    :::image type="content" source="e-inv-pol-response-type.jpg" alt-text="Screenshot of the setup of the new response type on the Electronic document tab of the Electronic document parameters page.":::

    > [!NOTE]
    > **ResponseData** is the default name of the response type. If you must change it, make sure that the new name matches the name that was defined for the related variable of the **To client** type in the corresponding feature setups. To validate the variable's value, go to **Globalization Studio**, and select the **Electronic invoicing** tile. On the **Electronic invoicing features** page, verify that the **Polish electronic invoice (PL)** electronic invoicing feature is selected. On the **Setups** tab, in the grid, select the **Submit customer invoice derived** feature setup. Then select **Edit** or **View**, depending on the status of the feature version.

1. Repeat steps 4 and 5 for the **Project invoice** and **Advance invoice** table names.
1. On the **Integration channels** tab, in the **Channels** section, in the **Channel** field, enter the [name of the data channel](#ImpChn) that you previously defined.
1. In the **Company** field, select a required legal entity. In the **Document context** field, select the [context configuration](#Context) that you previously created.
1. In the **Import sources** section, in the **Name** field, enter the **OutputFile** name that is [actually used](#OutputFile).
1. In the **Data entity name** field, select **Vendor invoice header**. In the **Model mapping** field, reference the **Vendor invoice import (PL)** configuration.

    :::image type="content" source="e-inv-pol-import-output.jpg" alt-text="Screenshot of the import channel configuration in Electronic document parameters.":::

1. Select **Save**, and close the page.

## =======================================

## Configure the integration channels

1. In the **Electronic reporting** workspace, on the **Reporting configurations** tile, select the **Customer invoice context model** configuration.
1. <a id="Context"></a>Select **Create configuration**, and then, in the dropdown dialog box, select **Derive from Name: Customer invoice context model, Microsoft** to create a derived configuration.
1. Open the derived configuration for editing in the designer, and then select **Map model to datasource**.
1. Open the **DataChannel** definition for editing in the designer.
1. In the **Data sources** tree, expand the **$Context\_Channel** container.
1. <a id="ImpChn"></a>In the **Value** field, select **Edit**, and then enter the name of the data channel. Make a note of the value, because you will use it in later configuration steps.

    :::image type="content" source="e-inv-pol-import-config.jpg" alt-text="Screenshot of the output channel configuration in Electronic reporting.":::

1. Save your changes and complete the derived configuration.

## Use the country-specific configuration for the Danish electronic invoice (DK) feature

Some parameters for the **Danish electronic invoice (DK)** electronic invoicing feature have default values. Before you deploy the feature to the service environment, review the default values, and update them as required, so that they better reflect your business operations.

To review and update the parameters for the **Danish electronic invoice (DK)** electronic invoicing feature, follow these steps.

1. Import the latest version of the **Danish electronic invoice (DK)** Globalization feature, **version 4** or later. Learn more in [Import features from the repository](../global/gs-e-invoicing-import-feature-global-repository.md).
1. Create a copy of the imported Globalization feature, and select your configuration provider for it. Learn more in [Create Globalization features](../global/gs-e-invoicing-create-new-globalization-feature.md).
1. On the **Versions** tab, verify that **Draft** is selected.
1. On the **Setups** tab, in the grid, select the **Sales invoice OIOUBL** feature setup, and then select **Edit**.
1. On the **Processing pipeline** tab, in the **Processing pipeline** section, select **Integrate with Edicom**.
1. In the **Parameters** section, select **Domain**, and then enter the service ID number that you obtained.
1. Select **Application**, and then enter the same service ID number.
1. Select **Destination**, and then enter the service ID number concatenated with the string "\_EDIWIN." For example, if the service ID number is **123456**, enter **123456\_EDIWIN**.
1. Select **Group**, and then enter the group code that you obtained.
1. Select **Auth token**, and then select the name of the secret that you created for the token.
1. Select **Save**, and close the page.
1. Repeat steps 4 through 11 for each of the following feature setups if your business process assumes the involvement of the related types of documents:

    - Sales credit note OIOUBL
    - Project invoice OIOUBL
    - Project credit note OIOUBL
    - Sales invoice PEPPOL
    - Sales credit note PEPPOL
    - Project invoice PEPPOL
    - Project credit PEPPOL

1. On the **Setups** tab, in the grid, select the **Get status** feature setup, and then select **Edit**.
1. On the **Export channel** tab, in the **Parameters** section, select **Auth token**, and then select the name of the secret that you created for the token.
1. Select **Domain**, and then enter the service ID number that you obtained.
1. Select **Application**, and then enter the same service ID number.
1. Select **Group**, and then enter the group code that you obtained.
1. Select **Data channel**, and then enter the name of the [integration channel](#ExChannel) that is configured on the **Electronic document parameters** page in Finance.
1. Select **Save**, and close the page.

## Finance configuration

Some additional parameters must be configured directly in Finance.

To configure the additional parameters directly in Finance, follow these steps.

1. In the **Feature management** workspace, make sure that the **Export channels for electronic invoicing integration** feature is enabled. Learn more in [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
1. Make sure that the country/region-specific **Document context** and **Electronic document model mapping** Electronic reporting (ER) configurations that are required for Denmark are imported. Learn more in [Set up Electronic document parameters](../global/gs-e-invoicing-set-up-parameters.md#set-up-electronic-document-parameters).
1. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
1. In the **Electronic document** section, add records for the **Customer Invoice journal** and **Project invoice** table names.
1. For each table name, set the **Document context** and **Electronic document model mapping** fields in accordance with step 1.
1. <a id="ExChannel"></a>In the **Integration channels** section, add a record for the channel that is used for electronic invoice submission in batch mode.
1. In the **Channel** column, enter **EdiStatus**. This channel name is used by default, but you can use a different channel name as you require. In this case, you must enter the same name in the value of the **$Context\_Channel** variable in the **DataChannel** definition in the **Customer invoice context model** ER configuration. You must also enter it in the parameters and applicability rules of the related feature setup.
1. In the **Company** column, select a required legal entity code.
1. In the **Document context** column, refer to the **Customer invoice context model** configuration by using the **Data channel context** definition.
1. In the **Channel type** column, select **Export**.
1. Save your changes, and close the page.

## Finance business data configuration

Follow the configuration steps in [Customer electronic invoices in Denmark](../norway/emea-dnk-e-invoices.md). Start from the [Configure parameters](../norway/emea-dnk-e-invoices.md#configure-parameters) section.

### Seller identification

Companies that submit electronic invoices can be identified by their CVR number or their [Global Location Number (GLN)](https://en.gs1.dk/services/gln). The GLN is also known as a European article numbering (EAN) location number.

To identify a company by its CVR number, follow these steps.

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
1. On the **Bank account information** FastTab, in the **Codes** section, in the **Routing number** field, make sure that a valid CVR number is entered for the legal entity.

    The CVR number is entered in the **Invoice\\cac:AccountingSupplierParty\\cac:Party\\cbc:EndpointID** element in the electronic invoice XML file that is generated. It's used as the seller's identification during the submission process.

To identify a company by its GLN, follow these steps.

1. Go to **Organization administration** \> **Global address book** \> **Registration types** \> **Registration types**.
1. Define a new registration type for Denmark that has the name **EAN**. You must enter the name exactly as it appears here.
1. Go to **Organization administration** \> **Organizations** \> **Legal entities**, and select **Registration IDs** on the Action Pane.
1. On the **Registration ID** FastTab, add the **EAN** registration type that you created.
1. In the **Registration number** field, enter a valid GLN.

    The GLN is entered in the **Invoice\\cac:AccountingSupplierParty\\cac:Party\\cbc:EndpointID** element in the electronic invoice XML file that is generated. It's used as the seller's identification during the submission process.

    > [!NOTE]
    > The GLN has higher priority than the CVR number. If both numbers are configured at the same time, the GLN is used.

### Buyer identification

1. Go to **Accounts receivable** \> **Customers** \> **All customers**, and select a customer.
1. On the **Invoice and delivery** FastTab, in the **EAN** field, make sure that a valid GLN is entered for the customer.

    The GLN is entered in the **Invoice\\cac:AccountingCustomerParty\\cac:Party\\cbc:EndpointID** element in the electronic invoice XML file that is generated. It's used as the buyer's identification during the submission process.

    > [!NOTE]
    > If no GLN is defined, the customer's tax exempt number is used.

### <a id="FormatType"></a>Configure the output format type

By default, all outgoing electronic invoices are generated in OIOUBL format for all customers. However, by using configurable electronic document property types, you can configure electronic invoices so that they are generated in PEPPOL format for specific customers.

> [!NOTE]
> Follow the configuration steps in this section only if you must also generate electronic invoices in PEPPOL format. If you generate them only in OIOUBL format, you can skip these steps.

#### Configure electronic document properties

To configure electronic document properties, follow these steps.

1. Go to **Accounts receivable** \> **Setup** \> **Electronic document property types**, and select **New**.
1. In the **Type** field, enter **FormatType**. You must enter the value exactly as it appears here.
1. Select **Applicability** to add an applicable table.
1. On the **Electronic document property type applicability setup** page, in the **Table name** field, select the **Customers** table name.
1. Save your changes, and return to the **Electronic document property types** page.

    ![Screenshot that shows the property type added on the Electronic document property types page.](../media/emea_dk_format_type_setup.jpg)

#### Enter the type of format

To enter the type of format for specific customers, follow these steps.

1. Go to **Accounts receivable** \> **Customers** \> **All customers**.
1. Select a specific customer in the list, and then, on the Action Pane, on the **Customer** tab, in the **Properties** group, select **Electronic document properties**.
1. In the **Value** column, enter **PEPPOL**. You must enter the value exactly as it appears here.

    > [!NOTE]
    > The system generates electronic invoices in PEPPOL format only if you enter the value **PEPPOL** here. If you enter a different value, or no value, electronic invoices are generated in the default OIOUBL format.

    ![Screenshot that shows PEPPOL entered in the Value column on the Electronic document properties page.](../media/emea_dk_format_type.jpg)

## Issue electronic invoices

After you complete all the required configuration steps, you can generate and submit electronic invoices for posted invoices by going to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Submit electronic documents**. Learn more about how to generate electronic invoices in [Submit electronic documents](../global/e-invoicing-submit-electronic-documents.md).

> [!IMPORTANT]
> In current implementations, the standard submission procedure that was described earlier only generates electronic invoices and stores them on the service side. The invoices aren't submitted. Submission of Danish electronic invoices requires that you complete the following additional steps.

To submit the generated electronic invoices in batch mode, follow these steps.

1. Go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Run submission process in export channels**.
1. In the **Channel** field, select the export channel that you [previously created](#ExChannel), and then select **OK**.

You can inquire about the results of the submission by going to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Electronic document submission log**. Learn more in [Work with Electronic document submission log](../global/e-invoicing-submission-log.md).

## Receive incoming electronic invoices

To import incoming invoices in OIOUBL and PEPPOL formats, follow these additional configuration steps for the same version of the **Danish electronic invoice (DK)** electronic invoicing feature that is used for outgoing invoice submission.

1. Import the latest version of the **Danish electronic invoice (DK)** Globalization feature. Learn more in [Import features from the repository](../global/gs-e-invoicing-import-feature-global-repository.md).
1. Create a copy of the imported Globalization feature, and select your configuration provider for it. Learn more in [Create Globalization features](../global/gs-e-invoicing-create-new-globalization-feature.md).
1. On the **Versions** tab, verify that **Draft** is selected.
1. On the **Setups** tab, in the grid, select **Incoming OIOUBL**, and then select **Edit**.
1. <a id="ImportChannel"></a>On the **Import channel** tab, in the **Parameters** section, select the **Data channel** parameter. Then, in the **Value** field, define the name of the data channel. Alternatively, leave the default value unchanged. For the OIOUBL format, the default channel name is **EdiOIOUBL**. For the PEPPOL format, it's **EdiPEPPOL**. In both cases, make a note of the value, because you must use it in later configuration steps.
1. Select the **Service ID** parameter, and then select the name of the secret that contains the service ID number.
1. Select the **Group** parameter, and then select the name of the secret that contains the group code.
1. Select the **Token** parameter, and then select the name of the secret that you created for the token.
1. On the **Applicability rules** tab, in the **Channel** field, make sure that the **Value** column contains the same [import channel](#ImportChannel) name that you defined earlier.
1. Select **Save**, and close the page.
1. If an import in PEPPOL format is also required, repeat steps 4 through 10 for the **Incoming PEPPOL** feature setup.
1. Complete and deploy the configured version of the **Danish electronic invoice (DK)** electronic invoicing feature.

### Finance configuration

Some additional parameters must be configured directly in Finance.

To configure the additional parameters directly in Finance, follow these steps.

1. Make sure that the latest version of the **Vendor invoice import (DK)** ER configuration is imported.

    > [!NOTE]
    > The **Vendor invoice import (DK)** format configuration is used for import invoices in OIOUBL format. It's based on the parent **Vendor invoice import** format configuration that implements invoice import in PEPPOL format. The formats use the **Invoice model** and **Vendor invoice Mapping to destination** configurations. All additional configurations that are required are automatically imported.

1. In the **Electronic reporting** workspace, on the **Reporting configurations** tile, select **Customer invoice context model**.
1. Select **Create configuration**, and then, in the dropdown dialog box, select **Derive from Name: Customer invoice context model, Microsoft** to create a derived configuration.

    > [!NOTE]
    > The derived configuration must differ from the configuration that is used for the invoice *submission* setup.

1. Open the derived configuration to edit it in the designer, and then select **Map model to datasource**.
1. Open the **DataChannel** definition to edit it in the designer.
1. In the **Data sources** tree, expand the **$Context\_Channel** container.
1. In the **Value** field, select **Edit**, and then enter the [import channel](#ImportChannel) name.
1. Save your changes, and complete the derived configuration.
1. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
1. On the **Integration channels** tab, in the **Channels** section, in the **Channel** field, enter the [import channel](#ImportChannel) name that you created earlier.
1. In the **Channels** section, in the **Company** field, select a required legal entity.
1. In the **Document context** field, select the **Customer invoice context model** configuration.
1. In the **Import sources** section, in the **Name** field, enter the same **ResponseXml** name that is used in the variable for **Decoded file** in the import feature setup.

    ![Screenshot that shows the ResponseXml variable in the import feature setup.](../media/isv_connector_responseXML.jpg)

1. In the **Data entity name** field, select **Vendor invoice header**.
1. In the **Model mapping** field, reference the **Vendor invoice import (DK)** configuration.

    ![Screenshot that shows Vendor invoice import (DK) referenced in the Model mapping field.](../media/isv_connector_import_channel.jpg)

1. If import in PEPPOL format is also required, create another import channel, and repeat steps 3 through 15 for it. In step 15, reference the **Vendor invoice import** configuration.
1. Select **Save**, and close the page.

### Configure Finance business data

You must configure the following types of master data to provide a match for incoming electronic invoices:

- Vendors
- Products
- Units

Follow the configuration steps in [Vendor electronic invoice import in Denmark](../denmark/emea-dnk-vend-e-invoice.md). Start from the [Configure vendor data](../denmark/emea-dnk-vend-e-invoice.md#configure-vendor-data) section.

### Receive electronic invoices

To receive electronic invoices, follow these steps.

1. Go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Receive electronic documents**.
1. Select **OK**, and then close the page.

To view the receipt logs for electronic invoices, go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Electronic document receipt log**.

To view successfully received invoices, go to **Accounts payable** \> **Invoices** \> **Pending vendor invoices**.

## Send responses for received electronic invoices

After incoming vendor invoices are successfully received, you can respond to invoice issuers about the decision to accept or reject the received invoices. Rejection responses can be sent for both incoming invoice formats, OIOUBL and PEPPOL. Acceptance responses aren't assumed. If no rejection response is sent during an agreed-on time, the invoices are considered automatically accepted.

For the PEPPOL format, a receipt acknowledgement message can also be sent. This message is a technical confirmation of invoice receipt. The invoices can still be rejected later from a business perspective.

### Configure responses

Responses can be configured by using electronic document property types in the same manner as [format types](#FormatType).

#### Configure electronic document properties

To configure electronic document properties, follow these steps.

1. Go to **Accounts receivable** \> **Setup** \> **Electronic document property types**, and select **New**.
1. In the **Type** field, enter **RejectResponse**. You must enter the value exactly as it appears here.
1. Select **Applicability** to add an applicable table.
1. On the **Electronic document property type applicability setup** page, in the **Table name** field, select the **VendInvoiceInfoTable** table name.
1. Save your changes, and return to the **Electronic document property types** page.
1. Select **New** to create another electronic document property type.
1. In the **Type** field, enter **MessageResponse**. You must enter the value exactly as it appears here.
1. Select **Applicability** to add an applicable table.
1. On the **Electronic document property type applicability setup** page, in the **Table name** field, select the **VendInvoiceInfoTable** table name.
1. Save your changes, and return to the **Electronic document property types** page.
1. Select the existing [FormatType](#FormatType) electronic document property type.
1. Select **Applicability** to add an applicable table.
1. On the **Electronic document property type applicability setup** page, in the **Table name** field, select the **Vendors** table name.

    > [!NOTE]
    > The same electronic document property type is used to determine which response type is generated for a specific vendor: **OIOUBL application response** or **PEPPOL invoice level response**.

1. Save your changes, and return to the **Electronic document property types** page.

    ![Screenshot that shows the property type added on the Electronic document property types page for responses.](../media/emea_dk_response_types_setup.jpg)

#### Define responses formats

To identify which response format type is used for a specific vendor, follow these steps.

1. Go to **Accounts payable** \> **Vendors** \> **All vendors**.
1. Select a specific vendor in the list, and then, on the Action Pane, on the **Vendor** tab, in the **Properties** group, select **Electronic document properties**.
1. In the **Value** column, enter **PEPPOL**. You must enter the value exactly as it appears here.

    > [!NOTE]
    > The system generates invoice-level responses in PEPPOL format only if you enter the value **PEPPOL** here. If you enter a different value, or no value, application responses are generated in the default OIOUBL format.

#### Enter responses

To enter responses for specific pending vendor invoices, follow these steps.

1. Go to **Accounts payable** \> **Invoices** \> **Pending vendor invoices**.
1. Select a specific pending vendor invoice in the list, and then, on the Action Pane, on the **Vendor invoice** tab, in the **Properties** group, select **Electronic document properties**.
1. Select the **RejectResponse** type.
1. In the **Value** column, enter the rejection reason. This text is sent back to the invoice issuer as justification for the rejection. **OIOUBL application response** or **PEPPOL invoice level response** messages are generated and sent only if you enter a non-empty value. 
1. Select the **MessageResponse** type.
1. In the **Value** column, enter any text that should be used as an acknowledgement message. This text is sent back to the invoice issuer as confirmation of invoice receipt. **PEPPOL message level response** messages are generated and sent only if you enter a non-empty value.

### Configure electronic invoicing feature setups

Some parameters for the **Danish electronic invoice (DK)** electronic invoicing feature have default values. Before you deploy the feature to the service environment, review the default values, and update the authorization credentials that are required for response submission via the ISV last-mile connector.

To review and update the authorization credentials, follow these steps.

1. Import the latest version of the **Danish electronic invoice (DK)** Globalization feature, **version 5** or later. Learn more in [Import features from the repository](../global/gs-e-invoicing-import-feature-global-repository.md).
1. Create a copy of the imported Globalization feature, and select your configuration provider for it. Learn more in [Create a feature based on an existing feature](../global/gs-e-invoicing-create-new-globalization-feature.md#create-a-feature-based-on-an-existing-feature).
1. On the **Versions** tab, verify that **Draft** is selected.
1. On the **Setups** tab, in the grid, select the **Application Response OIOUBL** feature setup, and then select **Edit**.
1. On the **Processing pipeline** tab, in the **Processing pipeline** section, select **Integrate with Edicom**.
1. In the **Parameters** section, select **Domain**, and then enter the service ID number that you obtained.
1. Select **Application**, and then enter the same service ID number.
1. Select **Destination**, and then enter the service ID number concatenated with the string "\_EDIWIN." For example, if the service ID number is **123456**, enter **123456\_EDIWIN**.
1. Select **Group**, and then enter the group code that you obtained.
1. Select **Auth token**, and then select the name of the secret that you created for the token.
1. Select **Save**, and close the page.
1. Repeat steps 4 through 11 for each of the following feature setups if your business process assumes that responses are sent in PEPPOL format:

    - Invoice Response PEPPOL
    - Message Response PEPPOL

### Configure electronic document parameters

To configure electronic document parameters, follow these steps.

1. Make sure that the latest country/region-specific **Document context** and **Electronic document model mapping** ER configurations that are required for Denmark are imported. Learn more in [Set up Electronic document parameters](../global/gs-e-invoicing-set-up-parameters.md#set-up-electronic-document-parameters).
1. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
1. In the **Electronic document** section, add a record for the **VendInvoiceInfoTable** table name.
1. Set the **Document context** and **Electronic document model mapping** fields in accordance with step 1.
1. In the **Company** column, you can select a legal entity code to limit the applicability of this electronic document type. If you don't select a value, electronic documents of this type are processed in all legal entities.
1. Save your changes, and close the page.

### Send responses

To generate and submit responses, follow these steps.

1. Go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Submit electronic documents**. Learn more in [Submit electronic documents](../global/e-invoicing-submit-electronic-documents.md).
1. Go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Run submission process in export channels**.
1. In the **Channel** field, select the export channel that you [previously created](#ExChannel), and then select **OK**.

You can inquire about the results of the submission by going to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Electronic document submission log**. In the **Document type** field, select **Vendor invoices** to filter only responses submissions. Learn more in [Work with Electronic document submission log](../global/e-invoicing-submission-log.md).

## Additional resources

- [Customer electronic invoices in Denmark](../norway/emea-dnk-e-invoices.md)
- [Vendor electronic invoice import in Denmark](../denmark/emea-dnk-vend-e-invoice.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

