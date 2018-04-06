---
# required metadata

title: Cash registers for France
description: This topic provides an overview of the cash register functionality that is available for France. It also provides guidelines for setting up the functionality.
author: EvgenyPopovMBS
manager: vastrup
ms.date: 04/06/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: RetailFunctionalityProfile, RetailFormLayout, RetailParameters
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: France
ms.search.industry: Retail
ms.author: epopov
ms.search.validFrom: 2018-4-06
ms.dyn365.ops.version: 7.3.2

---
# Cash registers for France

[!include[banner](../includes/banner.md)]

This topic provides an overview of the cash register functionality that is available for France in Microsoft Dynamics 365 for Retail. It also provides guidelines for setting up the functionality.

The functionality consists of the following parts:

- Common point-of-sale (POS) features that are available to customers in all countries or regions. Examples include an option to register different events in the POS audit log.
- France-specific features, such as digital signatures for sales transactions.

## Overview of cash register functionality for France

### Common POS features

To learn about POS features that are available to customers in all countries or regions, see [Microsoft Dynamics 365 for Retail documentation](../index.md).

The following POS localization features that are available to customers in all countries or regions can now be used specifically for France:

- **Register additional events in the POS audit event log.** If the **Audit** parameter in the POS functionality profile is enabled, the following events are registered in the POS audit event log:

    - Logging on
    - Logging off
    - Printing a copy of receipt
    - Entering the offline mode
    - Exiting the offline mode
    - Cleaning transactions from the Channel DB

### France-specific POS features

The following France-specific POS features are enabled when the **ISO code** parameter in the POS functionality profile is set to **FR**.

#### Digital signing overview

The following types of data (transactions, events) are digitally signed in POS:

- Sales transaction 
- Copy of receipt
- Closed shift/Z-report
- Audit event

The signature is created and recorded in the Channel DB at the same time that the transaction is finalized or the event is registered. The data that is signed is a text string that consists of several data fields, depending on the type of data. The general signing process is as following:

- Select the next "sequential number" for signing purposes per type of data;
- Extract data fields that must be signed from the record being signed;
- Build a string of the data fields separated by comma (",");
- Add the previous signature **for the same** type of data;
- Calculate a hash code of the string using the SHA-x algorithm;
- Encrypt the resulting string using a  digital certificate;
- Perform the base64url transformation for the resulting string;
- Store the string used for signing, the sequential number, the signature, and the footprint of the certificate in a "fiscal response" record linked to the transaction/event;
- Transfer the fiscal response to the ERP system in Headquarters together with the transaction/event.

#### Digital signing of sales transactions

Only transactions for cash sales are signed. Here are some examples of transactions that are excluded from the signing process:

- Prepayments (customer account deposit)
- Quotations
- Prepayments for sales orders (customer order deposit)
- Issuing a gift card and adding to a gift card
- Non-sales transactions (float entry, tender removal, and so on)

The data that is signed for a sales transaction is a text string that consists of the following data fields:

1. Total amount of sales lines including tax per tax rate
2. Total amount of sales including tax
3. Date and time of the transaction in the format YYYYMMDDHHMMSS
4. Register number
5. Sequential number of the signed sales transaction
6. Type of the sales transaction
7. Designation of the first signed sales transaction for the register (Y/N)
8. Previous signature for the same register. Blank value is used for the first signed sales transaction.

You can view the transaction signature, together with the transaction data that was used to generate it, on the **Fiscal transactions** FastTab of the **Retail store transactions** page in Retail Headquarters. 

#### Digital signing of receipt copies

Printing a receipt copy is registered as an event in the POS audit event log. Only copies of receipts for signed sales transactions are signed. The data that is signed for a receipt copy event is a text string that consists of the following data fields:

1. Receipt number of the original sales transaction
2. Retail transaction type of the original sales transaction
3. The number of the copy of this sales transaction
4. Staff ID of the operator printing the copy
5. Date and time of the receipt copy event in the format YYYYMMDDHHMMSS
6. Sequential number of the signed receipt copy event
7. Designation of the first signed receipt copy event for the register (Y/N)
8. Previous signature for the same register. Blank value is used for the first signed receipt copy event.

You can view the receipt copy signature, together with the event data that was used to generate it, on the **Signature** tab of the **Audit events** page in Retail Headquarters.

#### Digital signing of closed shifts

Closing a shift is registered as an event in the POS audit event log. The data that is signed for a shift closing event is a text string that consists of the following data fields:

1. Total amount of sales including tax per tax rate
2. Total amount of sales including tax
3. Date and time of the shift closing event in the format YYYYMMDDHHMMSS
4. Sequential number of the shift closing event
7. Designation of the first signed shift closing event for the register (Y/N)
8. Previous signature for the same register. Blank value is used for the first signed shift closing event.

You can view the signature of a closed shift, together with the shift data that was used to generate it, on the **Signature** tab of the **Shifts** page in Retail Headquarters.

#### Digital signing of events

The data that is signed for an event other than receipt copy or shift closing is a text string that consists of the following data fields:

1. Sequential number of the signed event
2. Pre-defined event code
3. Description of the event
4. Date and time of the event
5. Staff ID of the operator that raised the event
6. Register number
7. Designation of the first signed event for the register (Y/N)
8. Previous signature for the same register. Blank value is used for the first signed event.

You can view the event signature, together with the event data that was used to generate it, on the **Signature** tab of the **Audit events** page in Retail Headquarters.

#### Receipts

Receipts for France can include additional information that was implemented by using custom fields:

- **Transaction type**: You can add a field to a receipt format layout to identify the type of transaction. For example, a sales receipt will include the text "Sales".
- **Sequential number of signed sales transaction**: The sequential number of a signed sales transaction can appear on a receipt to associate the printed receipt with a digital signature in the database.
- **Extract from digital signature**: The extract from the digital signature may be printed on a receipt to confirm that the transaction is signed. The extract is a concatenation of the 3rd, 7th, 13th, and 19th symbols of the signature. 
- **Reprint number**: The number of the copy of a receipt may appear on a receipt or a receipt copy. It is equal to 0 for the original receipt.
- **Line count**: The number of printed item lines of a receipt may be printed on the receipt.
- **Sales totals**: Custom fields for receipt totals exclude non-sales amounts from the total transaction amounts. Non-sales amounts include amounts for the following operations:
  - Prepayments (customer account deposit)
  - Prepayments for sales orders (customer order deposit)
  - Issuing a gift card
  - Adding funds to a gift card
- **Certification data**: The category and number of the certificate of compliance issued by an authorized body per the NF 525 certification requirements may appear on a receipt. 
- **Build number**: The POS build number may appear on a receipt.

#### Restrincting shift duration

There is an option to enforce daily shift closing in POS. A shift cannot last longer than a specified **Shift closing time**. The operator will start receiving warnings that the shift must be closed several minutes before the time; this is controlled by the **Shift closing interval (minutes)** parameter.

#### X and Z reports

The information that is included on X and Z reports is based on French requirements:

- Total sales, including only amounts for cash sales transactions and exclude issue gift card operations and prepayments
- Total returns
- Cumulative grand total
- Cumulative perpetual grand total
- VAT amounts per tax rate

The totals are also stored in the closed shift record and transferred to Headquarters.

#### Period grand total journal

Period grand total journal summarizes sales totals per store and fiscal period.

Period grand total journals are maintained on the **Period grand total journal** page. To create a new journal, you need to specify a store. If previous journals exist for the store, the new journal period will be automatically identified as the next fiscal period after the last closed journal for the store. Otherwise, you need to specify the end date of the journal, and the period will be identified as the fiscal period that includes that date.

The journal may then be calculated: shifts closed in the journal's period are selected, and totals are calculated for these shifts. You can view the journal's tax totals per sales tax code, as well as the shifts included in the journal.

After being calculated, the journal may be closed. The closed journal may not be modified, and it is not possible to create another journal for a previous, the same, or intersecting period. The closed journal is digitally signed. You can view the journal signature, together with the journal data that was used to generate it, on the **Signature details** tab of the **Period grand total journal** page in Retail Headquarters.

The last closed journal for a store may be cancelled. After that, it is possible to create another journal for the same store and period.

#### Archive

Archive is an XML file that can be exported from a closed period grand total journal. It includes the closed period's totals and detailed sales transaction and event data. The exported file is digitally signed; the signature is contained in a separate file.

The archive format is implemented by using [Electronic reporting](../../dev-itpro/analytics/general-electronic-reporting.md). 

## Setting up Retail for France

This section describes the Retail settings that are specific to and recommended for France. For more information about how to set up Retail, see [Microsoft Dynamics 365 for Retail documentation](../index.md).

To use the France-specific functionality for Retail, you must complete these tasks:

- Set the **Country/region** field to **FRA** (France) in the primary address of the legal entity.
- Set the **ISO code** field to **FR** (France) in the POS functionality profile of every store that is located in France.

You must also specify the following settings for France. Note that you need to run appropriate distribution jobs after completing the setup.

### Set up the legal entity

Make the following changes on the **Legal entities** page:

- **Bank account information > Routing number**: specify the VAT identifier of the organization
- **Statutory reporting > NAF code**: specify the NAF code of the organization
- **Tax registration > Tax registration number**: specify the SIRET number of the organization

This settings will be used in archive format.
  
### Set up value-added tax (VAT) per French requirements

You must create sales tax codes, sales tax groups, and item sales tax groups. You must also set up sales tax information for products and services. For more information about how to set up and use sales tax in Microsoft Dynamics 365 for Finance and Operations, and in Retail, see [Sales tax overview](../../financials/general-ledger/indirect-taxes-overview.md).

You must also specify sales tax groups and enable the **Prices include sales tax** option for stores that are located in France.

### Set up functionality profiles

Enable auditing by setting the **Audit** checkbox.

Enforce daily shift closing:

- Set the **Enforce daily shift closing** checkbox;
- Specify **Shift closing time** and **Shift closing interval (minutes)**.

Set up required receipt numbering.

### Configure custom fields so that they can be used in receipt formats for sales receipts

You can configure the language text and custom fields that are used in the POS receipt formats. The default company of the user who creates the receipt setup should be the same as the legal entity where the language text setup is created. Alternatively, the same language texts should be created in both the user's default company and the legal entity of the store that the setup is created for.

On the **Language text** page, add the following records for the labels of the custom fields for receipt layouts. Note that the **Language ID**, **Text ID**, and **Text** values that are shown in the table are just examples. You can change them to meet to your requirements, however, you must use unique Text ID values that are equal to or greater than 900001.

| Language ID | Text ID | Text ID                    |
|-------------|---------|----------------------------|
| en-US       | 900001  | Transaction type           |
| en-US       | 900002  | Sequential number          |
| en-US       | 900003  | Digital signature          |
| en-US       | 900004  | Reprint number             |
| en-US       | 900005  | Sales tax amount           |
| en-US       | 900006  | Sales total                |
| en-US       | 900007  | Sales total tax            |
| en-US       | 900008  | Sales total including tax  |
| en-US       | 900009  | Build number               |
| en-US       | 900010  | Certification category     |
| en-US       | 900011  | Certificate number         |
| en-US       | 900012  | Line count                 |

On the **Custom fields** page, add the following records for the custom fields for receipt layouts. Note that **Caption text ID** values must correspond to the **Text ID** values that you specified on the **Language text** page.

| Name                            | Type    | Caption text ID |
|---------------------------------|---------|-----------------|
| TRANSACTIONTYPE                 | Receipt | 900001          |
| SEQUENTIALNUMBER                | Receipt | 900002          |
| DIGITALSIGNATURE                | Receipt | 900003          |
| REPRINTNUMBER                   | Receipt | 900004          |
| SALESTAXAMOUNT                  | Receipt | 900005          |
| SALESTOTAL                      | Receipt | 900006          |
| SALESTOTALTAX                   | Receipt | 900007          |
| SALESTOTALINCLUDETAX            | Receipt | 900008          |
| BUILDNUMBER                     | Receipt | 900009          |
| CERTIFICATIONCATEGORY           | Receipt | 900010          |
| CERTIFICATENUMBER               | Receipt | 900011          |
| LINECOUNT                       | Receipt | 900012          |
            
### Configure receipt formats

For all required receipt formats, change the value of the **Print behavior** field to **Always print** for the receipt format.

In the Receipt format designer, add the following custom fields to the appropriate receipt sections. Note that field names correspond to the language texts that you defined in the previous section.

1. Header:

    - **Transaction type**: This field identifies the type of receipt.

2. Lines:

    - It is recommended that you add the following standard fields: **Unit price with tax**, **Total price with tax**, and **Tax ID**.

3. Footer:

    - **Sales total**: This field prints the receipt's total cash sale amount. The amount excludes tax. Prepayments and gift card operations are excluded.
    - **Sales total tax**: This field prints the receipt's total tax amount for cash sales. Prepayments and gift card operations are excluded. 
    - **Sales total including tax**: This field prints the receipt's total cash sale amount. The amount includes tax. Prepayments and gift card operations are excluded.
    - **Tax ID**: This standard field enables printing sales tax summary per sales tax code. The field must be added to a new line.
    - **Sales tax amount**: This field prints the receipt's tax amount for cash sales per sales tax code. Prepayments and gift card operations are excluded. The field must be added to the same line as **Tax ID**.
    - **Sequential number**: This field prints the sequential number of a signed sales transaction.
    - **Digital signature**: This field prints the extract from the digital signature.
    - **Reprint number**: This field prints the number of the copy of a receipt.
    - **Build number**: This field prints the POS build number.
    - **Certification category**: This field prints the category of the certificate of compliance issued by an authorized body per the NF 525 certification requirements.
    - **Certificate number**: This field prints the number of the certificate of compliance issued by an authorized body per the NF 525 certification requirements.
    - **Line count**: This field prints the number of printed item lines of a receipt.
    - **Text**: Add a text field and specify the VAT identifier of the organization.
    - **Text**: Add a text field and specify the NAF code of the organization.
    - **Text**: Add a text field and specify the SIRET number of the organization.
    - **Store name**: This standard field prints the name of the store.
    - **Store address**: This standard field prints the address of the store.

For more information about how to work with receipt formats, see [Receipt templates and printing](../receipt-templates-printing.md).

### Configure the digital signature parameters for Retail Headquarters (INCOMPLETE)

### Configure the archive export format (INCOMPLETE)

The archive configuration is available for download from Microsoft Dynamics Lifecycle Services (LCS). For more information, see [Import electronic reporting configurations](../../dev-itpro/analytics/electronic-reporting-import-ger-configurations.md). You must download the following configurations:

- **Retail channel data** data model
- **???Retail data archive (FR)** format

After you import the configurations, on the **Retail parameters** page, on the **Electronic documents** tab, in the **Retail data archive export format** field, select the **???Retail data archive (FR)** format.

### Configure Retail channel components

To enable France-specific functionality, you must configure extensions for Retail channel components. For more information, see the [deployment guidelines](./emea-fra-deployment.md).
