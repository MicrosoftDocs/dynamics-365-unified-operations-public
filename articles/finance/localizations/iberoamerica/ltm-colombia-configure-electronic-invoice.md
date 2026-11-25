---
title: Configure electronic invoice parameters for Colombia
description: Learn how to configure the information required to generate the electronic invoice XML for Colombia.
author: MatiasPizmeny01
ms.topic: how-to
ms.date: 11/25/2026
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-mpizmeny
---

# Configure electronic invoice parameters for Colombia

[!INCLUDE [banner](../../includes/banner.md)]

This article explains how to set up the information required to generate the electronic invoice XML for Colombia.

## Prerequisites

Before completing the procedures in this article, ensure you meet the following prerequisites:

- Enable both the country/region-specific Latin American (LATAM) feature for Colombia and the general LATAM feature.
- Set the company's address to Colombia.
- Download the specific report configurations from the Dataverse configuration repository for Colombia Electronic Invoices:

| Element |                    Format name                    |
|:-------:|:-------------------------------------------------:|
| Model   | :::no-loc text="Invoice Model LATAM":::                               |
| Mapping | :::no-loc text="(Invoice Model LATAM) Invoice Model mapping LATAM"::: |
| Format  | :::no-loc text="Inventory e-Invoice format (CO)":::                   |
| Format  | :::no-loc text="Inventory e-CreditNote (CO)":::                       |
| Format  | :::no-loc text="Inventory e-DebitNote (CO)":::                        |
| Format  | :::no-loc text="Inventory e-Invoice (CO)":::                          |
| Format  | :::no-loc text="Project e-Invoice format (CO)":::                     |
| Format  | :::no-loc text="Project e-CreditNote (CO)":::                         |
| Format  | :::no-loc text="Project e-DebitNote (CO)":::                          |
| Format  | :::no-loc text="Project e-Invoice (CO)":::                            |

For more information, see [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).
- Configure the Electronic reporting (ER) parameters. For more information, see [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- Configure all the LATAM extensions before continuing with the configuration in this article.

## Configuration required for Colombia electronic invoices

The following configurations are required for Colombia electronic invoices.

- Configure the tax application
- Configure the legal entity
- Configure the document classes
- Configure the sales point prefix
- Configure the field master lists
- Configure the fiscal information
- Configure the addresses
- Configure other tax applications
- Configure charges and discounts
- Configure taxes

Each configuration is described in the following sections.

### Configure the tax application

To configure the tax application, go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax application**, and select **New** to create a tax application record with the code **COFE** (Colombian electronic invoice). Use this tax application record to assign the fiscal codification to each element in Microsoft Dynamics 365 Finance as required.

### Configure the legal entity

To configure the legal entity, follow these steps:

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
1. Select the legal entity that you want to work with.
1. Complete the address fields with the country/region, state, and county.
1. Complete the contact information with the email address and set it to **Primary**.
1. In the LATAM section, complete the **Taxpayer type** with an option that represents organizations.
1. Complete the **Based in country/region** field with **COL**.
1. Complete the **Country/region document type** field with the option that represents the identification document type used by the organization.
1. In the **Country/region identification number** field, enter the company ID number with the verification code at the end separated by a middle hyphen (for example, 123456789-0).

### Configure the document classes

This configuration applies to invoices, credit notes, and debit notes.

To configure document classes, follow these steps:

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**.
1. For each **Document class** that you want to use in Electronic Invoicing:
   1. Select the record and then go to **Tax application**.
   1. On the **Tax application** page, in the **Tax application ID** field, enter the ID that's used for Colombian electronic invoicing.
   1. In the **Tax application code** field, enter the code according to Colombian regulations.
   1. In the **Letter code** field, enter **R** for debit and credit notes to enable the **Reference code** field when posting a transaction.
   1. In the **Legal Description** field, enter the electronic document description.
   1. Set the **Require CA number** slider to **Yes**.
   1. Set the **Use reference document** slider to **Yes**.
   1. In the **Additional data** section, set the list 1 field to **Required**.
   1. In the **Document mask** section, set the entry parameter for the **Customer** record to **Auto**.

### Configure the sales point prefix

To configure the sales point prefix, follow these steps:

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Sales point prefix** and, for the sales point used for electronic invoicing, follow these steps:
1. Set the **Validate CA** slider to **Yes**.
1. Complete the **Prefix** field with the authorized prefix code for electronic invoicing.
1. In the **Report/Service ID** field, select the **SSRS Reports / Services references** configured for electronic invoicing (see #Configure SSRS Reports / Services references).

### Configure CUFE parameters

To configure the CUFE parameters, follow these steps:

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **LATAM parameters**.
1. On the navigation pane, go to **Functionalities**.
1. Set the **Enable additional authorization code** slider to **Yes**.
1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class sales point** and, for the sales point and document class used for electronic invoicing, follow these steps:
1. Select the **Sales CA** button on the top menu and create a record.
1. Enter the **Resulution number** in the **Authorization code (CA)** field.
1. Enter the **Technical key** in the **Additional CA** field.
1. Enter the valid date range of the resolution in the **Date from** and **Date to** fields.
1. Enter the folio range in the **From voucher number** and **To voucher number** fields.

### Configure the field master lists

To configure field master lists, follow these steps:

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Fields master List**.
1. In **LIST 1**, configure the codes for operation types and for credit and debit note types.
1. In **LIST 9**, configure a document type for reference (not mandatory).
1. In **LIST 10**, configure the codes for reference reasons for credit and debit notes according to the Colombian normative.

Learn more in [Field list configuration for Latin America](ltm-core-field-master-lists.md).

### Configure the fiscal information

To configure fiscal information, follow these steps:

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax ID type**, and follow these steps for each record in the list:
1. Select the record, and then select **Tax application**.
1. On the **Tax application** page, in the **Tax application ID** field, enter the code that is used for Colombian electronic invoicing.
1. In the **Tax application code** field, enter the code for tax IDs according to the Colombian normative.
1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Taxpayer type**. In the records that are used, go to the **Tax application** menu, and then follow these steps:
1. Create a record that has the tax application code that is used for Colombian electronic invoicing.
1. In the **Tax application code** field, enter the code of the taxpayer responsibility according to the Colombian normative.

Learn more in [Taxpayer types for Latin America](ltm-core-taxpayer-type.md) and [Tax ID types for Latin America](ltm-core-tax-id-type.md).

### Configure the addresses

To configure addresses, follow these steps:

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**.
1. For each record (Country/region, State, and County) used in electronic invoicing, go to **LATAM** \> **Tax application** to assign the tax application codes according to the Colombian normative.

Learn more in [Address setup for Latin America](ltm-core-address-setup.md).

### Other tax application configurations

#### Methods of payment

To configure the methods of payment, follow these steps:

1. Go to **Accounts receivable** \> **Payments setup** \> **Methods of payment**.
1. For each record in the list:
   1. Select the record, and then go to **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application ID** field, enter the code that's used for Colombian electronic invoicing.
   1. In the **Tax application code** field, enter the code for the payment method according to the Colombian normative.

#### Terms of payment

To configure the terms of payment, follow these steps:

1. Go to **Accounts receivable** \> **Payments setup** \> **Terms of payment**.
1. For each record in the list:
   1. Select the record, and then go to **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application ID** field, enter the code that's used for Colombian electronic invoicing.
   1. In the **Tax application Code** field, enter the code for the term of payment according to the Colombian normative (cash or credit).

#### Configure released products

To configure released products, follow these steps:

1. Go to **Product information management** \> **Products** \> **Released products**.
1. For each record in the list:
   1. Select the record and in the top menu go to **LATAM** \> **Tax application**.
   1. Create a new record.
   1. In the **Tax application ID** field, select the one used for Colombia electronic invoicing.
   1. In the **Tax application code** field, enter the code that identifies the product or service.
   1. In the **User-defined field 1** field, enter the number for the codification standard used for the product or service.
   1. In the **User-defined field 2** field, enter the name for the codification standard used for the product or service.
   1. In the **User-defined field 3** field, enter the code for the **SchemeAgencyID** used for the product or service.

#### Configure units

To configure units, follow these steps:

1. Go to **Organization administration** \> **Setup** \> **Units** \> **Units**.
1. For each record in the list:
   1. Select the record, and then select **Tax application**.
   1. Create a new record.
   1. In the **Tax code** field, enter the code according to the Colombian normative for units.

#### Configure currencies

To configure currencies, follow these steps:

1. Go to **General ledger** \> **Currencies** \> **Currencies**.
1. For each record in the list:
   1. Select the record and then go to **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application ID** field, select the code that's used for Colombian electronic invoicing.
   1. In the **Tax application code** field, enter the currency code according to the Colombian normative.

### Configure charges and discounts

This section explains how to configure global line charges and discounts.

#### Configure global and line charges

To configure global and line charges, follow these steps:

1. Go to **Accounts receivable** > **Charges setup** > **Charges code**.
1. For each record that you use as a global or line charge, follow these steps:
   1. Select a record and go to **LATAM** > **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application ID** field, select the one used for Colombia Electronic Invoice.
   1. In the **Tax application code** field, enter the code according to the Colombian normative.

#### Configure global discounts

To configure global discounts, follow these steps:

1. Go to **Accounts receivable** > **Charges setup** > **Charges code**.
1. For each record that you use as a global discount, follow these steps:
   1. Select a record and go to **LATAM** > **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application ID** field, select the one used for Colombia Electronic Invoice.
   1. In the **Tax application code** field, enter the code according to the Colombian normative.

#### Line discounts

To use line discounts in the Colombian electronic invoice, use the finance and operations apps line discount feature.

> [!NOTE]
> To enter a global discount, use the **Maintain charges** button on the sales orders, enter the amount as a negative, and set the tax code for the global discount to **Excluded**.

> [!NOTE]
> The charge code description is used in the discount or charge reason description of the invoice.

### Configure taxes

To configure the taxes for each tax and percentage used, follow these steps:

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax codes**.
1. For each record in the list:
   1. Select the record and then go to **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application ID** field, select the code that's used for Colombian electronic invoicing.
   1. In the **Income tax code** field, enter the code that identifies the tax type according to the Colombian normative.
   1. In the **Code regime** field, enter the tax name according to the Colombian normative.
   1. In the **User-defined field 2**, enter the tax percentage according to the tax codes of the Colombian normative.

## Configure electronic document references

When you issue an electronic document that has an associated document or period, select **References** on the posting page and add the associated document or period.

### Reference a document

To reference a document, follow these steps:

1. In the **Reference code** field, enter the number code for reference reason according to the Colombian normative.
1. Complete the **Reference date** field.
1. Complete the **Reference document number** field with the complete document number referenced.
1. Complete the **Reference reason** with a motive (not mandatory).

> [!NOTE]
> The referenced document must be validated and approved by the fiscal authority and the XML response attached in the invoice journal.

### Reference a period

When you reference a period, enter two lines of references. In the first line, enter the starting date of the period in the **Reference date** field. In the second line, enter the ending date of the period in the **Reference date** field.  

Also, enter the phrase **StartDate** in the **Reference reason** field for the first line and **EndDate** for the second line to indicate the starting and ending dates of the period.  

Learn more in [Configure electronic document references](ltm-electronic-doc-references.md).

## Configure lookups

You must configure the required lookups to issue an electronic document.  

To configure lookups, follow these steps:

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.  
1. Select the report to configure on the left menu.
1. Go to **Application specific parameters** setup in the top menu.
1. Select the report version to configure.
1. In the **Lookups** section, select the **VAT/WithholdingTax** lookup.  
1. In the **Conditions** section, add the required **Lookup results** and select the corresponding tax codes for each one.  
1. In the **Conditions** section, add the **N/A** lookup result for taxes that shouldn't appear in the electronic document submission, such as self-withholdings.  

> [!NOTE]
> To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** field as Not Applicable with blank and non-blank conditions.

## Configure SSRS reports and services references

For electronic invoicing, you must configure the **SSRS Reports / Services references**.

To configure SSRS reports and services references, follow these steps:

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **SSRS Reports / Services references**.
1. Create a new record.
1. Enter a code and description in the **Report/Service ID** and **Report/Service name** fields.
1. On the **Settings** tab, select **Service** for the **Report/Service type** field.
1. In the **Sales point type** field, select **Pre-printed** (it must match the sales point type used for electronic invoicing).
1. In the **Parameter** section, add the following lines:
    1. **Name:** TaxApplicationId - **Value:** COFE (this code must match the tax application used for electronic invoicing).
    1. **Name:** Environment - **Value:** 2 or 1 (this code defines whether the environment is 2: Testing or 1: Production).

> [!NOTE]
> This configuration applies to all sales points used for every invoice, credit note, and debit note.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
