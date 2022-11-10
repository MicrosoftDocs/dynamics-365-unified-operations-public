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
1. Commerce headquarters downloads the transaction data together with fiscal transactions from CSU via Commerce Data Exchange (CDX). The data is stored in the headquarters DB throughout the period of life of your production environment.
1. Commerce headquarters submits the e-invoice the ZATCA. The submission is done by means of integration with the [Electronic Invoicing service](../../finance/localizations/e-invoicing-sa-get-started.md). For more information about the common electronic invoicing capabilities available for Saudi Arabia, see [Customer electronic invoices in Saudi Arabia](../../finance/localizations/emea-sau-e-invoices.md).

## Set up Comerce for Saudi Arabia

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
