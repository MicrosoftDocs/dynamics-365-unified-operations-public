---
# required metadata

title: Cash register functionality for Norway
description: This topic provides an overview of the cash register functionality that is available for Norway. It also provides guidelines for setting up the functionality.
author: EvgenyPopovMBS
ms.date: 09/28/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: RetailPosPermissionGroup, RetailFunctionalityProfile, RetailFormLayout, RetailParameters
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Norway
ms.search.industry: Retail
ms.author: epopov
ms.search.validFrom: 2017-10-31
ms.dyn365.ops.version: Application update 4
---
# Cash register functionality for Norway

[!include [banner](../includes/banner.md)]

This topic provides an overview of the cash register functionality that is available for Norway in Dynamics 365 Commerce. It also provides guidelines for setting up the functionality. The functionality consists of the following parts:

- Common point-of-sale (POS) features that are available to customers in all countries or regions. Examples include an option that lets you prevent a copy of a receipt from being printed more than one time.
- Norway-specific features, such as digital signatures for sales transactions.

## Overview of cash register functionality for Norway

### Common POS features

To learn about POS features that are available to customers in all countries or regions, see [Help resources for Dynamics 365 Retail](../index.md).

The following POS localization features that were previously implemented and made available to customers in all countries or regions can now be used specifically for Norway:

- **Print text fields on a receipt in a large font size.** You can use the **Font size** parameter in the Receipt format designer to specify that the large font size should be used for a field in the receipt format. (The large font size is approximately double the usual font size.) For example, you can use this parameter to print the "Copy" indicator on a copy of a receipt in large characters.
- **Register the printing of receipt copies in the POS audit event log.** You can use the **Audit** parameter in the POS functionality profile to enable copies of receipts to be printed and other POS audit events to be registered. The audit events are registered in the channel database and in Headquarters. You can view the audit events on the **Audit events** page.
- **Prevent a copy of a receipt from being printed more than one time.** When the **Audit** parameter in the POS functionality profile is enabled, the **Allow printing receipt copies** POS permission controls whether copies of receipts can be printed. There is also an option that lets you prevent a copy of a receipt from being printed more than one time.

Additionally, the following POS feature was implemented for Norway but made available to customers in all countries or regions:

- **Register additional events in the POS audit event log.** If the **Audit** parameter in the POS functionality profile is enabled, the following events are registered in the POS audit event log:

    - Price checks
    - Tax overrides
    - Corrections to line quantities
    - Clearing transactions from the channel database

### Norway-specific POS features

The following Norway-specific POS features are enabled when the **ISO code** parameter in the POS functionality profile is set to **No**.

#### Digital signing of sales transactions

Every sales transaction is digitally signed. The signature is created and recorded in the POS transaction journal at the same time that the transaction is finalized. The signature is also available in the journal that is exported for audit purposes.

Only transactions for cash sales are signed. Here are some examples of transactions that are excluded from the signing process:

- Prepayments (customer account deposit)
- Prepayments for sales orders (customer order deposit)
- Issuing a gift card
- Non-sales transactions (float entry, tender removal, and so on)

The data that is signed is a text string that consists of the following data fields. The data fields are separated by semicolons.

1. Previous signature for the same POS (A zero \[**0**\] is used for the first transaction.)
2. Transaction date
3. Transaction time
4. Sequential signed transaction number
5. Transaction amount including tax
6. Transaction amount excluding tax

The digital signing process uses an RSA 1024-bit key that has a SHA-1 hash function (RSA-SHA1-1024). A certificate that is installed on Commerce Scale Unit is used for signing. The unique identifier of the certificate (footprint) is recorded together with the signature.

The signature is stored in the store database and the headquarters (HQ) database together with the transaction data. You can view the transaction signature, together with the transaction data that was used to generate it, on the **Fiscal transactions** FastTab of the **Store transactions** page.

#### Receipts

Receipts for Norway can include additional information that was implemented by using custom fields:

- **Receipt title** – You can add a field to a receipt format layout to identify the type of receipt. For example, a sales receipt will include the text "Sales receipt".
- **Signed transaction sequential number** – The sequential number of a signed transaction can appear on the receipt to associate a printed receipt with a digital signature in the database.
- **Receipt totals** – Custom fields for receipt totals exclude non-sales amounts from total transaction amounts. Non-sales amounts include amounts for the following operations:

    - Prepayments (customer account deposit)
    - Prepayments for sales orders (customer order deposit)
    - Issuing a gift card
    - Adding funds to a gift card

#### X and Z reports

The information that is included on X and Z reports is based on Norwegian requirements. For example, **Total cash sales** amounts include only amounts for cash sales transactions and exclude issue gift card operations and prepayments. Total cash sales are also listed per item group and payment method. In addition, cumulative **Grand total sales** and **Grand total returns** amounts are maintained and printed.

#### SAF-T Cash Register audit file

You can export the POS transaction journal in the predefined Standard Audit File - Tax (SAF-T) Cash Register format. The audit file includes information about the organization, relevant master data (such as item groups, items, and tax codes), cash sales transaction data together with signatures for those transactions, non-sales event data, and end-of-date report data.

The audit file can be exported for the following scenarios:

- Per store
- All stores
- Per terminal
- All terminals

You can also send a report from one legal entity on behalf of another legal entity. In this case, you must run the export from the operating legal entity and specify the reporting legal entity as the sender of the report.

The SAF-T Cash Register format is implemented at Headquarters by using [Electronic reporting](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md). 

## Setting up Commerce for Norway

This section describes the settings that are specific to and recommended for Norway. For more information, see [Help resources for Dynamics 365 Retail](../index.md).

To use the Norway-specific functionality, you must complete these tasks:

- Set the **Country/region** field to **NOR** (Norway) in the primary address of the legal entity.
- Set the **ISO code** field to **NO** (Norway) in the POS functionality profile of every store that is located in Norway.

You must also specify the following settings for Norway.

### Set up the legal entity

Make sure that the name of the legal entity is specified. This name will be printed on X and Z reports.

Additionally, on the **Bank account information** FastTab, in the **Routing number** field, specify the organization number.

### Set up value-added tax (VAT) per Norwegian requirements


You must create sales tax codes, sales tax groups, and item sales tax groups. You must also set up sales tax information for products and services. For more information about how to set up and use sales tax, see [Sales tax overview](../../finance/general-ledger/indirect-taxes-overview.md).

You must also specify sales tax groups and enable the **Prices include sales tax** option for stores that are located in Norway.

### Set up functionality profiles

You must enable auditing and set up receipt numbering.

### Update POS permissions groups and individual permission settings for store workers

Set the **Allow printing receipt copy** permission to an appropriate value:

- **Allow always** – The operator can print a copy of a receipt multiple times.
- **Allow only once** – The operator can print a copy of a receipt only one time.
- **Allow only once, and only if HQ DB is available** – The operator can print a copy of a receipt only one time, and only if the HQ database is available through Commerce Data Exchange: Real-time Service, so that the system can verify that no copies of the receipt have previously been printed in any store.
- **Never** – The operator can't print a copy of a receipt.

### Configure custom fields so that they can be used in receipt formats for sales receipts

On the **Language text** page, add the following records for the labels of the custom fields for receipt layouts. Note that the **Language ID**, **Text ID**, and **Text** values that are shown in the table are just examples. You can change them to meet to your requirements.

| Language ID | Text                   | Text ID |
|-------------|------------------------|---------|
| en-US       | Receipt title          | 900011  |
| en-US       | Is gift card           | 900012  |
| en-US       | Total (sales)          | 900013  |
| en-US       | Tax total (sales)      | 900014  |
| en-US       | Total with tax (sales) | 900015  |
| en-US       | Tax amount (sales)     | 900016  |
| en-US       | Cash transaction ID    | 900017  |

On the **Custom fields** page, add the following records for the custom fields for receipt layouts. Note that **Caption text ID** values must correspond to the **Text ID** values that you specified on the **Language text** page.

| Name                            | Type    | Caption text ID |
|---------------------------------|---------|-----------------|
| ReceiptTitle                    | Receipt | 900011          |
| IsGiftCard                      | Receipt | 900012          |
| SalesTotalExt                   | Receipt | 900013          |
| TaxTotalExt                     | Receipt | 900014          |
| TotalWithTaxExt                 | Receipt | 900015          |
| AmountPerTaxExt                 | Receipt | 900016          |
| CashTransactionSequentialNumber | Receipt | 900017          |

### Configure receipt formats

For all required receipt formats, change the value of the **Print behavior** field to **Always print** for the receipt format.

In the Receipt format designer, add the following custom fields to the appropriate receipt sections. Note that field names correspond to the language texts that you defined in the previous section.

1. Header:

    - **Receipt title** – This field identifies the type of receipt.
    - **Cash transaction ID** – This field prints the sequential number of the signed cash transaction.

2. Lines:

    - **Is gift card** – This field marks the receipt line as related to the Issue gift card or Add to gift card operation.

3. Footer:

    - **Total (sales)** – This field prints the receipt's total cash sale amount. The amount excludes tax. Prepayments and gift card operations are excluded.
    - **Tax total (sales)** – This field prints the receipt's total tax amount for cash sales. Prepayments and gift card operations are excluded.
    - **Total with tax (sales)** – This field prints the receipt's total cash sale amount. The amount includes tax. Prepayments and gift card operations are excluded.
    - **Tax amount (sales)** – This field prints the receipt's tax amount for cash sales per tax code. Prepayments and gift card operations are excluded.

For more information about how to work with receipt formats, see [Set up and design receipt formats](../receipt-templates-printing.md).

### Set up fiscal registration

Complete the fiscal registration setup steps that are described in [Set up the fiscal integration for Commerce channels](./setting-up-fiscal-integration-for-retail-channel.md):

1. [Set up a fiscal registration process](./setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process). Be sure to note the settings of the fiscal registration process that are [specific to France](#configure-the-fiscal-registration-process).
1. [Set error handling settings](./setting-up-fiscal-integration-for-retail-channel.md#set-error-handling-settings).
1. [Enable manual execution of postponed fiscal registration](./setting-up-fiscal-integration-for-retail-channel.md#enable-manual-execution-of-postponed-fiscal-registration).

#### Configure the fiscal registration process

To enable the fiscal registration process for France in Commerce headquarters, follow these steps.

1. Download configuration files for the fiscal document provider and the fiscal connector from the Commerce SDK:

    1. Open the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository.
    2. Open the last available release branch (for example, **[release/9.34](https://github.com/microsoft/Dynamics365Commerce.Solutions/tree/release/9.34)**).
    3. Open **src \> FiscalIntegration \> SequentialSignatureNorway \> CommerceRuntime**.
    4. Download the fiscal connector configuration file at **Connector.SequentialSignatureNorwaySample \> Configuration \> ConnectorSequentialSignatureNorwaySample.xml** (for example, [the file for release/9.33](https://github.com/microsoft/Dynamics365Commerce.Solutions/blob/release/9.33/src/FiscalIntegration/SequentialSignatureNorway/CommerceRuntime/Connector.SequentialSignatureNorwaySample/Configuration/ConnectorSequentialSignatureNorwaySample.xml)).
    5. Download the fiscal document provider configuration file at **DocumentProvider.SequentialSignatureSample \> Configuration \> DocumentProviderSequentialSignatureNorwaySample.xml** (for example, [the file for release/9.33](https://github.com/microsoft/Dynamics365Commerce.Solutions/blob/release/9.33/src/FiscalIntegration/SequentialSignatureNorway/CommerceRuntime/DocumentProvider.SequentialSignatureNorwaySample/Configuration/DocumentProviderSequentialSignatureNorwaySample.xml)).

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

You must configure certificates that will be used for digital signing of records on the Commerce channel side for sales transactions. The signing is done by using a digital certificate that is stored in Azure Key Vault. For the offline mode of Modern POS, the signing can also be done by using a digital certificate that is stored in the local storage of the machine that Modern POS is installed on.

> [!NOTE]
> You can use either a digital certificate that is issued by an accredited body or a self-signed certificate for digital signing.

The following steps must be completed before you can use a digital certificate that is stored in Key Vault storage:

1. The Key Vault storage must be created. We recommend that you deploy the storage in the same geographical region as the Commerce Scale Unit.
1. The certificate must be uploaded to the Key Vault storage as base64 string secret.
1. The Application Object Server (AOS) application must be authorized to read secrets from the Key Vault storage.

For more information about how to work with Key Vault, see [Get started with Azure Key Vault](/azure/key-vault/key-vault-get-started).

Next, on the **Key Vault parameters** page, you must specify the parameters for accessing the Key Vault storage:

- **Name** and **Description** – The name and description of the Key Vault storage.
- **Key Vault URL** – The URL of the Key Vault storage.
- **Key Vault client** – An interactive client ID of the Azure Active Directory (Azure AD) application that is associated with the Key Vault storage for authentication purposes. This client should have access to read secrets from the storage.
- **Key Vault secret key** – A secret key that is associated with the Azure AD application that is used for authentication in the Key Vault storage.
- **Name**, **Description**, and **Secret reference** – The name, description, and secret reference of the certificate.

Next, you must configure a connector for your certificates that are stored in Key Vault or local certificate storage. It is used for signing on the channel side.

1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector technical profiles**.
1. On the **Settings** FastTab, specify the following parameters for digital signatures:
    - **Secret name** – Select the secret name that you configured earlier in **Key Vault parameters** page.
    - **Local certificate thumbprint** – Provide a thumbprint for a certificate that is stored locally.
    - **Hash algorithm** – Specify one of the cryptographic hash algorithms that are supported by Microsoft .NET, such as **SHA256**.
    - **Certificate store name** – This field is optional. Use this field to specify a default store name that should be used to search local certificates.
    - **Certificate store location** – This field is optional. Use this field to specify a default store location that should be used to search local certificates.
    - **Try local certificate first** – If this option is selected, the certificate from local store will be used by default for signing data instead of the certificate from Key Vault.
    - **Activate health check** – For more information about the health check feature, see [Fiscal registration health check](./fiscal-integration-for-retail-channel.md#fiscal-registration-health-check).

> [!NOTE]
> The default store name and store location are added to simplify the process of searching local certificates in the Commerce runtime. X509StoreProvider has a list of folders where certificates are stored. If the default store name and the default store location aren't specified, X509StoreProvider tries to find a certificate in the other folders on its list.

### Configure the SAF-T Cash Register export format

The SAF-T Cash Register configuration is available for download from Microsoft Dynamics Lifecycle Services (LCS). For more information, see [Import electronic reporting configurations](../../fin-ops-core/dev-itpro/analytics/electronic-reporting-import-ger-configurations.md). You must download the following configurations:

- **Retail channel data.version.1** – The data model configuration.
- **DMM Retail channel data.version.1.12** – The data model mapping configuration.
- **NO SAF T Cash Register.version.1.15** – The format configuration.

After you import the configurations, on the **Commerce parameters** page, on the **Electronic documents** tab, in the **SAF-T Cash register export format** field, select the name of the format configuration that was imported.

You must also map required master data to predefined SAF-T standard codes. For more information, see the SAF-T Cash register documentation that is provided by the Norwegian Tax Administration. To create the mapping, you must set the new **SAF-T Cash register code** field on the following pages:

- Item groups
- Payment methods
- Sales tax codes

### Configure channel components

To enable Norway-specific functionality, you must configure extensions for channel components. For more information, see the [deployment guidelines](./emea-nor-loc-deployment-guidelines.md).



[!INCLUDE[footer-include](../../includes/footer-banner.md)]