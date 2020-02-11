---
# required metadata

title: Cash register functionality for France
description: This topic provides an overview of the cash register functionality that is available for France. It also provides guidelines for setting up the functionality.
author: EvgenyPopovMBS
manager: vastrup
ms.date: 04/13/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: RetailFunctionalityProfile, RetailFormLayout, RetailParameters
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
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

The functionality consists of the following parts:

- Common point-of-sale (POS) features that are available to customers in all countries or regions. Examples include an option to register various events in the POS audit log.
- France-specific features, such as digital signatures for sales transactions.

## Overview

### Common POS features

To learn about POS features that are available to customers in all countries or regions, see [Help resources for Dynamics 365 Retail](../index.md).

The following POS localization features that are available to customers in all countries or regions can now be used specifically for France:

- **Register additional events in the POS audit event log.** If the **Audit** option in the POS functionality profile is set to **Yes**, the following events are registered in the POS audit event log:

    - Sign-in
    - Sign-out
    - Printing a copy of a receipt
    - Starting offline mode
    - Ending offline mode
    - Cleanup of transactions from the channel database

### France-specific POS features

The following France-specific POS features are enabled when the **ISO code** field in the POS functionality profile is set to **FR**.

#### Digital signing overview

The following types of data (transactions and events) are digitally signed in POS:

- Sales transactions
- Copies of receipts
- Closed shift/Z reports
- Audit events

The signature is created and recorded in the channel database at the same time that the transaction is finalized or the event is registered. The data that is signed is a text string that consists of several data fields. These fields vary, depending on the type of data. The general signing process consists of the following steps:

1. Based on the type of data, select the next sequential number for signing purposes.
2. Extract the data fields that must be signed from the record that is being signed.
3. Build a string that consists of a comma-separated list of the data fields.
4. Add the previous signature for the same type of data.
5. Calculate a hash code of the string by using the SHA-x algorithm.
6. Encrypt the resulting string by using a digital certificate.
7. Do the base64url transformation for the resulting string.
8. Store the string that is used for signing, the sequential number, the signature, and the thumbprint of the certificate in a fiscal response record that is linked to the transaction or event.
9. Transfer the fiscal response to the enterprise resource planning (ERP) system in Headquarters, together with the transaction or event.

#### Digital signing of sales transactions

Only transactions for cash sales are signed. Here are some examples of transactions that are excluded from the signing process:

- Prepayments (customer account deposits)
- Quotations
- Prepayments for sales orders (customer order deposits)
- Issuing a gift card and adding funds to a gift card
- Non-sales transactions (float entry, tender removal, and so on)

The data that is signed for a sales transaction is a text string that consists of the following data fields:

1. The total amount of sales lines. The amount includes tax per tax rate.
2. The total amount of sales. The amount includes tax.
3. The date and time of the transaction, in the format YYYYMMDDHHMMSS.
4. The register number.
5. The sequential number of the signed sales transaction.
6. The type of sales transaction.
7. A value (Y/N) that indicates whether the transaction is the first signed sales transaction for the register.
8. The previous signature for the same register. A blank value is used for the first signed sales transaction.

You can view the transaction signature, together with the transaction data that was used to generate it, on the **Fiscal transactions** FastTab of the **Store transactions** page in Headquarters.

#### Digital signing of receipt copies

When a copy of a receipt is printed, the event is registered in the POS audit event log. Only copies of receipts for signed sales transactions are signed. The data that is signed for a receipt copy event is a text string that consists of the following data fields:

1. The receipt number of the original sales transaction.
2. The type of transaction for the original sales transaction.
3. The number of the receipt copy for this sales transaction.
4. The staff ID of the operator who is printing the receipt copy.
5. The date and time of the receipt copy event, in the format YYYYMMDDHHMMSS.
6. The sequential number of the signed receipt copy event.
7. A value (Y/N) that indicates whether the transaction is the first signed receipt copy event for the register.
8. The previous signature for the same register. A blank value is used for the first signed receipt copy event.

You can view the signature of the receipt copy, together with the event data that was used to generate it, on the **Signature** tab of the **Audit events** page in Headquarters.

#### Digital signing of closed shifts

When a shift is closed, the event is registered in the POS audit event log. The data that is signed for a shift closing event is a text string that consists of the following data fields:

1. The total amount of sales. The amount includes tax per tax rate.
2. The total amount of sales. The amount includes tax.
3. The date and time of the shift closing event, in the format YYYYMMDDHHMMSS.
4. The sequential number of the shift closing event.
5. A value (Y/N) that indicates whether the transaction is the first signed shift closing event for the register.
6. The previous signature for the same register. A blank value is used for the first signed shift closing event.

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

- **Certification data** – A receipt can include the category and number of the certificate of compliance that an authorized body issued per the NF 525 certification requirements.
- **Build number** – A receipt can include the POS build number.

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

Period grand total journals summarize sales totals per store and fiscal period.

Period grand total journals are maintained on the **Period grand total journal** page. To create a new journal, you must specify a store. If previous journals exist for the store, the next fiscal period after the last closed journal for the store is automatically used as the new journal period. If previous journals do not exist, you can specify the end date of the journal. In this case, the fiscal period that includes the specified date is used as the journal period.

The journal can then be calculated. Shifts that were closed during the journal period are selected, and totals are calculated for those shifts. You can view the journal's tax totals per sales tax code. You can also view the shifts that are included in the journal.

After the journal is calculated, it can be closed. A closed journal can't be modified, and another journal can't be created for a previous period, the same period, or an intersecting period. However, the last closed journal for a store can be canceled. In that case, another journal can be created for the same store and period.

A closed journal is digitally signed. You can view the journal signature, together with the journal data that was used to generate it, on the **Signature details** tab of the **Period grand total journal** page in Headquarters.

#### Archive

An archive is an XML file that can be exported from a Period grand total journal that has been closed. It includes the totals for the closed period, and also includes detailed data about sales transactions and events. The exported file is digitally signed, and the signature is contained in a separate file.

The archive format is implemented by using [Electronic reporting (ER)](../../dev-itpro/analytics/general-electronic-reporting.md).

## Setting up Commerce for France

This section describes the Commerce settings that are specific to and recommended for France. For more information, see [Help resources for Dynamics 365 Retail](../index.md).

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
| en-US       | 900005  | Sales tax amount          |
| en-US       | 900006  | Sales total               |
| en-US       | 900007  | Sales total tax           |
| en-US       | 900008  | Sales total including tax |
| en-US       | 900009  | Build number              |
| en-US       | 900010  | Certification category    |
| en-US       | 900011  | Certificate number        |
| en-US       | 900012  | Line count                |

On the **Custom fields** page, add the following records for the custom fields for receipt layouts. Note that **Caption text ID** values must correspond to the **Text ID** values that you specified on the **Language text** page.

| Name                  | Type    | Caption text ID |
|-----------------------|---------|-----------------|
| TRANSACTIONTYPE       | Receipt | 900001          |
| SEQUENTIALNUMBER      | Receipt | 900002          |
| DIGITALSIGNATURE      | Receipt | 900003          |
| REPRINTNUMBER         | Receipt | 900004          |
| SALESTAXAMOUNT        | Receipt | 900005          |
| SALESTOTAL            | Receipt | 900006          |
| SALESTOTALTAX         | Receipt | 900007          |
| SALESTOTALINCLUDETAX  | Receipt | 900008          |
| BUILDNUMBER           | Receipt | 900009          |
| CERTIFICATIONCATEGORY | Receipt | 900010          |
| CERTIFICATENUMBER     | Receipt | 900011          |
| LINECOUNT             | Receipt | 900012          |

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
    - **Sales tax amount** – This field prints the receipt's tax amount for cash sales per sales tax code. Prepayments and gift card operations are excluded. The field must be added to the same line as the **Tax ID** field.
    - **Sequential number** – This field prints the sequential number of a signed sales transaction.
    - **Digital signature** – This field prints the extract from the digital signature.
    - **Reprint number** – This field prints the number of a receipt copy.
    - **Build number** – This field prints the POS build number.
    - **Certification category** – This field prints the category of the certificate of compliance that an authorized body issued per the NF 525 certification requirements.
    - **Certificate number** – This field prints the number of the certificate of compliance that an authorized body issued per the NF 525 certification requirements.
    - **Line count** – This field prints the number of printed item lines on a receipt.
    - **Text** – Add a text field, and specify the VAT identifier of the organization.
    - **Text** – Add a text field, and specify the NAF code of the organization.
    - **Text** – Add a text field, and specify the SIRET number of the organization.
    - **Store name** – This standard field prints the name of the store.
    - **Store address** – This standard field prints the address of the store.

For more information about how to work with receipt formats, see [Set up and design receipt formats](../receipt-templates-printing.md).

### Configure the digital signature parameters for Headquarters

To digitally sign Period grand total journals and archives, you must set up digital signature parameters. The signing is done by using a digital certificate that is stored in Microsoft Azure Key Vault storage. The following steps must be completed before you can use a certificate that is stored in Key Vault storage:

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

Finally, on the **Commerce parameters** page, you must specify the parameters for digital signatures:

- **Certificate** – Select the certificate that you configured in the previous step.
- **Hash function** – Specify one of the cryptographic hash algorithms that are supported by Microsoft .NET, such as **SHA1**.
- **Encoding** – Specify the encoding of the signed data, such as **UTF-8**.

### Configure the archive export format

You can download the ER configuration for the archive from Microsoft Dynamics Lifecycle Services (LCS). For more information, see [Import electronic reporting configurations](../../dev-itpro/analytics/electronic-reporting-import-ger-configurations.md). You must download the following versions, or later versions, of the configurations:

- **Retail channel data.version.2** data model
- **Archiving DMM.version.2.1** data model mapping
- **Retail data archive FR .version.2.1** format

After you import the configurations, on the **Commerce parameters** page, on the **Electronic documents** tab, in the **Retail data archive export format** field, select the **Retail data archive FR .version.2.1** format.

### Renitialize Commerce components

> [!NOTE]
> You only need to complete the steps of this section if you are updating an existing evironment.

To enable audit events, you must reinitialize the Commerce Extensible enumerations. To enable transmitting France-specific data from POS to HQ, you must reinitialize the Commerce Scheduler.

On the **General** FastTab of the **Commerce parameters** page, click **Initialize**. For more information, see [Initialize seed data in new Retail environments](../enable-configure-retail-functionality.md)

There is an option to separately configure the scheduler. Click **Commerce scheduler** \> **Initialize commerce scheduler**. On the **Initialize Commerce scheduler** page, click **OK**.

### Configure channel components

To enable France-specific functionality, you must configure extensions for channel components. For more information, see the [deployment guidelines](./emea-fra-deployment.md).
