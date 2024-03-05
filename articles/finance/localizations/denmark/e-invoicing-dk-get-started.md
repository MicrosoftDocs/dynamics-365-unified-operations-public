---
title: Get started with Electronic invoicing for Denmark
description: This article explains how to get started with Electronic invoicing for Denmark in Microsoft Dynamics 365 Finance.
author: ikondratenko
ms.date: 12/14/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: johnmichalak
ms.search.region: Denmark
ms.author: ikondratenko
ms.search.validFrom: 2023-12-01
ms.dyn365.ops.version: AX 10.0.36
ms.custom: 
ms.assetid: 
ms.search.form: 
---

# Get started with Electronic invoicing for Denmark

[!include [banner](../../includes/banner.md)]

This article provides information that will help you get started with Electronic invoicing for Denmark. It includes information about how to configure the system so that you can generate, submit, and receive electronic invoices in the Denmark-specific [OIOUBL](http://www.oioubl.info/Classes/da/Invoice.html) format and, if necessary, in [Pan-European Public Procurement Online (PEPPOL)](https://docs.peppol.eu/poacc/billing/3.0/) format. The steps in this article are general and country/region-dependent in Regulatory Configuration Service (RCS) and Microsoft Dynamics 365 Finance.

## Prerequisites

Before you begin the procedures in this article, the following prerequisites must be met:

- The company must be registered in the [Danish Central Business Register (CVR)](https://datacvr.virk.dk/) and in the Danish electronic invoicing infrastructure, [NemHandel](https://nemhandel.dk/).
- The company must have a signed agreement with the provider of electronic document delivery service that secures electronic document interchange in the OIOUBL and PEPPOL formats.
- Among the registered profile IDs, the company should have the following profiles that Finance uses for electronic document interchange:

    - **Procurement-BilSim-1.0** – This profile is used to interchange documents in OIOUBL format.
    - **urn:fdc:peppol.eu:2017:poacc:billing:01:1.0** – This profile is used to interchange documents in PEPPOL format.

- The company must obtain, from the service provider, the required credentials to enable integration of the Electronic Invoicing service with the [Electronic Invoicing service independent software vendor (ISV) last-mile connector](../global/e-invoicing-isv-connector.md).
- Become familiar with Electronic invoicing as described in [Electronic invoicing overview](../global/e-invoicing-service-overview.md) and [Electronic invoicing components](../global/e-invoicing-administration-integration-components.md).
- Sign up for RCS, and set up Electronic invoicing. For more information, see the following articles:

    - [Sign up for and install the Electronic Invoicing service](../global/e-invoicing-sign-up-install.md)
    - [Set up Electronic invoicing](../global/e-invoicing-set-up-overview.md)

- Activate the integration between Finance and the Electronic Invoicing service as described in [Activate and setup integration with Electronic invoicing](../global/e-invoicing-activate-setup-integration.md).
- In the Azure key vault, create the secret for the token that grants authorization to access the infrastructure of the provider of electronic document delivery service, and set up Key Vault as described in [Customer certificates and secrets](../global/e-invoicing-customer-certificates-secrets.md).

## Country-specific configuration for the Danish electronic invoice (DK) feature

Some parameters for the **Danish electronic invoice (DK)** electronic invoicing feature have default values. Before you deploy the feature to the service environment, review the default values, and update them as required, so that they better reflect your business operations.

1. Import the latest version of the **Danish electronic invoice (DK)** Globalization feature, **version 4** or later. For more information, see [Import features from the Global repository](../global/e-invoicing-import-feature-global-repository.md).
2. Create a copy of the imported Globalization feature, and select your configuration provider for it. For more information, see [Create a Globalization feature](../global/e-invoicing-create-new-globalization-feature.md).
3. On the **Versions** tab, verify that **Draft** is selected.
4. On the **Setups** tab, in the grid, select the **Sales invoice OIOUBL** feature setup, and then select **Edit**.
5. On the **Processing pipeline** tab, in the **Processing pipeline** section, select **Integrate with Edicom**.
6. In the **Parameters** section, select **Domain**, and then enter the service ID number that you obtained.
7. Select **Application**, and then enter the same service ID number.
8. Select **Destination**, and then enter the service ID number concatenated with the string **\_EDIWIN**. For example, if the service ID number is **123456**, enter **123456\_EDIWIN**.
9. Select **Group**, and then enter the group code that you obtained.
10. Select **Auth token**, and then select the name of the secret that you created for the token.
11. Select **Save**, and close the page.
12. Repeat steps 4 through 11 for each of the following feature setups if your business process assumes the involvement of the related types of documents:

    - Sales credit note OIOUBL
    - Project invoice OIOUBL
    - Project credit note OIOUBL
    - Sales invoice PEPPOL
    - Sales credit note PEPPOL
    - Project invoice PEPPOL
    - Project credit PEPPOL

13. On the **Setups** tab, in the grid, select the **Get status** feature setup, and then select **Edit**.
14. On the **Export channel** tab, in the **Parameters** section, select **Auth token**, and then select the name of the secret that you created for the token.
15. Select **Domain**, and then enter the service ID number that you obtained.
16. Select **Application**, and then enter the same service ID number.
17. Select **Group**, and then enter the group code that you obtained.
18. Select **Data channel**, and then enter the name of the [integration channel](#ExChannel) that's configured on the **Electronic document parameters** page in Finance.
19. Select **Save**, and close the page.

## Finance configuration

Some additional parameters must be configured directly in Finance.

1. In the **Feature management** workspace, make sure that the **Export channels for electronic invoicing integration** feature is enabled. For more information, see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
2. Make sure that the country/region-specific **Document context** and **Electronic document model mapping** Electronic reporting (ER) configurations that are required for Denmark are imported. For more information, see [Set up Electronic invoicing parameters](../global/e-invoicing-set-up-parameters.md#set-up-electronic-document-parameters).
3. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
4. In the **Electronic document** section, add records for the **Customer Invoice journal** and **Project invoice** table names.
5. For each table name, set the **Document context** and **Electronic document model mapping** fields in accordance with step 1.
6. <a id="ExChannel"></a>In the **Integration channels** section, add a record for the channel that will be used for electronic invoice submission in batch mode.
7. In the **Channel** column, enter **EdiStatus**. This channel name is used by default, but you can use a different channel name as you require. In this case, you must enter the same name in the value of the **$Context\_Channel** variable in the **DataChannel** definition in the **Customer invoice context model** ER configuration. You must also enter it in the parameters and applicability rules of the related feature setup.
8. In the **Company** column, select a required legal entity code.
9. In the **Document context** column, refer to the **Customer invoice context model** configuration by using the **Data channel context** definition.
10. In the **Channel type** column, select **Export**.
11. Save your changes, and close the page.

## Finance business data configuration

Follow the configuration steps in [Customer electronic invoices in Denmark](../norway/emea-dnk-e-invoices.md). Start from the [Configure parameters](../norway/emea-dnk-e-invoices.md#configure-parameters) section.

### Seller identification

Companies that submit electronic invoices can be identified by their CVR number or their [Global Location Number (GLN)](https://en.gs1.dk/services/gln). The GLN is also known as a European article numbering (EAN) location number.

To identify a company by its CVR number, follow these steps.

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
2. On the **Bank account information** FastTab, in **Codes** section, in the **Routing number** field, make sure that a valid CVR number is entered for the legal entity.

    The CVR number will be entered in the **Invoice\\cac:AccountingSupplierParty\\cac:Party\\cbc:EndpointID** element in the electronic invoice XML file that's generated. It will be used as the seller's identification during the submission process.

To identify a company by its GLN, follow these steps.

1. Go to **Organization administration** \> **Global address book** \> **Registration types** \> **Registration types**.
2. Define a new registration type for Denmark that has the name **EAN**. You must enter the name exactly as it appears here.
3. Go to **Organization administration** \> **Organizations** \> **Legal entities**, and select **Registration IDs** on the top menu.
4. On the **Registration ID** FastTab, add the **EAN** registration type that you created.
5. In the **Registration number** field, enter a valid GLN.

    The GLN will be entered in the **Invoice\\cac:AccountingSupplierParty\\cac:Party\\cbc:EndpointID** element in the electronic invoice XML file that's generated. It will be used as the seller's identification during the submission process.

    > [!NOTE]
    > The GLN has higher priority than the CVR number. If both numbers are configured at the same time, the GLN is used.

### Buyer identification

1. Go to **Accounts receivable** \> **Customers** \> **All customers**, and select a customer.
2. On the **Invoice and delivery** FastTab, in the **EAN** field, make sure that a valid GLN is entered for the customer.

    The GLN will be entered in the **Invoice\\cac:AccountingCustomerParty\\cac:Party\\cbc:EndpointID** element in the electronic invoice XML file that's generated. It will be used as the buyer's identification during the submission process.

    > [!NOTE]
    > If no GLN is defined, the customer's tax exempt number is used.

### Configure the output format type

By default, all outgoing electronic invoices are generated in OIOUBL format for all customers. However, by using configurable electronic document property types, you can configure electronic invoices so that they're generated in PEPPOL format for specific customers.

> [!NOTE]
> Follow the configuration steps in this section only if you must also generate electronic invoices in PEPPOL format. If you generate them only in OIOUBL format, you can skip these steps.

#### Configure electronic document properties

1. Go to **Accounts receivable** \> **Setup** \> **Electronic document property types**, and select **New**.
2. In the **Type** field, enter **FormatType**. You must enter the value exactly as it appears here.
3. Select **Applicability** to add an applicable table.
4. On the **Electronic document property type applicability setup** page, in the **Table name** field, select the **Customers** table name.
5. Save your changes, and return to the **Electronic document property types** page.

    ![Screenshot that shows the property type added on the Electronic document property types page.](../media/emea_dk_format_type_setup.jpg)

#### Enter the type of format

Follow these steps to enter the type of format for specific customers.

1. Go to **Accounts receivable** \> **Customers** \> **All customers**.
2. Select a specific customer in the list, and then, on the Action Pane, on the **Customer** tab, in the **Properties** group, select **Electronic document properties**.
3. In the **Value** column, enter **PEPPOL**. You must enter the value exactly as it appears here.

    > [!NOTE]
    > The system generates electronic invoices in PEPPOL format only if the value **PEPPOL** is entered. If another value or no value is entered, electronic invoices are generated in the default OIOUBL format.

    ![Screenshot that shows PEPPOL entered in the Value column on the Electronic document properties page.](../media/emea_dk_format_type.jpg)

## Issue electronic invoices

After you complete all the required configuration steps, you can generate and submit electronic invoices for posted invoices by going to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Submit electronic documents**. For more information about how to generate electronic invoices, see [Submit electronic documents to Electronic invoicing](../global/e-invoicing-submit-electronic-documents.md).

> [!IMPORTANT]
> In current implementations, the standard submission procedure that was described earlier only generates electronic invoices and stores them on the service side. The invoices aren't submitted. Submission of Danish electronic invoices requires that you complete the following additional steps.

To submit the generated electronic invoices in batch mode, follow these steps.

1. Go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Run submission process in export channels**.
2. In the **Channel** field, select the export channel that you [previously created](#ExChannel), and then select **OK**.

You can inquire about the results of the submission by going to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Electronic document submission log**). For more information, see [Work with Electronic document submission log](../global/e-invoicing-submission-log.md).

## Receive incoming electronic invoices

To import incoming invoices in OIOUBL and PEPPOL formats, follow these additional configuration steps for the same version of the **Danish electronic invoice (DK)** electronic invoicing feature that's used for outgoing invoice submission.

1. In RCS, on the **Globalization features** tile, on the **Electronic invoicing** tile, select the required version of the **Danish electronic invoice (DK)** electronic invoicing feature.
2. On the **Setups** tab, in the grid, select **Incoming OIOUBL**, and then select **Edit**.
3. <a id="ImportChannel"></a>On the **Import channel** tab, in the **Parameters** section, select the **Data channel** parameter. Then, in the **Value** field, define the name of the data channel. Alternatively, leave the default value unchanged. The default channel name for the OIOUBL format is **EdiOIOUBL** and for the PEPPOL format is **EdiPEPPOL**. In both cases, make a note of the value, because you'll use it in later configuration steps.
4. Select the **Service ID** parameter, and then select the name of the secret that contains the service ID number.
5. Select the **Group** parameter, and then select the name of the secret that contains the group code.
6. Select the **Token** parameter, and then select the name of the secret that you created for the token.
7. On the **Applicability rules** tab, in the **Channel** field, make sure that the **Value** column contains the same [import channel](#ImportChannel) name that you defined earlier.
9. <a id="OutputFile"></a>On the **Variables** tab, make a note of the **OutputFile** name, because you'll use it in later configuration steps.
10. Select **Save**, and close the page.
11. If an import in the PEPPOL format is also required, repeat steps 2 through 10 for the **Incoming PEPPOL** feature setup.
12. Complete and deploy the configured version of the **Danish electronic invoice (DK)** electronic invoicing feature.

### Finance configuration

Some additional parameters must be configured directly in Finance.

1. Make sure that the latest version of the **Vendor invoice import (DK)** ER configuration is imported.

    > [!NOTE]
    > The **Vendor invoice import (DK)** format configuration is used for import invoices in the OIOUBL format and based on the parent **Vendor invoice import** format configuration which implements invoices import in the PEPPOL format. The formats use the **Invoice model** and **Vendor invoice Mapping to destination** configurations. All required additional configurations are automatically imported.

2. In the **Electronic reporting** workspace, on the **Reporting configurations** tile, select **Customer invoice context model**.
3. Select **Create configuration**, and then, in the dropdown dialog box, select **Derive from Name: Customer invoice context model, Microsoft** to create a derived configuration.

    > [!NOTE]
    > The derived configuration must differ from the configuration that's used for the invoice *submission* setup.

4. Open the derived configuration to edit it in the designer, and then select **Map model to datasource**.
5. Open the **DataChannel** definition to edit it in the designer.
6. In the **Data sources** tree, expand the **$Context\_Channel** container.
7. In the **Value** field, select **Edit**, and then enter the [import channel](#ImportChannel) name.
8. Save your changes, and complete the derived configuration.
9. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
10. On the **Integration channels** tab, in the **Channels** section, in the **Channel** field, enter the [import channel](#ImportChannel) name that you created earlier.
11. In the **Channels** section, in the **Company** field, select a required legal entity.
12. In the **Document context** field, select the **Customer invoice context model** configuration.
13. In the **Import sources** section, in the **Name** field, enter the same **ResponseXml** name that's used in the variable for **Decoded file** in the import feature setup.

    ![Screenshot that shows the ResponseXml variable in the import feature setup.](../media/isv_connector_responseXML.jpg)

14. In the **Data entity name** field, select **Vendor invoice header**.
15. In the **Model mapping** field, reference the **Vendor invoice import (DK)** configuration.

    ![Screenshot that shows Vendor invoice import (DK) referenced in the Model mapping field.](../media/isv_connector_import_channel.jpg)

16. If an import in the PEPPOL format is also required, create another import channel and repeat steps 3 through 15 for this channel. Use the **Vendor invoice import** configuration on the step 15.
17. Select **Save**, and close the page.

### Configure Finance business data

You must configure the following types of master data to provide a match for incoming electronic invoices:

- Vendors
- Products
- Units

Follow the configuration steps in [Vendor electronic invoice import in Denmark](../denmark/emea-dnk-vend-e-invoice.md). Start from the [Configure vendor data](../denmark/emea-dnk-vend-e-invoice.md#configure-vendor-data) section.

### Receive electronic invoices

Follow these steps to receive electronic invoices.

1. Go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Receive electronic documents**.
2. Select **OK**, and then close the page.

To view the receipt logs for electronic invoices, go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Electronic document receipt log**.

To view successfully received invoices, go to **Accounts payable** \> **Invoices** \> **Pending vendor invoices**.

## Additional resources

- [Electronic invoicing overview](../global/e-invoicing-service-overview.md)
- [Get started with Electronic invoicing service administration](../e-invoicing-get-started-service-administration.md)
- [Get started with Electronic invoicing](../e-invoicing-get-started.md)
- [Customer electronic invoices in Denmark](../norway/emea-dnk-e-invoices.md)
- [Vendor electronic invoice import in Denmark](../denmark/emea-dnk-vend-e-invoice.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
