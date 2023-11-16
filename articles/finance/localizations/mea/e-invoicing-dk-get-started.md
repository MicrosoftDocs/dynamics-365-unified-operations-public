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

- The company must be registered in the Danish authorities and in the Danish electronic invoicing infrastructure [NemHandel](https://nemhandel.dk/).
- The company must have a signed agreement with the provider of electronic documents delivery service and obtain the required credentials to enable submission and reception of electronic invoices generated in Microsoft D365 Finance.
- Become familiar with Electronic invoicing as it's described in [Electronic invoicing overview](../global/e-invoicing-service-overview.md) and [Electronic invoicing components](../global/e-invoicing-administration-integration-components.md).
- Sign up for RCS, and set up Electronic invoicing. For more information, see the following articles:

    - [Sign up for and install the Electronic Invoicing service](../global/e-invoicing-sign-up-install.md)
    - [Set up Electronic invoicing](../global/e-invoicing-set-up-overview.md)  
- Activate the integration between your Finance and the Electronic Invoicing service as described in [Activate and setup integration with Electronic invoicing](../global/e-invoicing-activate-setup-integration.md).
- Create secrets in Azure Key Vault, and set up Key Vault as described in [Customer certificates and secrets](../global/e-invoicing-customer-certificates-secrets.md):

    - The **Service ID** which uniquely identifies the company by the provider of electronic documents delivery service.
    - The **Group ID** which is required for internal routing within the infrastructure of the provider of electronic documents delivery service.
    - The **Token** which grants the authorization to access the infrastructure of the provider of electronic documents delivery service.

- Make sure that the following Electronic reporting (ER) format configurations are imported. For more information, see [Import Electronic reporting (ER) configurations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-import-ger-configurations.md).

    - OIOUBL Sales invoice (DK)
    - OIOUBL Sales credit note (DK)
    - OIOUBL Project invoice (DK)
    - OIOUBL Project credit note (DK)
 
- PEPPOL.

    - Peppol Sales Invoice
    - Peppol Sales Credit Note
    - Peppol Project Invoice
    - Peppol Project Credit Note

> [!NOTE]
> The specified above ER formats are based on the **Invoice model** configuration and the **Invoice model mapping** configuration. All required additional configurations are automatically imported.

## Country/region-specific configuration for the Danish electronic invoice (DK) feature

Some of the parameters from the **Danish electronic invoice (DK)** electronic invoicing feature are published with default values. Before you deploy the electronic invoicing feature to the service environment, review the default values, and update them as required so that they better reflect your business operations.

1. Import the latest version of the **Danish electronic invoice (DK)** Globalization feature as described in [Import features from the Global repository](../global/e-invoicing-import-feature-global-repository.md).
2. Create a copy of the imported Globalization feature, and select your configuration provider for it, as described in [Create a Globalization feature](../global/e-invoicing-create-new-globalization-feature.md).
3. On the **Versions** tab, verify that the **Draft** version is selected.
4. On the **Setups** tab, in the grid, select the **OIOUBL Sales invoice processing** feature setup, and then select **Edit**.
5. On the **Processing pipeline** tab, in the **Processing pipeline** section, select the **QQQQ ISV connector QQQQ** action.
6. In the **Parameters** section, select **ServiceID**, and then select the name of the secret that you previously created for the legal entity's Service ID.
7. Select **Group ID**, and then select the name of the secret that you previously created for the legal entity's Group ID.
8. Select **Token**, and then select the name of the secret that you created for the token.
9. Select **Service URI**, and make sure that a valid URI is configured. QQQQ !!!!!!!!!!!!!!!!!!!  QQQQQQQQ.
10. I
11. I.
12. Select **Save**, and close the page.
13. On the **Setups** tab, in the grid, select the **Submit customer invoice** feature setup, and then select **Edit**.
14. On the **Applicability rules** tab, in the **LegalEntityID** field, make sure that a valid legal entity code is configured in the **Value** column.
15. Select **Save** (if you made any changes), and close the page.
16. Repeat steps 5 through 13 for the following feature setups if your business process assumes involvement of the related types of documents:
  
   - OIOUBL Sales credit note processing
   - OIOUBL Project invoice processing
   - OIOUBL Project credit note processing
   - Peppol Sales invoice processing
   - Peppol Sales credit note processing
   - Peppol Project invoice processing
   - Peppol Project credit processing


Configure the ISV connector [ Use the electronic invoicing service ISV connectors](../global/e-invoicing-isv-connector.md):

## Finance configuration

Some additional parameters must be configured directly in Finance.

1. Make sure that the country/region-specific **Document context** and **Electronic document model mapping** ER configurations that are required for Denmark are imported. For more information, see [Set up Electronic invoicing parameters](../global/e-invoicing-set-up-parameters.md#set-up-electronic-document-parameters).
2. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
3. In the **Electronic document** section, add records for the **Customer Invoice journal** and **Project invoice** table names.
4. For each table name, set the **Document context** and **Electronic document model mapping** fields in accordance with step 1.





5. For the **Customer Invoice journal** table name, select **Response types**.
6. Create a response type that has the same name that was defined for the related variable of the **To client** type in the corresponding feature setups in RCS. Enter the following values:

    - In the **Submission status** field, select **Pending**.
    - In the **Model mapping** field, select **KSeF response data import format (PL)**.

7. Repeat steps 5 through 6 for the **Project invoice** and **Advance invoice** electronic documents.
8. In the **Feature management** workspace, the **Export channels for electronic invoicing integration** feature must be enabled. For more information, see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
9. In the **Electronic reporting** workspace, on the **Reporting configurations** tile, select the **Customer invoice context model** configuration.
10. <a id="ExportChannel"></a>Select **Create configuration**, and then, in the drop-down dialog box, select the **Derive from Name: Customer invoice context model, Microsoft** option to create a derived configuration.
11. Open the derived configuration for editing in the designer, and select **Map model to datasource**.
12. Open the **DataChannel** definition for editing in designer. In the **Data sources** tree, expand the **$Context\_Channel** container.
13. In the **Value** field, select **Edit**, and enter the data channel name. The value is the name of the data channel that is configured in the **Export channel** section for the **Submit batch** feature setup in RCS.
14. Save your changes, and complete the derived configuration.
15. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
16. <a id="channel"></a>On the **Integration channels** tab, add a channel that has the same name that was used in step 13.
17. In the **Company** column, enter a required legal entity code. In the **Document context** column, refer to the derived configuration.
18. Save your changes, and close the page.

## Finance business data configuration

Please do the configuration steps described in the [Customer electronic invoices in Denmark](../norway/emea-dnk-e-invoices.md) article startin from the  [Configure parameters](../norway/emea-dnk-e-invoices.md#configure-parameters) section.





### Configure additional data

You can add any additional arbitrary data to invoices. This data will be put in a special section of electronic invoices that is named *DodatkowyOpis*.

#### Configure electronic document properties

1. Go to **Accounts receivable** \> **Setup** \> **Electronic document property types**.
2. Select **New** to add a property type.
2. In the **Type** field, enter the value to use as an additional data key (*Klucz*) in the resulting XML file of an e-invoice.
3. Select **Applicability** to add an applicable table.
4. On the **Electronic document property type applicability setup** page, in **Table name** field, select **Customer invoice journal** and **Project invoice**.
5. Add as many additional document properties as you require.
6. Save your changes, and return to the **Electronic document property types** page.

    ![Property type added on the Electronic document property types page.](../media/e-invoicing-pol-parameters.jpg)

#### Enter additional data

Follow these steps to enter additional invoice data.

1. Go to **Accounts payable** \> **Inquiries and reports** \> **Invoice** \> **Invoice journal**.
2. Select an invoice in the list, and then, on the Action Pane, on the **Invoice** tab, in the **Properties** group, select **Electronic document properties**.
3. Enter a required value. This value will be used in the *Wartosc* field in the resulting XML file of an e-invoice.

    ![Value entered on the Electronic document properties page.](../media/e-invoicing-pol-values.jpg)

> [!NOTE]
> You can enter additional data for project invoices in a similar way at **Project management and accounting** \> **Project invoices** \> **Project invoice**.

## Issue electronic invoices

When you've completed all the required configuration steps, you can generate and submit electronic invoices for posted invoices. 
For more information about how to generate electronic invoices, see [Issue electronic invoices in Finance and Supply chain management](../e-invoicing-issuing-electronic-invoices-finance-supply-chain-management.md).

You can inquire about the results of the submission at **Organization administration** \> **Periodic** \> **Electronic documents** \> **Electronic document submission log**).

## Receive incoming electronic invoices

Complete the following additional configuration steps for the same version of the **Polish electronic invoice (PL)** electronic invoicing feature that's used for outgoing invoice submission.

1. In RCS, on the **Globalization features** tile, on the **Electronic invoicing** tile, select the same version of the **Polish electronic invoice (PL)** electronic invoicing feature that was configured for outgoing invoices submission.
2. On the **Setups** tab, in the grid, select **Import vendor invoice**, and then select **Edit**.
3. On the **Import channel** tab, in the **Parameters** section, select the **Data channel** parameter. Then, in the **Value** field, define the name of the data channel. Alternatively, leave the default value unchanged. Whatever you do, make a note of the value, because you will use it in later configuration steps.
4. Select the **Service URI** parameter, and make sure that a valid URI is configured.
5. Select the **Client ID** parameter, and then select the name of the secret that contains the client identifier.
6. Select the **Certificate name** parameter, and then select the name of the digital certificate that you created.
7. Select the **Start date** parameter, and then define the initial date for the first receipt of invoices from KSEF. All invoices that have dates between the **Start date** value and the current receiving date will be downloaded. Each successive receiving process will start from the date of the previous process.
8. On the **Applicability rules** tab, in the **Channel** field, make sure that the **Value** column contains the same import channel name that you previously defined.
9. <a id="OutputFile"></a>On the **Variables** tab, make a note of the **OutputFile** name, because you will use it in later configuration steps.
10. Select **Save**, and close the page. 

### Finance configuration

Some additional parameters must be configured directly in Finance.

1. Make sure that the following Electronic Reporting configurations are imported:

    - Vendor invoice import (PL)
    - Vendor invoice Mapping to destination (PL)

2. In the **Electronic reporting** workspace, on the **Reporting configurations** tile, select the **Customer invoice context model** configuration.
3. Select **Create configuration**, and then, in the drop-down dialog box, select **Derive from Name: Customer invoice context model, Microsoft** to create a derived configuration.

    > [!NOTE]
    > The derived configuration must differ from the [configuration](#ExportChannel) that's used for the invoice *submission* setup. 

4. Open the derived configuration for editing in the designer, and then select **Map model to datasource**.
5. Open the **DataChannel** definition for editing in the designer.
6. In the **Data sources** tree, expand the **$Context\_Channel** container.
7. In the **Value** field, select **Edit**, and then enter the data channel name.
8. Save your changes, and complete the derived configuration.
9. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
10. On the **Integration channels** tab, in the **Channels** section, in the **Channel** field, enter the same import channel name that you created earlier.
11. In the **Channels** section, in the **Company** field, select a required legal entity. In the **Document context** field, select the configuration that you created earlier.
12. In the **Import sources** section, in the **Name** field, enter the same **OutputFile** name that you [created earlier](#OutputFile).
13. In the **Data entity name** field, select **Vendor invoice header**. In the **Model mapping** field, reference the **Vendor invoice import (PL)** configuration.
14. Select **Save**, and close the page.

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

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

