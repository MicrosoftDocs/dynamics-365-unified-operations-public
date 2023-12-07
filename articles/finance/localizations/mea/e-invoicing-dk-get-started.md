---
title: Electronic invoicing for Denmark
description: This article provides information that will help you get started with Electronic invoicing for Denmark in Microsoft Dynamics 365 Finance.
author: ikondratenko
ms.date: 11/15/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
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

This article provides information that will help you get started with Electronic invoicing for Denmark and configure the system to enable generation, submission and reception of electronic invoices in Danish-specific [OIOUBL](http://www.oioubl.info/Classes/da/Invoice.html) format and, if necessary, in [Pan-European Public Procurement Online (PEPPOL)](https://docs.peppol.eu/poacc/billing/3.0/) format. 

The article guides you through the configuration steps that are general and country/region-dependent in Regulatory Configuration Service (RCS) and in Microsoft Dynamics 365 Finance.

## Prerequisites

Before you begin the procedures in this article, complete the following prerequisites:

- The company must be registered in the [Danish Central Business Register (CVR)](https://datacvr.virk.dk/) and in the Danish electronic invoicing infrastructure [NemHandel](https://nemhandel.dk/).
  > [!IMPORTANT]
- The company must have a signed agreement with the provider of electronic documents delivery service and obtain the required credentials to enable integration of the electronic invoicing service with the [Electronic invoicing service ISV last-mile connector](../global/e-invoicing-isv-connector.md)
- Become familiar with Electronic invoicing as it's described in [Electronic invoicing overview](../global/e-invoicing-service-overview.md) and [Electronic invoicing components](../global/e-invoicing-administration-integration-components.md).
- Sign up for RCS, and set up Electronic invoicing. For more information, see the following articles:

    - [Sign up for and install the Electronic Invoicing service](../global/e-invoicing-sign-up-install.md)
    - [Set up Electronic invoicing](../global/e-invoicing-set-up-overview.md)  
- Activate the integration between your Finance and the Electronic Invoicing service as described in [Activate and setup integration with Electronic invoicing](../global/e-invoicing-activate-setup-integration.md).
- Create the secret in the Azure Key Vault for the **Token** which grants the authorization to access the infrastructure of the provider of electronic documents delivery service, and set up Key Vault as described in [Customer certificates and secrets](../global/e-invoicing-customer-certificates-secrets.md).


## Country-specific configuration for the Danish electronic invoice (DK) feature

Some of the parameters from the **Danish electronic invoice (DK)** electronic invoicing feature are published with default values. Before you deploy the electronic invoicing feature to the service environment, review the default values, and update them as required so that they better reflect your business operations.

1. Import the latest version of the **Danish electronic invoice (DK)** Globalization feature **version X** or later as described in [Import features from the Global repository](../global/e-invoicing-import-feature-global-repository.md).
2. Create a copy of the imported Globalization feature, and select your configuration provider for it, as described in [Create a Globalization feature](../global/e-invoicing-create-new-globalization-feature.md).
3. On the **Versions** tab, verify that the **Draft** version is selected.
4. On the **Setups** tab, in the grid, select the **Sales invoice OIOUBL** feature setup, and then select **Edit**.
5. On the **Processing pipeline** tab, in the **Processing pipeline** section, select the **Integrate with Edicom** action.
6. In the **Parameters** section, select **Domain**, and then enter the obtaind **Service ID** number.
7. Select **Application**, and then enter the same **Service ID** number.
8. Select **Destination**, and then enter the **Service ID** number concatenated with the **_EDIWIN** value.
   > [!NOTE]
   > For example, if the **Service ID** number is *123456* the **Destination** value should be *123456_EDIWIN*.
   
9. Select **Group**, and then enter the obtaind **Group** code.
10. Select **Auth token**, and then select the name of the secret that you created for the token.
11. Select **Save**, and close the page.
12. Repeat steps 4 through 109 for the following feature setups if your business process assumes involvement of the related types of documents:
  
   - Sales credit note OIOUBL
   - Project invoice OIOUBL
   - Project credit note OIOUBL
   - Sales invoice PEPPOL
   - Sales credit note PEPPOL
   - Project invoice PEPPOL
   - Project credit PEPPOL

13. On the **Setups** tab, in the grid, select the **Get status** feature setup, and then select **Edit**.
14. In the **Export channel** tab, in the **Parameters** section, select the **Auth token**, and then select the name of the secret that you created for the token.
15. Select **Domain**, and then enter the obtaind **Service ID** number.
16. Select **Application**, and then enter the same **Service ID** number.
17. Select **Group**, and then enter the obtaind **Group** code.
18. Select **Data channel**, and then enter the name of [integration channel](#ExChannel) configured in **Electronic document parameters** in Finance.
19.  Select **Save**, and close the page.

## Finance configuration

Some additional parameters must be configured directly in Microsoft Dynamics 365 Finance.

1. In the **Feature management** workspace, the **Export channels for electronic invoicing integration** feature must be enabled. For more information, see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
2. Make sure that the country/region-specific **Document context** and **Electronic document model mapping** ER configurations that are required for Denmark are imported. For more information, see [Set up Electronic invoicing parameters](../global/e-invoicing-set-up-parameters.md#set-up-electronic-document-parameters).
3. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
4. In the **Electronic document** section, add records for the **Customer Invoice journal** and **Project invoice** table names.
5. For each table name, set the **Document context** and **Electronic document model mapping** fields in accordance with step 1.
6. <a id="ExChannel"></a>In the **Integration channels** section add the record for the channel which will be used for electronic invoices submission in a batch mode.
7. In the **Channel**, column enter the **EdiStatus** value. This channel name is used by default. You can use different channel name if needed. In this case you need to accordingly adjust it in the **Customer invoice context model** ER configuration, in the **DataChannel** definition, in the **$Context_Channel** variable's value and in the related feature setup **Parameters** and **Applicability rules**.
8. In the **Company column** column, select a required legal entity code.
9. In the **Document context** column, refer to the **Customer invoice context model** configuration with **Data channel context** definition.
10. In the **Channel type** column, select the **Export** value.
11. Save your changes, and close the page.

## Finance business data configuration

Please do the configuration steps described in the [Customer electronic invoices in Denmark](../norway/emea-dnk-e-invoices.md) article starting from the  [Configure parameters](../norway/emea-dnk-e-invoices.md#configure-parameters) section.

### Seller identification

A company which submints electronic invoices can be idendified eithr by its CVR number or by its [Global Location Number (GLN)](https://en.gs1.dk/services/gln).
To use identification by the CVR number please complete the following configuration steps.
1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
2. On the **Bank account information** FastTab, in **Codes** section, **Routing number** field, make sure that a valid Legal Entity CVR number is defined here.
3. The CVR number will be populated to **Invoice\\cac:AccountingSupplierParty\\cac:Party\\cbc:EndpointID** element in the generated electronic invoice XML file and used for the Seller's identification during the submission process.

To use identification by the GLN (EAN) number please complete the following configuration steps.
1. Go to **Organization administration** \> **Global address book** \> **Registration types** \> **Registration types**.
2. Define a new registration type for Denmark with the **EAN** name, exactly as writteh here.
3. Go to **Organization administration** \> **Organizations** \> **Legal entities**, and select the **Registration IDs** from the top menu.
4. On the **Registration ID** FastTab, add a resitratoin ID of **EAN** registration type created on step 2.
5. In the **Registration number** field enter a valid GLN number.
6. The GLN number will be populated to **Invoice\\cac:AccountingSupplierParty\\cac:Party\\cbc:EndpointID** element in the generated electronic invoice XML file and used for the Seller's identification during the submission process.
   
    > [!NOTE]
    > The GLN number has higher priority than CVR number. If both numbers are configured simultaneously then the GLN number will be used.


### Buyer identification

1. Go to **Accounts receivable** \> **Customers** \> **All customers**,  and select a customer.
2. On the **Invoice and delivery** FastTab, in the **EAN** field, make sure a valid customer's GLN number is defined here.
3. The GLN number will be populated to **Invoice\\cac:AccountingCustomerParty\\cac:Party\\cbc:EndpointID** element in the generated electronic invoice XML file and used for the Buyer's identification during the submission process.

    > [!NOTE]
    > If the GLN number is not defined then the customer's Tax exempt number will be used.

### Configure output format type

By default all outgoing electronic invoices will be generated in **OIOUBL** format for all customers. User can configure generation of electronic invoices in **PEPPOL** format for specific customers using configurable electronic document property types.
> [!NOTE]
> Perform the configuration steps described in this chapter only if you additionally need to generate electronic invoices in **PEPPOL** format. Skip these configuration steps if only generation in **OIOUBL** format is required.

#### Configure electronic document properties

1. Go to **Accounts receivable** \> **Setup** \> **Electronic document property types**.
2. Select **New** to add a property type.
2. In the **Type** field, enter the **FormatType** value exactly as specified here.
3. Select **Applicability** to add an applicable table.
4. On the **Electronic document property type applicability setup** page, in the **Table name** field, select the **Customers** table name.
5. Save your changes, and return to the **Electronic document property types** page.

    ![Property type added on the Electronic document property types page.](../media/emea_dk_format_type_setup.jpg)

#### Enter the type of format

Follow these steps to enter the type of format for specific customers.

1. Go to **Accounts receivable** \> **Customers** \> **All customers**.
2. Select a specific customer in the list, and then, on the Action Pane, on the **Customer** tab, in the **Properties** group, select **Electronic document properties**.
3. In the **Value** column, enter the **PEPPOL** value exactly as specified here.
    > [!NOTE]
    > Only if the **PEPPOL** value is entered, the system will generate electronic invoices in the PEPPOL format. All other values or missing values will lead to generation of electronic invoices in the default OIOUBL format.
    
    ![Value entered on the Electronic document properties page.](../media/emea_dk_format_type.jpg)


## Issue electronic invoices

When you've completed all the required configuration steps, you can generate and submit electronic invoices for posted invoices at **Organization administration** \> **Periodic** \> **Electronic documents** \> **Submit electronic documents**). 
For more information about how to generate electronic invoices, see [Submit electronic documents to Electronic invoicing](../global/e-invoicing-submit-electronic-documents.md).

> [!NOTE]
> For Danish electronic invoices submission, additional steps must be completed in addition to the standard submission procedure that was described earlier.

In current implementation, the standard submission procedure just generates electronic invoices and stores them on the service side. It doesn't actually submit them. To submit the generated electronic invoices in a batch mode, follow these steps.

1. Go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Run submission process in export channels**.
2. In the **Channel** field, select the export channel that you [previously created](#ExChannel). Then select **OK**.

You can inquire about the results of the submission at **Organization administration** \> **Periodic** \> **Electronic documents** \> **Electronic document submission log**). 
For more information, see [Work with Electronic document submission log](../global/e-invoicing-submission-log.md).


## Receive incoming electronic invoices

To enable import of incoming invoices in OIOUBL format, complete the following additional configuration steps for the same version of the **Danish electronic invoice (DK)** electronic invoicing feature that's used for outgoing invoice submission.

1. In RCS, on the **Globalization features** tile, on the **Electronic invoicing** tile, select the required version of the **Danish electronic invoice (DK)** electronic invoicing feature.
2. On the **Setups** tab, in the grid, select **Import vendor invoice**, and then select **Edit**.
3. <a id="ImportChannel"></a>On the **Import channel** tab, in the **Parameters** section, select the **Data channel** parameter. Then, in the **Value** field, define the name of the data channel. Alternatively, leave the default value unchanged. Whatever you do, make a note of the value, because you will use it in later configuration steps.
4. Select the **Service ID** parameter, and then select the name of the secret that contains the Service identifier.
5. Select the **Group** parameter, and then select the name of the secret that contains the Group identifier.
6. Select the **Token** parameter, and then select the name of the secret created for the token.
7. On the **Applicability rules** tab, in the **Channel** field, make sure that the **Value** column contains the same [import channel](#ImportChannel) name that you previously defined in step 3.
9. <a id="OutputFile"></a>On the **Variables** tab, make a note of the **OutputFile** name, because you will use it in later configuration steps.
10. Select **Save**, and close the page.
11. Complete, publish and deploy the configured version of the **Danish electronic invoice (DK)** electronic invoicing feature.

### Finance configuration

Some additional parameters must be configured directly in Finance.

1. Make sure that the latest version of the **Vendor invoice import (DK)** Electronic Reporting configuration isimported.

    > [!NOTE]
    > The **Vendor invoice import (DK)** format configuration is based on the parent **Vendor invoice import** format configuration. The formats use the **Invoice model** configuration and the **Vendor invoice Mapping to destination** configuration. All required additional configurations are automatically imported.

2. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
3. On the **Integration channels** tab, in the **Channels** section, in the **Channel** field, enter the same [import channel](#ImportChannel) name that you created earlier.
3. In the **Channels** section, in the **Company** field, select a required legal entity. In the **Document context** field, select the **Customer invoice context model** configuration.
4. In the **Import sources** section, in the **Name** field, enter the same **OutputFile** name that you [created earlier](#OutputFile).
5. In the **Data entity name** field, select **Vendor invoice header**. In the **Model mapping** field, reference the **Vendor invoice import (DK)** configuration.
6. Select **Save**, and close the page.

### Configure Finance business data

You must configure the following types of master data to provide a match for incoming electronic invoices:

- Vendors
- Products
- Units

Please do the configuration steps described in the [Vendor electronic invoice import in Denmark](../denmark/emea-dnk-vend-e-invoice.md) article startin from the  [Configure vendor data](../denmark/emea-dnk-vend-e-invoice.md#configure-vendor-data) section.

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

