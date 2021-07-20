---
# required metadata

title: Cash register functionality for France
description: This topic provides an overview of the cash register functionality that is available for France. It also provides guidelines for setting up the functionality.
author: EvgenyPopovMBS
manager: annbe
ms.date: 07/14/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: RetailFunctionalityProfile, RetailFormLayout, RetailParameters
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: France
ms.search.industry: Retail
ms.author: epopov
ms.search.validFrom: 2018-2-28
ms.dyn365.ops.version: 7.3.2

---
# Cash register functionality for France

[!include [banner](../includes/banner.md)]

This topic provides an overview of the cash register functionality that is available for France in Dynamics 365 Commerce. It also provides guidelines for setting up the functionality.

## Certification information

This version of the cash register functionality for France has passed an audit according to the NF 525 certification requirements and is granted certificates of compliance with the following categories and numbers: 

- **Microsoft Dynamics 365 Finance and Operations, version 10**:
    - Certificate category: B
    - Certificate number: 0350
- **Microsoft Dynamics 365 Commerce, version 10**:
    - Certificate category: B
    - Certificate number: 0203

Up-to-date certificates can be found on the [portal of the certification body](https://certificates.infocert.org/).

## Overview

The functionality consists of the following parts:

- Common point-of-sale (POS) features that are available to customers in all countries or regions. Examples include an option to register various events in the POS audit log.
- France-specific features, such as digital signatures for sales transactions.

### Common POS features

To learn about POS features that are available to customers in all countries or regions, see [Commerce home page](../index.md).

The following POS localization features that are available to customers in all countries or regions can now be used specifically for France:

- **Register additional events in the POS audit event log.** If the **Audit** option in the POS functionality profile is set to **Yes**, the following events are registered in the POS audit event log:

    - Sign-in
    - Sign-out
    - Printing a copy of a receipt
    - Starting offline mode
    - Ending offline mode
    - Applying a manager override
    - Voiding a transaction    - 
    - Cleanup of transactions from the channel database
    - Applying a major update of the software with compliance impact

### France-specific POS features

The following France-specific POS features are enabled when the **ISO code** field in the POS functionality profile is set to **FR**.

#### Digital signing overview

The following types of records (transactions and events) are digitally signed in POS:

- Sales transactions
- Copies of receipts
- Closed shifts/Z reports
- Audit events

The signature is created and recorded in the channel database at the same time that the transaction is finalized or the event is registered. The data that is signed is a text string that consists of several data fields. These fields vary, depending on the type of record. The general signing process consists of the following steps:

1. Select the next sequential number for signing purposes for the same register and type of record. 
1. Extract the data fields that must be signed from the record that is being signed.
1. Build a string that consists of a comma-separated list of the data fields.
1. Add the previous signature for the same register and type of record.
1. Calculate a hash code of the string by using the SHA-x algorithm.
1. Encrypt the resulting string by using a digital certificate.
1. Do the base64url transformation for the resulting string.
1. Store the string that is used for signing, the sequential number, the signature, the hash algorithm identification and the thumbprint of the certificate in a fiscal response record that is linked to the transaction or event.
1. Transfer the fiscal response to the enterprise resource planning (ERP) system in Headquarters, together with the transaction or event.

#### Digital signing of sales transactions

Only transactions for cash sales are signed. Here are some examples of transactions that are excluded from the signing process:

- Prepayments (customer account deposits)
- Quotations
- Prepayments for sales orders (customer order deposits)
- Issuing a gift card and adding funds to a gift card
- Non-sales transactions (float entry, tender removal, and so on)

The data that is signed for a sales transaction is a text string that consists of the following data fields:

1. The total amounts of sales lines including tax per tax rate.
2. The total amount of sales including tax.
3. The date and time of the transaction, in the format YYYYMMDDHHMMSS.
4. The register number.
5. The sequential number of the signed sales transaction.
6. The type of sales transaction.
7. A value (Y/N) that indicates whether the transaction is the first signed sales transaction for the register.
8. The previous signature for the same register. A blank value is used for the first signed sales transaction.

You can view the transaction signature, together with the transaction data that was used to generate it, on the **Fiscal transactions** FastTab of the **Store transactions** page in Headquarters.

#### Digital signing of receipt copies

When a copy of a receipt is printed, the event is registered in the POS audit event log. Only copies of receipts for signed sales transactions are signed. The data that is signed for a receipt copy event is a text string that consists of the following data fields:

1. The register number that the copy of receipt is printed from.
2. The sequential number of the signed receipt copy event.
3. The type of transaction for the original sales transaction.
4. The number of the receipt copy for this sales transaction.
5. The staff ID of the operator who prints the receipt copy.
6. The date and time of the receipt copy event, in the format YYYYMMDDHHMMSS.
7. The register number of the original sales transaction.
8. The sequential number of the original sales transaction.
9. A value (Y/N) that indicates whether the transaction is the first signed receipt copy event for the register.
10. The previous signature for the same register. A blank value is used for the first signed receipt copy event.

You can view the signature of the receipt copy, together with the event data that was used to generate it, on the **Signature** tab of the **Audit events** page in Headquarters.

#### Digital signing of closed shifts

When a shift is closed, the event is registered in the POS audit event log. The data that is signed for a shift closing event is a text string that consists of the following data fields:

1. The total amount of sales and returns for the shift including tax per tax rate.
2. The total amount of sales and returns for the shift including tax.
3. The perpetual (cumulative) grand total of absolute values of sales and returns for shifts of the same register including tax. 
4. The date and time of the shift closing event, in the format YYYYMMDDHHMMSS.
5. The date and time of the shift.
6. The sequential number of the shift closing event.
7. A value (Y/N) that indicates whether the transaction is the first signed shift closing event for the register.
8. The previous signature for the same register. A blank value is used for the first signed shift closing event.

You can view the signature of a closed shift, together with the shift data that was used to generate it, on the **Signature** tab of the **Shifts** page in Headquarters.

#### Digital signing of events

The data that is signed for an event other than a receipt copy or shift closing event is a text string that consists of the following data fields:

1. The sequential number of the signed event.
2. A predefined event code.
3. A description of the event.
4. The date and time of the event.
5. The staff ID of the operator who raised the event.
6. The register number.
7. A value (Y/N) that indicates whether the transaction is the first signed event for the register.
8. The previous signature for the same register. A blank value is used for the first signed event.

You can view the event signature, together with the event data that was used to generate it, on the **Signature** tab of the **Audit events** page in Headquarters.

#### Receipts

Receipts for France can include additional information that was implemented by using custom fields:

- **Transaction type** – You can add a field to a receipt format layout to identify the type of transaction. For example, a sales receipt will include the text "Sales."
- **Sequential number of signed sales transaction** – A receipt can include the sequential number of a signed sales transaction. This number is used to associate the printed receipt with a digital signature in the database.
- **Extract from digital signature** – A receipt can include an extract from the digital signature. This extract is used to confirm that the transaction is signed. It consists of a concatenation of the third, seventh, thirteenth, and nineteenth symbols of the signature.
- **Reprint number** – An original receipt or a receipt copy can include the number of the receipt copy. For an original receipt, the value is **0** (zero).
- **Line count** – A receipt can include the number of printed item lines on the receipt.
- **Sales totals** – Custom fields for receipt totals exclude non-sales amounts from the total transaction amounts. Non-sales amounts include amounts for the following operations:

    - Prepayments (customer account deposits)
    - Prepayments for sales orders (customer order deposits)
    - Issuing a gift card
    - Adding funds to a gift card

- **Certification data** – A receipt can include the category and number of a certificate of compliance that an authorized body issued per the NF 525 certification requirements.
- **Software version** - A receipt can include the version of the software certified per the NF 525 certification requirements that is used to produce receipts.

#### Restricting the duration of shifts

There is an option to enforce daily shift closing in POS. A shift can't last longer than the time that is specified in the **Shift closing time** field. Several minutes before that time, the operator will start to receive warnings that the shift must be closed. The number of minutes is determined by the value of the **Shift closing interval (minutes)** field.

#### X and Z reports

The information that is included on X and Z reports is based on French requirements:

- **Total sales** for the shift. This information includes amounts only for cash sales transactions. Prepayments and operations for issuing a gift card are excluded.
- **Total returns** for the shift.
- **Cumulative grand total**. This amount is calculated as the cumulative grand total amount of the previous shift plus the total sales amount of this shift minus the absolute value of the total returns amount of this shift.
- **Cumulative perpetual grand total**. This amount is calculated as the cumulative perpetual grand total amount of the previous shift plus the total sales amount of this shift plus the absolute value of the total returns amount of this shift.
- Value-added tax (VAT) amounts per tax rate.

The totals are also stored in the closed shift record and transferred to Headquarters.

#### Period grand total journal

Period grand total journals summarize sales totals per store and fiscal period (e.g., month). In addition, an annual journal summarizes sales totals per store and fiscal year.

Period grand total journals are maintained on the **Period grand total journal** page. To create a new journal, you must specify a store. If previous journals exist for the store, the next fiscal period after the last closed journal for the store is automatically used as the new journal period. If previous journals do not exist, you can specify the end date of the journal. In this case, the fiscal period that includes the specified date is used as the journal period.

The journal can then be calculated. Shifts that were closed during the journal period are selected, and totals are calculated for those shifts. You can view the journal's tax totals per sales tax code. You can also view the shifts that are included in the journal.

After the journal is calculated, it can be closed. A closed journal can't be modified, and another journal can't be created for a previous fiscal period, the same period, or an intersecting period. However, the last closed journal for a store can be canceled. In that case, another journal can be created for the same store and fiscal period.

A closed journal is digitally signed. You can view the journal signature, together with the journal data that was used to generate it, on the **Signature details** tab of the **Period grand total journal** page in Headquarters.

A period grand total journal can also be marked as **Annual** when being created. An annual journal summarizes period grand total journals for the fiscal periods of a fiscal year. It is only possible to create an annual journal for a fiscal year if a journal for the last fiscal period of the fiscal year has been created, calculated and closed. It is not, however, required that journals for all fiscal periods of the fiscal year exist. For example, if a new store is opened in the middle of the year, the first journal will correspond to the fiscal period that the store is opened in. In this case, the first annual journal will summarize jornals for fiscal periods from the fiscal period that the store is opened in to the last fiscal period of the fiscal year.

#### Fiscal archive

A fiscal archive is an XML file that can be exported from a period grand total journal that has been closed. It includes the totals for the closed period, and also includes detailed data about sales transactions and events. The exported file is digitally signed, and the signature is contained in a separate file. It is required to keep exported fiscal archives on a secured external media for the legal retention period.

Commerce also includes a tool that can be used to verify the integrity of a fiscal archive and detect violations of the signature of the archive and of the chains of signed records in the archive. This tool is developed in form of a Powershell script that is available via the Commerce SDK. See [Fiscal archive](./emea-fra-fiscal-archive.md) for a detailed structure of the fiscal archive format and a guidance on how to use the fiscal archive integrity verification tool.

## Setting up Commerce for France

This section describes the Commerce settings that are specific to and recommended for France. For more information, see [Commerce home page](../index.md).

To use the France-specific functionality, you must complete these tasks:

- Set the **Country/region** field to **FRA** (France) in the primary address of the legal entity.
- Set the **ISO code** field to **FR** (France) in the POS functionality profile of every store that is located in France.

You must also specify the following settings for France. Note that you must run appropriate distribution jobs after you complete the setup.

### Set up the legal entity

You must make the following changes on the **Legal entities** page. These settings are used in the archive format.

- On the **Bank account information** FastTab, in the **Routing number** field, specify the VAT identifier of the organization.
- On the **Statutory reporting** FastTab, in the **NAF code** field, specify the Nomenclature des Activités Françaises (NAF) code of the organization.
- On the **Tax registration** FastTab, in the **Tax registration number** field, specify the Système d'identification du répertoire des établissements (SIRET) number of the organization.

### Set up VAT per French requirements

You must create sales tax codes, sales tax groups, and item sales tax groups. You must also set up sales tax information for products and services. For more information about how to set up and use sales tax, see [Sales tax overview](../../financials/general-ledger/indirect-taxes-overview.md).

You must also specify sales tax groups and enable the **Prices include sales tax** option for stores that are located in France.

### Set up functionality profiles

You must enable auditing by setting the **Audit** option to **Yes**.

To enforce daily shift closing, you must make the following changes:

- Set the **Enforce daily shift closing** option to **Yes**.
- Set the **Shift closing time** and **Shift closing interval (minutes)** fields.

### Configure custom fields so that they can be used in receipt formats for sales receipts

You can configure the language text and custom fields that are used in the POS receipt formats. The default company of the user who creates the receipt setup should be the same legal entity where the language text setup is created. Alternatively, the same language texts should be created in both the user's default company and the legal entity of the store that the setup is created for.

On the **Language text** page, add the following records for the labels of the custom fields for receipt layouts. Note that the **Language ID**, **Text ID**, and **Text** values that are shown in the table are just examples. You can change them to meet to your requirements. However, the **Text ID** values that you use must be unique, and they must be equal to or higher than 900001.

| Language ID | Text ID | Text ID                   |
|-------------|---------|---------------------------|
| en-US       | 900001  | Transaction type          |
| en-US       | 900002  | Sequential number         |
| en-US       | 900003  | Digital signature         |
| en-US       | 900004  | Reprint number            |
| en-US       | 900005  | Sales tax basis           |
| en-US       | 900006  | Sales tax amount          |
| en-US       | 900007  | Sales total               |
| en-US       | 900008  | Sales total tax           |
| en-US       | 900009  | Sales total including tax |
| en-US       | 900010  | NF 525 Certificate        |
| en-US       | 900011  | Line count                |

On the **Custom fields** page, add the following records for the custom fields for receipt layouts. Note that **Caption text ID** values must correspond to the **Text ID** values that you specified on the **Language text** page.

| Name                            | Type    | Caption text ID |
|---------------------------------|---------|-----------------|
| TRANSACTIONTYPE_FR              | Receipt | 900001          |
| SEQUENTIALNUMBER_FR             | Receipt | 900002          |
| DIGITALSIGNATURE_FR             | Receipt | 900003          |
| REPRINTNUMBER_FR                | Receipt | 900004          |
| SALESTAXBASIS_FR                | Receipt | 900005          |
| SALESTAXAMOUNT_FR               | Receipt | 900006          |
| SALESTOTAL_FR                   | Receipt | 900007          |
| SALESTOTALTAX_FR                | Receipt | 900008          |
| SALESTOTALINCLUDETAX_FR         | Receipt | 900009          |
| CERTIFICATENUMBERANDCATEGORY_FR | Receipt | 900010          |
| LINECOUNT_FR                    | Receipt | 900011          |

### Configure receipt formats

For every required receipt format, change the value of the **Print behavior** field to **Always print**.

In the Receipt format designer, add the following custom fields to the appropriate receipt sections. Note that field names correspond to the language texts that you defined in the previous section.

- **Header:** Add the following field:

    - **Transaction type** – This field identifies the type of receipt.

- **Lines:** We recommend that you add the following standard fields:

    - **Unit price with tax**
    - **Total price with tax**
    - **Tax ID**

- **Footer:** Add the following fields:

    - **Sales total** – This field prints the receipt's total cash sale amount. The amount excludes tax. Prepayments and gift card operations are excluded.
    - **Sales total tax** – This field prints the receipt's total tax amount for cash sales. Prepayments and gift card operations are excluded. 
    - **Sales total including tax** – This field prints the receipt's total cash sale amount. The amount includes tax. Prepayments and gift card operations are excluded.
    - **Tax ID** – This standard field enables a sales tax summary to be printed per sales tax code. The field must be added to a new line.
    - **Sales tax basis** – This field prints the receipt's tax basis for cash sales per sales tax code. Prepayments and gift card operations are excluded. The field must be added to the same line as the **Tax ID** field.
    - **Sales tax amount** – This field prints the receipt's tax amount for cash sales per sales tax code. Prepayments and gift card operations are excluded. The field must be added to the same line as the **Tax ID** field.
    - **Sequential number** – This field prints the sequential number of a signed sales transaction.
    - **Digital signature** – This field prints the extract from the digital signature.
    - **Reprint number** – This field prints the number of a receipt copy.
    - **NF 525 Certificate** – This field prints the category and number of the certificate of compliance that an authorized body issued per the NF 525 certification requirements.

    > [!NOTE]
    > By default, the certificate category and number that are assigned to [Finance and Operations](#certification-information) are printed. If you're implementing Commerce, you must override the certificate category and number.

    - **Text** – Add a text field, and specify the version of software certified per the NF 525 certification requirements that is used to produce receipts, for example:
        - **Microsoft Dynamics 365 Finance and Operations v.10**; or
        - **Microsoft Dynamics 365 Commerce v.10**.

    > [!NOTE]
    > If you customize the POS application, and your customizations affect the compliance of the application, you might have to request a new certificate of compliance from an accredited body. In this case, you must override the certificate category and number, as well as specify a corresponding software version number. Otherwise, the default values for the certificate category and number will be printed.

    - **Line count** – This field prints the number of printed item lines on a receipt.
    - **Text** – Add a text field, and specify the VAT identifier of the organization.
    - **Text** – Add a text field, and specify the NAF code of the organization.
    - **Text** – Add a text field, and specify the SIRET number of the organization.
    - **Store name** – This standard field prints the name of the store.
    - **Store address** – This standard field prints the address of the store.

For more information about how to work with receipt formats, see [Set up and design receipt formats](../receipt-templates-printing.md).

### Set up fiscal registration

Complete the fiscal registration setup steps that are described in [Set up the fiscal integration for Commerce channels](./setting-up-fiscal-integration-for-retail-channel.md):

- [Set up a fiscal registration process](./setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process). Be sure to note the settings for the fiscal registration process that are [specific to France](#configure-the-fiscal-registration-process).
- [Set error handling settings](./setting-up-fiscal-integration-for-retail-channel.md#set-error-handling-settings).
- [Enable manual execution of postponed fiscal registration](./setting-up-fiscal-integration-for-retail-channel.md#enable-manual-execution-of-postponed-fiscal-registration).

#### Configure the fiscal registration process

To enable the fiscal registration process for France, follow these steps to set up Headquarters:

1. Download configuration files for the fiscal document provider and the fiscal connector from Commerce SDK:
    - Open the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository.
    - Open the last available release branch (for example, [release/9.30](https://github.com/microsoft/Dynamics365Commerce.Solutions/tree/release/9.30).
    - Open **src \> FiscalIntegration \> SequentialSignatureFrance \> Configurations**.
    - Dowload the fiscal connector configuration file **Connector \> ConnectorMicrosoftSequentialSignatureFRA.xml** (for example, [the file for release/9.30](https://github.com/microsoft/Dynamics365Commerce.Solutions/blob/release/9.30/src/FiscalIntegration/SequentialSignatureFrance/Configurations/Connector/ConnectorMicrosoftSequentialSignatureFRA.xml)).
    - Dowload the fiscal document provider configuration file **DocumentProvider \> DocumentProviderMicrosoftSequentialSignatureFRA.xml** (for example, [the file for release/9.30](https://github.com/microsoft/Dynamics365Commerce.Solutions/blob/release/9.30/src/FiscalIntegration/SequentialSignatureFrance/Configurations/DocumentProvider/DocumentProviderMicrosoftSequentialSignatureFRA.xml)).
2. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Shared parameters**. On the **General** tab, set the **Enable fiscal integration** option to **Yes**.
3. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connectors** and load the fiscal connector configuration file that you downloaded earlier.
4. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal document providers** and load the fiscal document provider configuration file that you downloaded earlier.
5. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector functional profiles**. Create a new connector functional profile and select the document provider and the connector that you loaded earlier. Update the data mapping settings as required.
6. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector technical profiles**. Create a new connector technical profile and select the connector that you loaded earlier. Set the connector type as **Internal**. Update the other connection settings as required.
7. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connector groups**. Create a new fiscal connector group for the connector functional profile that you created earlier.
8. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal registration processes**. Create a new fiscal registration process, create a fiscal registration process step, and select the fiscal connector group that you created earlier.
9. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**. Select a functionality profile that is linked to the store where the registration process should be activated. On the **Fiscal registration process** FastTab, select the fiscal registration process that you created earlier. On the **Fiscal services** FastTab, select the connector technical profile that you created earlier. 
10.  Open the distribution schedule (**Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**), and select jobs **1070** and **1090** to transfer data to the channel database.

### Configure the digital signature parameters

You need to configure certificates to be used for digital signing of records on the Commerce channel side (that is, sales transactions and audit events) and on the Commerce Headquarters side (that is, period grand total journals and fiscal archives). The signing is done by using a digital certificate that is stored in a Microsoft Azure Key Vault storage. For the offline mode of Modern POS, the signing can also be done by using a digital certificate that is stored in the local storage of the machine that Modern POS is installed on. The [User-defined certificate profiles for retail stores](./certificate-profiles-for-retail-stores.md) feature  enables configuring certificates that are stored in Key Vault and supports failover to offline when Key Vault or Headquarters are not available. The feature extends the [Manage secrets for retail channels](../dev-itpro/manage-secrets) feature.

The following steps must be completed before you can use a digital certificate stored in an Azure Key Vault storage:

- The Key Vault storage must be created. We recommend that you deploy the storage in the same geographical region as the Commerce Scale Unit.
- The certificate must be uploaded to the Key Vault storage.
- The Application Object Server (AOS) application must be authorized to read secrets from the Key Vault storage.

For more information about how to work with Key Vault, see [Get started with Azure Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-get-started).

Then, on the **Key Vault parameters** page, you must specify the parameters for accessing the Key Vault storage:

- **Name** and **Description** – The name and description of the Key Vault storage.
- **Key Vault URL** – The URL of the Key Vault storage.
- **Key Vault client** – An interactive client ID of the Azure Active Directory (Azure AD) application that is associated with the Key Vault storage for authentication purposes. This client should have access to read secrets from the storage.
- **Key Vault secret key** – A secret key that is associated with the Azure AD application that is used for authentication in the Key Vault storage.
- **Name**, **Description**, and **Secret reference** – The name, description, and secret reference of the certificate.

Then, you need to configure a certificate profile for your certificates stored in Key Vault or local certificate storage. The certificate profile is used for signing on the channel side:

1. Open **Retail and Commerce \> Channel setup \> Fiscal integration \> Certificate profiles**. 
2. Create a new certificate profile.
3. On the **Legal entities** FastTab, add required legal entities.
4. Click **Settings**.
5. Add a new certificate. Certificates stored in Key Vault and local certificates are supported. You can add as many certificates as you need and set priorities of the certificates. If a certificate with a higher priority is not available, the next certificate will be used according to priority.
   - For a certificate stored in Key Vault, you must select the certificate from the dropdown list.
   - For a certificate stored locally, you must specify the thumbprint of the certificate.
6. Open **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector technical profiles**.
7. On the **Settings** FastTab, you must specify the parameters for digital signatures:
   - Certificate profile – Select the certificate profile that you configured on the previous step.
   - Hash algorithm – Specify one of the cryptographic hash algorithms that are supported by Microsoft .NET, such as SHA256.
   - Activate health check – For more information about the Health Check feature, see [Fiscal registration health check](./fiscal-integration-for-retail-channel.md#fiscal-registration-health-check).

Finally, on the **Commerce parameters** page, you must specify the parameters for digital signing on the Headquarters side:

- **Certificate** – Select the certificate that you configured in the previous step.
- **Hash function** – Specify one of the cryptographic hash algorithms that are supported by Microsoft .NET, such as **SHA1**.
- **Encoding** – Specify the encoding of the signed data, such as **UTF-8**.

### Configure the archive export format

You can download the ER configuration for the archive from Microsoft Dynamics Lifecycle Services (LCS). For more information, see [Import electronic reporting configurations](../../dev-itpro/analytics/electronic-reporting-import-ger-configurations.md). You must download the following versions, or later versions, of the configurations:

- **Retail channel data.version.2** data model
- **Archiving DMM.version.2.3** data model mapping
- **Retail data archive FR .version.2.5** format

After you import the configurations, on the **Commerce parameters** page, on the **Electronic documents** tab, in the **Retail data archive export format** field, select the **Retail data archive FR .version.2.5** format or the format that you downloaded earlier.

### Renitialize Commerce components

> [!NOTE]
> You only need to complete the steps of this section if you are updating an existing environment.

To enable audit events, you must reinitialize the Commerce Extensible enumerations. To enable transmitting France-specific data from POS to HQ, you must reinitialize the Commerce Scheduler.

On the **General** FastTab of the **Commerce parameters** page, click **Initialize**. For more information, see [Initialize seed data in new Retail environments](../enable-configure-retail-functionality.md)

There is an option to separately configure the scheduler. Click **Commerce scheduler** \> **Initialize commerce scheduler**. On the **Initialize Commerce scheduler** page, click **OK**.

### Configure channel components

To enable France-specific functionality, you must configure extensions for channel components. For more information, see the [deployment guidelines](./emea-fra-deployment.md).

