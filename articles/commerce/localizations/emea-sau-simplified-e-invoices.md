---
title: Generate and submit simplified electronic invoices for Saudi Arabia
description: This article provides an overview and setup guidelines for the functionality of simplified electronic invoices that is available for Saudi Arabia in Microsoft Dynamics 365 Commerce.
author: EvgenyPopovMBS
ms.date: 11/25/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: v-chgriffin
ms.search.region: Saudi Arabia
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2022-11-21

---
# Generate and submit simplified electronic invoices for Saudi Arabia

[!include[banner](../includes/banner.md)]

This article provides an overview of the functionality of simplified electronic invoices (e-invoices) that is available for Saudi Arabia in Microsoft Dynamics 365 Commerce. It also provides guidelines for setting up the functionality.

## Overview of the electronic invoicing functionality for Saudi Arabia

The electronic invoicing functionality that is available to Saudi Arabia in Commerce provides the following capabilities:

- Generation of an XML file of a simplified e-invoice upon concluding a sales transaction in Commerce point of sale (POS).
- Generation of a cryptographic stamp (that is, a digital signature) for the simplified e-invoice.
- Generation and printing of QR code for the simplified e-invoice that includes the cryptographic stamp.
- Submission of the simplified e-invoice from Commerce headquarters to Saudi Arabian tax authorities (Zakat, Tax and Customs Authority - ZATCA) for reporting purposes.

For more information about the electronic invoicing requirements for Saudi Arabia, see the [E-Invoicing portal by ZATCA](https://zatca.gov.sa/en/E-Invoicing/Pages/default.aspx).

The high-level, end-to-end process flow in Commerce for Saudi Arabia is as follows:

1. When the checkout process is completed for a sales transaction in POS, POS sends a request to generate and digitally sign a simplified e-invoice to the Commerce runtime (CRT) via Commerce Scale Unit (CSU). The generation and digital signing of a simplified e-invoice is implemented by using the [Fiscal registration framework](./fiscal-integration-for-retail-channel.md) and an [internal](./fiscal-integration-for-retail-channel.md#fiscal-registration-is-done-internally-in-the-crt) connector.

    > [!NOTE]
    > If POS is in the offline mode, the generation and digital signing of an e-invoice occurs in the local copy of CRT on the POS machine.

1. CRT generates a simplified e-invoice in an XML format. The XML format of e-invoice for Saudi Arabia is implemented by using [Electronic reporting (ER)](../../dev-itpro/analytics/general-electronic-reporting.md). The format is common for simplified e-invoices in Commerce and regular tax e-invoices in Dynamics 365 Finance.
1. CRT sends a request to Commerce headquarters to provide a digital certificate.
1. Commerce headquarters extracts the digital certificate from Azure Key Vault and sends it back to CRT. For more information about how Commerce handles digital certificates, see the [Configure the digital signature parameters](#configure-the-digital-signature-parameters) section.

    > [!NOTE]
    > If POS is in the offline mode, the local copy of CRT uses a digital certificate installed locally on the POS machine.

1. CRT calculates the invoice hash, digitally signs the e-invoice data, and generates a QR code that includes the invoice hash and digital signature data. CRT  also amends the XML invoice with the invoice hash and digital signature data. The e-invoice, the invoice hash, the QR code, and other information are saved in the channel database (DB) in a fiscal transaction that is linked to the sales transaction.
1. POS requests a sales receipt from CRT. CRT builds the receipt, including the QR code, and sends it back to POS. POS sends the receipt to the receipt printer.
1. Commerce headquarters downloads the sales transaction data together with fiscal transactions from CSU via Commerce Data Exchange (CDX). The data is stored in the headquarters DB throughout the period of life of your production environment.
1. Commerce headquarters extracts the simplified e-invoice in the XML format from the fiscal transaction that is linked to the sales transaction and submits the e-invoice to ZATCA. The submission is done by means of integration with the [Electronic Invoicing service](../../finance/localizations/e-invoicing-sa-get-started.md). For more information about the common electronic invoicing capabilities available to Saudi Arabia, see [Customer electronic invoices in Saudi Arabia](../../finance/localizations/emea-sau-e-invoices.md).

## Set up Commerce for Saudi Arabia

This section describes the Commerce settings that are specific to and recommended for Saudi Arabia. For more information about common Commerce features and settings, see [Commerce home page](../index.md).

As a prerequisite, you should complete the setup of the electronic invoicing functionality for Saudi Arabia, including the Electronic invoicing service configuration. For more information, see [Customer electronic invoices in Saudi Arabia](../../finance/localizations/emea-sau-e-invoices.md).

To use the Saudi Arabia-specific Commerce functionality, you must complete these tasks:

- Set the **Country/region** field to **SAU** (Saudi Arabia) in the primary address of the legal entity.
- Set the **ISO code** field to **SA** (Saudi Arabia) in the POS functionality profile of every store that is located in Saudi Arabia.

You must also specify the following settings for Saudi Arabia. Note that you must run appropriate distribution jobs after you complete the setup.

1. [Enable Commerce features](#enable-features-for-saudi-arabia) for Saudi Arabia in the **Feature management** workspace.
1. [Set up VAT](#set-up-vat-per-saudi-arabia-requirements) per the Saudi Arabia VAT regulations.
1. [Configure custom fields](#configure-custom-fields-so-that-they-can-be-used-in-receipt-formats-for-sales-receipts) and [receipt formats](#configure-receipt-formats) to print QR codes in receipts and comply with the local regulatory requirements.
1. [Configure the fiscal registration functionality](#set-up-fiscal-registration) for Saudi Arabia to enable generation and digital signing of simplified e-invoices.
1. [Configure digital certificates](#configure-the-digital-signature-parameters) and other parameters of digital signing for the Commerce channel side.
1. [Specify Electronic reporting (ER) configurations](#specify-electronic-reporting-configurations) that should be used to generate simplified e-invoices in POS and submit these simplified e-invoices from Commerce headquarters.
1. [Configure e-invoice submission](#configure-e-invoice-submission) for simplified e-invoices generated in POS.
1. [Enable the digital signature in offline mode](#enable-the-digital-signature-in-offline-mode).

### Enable features for Saudi Arabia

You must enable the following features in the **Feature management** workspace:

- KSA Electronic-Invoicing capability for the fiscal integration framework
- (Saudi Arabia) Electronic invoicing integration

### Set up VAT per Saudi Arabia requirements

You must create sales tax codes, sales tax groups, and item sales tax groups. You must also set up sales tax information for products and services. For more information about how to set up and use sales tax, see [Sales tax overview](../../finance/general-ledger/indirect-taxes-overview) and [Configure sales tax codes](../../finance/localizations/emea-sau-e-invoices.md#configure-sales-tax-codes).

You must also specify sales tax groups and enable the **Prices include sales tax** option for stores that are located in Saudi Arabia.

### Configure custom fields so that they can be used in receipt formats for sales receipts

You can configure the language text and custom fields that are used in the POS receipt formats. The default company of the user who creates the receipt setup should be the same legal entity where the language text setup is created. Alternatively, the same language texts should be created in both the user's default company and the legal entity of the store that the setup is created for.

On the **Language text** page, on the **POS** tab, add the following records for the labels of the custom fields for receipt layouts. Note that the **Language ID**, **Text ID**, and **Text** values that are shown in the table are just examples. You can change them to meet your requirements. However, the **Text ID** values that you use must be unique, and they must be equal to or higher than 900001.

| Language ID | Text ID | Text                      |
|-------------|---------|---------------------------|
| en-US       | 900001  | QR Code                   |

On the **Custom fields** page, add the following records for the custom fields for receipt layouts. Note that **Caption text ID** values must correspond to the **Text ID** values that you specified on the **Language text** page.

| Name                            | Type    | Caption text ID |
|---------------------------------|---------|-----------------|
| INVOICEQRCODE_SA                | Receipt | 900001          |

On the **Commerce parameters** page, on the **Configuration parameters** tab, add the following records:

| Name                                   | Value    |
|----------------------------------------|----------|
| RetailEInvoiceFeature_SA.QrCodeHeight  | 200      |
| RetailEInvoiceFeature_SA.QrCodeWidth   | 200      |

### Configure receipt formats

For every required receipt format, change the value of the **Print behavior** field to **Always print**. You must also configure hardware profiles to support receipt printers and to enable Hardware station. For more information about how to work with POS peripherals, see [Peripherals](../retail-peripherals-overview.md).

In the Receipt format designer, add the following custom fields to the appropriate receipt sections. Note that field names correspond to the language texts that you defined in the previous section.

- **Footer:** Add the following fields:

    - **QR Code** – This field prints the QR code for the receipt.

For more information about how to work with receipt formats, see [Set up and design receipt formats](../receipt-templates-printing.md).

### Set up fiscal registration

Complete the fiscal registration setup steps that are described in [Set up the fiscal integration for Commerce channels](./setting-up-fiscal-integration-for-retail-channel.md):

1. [Set up a fiscal registration process](./setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process). Be sure to note the settings of the fiscal registration process that are [specific to Saudi Arabia](#configure-the-fiscal-registration-process).
1. [Set error handling settings](./setting-up-fiscal-integration-for-retail-channel.md#set-error-handling-settings).
1. [Enable manual execution of deferred fiscal registration](./setting-up-fiscal-integration-for-retail-channel.md#enable-manual-execution-of-deferred-fiscal-registration).

#### Configure the fiscal registration process

To enable the fiscal registration process for Saudi Arabia in Commerce headquarters, follow these steps.

1. Download configuration files for the fiscal document provider and the fiscal connector from the Commerce SDK:

    1. Open the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository.
    2. Open the last available release branch.
    3. Open **src \> FiscalIntegration \> ElectronicInvoiceSaudiArabia**.
    4. Download the fiscal connector configuration file at **ConnectorSample.xml**.
    5. Download the fiscal document provider configuration file at **DocumentProviderSample.xml**.

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Shared parameters**. On the **General** tab, set the **Enable fiscal integration** option to **Yes**.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connectors**, and load the fiscal connector configuration file that you downloaded earlier.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal document providers**, and load the fiscal document provider configuration file that you downloaded earlier.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector functional profiles**. Create a new connector functional profile, and select the document provider and the connector that you loaded earlier. Update the data mapping settings as required.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector technical profiles**. Create a new connector technical profile, and select the connector that you loaded earlier. Set the connector type to **Internal**. Update the other connection settings as required.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connector groups**, and create a new fiscal connector group for the connector functional profile that you created earlier.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal registration processes**. Create a new fiscal registration process, create a fiscal registration process step, and select the fiscal connector group that you created earlier.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**. Select a functionality profile that is linked to the store where the registration process should be activated. On the **Fiscal registration process** FastTab, select the fiscal registration process that you created earlier. On the **Fiscal services** FastTab, select the connector technical profile that you created earlier. 
1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**. Open the distribution schedule, and select jobs **1070** and **1090** to transfer data to the channel database.

### Configure the digital signature parameters

To digitally sign and submit simplified e-invoices, you must obtain so called Cryptographic Stamp Identifiers (CSIDs) from ZATCA. The CSIDs are got in form of digital certificates. For more information on how to obtain CSIDs, see [Electronic invoicing onboarding in Saudi Arabia](../../finance/localizations/e-invoicing-sa-onboarding.md). You must obtain a CSID for each POS register that you are going to use, because sequential numbering and digital signing of simplified e-invoices is done per POS register.

The digital certificates that are to be used for digital signing of simplified e-invoices are stored in Azure Key Vault. For the offline mode of Modern POS, the signing can also be done by using a digital certificate that is stored in the local storage of the machine that Modern POS is installed on. The [User-defined certificate profiles for retail stores](./certificate-profiles-for-retail-stores.md) feature enables configuration of certificates that are stored in Key Vault. It also supports failover to offline mode when Key Vault or Commerce headquarters aren't available. This feature extends the [Manage secrets for retail channels](../dev-itpro/manage-secrets.md) feature.

To configure certificates and certificate profiles that can be used for digital signing, follow the steps in [Set up certificate profiles](./certificate-profiles-for-retail-stores.md#set-up-certificate-profiles). You must configure a certificate profile for each individual CSID that you obtain from ZATCA.

After you configure certificate profiles, go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector technical profiles** and select the connector technical profile that you created earlier. To configure certificate profiles per POS register, select the **Override** menu item and create records for all registers that you need to specify CSIDs for. In each record, specify a corresponding certificate profile in the **Certificate profile** field on the **Device** FastTab. For more details on how to override connector technical profile settings, see [Create connector technical profiles](./setting-up-fiscal-integration-for-retail-channel.md#create-connector-technical-profiles).

### Specify Electronic Reporting configurations

Depending on your purposes, you can download the ER configurations for electronic invoicing from the following sources:

- If you don't have to customize the ER configurations that are provided by Microsoft or create your own ER configurations, you can import the Microsoft-provided configurations from Microsoft Dynamics Lifecycle Services. For more information, see [Import a configuration from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md). Alternatively, you can [download ER configurations from the Global repository of Configuration service](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).
- If you must customize the ER configurations that are provided by Microsoft or create your own ER configurations, you must provision a Regulatory Configuration Services (RCS) environment. For more information about how to work with RCS, see [Import ER configurations from RCS](../../fin-ops-core/dev-itpro/analytics/rcs-download-configurations.md).

You must download the latest versions of the following configurations:

- E-invoice generation configurations:
    - **Invoice model** data model
    - **Invoice model mapping for commerce (SA)** data model mapping
    - **Sales e-invoice (SA)** format
- E-invoice submission configurations:
    - **Customer invoice context model** data model
    - **Retail channel data** data model
    - **Retail fiscal document mapping** data model mapping
    - **Retail fiscal document format** format

You must also configure legal entity-specific parameters of the e-invoice format:

1. Open the **Electronic reporting** workspace.
1. Click **Reporting configurations**.
1. On the **Configurations** page, select the *Sales e-invoice (SA)* format that you imported earlier, and click **Configurations > Application specific parameters > Setup**.
1. On the **Application specific parameters** page, select the version of the format configuration that you want to configure the parameters for.
1. On the **Lookups** FastTab, select the record for the *PaymentMethodSubstitutionLookup* lookup.
1. On the **Conditions** FastTab, create records to link methods of payment that are configured for customers in the **Accounts receivable** module to payment means that are defined for e-invoices by ZATCA:
    1. In the **Lookup result** field, select a payment means code.
    1. In the **Name** field, select a customer payment method that must correspond to the payment means code. You can also select \*Blank\* if you want the payment means code to be selected when the customer payment method is not specified, and \*Not blank\* if you want the payment means code to be selected for any customer payment method.
    1. The **Line** field is populated automatically. It defines the order in which payment means codes are searched for a customer payment method. You can change the order by using the **Move up** and **Move down** buttons.
1. Complete the configuration by setting **State** to *Completed*.

### Configure e-invoice submission

Before setting up e-invoice submission parameters for Commerce, you must configure the Electronic invoicing service to be used for Saudi Arabia. For more information, see [Get started with Electronic invoicing for Saudi Arabia](../../finance/localizations/e-invoicing-sa-get-started.md). To support the configuration of CSIDs per POS register, you need to make the following steps for each POS register in your Electronic Invoicing environment:

1. Add a corresponding CSID certificate to Key Vault parameters of the environment.
2. Create a feature setup for the electronic invoicing feature. To do this, you can configure the first feature setup and then create new feature setups by copying them from the first one and modifying its parameters.
3. In the  Specify the name of the CSID certificate added earlier and modify 

Follow these steps to set up e-invoice submission parameters that are specific to Commerce for Saudi Arabia.

1. Open **Electronic document parameters**.
1. On the **Electronic document** tab, create a new record and specify the following parameters:
    1. Select *Fiscal transaction document* in the **Table name** field.
    1. Select *Retail fiscal document context* in the **Document context** field.
    1. Select *Retail fiscal document mapping* in the **Electronic document model mapping** field.
    1. Select number sequences for submitted file names and batch submission IDs.
1. On the **Features** tab, mark the **Saudi Arabia electronic invoice** feature as **Enabled**.
1. On the **Electronic Invoicing** tab, set the following fields:
    1. **Endpoint URL**: specify the endpoint URL of the Electronic invoicing service instance that you are using.
    1. **Environment**: specify the name of your Electronic Invoicing environment in the Regulatory Configuration Service (RCS).

### Enable the digital signature in offline mode

To enable the digital signature in offline mode, you must follow these steps after you activate POS on a new device.

1. Sign in to POS.
1. On the **Database connection status** page, ensure that the offline database is fully synchronized. When the value of the **Pending downloads** field is **0** (zero), the database is fully synchronized.
1. Sign out of POS.
1. Wait for the offline database to be fully synchronized.
1. Sign in to POS.
1. On the **Database connection status** page, ensure that the offline database is fully synchronized. When the value of the **Pending transactions in offline database** field is **0** (zero), the database is fully synchronized.
1. Restart POS.

## E-invoice submission

To initiate the submission of simplified e-invoices to ZATCA, run the **Submit electronic documents** periodic operation in Commerce headquarters.

You can check the submission log on the **Electronic document submission log** page.
