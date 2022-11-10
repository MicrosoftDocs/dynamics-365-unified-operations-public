---
title: Generate and submit simplified electronic invoices for Saudi Arabia
description: This article provides an overview and setup guidelines for the functionality of simplified electronic invoices that is available for Saudi Arabia in Microsoft Dynamics 365 Commerce.
author: EvgenyPopovMBS
ms.date: 11/21/2022
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

The electronic invoicing functionality that is available for Saudi Arabia in Commerce provides the following capabilities:

- Generation of an XML file of a simplified e-invoice upon concluding a sales transaction in Commerce point of sale (POS).
- Generation of a cryptographic stamp for the simplified e-invoice.
- Generation and printing of QR code for the simplified e-invoice that includes the cryptographic stamp.
- Submission of the simplified e-invoice from Commerce headquarters to Saudi Arabian tax authorities (Zakat, Tax and Customs Authority - ZATCA) for reporting purposes.

For more information about the electronic invoicing requirements for Saudi Arabia, see [E-Invoicing portal by ZATCA](https://zatca.gov.sa/en/E-Invoicing/Pages/default.aspx).

The high-level, end-to-end process flow for Saudi Arabia is as follows:

1. When the checkout process is completed for a sales transaction in POS, POS sends a request to generate and digitally sign an e-invoice to the Commerce runtime (CRT) via Commerce Scale Unit (CSU). The generation and digital signing of an e-invoice is implemented by using the [Fiscal registration framework](./fiscal-integration-for-retail-channel.md) and an [internal](./fiscal-integration-for-retail-channel.md#fiscal-registration-is-done-internally-in-the-crt) connector.

    > [!NOTE]
    > If POS is in the offline mode, the generation and digital signing of an e-invoice occurs in the local copy of CRT on the POS machine.

1. CRT generates a simplified e-invoice in an XML format. The XML format of e-invoice for Saudi Arabia is implemented by using [Electronic reporting (ER)](../../dev-itpro/analytics/general-electronic-reporting.md). The format is common for simplified e-invoices in Commerce and regular tax e-invoices in Dynamics 365 Finance.
1. CRT sends a request to Commerce headquarters to provide a digital certificate.
1. Commerce headquarters extracts the digital certificate from Azure Key Vault and sends it back to CRT. For more information about how Commerce handles digital certificates, see the [Configure the digital signature parameters](#configure-the-digital-signature-parameters) section.

    > [!NOTE]
    > If POS is in the offline mode, the local copy of CRT uses a digital certificate installed locally on the POS machine.

1. CRT digitally signs the e-invoice data. The e-invoice and the signature, together with other information, is saved in the channel database (DB) in a fiscal transaction that is linked to the sales transaction.
1. POS requests a sales receipt from CRT. CRT builds the receipt, including a QR code, and sends it back to POS. POS sends the receipt to the receipt printer.
1. Commerce headquarters downloads the sales transaction data together with fiscal transactions from CSU via Commerce Data Exchange (CDX). The data is stored in the headquarters DB throughout the period of life of your production environment.
1. Commerce headquarters extracts the e-invoice in the XML format from the fiscal transaction linked to the sales transaction and submits the e-invoice to ZATCA. The submission is done by means of integration with the [Electronic Invoicing service](../../finance/localizations/e-invoicing-sa-get-started.md). For more information about the common electronic invoicing capabilities available for Saudi Arabia, see [Customer electronic invoices in Saudi Arabia](../../finance/localizations/emea-sau-e-invoices.md).

## Set up Comerce for Saudi Arabia

This section describes the Commerce settings that are specific to and recommended for Saudi Arabia. For more information about common Commerce features and settings, see [Commerce home page](../index.md).

To use the Saudi Arabia-specific functionality, you must complete these tasks:

- Set the **Country/region** field to **SAU** (Saudi Arabia) in the primary address of the legal entity.
- Set the **ISO code** field to **SA** (Saudi Arabia) in the POS functionality profile of every store that is located in Saudi Arabia.

You must also specify the following settings for Saudi Arabia. Note that you must run appropriate distribution jobs after you complete the setup.

1. [Enable Commerce features](#enable-features-for-saudi-arabia) for Saudi Arabia in the **Feature management** workspace.
1. [Specify a tax registration number](#set-up-the-legal-entity) of the organization on the **Legal entities** page.
1. [Set up VAT](#set-up-vat-per-saudi-arabia-requirements) per the Saudi Arabia VAT regulations.
1. [Configure custom fields](#configure-custom-fields-so-that-they-can-be-used-in-receipt-formats-for-sales-receipts) and [receipt formats](#configure-receipt-formats) to comply with the local regulatory requirements.
1. [Configure the fiscal registration functionality](#set-up-fiscal-registration) for Saudi Arabia to enable digital signing of sales transactions and audit events.
1. [Configure digital certificates](#configure-the-digital-signature-parameters) and other parameters of digital signing for the Commerce channel and Commerce headquarters sides.
1. [Specify Electronic reporting (ER) formats](#configure-the-z-report-and-archive-export-formats) that should be used to export Z-reports and fiscal archives from Commerce headquarters.
1. [Reinitialize Commerce components](#reinitialize-commerce-components) to enable France-specific audit events and transmission of France-specific data from POS to Commerce headquarters.
1. [Configure channel components](#configure-channel-components) to enable France-specific extensions of the components.

    > [!IMPORTANT]
    > You should configure channel components only if you're using Commerce version 10.0.28 or earlier. As of version 10.0.29, all required Commerce channel components for France are enabled out of the box. If you're using Commerce version 10.0.28 or earlier, and are migrating to Commerce version 10.0.29 or later, you must follow the steps in [Migrate to Commerce version 10.0.29 or later](./emea-fra-fi-deployment.md#migrate-to-commerce-version-10029-or-later).

1. [Enable the digital signature in offline mode](#enable-the-digital-signature-in-offline-mode).
1. [Validate your configuration](#compliance-checklist) to make sure all France-specific features work properly.

### Enable features for Saudi Arabia

You must enable the following features in the **Feature management** workspace:

- KSA Electronic-Invoicing capability for the fiscal integration framework

### Set up the legal entity

You must make the following changes on the **Legal entities** page.

- On the **Tax registration** FastTab, in the **Tax registration number** field, specify the VAT registration number of the organization.

### Set up VAT per Saudi Arabia requirements

You must create sales tax codes, sales tax groups, and item sales tax groups. You must also set up sales tax information for products and services. For more information about how to set up and use sales tax, see [Sales tax overview](/dynamics365/finance/general-ledger/indirect-taxes-overview).

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

On the **Commerce parameters** page, on the **Configuration parameters** tab, add the following records^

| Name                                   | Value    |
|----------------------------------------|----------|
| RetailEInvoiceFeature_SA.QrCodeHeight  | 200      |
| RetailEInvoiceFeature_SA.QrCodeWidth   | 200      |

### Configure receipt formats

For every required receipt format, change the value of the **Print behavior** field to **Always print**. You must also configure hardware profiles to support receipt printers and to enable Hardware station. For more information about how to work with POS peripherals, see [Peripherals](../retail-peripherals-overview.md).

In the Receipt format designer, add the following custom fields to the appropriate receipt sections. Note that field names correspond to the language texts that you defined in the previous section.

- **Footer:** Add the following fields:

    - **QR Code** – This field the QR code for the receipt.

For more information about how to work with receipt formats, see [Set up and design receipt formats](../receipt-templates-printing.md).

### Set up fiscal registration

Complete the fiscal registration setup steps that are described in [Set up the fiscal integration for Commerce channels](./setting-up-fiscal-integration-for-retail-channel.md):

1. [Set up a fiscal registration process](./setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process). Be sure to note the settings of the fiscal registration process that are [specific to France](#configure-the-fiscal-registration-process).
1. [Set error handling settings](./setting-up-fiscal-integration-for-retail-channel.md#set-error-handling-settings).
1. [Enable manual execution of deferred fiscal registration](./setting-up-fiscal-integration-for-retail-channel.md#enable-manual-execution-of-deferred-fiscal-registration).

#### Configure the fiscal registration process

To enable the fiscal registration process for France in Commerce headquarters, follow these steps.

1. Download configuration files for the fiscal document provider and the fiscal connector from the Commerce SDK:

    1. Open the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository.
    2. Open the last available release branch.
    3. Open **src \> FiscalIntegration \> SequentialSignatureFrance \> Configurations**.
    4. Download the fiscal connector configuration file at **Connector \> ConnectorMicrosoftSequentialSignatureFRA.xml**.
    5. Download the fiscal document provider configuration file at **DocumentProvider \> DocumentProviderMicrosoftSequentialSignatureFRA.xml**.

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

You must configure certificates that will be used for digital signing of records on the Commerce channel side (sales transactions and audit events) and on the Commerce headquarters side (period grand total journals, Z reports, and fiscal archives). The signing is done by using a digital certificate that is stored in Azure Key Vault. For the offline mode of Modern POS, the signing can also be done by using a digital certificate that is stored in the local storage of the machine that Modern POS is installed on. The [User-defined certificate profiles for retail stores](./certificate-profiles-for-retail-stores.md) feature enables configuration of certificates that are stored in Key Vault. It also supports failover to offline mode when Key Vault or Commerce headquarters isn't available. This feature extends the [Manage secrets for retail channels](../dev-itpro/manage-secrets.md) feature.

> [!NOTE]
> You can use either a digital certificate that is issued by an accredited body or a self-signed certificate for digital signing. Only certificates that have RSA-2048-bit or Elliptic Curve Digital Signature Algorithm (ECDSA) 224-bit minimum private keys are acceptable. Commerce supports only RSA-2048-bit or longer keys. If you want to use an ECDSA key, you must implement a customization.

To configure certificates and certificate profiles that can be used for digital signing, follow the steps in [Set up certificate profiles](./certificate-profiles-for-retail-stores.md#set-up-certificate-profiles).

After you configure certificate profiles, go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector technical profiles**, select the connector technical profile that you created earlier, and then, on the **Settings** FastTab, set the following parameters for digital signatures:

- **Certificate profile** – Select the certificate profile that you configured earlier.
- **Hash algorithm** – Specify one of the cryptographic hash algorithms that are supported by Microsoft .NET (for example, **SHA256**).
- **Activate health check** – For more information about the health check feature, see [Fiscal registration health check](./fiscal-integration-for-retail-channel.md#fiscal-registration-health-check).

Finally, on the **Commerce parameters** page (**Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**), you must specify the following parameters for digital signing on the Commerce headquarters side:

- **Certificate** – Select a certificate that is stored in Key Vault.
- **Hash function** – Specify one of the cryptographic hash algorithms that are supported by Microsoft .NET, such as **SHA256**.
- **Encoding** – Specify the encoding of the signed data, such as **UTF-8**.
- You can also specify a number sequence to use for automatic numbering of period grand total journals. On the **Number sequences** tab, select a record where the **Reference** field is set to **Period grand total journal**, and then select a number sequence code in it.

> [!NOTE]
> The following hash functions aren't acceptable: CRC16, CRC32, SHA-1, and MD5. Commerce supports only the SHA256, SHA384, and SHA512 hash functions. If you want to use a different hash function, you must implement a customization.

### Configure the Z report and archive export formats

Depending on your purposes, you can download the ER configurations for the Z report and archive from the following sources:

- If you don't have to customize the ER configurations that are provided by Microsoft or create your own ER configurations, you can import the Microsoft-provided configurations from Microsoft Dynamics Lifecycle Services. For more information, see [Import a configuration from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md). Alternatively, you can [download ER configurations from the Global repository of Configuration service](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).
- If you must customize the ER configurations that are provided by Microsoft or create your own ER configurations, you must provision a Regulatory Configuration Services (RCS) environment. For more information about how to work with RCS, see [Import ER configurations from RCS](../../fin-ops-core/dev-itpro/analytics/rcs-download-configurations.md).

You must download the following versions (or later versions) of the configurations:

- **Retail channel data.version.2** data model
- **Archiving DMM.version.2.3** data model mapping
- **Retail Z-Report (FR).version.24.23.3** format
- **Retail data archive (FR).version.2.5** format

After you import the configurations, select ER formats for the Z report and archive in the following fields on the **Electronic documents** tab of the **Commerce parameters** page:

- **Z-Report export format** – Select the **Retail Z-Report (FR).version.24.23.3** format or the format that you downloaded earlier.
- **Retail data archive export format** – Select the **Retail data archive (FR).version.2.5** format or the format that you downloaded earlier.

### Reinitialize Commerce components

> [!NOTE]
> You only need to complete the steps of this section if you are updating an existing environment.

To enable audit events, you must reinitialize the Commerce extensible enumerations. To enable France-specific data to be transmitted from POS to Commerce headquarters, you must reinitialize the Commerce scheduler.

1. On the **Commerce parameters** page, on the **General** FastTab, select **Initialize**. For more information, see [Initialize seed data in new Retail environments](../enable-configure-retail-functionality.md).
1. There is an option to separately configure the scheduler. Go to **Commerce scheduler** \> **Initialize Commerce scheduler**. In the **Initialize Commerce scheduler** dialog box, select **OK**.

### Configure channel components

> [!IMPORTANT]
> You should configure channel components only if you're using Commerce version 10.0.28 or earlier. As of version 10.0.29, all required Commerce channel components for France are enabled out of the box. If you're using Commerce version 10.0.28 or earlier, and are migrating to Commerce version 10.0.29 or later, you must follow the steps in [Migrate to Commerce version 10.0.29 or later](./emea-fra-fi-deployment.md#migrate-to-commerce-version-10029-or-later).

To enable France-specific functionality, you must configure extensions for channel components. For more information, see the [deployment guidelines](./emea-fra-fi-deployment.md).

> [!NOTE]
> This version of the Commerce functionality for France is based on the [Fiscal integration framework](./fiscal-integration-for-retail-channel.md). For information about the legacy digital signing sample for France, see [Deployment guidelines for cash registers for France (legacy)](./emea-fra-deployment.md). For guidance about how to enable the fiscal integration functionality for France in existing environments that use the legacy digital signing sample, see [Migrate from legacy Commerce functionality for France](./emea-fra-fi-migration.md).

### Enable the digital signature in offline mode

To enable the digital signature in offline mode, you must follow these steps after you activate POS on a new device.

1. Sign in to POS.
1. On the **Database connection status** page, ensure that the offline database is fully synchronized. When the value of the **Pending downloads** field is **0** (zero), the database is fully synchronized.
1. Sign out of POS.
1. Wait for the offline database to be fully synchronized.
1. Sign in to POS.
1. On the **Database connection status** page, ensure that the offline database is fully synchronized. When the value of the **Pending transactions in offline database** field is **0** (zero), the database is fully synchronized.
1. Restart POS.
