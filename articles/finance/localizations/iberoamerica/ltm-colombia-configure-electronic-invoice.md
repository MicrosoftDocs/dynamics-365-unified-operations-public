---
title: Configure electronic invoice parameters for Colombia
description: Learn how to configure the information required to generate the electronic invoice XML for Colombia.
author: Fhernandez0088
ms.topic: how-to
ms.date: 08/18/2025
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Configure electronic invoice parameters for Colombia

[!include [banner](../../includes/banner.md)]

This article explains how to configure the information that is required to generate the electronic invoice XML for Colombia.

## Prerequisites

Before you complete the procedures in this article, the following prerequisites must be met:

- Both the country/region specific Latin American (LATAM) feature for Colombia and the general LATAM feature must be enabled.
- The company's address must be set to Colombia.
- You must download the specific report configurations from the Dataverse configuration repository for Colombia Electronic Invoices:

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

Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).
- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- Be sure to have already configured all the LATAM extensions before continuing with the configuration in this article.

## Configuration required for Colombia electronic invoices
The following configurations are required for Columbia electronic invoices. 
- Configure the tax application
- Configure the legal entity
- Configure the document classes
- Configure the sales point prefix
- Configure the field master lists
- Configure the fiscal information
- Configure the addresses
- Other tax application configurations
Each configuration is explained in the following sections.
### Configure the tax application

To configure the Tax application, go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax application** and select **New** to create a tax application record that has the code **COFE** (Colombian electronic invoice). Use this tax application record to assign the fiscal codification to each element in Microsoft Dynamics 365 Finance as required.

### Configure the legal entity
To configure the legal entity, follow these steps.
1. Go to **Organization administration** \> **Organizations** \> **Legal entities**, and follow these steps:
   1. Select the legal entity that you want to work with.
   1. Complete the address with country/region, state, and county.            
   1. Complete the contact information with the email address and set it to **Primary**.
   1. In the LATAM section complete the **Taxpayer type** with an option that represents organizations.
   1. Complete the **Based in country/region** with **COL**.
   1. Complete the **Country/region document type** with the option that represents the identification document type used by the organization.
   1. In the LATAM section complete the **Country/region identification number** field, enter the company ID number with the verification code at the end separated with a middle hyphen (i.e. 123456789-0).

### Configure the document classes

This configuration applies to Invoices, Credit notes and Debit notes.
To configure document classes, 
1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**, and follow these steps for each **Document class** that you want to use in Electronic Invoicing:
   1. Select the record and then go to **Tax application**.
   1. On the **Tax application** page, in the **Tax application id** field, enter the ID that is used for Colombian electronic invoicing.
   1. In the **Tax application code** field, enter the code according to the Colombian normative.
   1. In the **Letter code** field, enter **R** for debit and credit notes to enable the **Reference code** field when posting a transaction.
   1. In the **Legal Description** field, enter the electronic document description.
   1. Set the **Require CA number** slider to **Yes**.
   1. Set the **use reference document** slider to **Yes**.
   1. In the **Additional data** section, set the list 1 field to **Required**.

### Configure the sales point prefix

To configure the sales point prefix, follow these steps.
1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Sales point prefix** and for the sales point used for electronic invoicing follow these steps: 
1. Complete the **Prefix** field with the authorized prefix code for electronic invoicing.
1. In the field **Report/Service Id** select the **SSRS Reports / Services references** configured for electronic invoicing (see #Configure SSRS Reports / Services references)

### Configure the field master lists
To configure field master lists, follow these steps.
1. Go to **Organization administration > Setup > LATAM > Fields master List**.
1. In the **LIST 1** configure the codes for operation types and for credit and debit note types.
1. In the **LIST 9** configure a document type for reference (not mandatory).
1. In the **LIST 10** configure the codes for reference reasons for credit and debit notes according to the Colombian normative.

Learn more in [Field list configuration for Latin America](ltm-core-field-master-lists.md).

### Configure the fiscal information
To configure fiscal information, follow these steps.
1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax ID type**, and follow these steps for each record in the list:
1. Select the record, and then select **Tax application**.
1. On the **Tax application** page, in the **Tax application id** field, enter the code that is used for Colombian electronic invoicing.
1. In the **Tax application code** field, enter the code for tax IDs according to the Colombian normative.
1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Taxpayer type**. In the records that are used, go to the **Tax application** menu, and then follow these steps:
1. Create a record that has the tax application code that is used for Colombian electronic invoicing.
1. In the **Tax application code** field, enter the code of the taxpayer responsibility according to the Colombian normative.

Learn more in [Taxpayer types for Latin America](ltm-core-taxpayer-type.md) and [Tax ID types for Latin America](ltm-core-tax-id-type.md).

### Configure the addresses

To configure addresses, follow these steps.
1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**. 
1. For each record (Country/region, State and County) used in electronic invoicing go to **LATAM** \> **Tax application** to assign the tax application codes for according to the Colombian normative.

Learn more in [Address setup for Latin America](ltm-core-address-setup.md).

### Other tax application configurations

Go to **Accounts receivable** \> **Payments setup** \> **Methods of payment**, and follow these steps for each record in the list:

1. Select the record, and then ho to **Tax application** in the top menu.
1. Create a new record.
1. In the **Tax application id** field, enter the code that is used for Colombian electronic invoicing.
1. In the **Tax application code** field, enter the code for the payment method according to the Colombian normative.

Go to **Accounts receivable** \> **Payments setup** \> **Terms of payment**, and follow these steps for each record in the list:

1. Select the record, and then ho to **Tax application** in the top menu.
1. Create a new record.
1. In the **Tax application id** field, enter the code that is used for Colombian electronic invoicing.
1. In the **Tax application code** field, enter the code for the term of payment according to the Colombian normative (cash or credit).

Go to **Product information management** \> **Products** \> **Released products**, and follow these steps for each record in the list:

1. Select the record and in the top menu go to **LATAM > **Tax application**.
1. Create a new record.
1. In the **Tax application Id** field select the one used for Colombia electronic invoicing.
1. In the **Tax application code** field enter the code that identifies the product/service.
1. In the **User-defined field 1** field enter the number for the codification standard used for the product/service.
1. In the **User-defined field 2** enter the name for the codification standard used for the product/service. 
1. In the **User-defined field 3** enter code for the **SchemeAgencyID** used for the product/service.

Go to **Organization administration** \> **Setup** \> **Units** \> **Units**, and follow these steps for each record in the list:

1. Select the record, and then select **Tax application**.
1. Crate a new record.
1. In the **Tax code** field, enter the code according to the Colombian normative for units.

Go to **General ledger** \> **Currencies** \> **Currencies**, and follow these steps for each record in the list:

1. Select the record and then go to **Tax application** in the top menu.
1. Create a new record.
1. In the **Tax application id** field, select the code that is used for Colombian electronic invoicing.
1. In the **Tax application code** field, enter the currency code according to the Colombian normative.

### Configure the taxes 

To configure the taxes for each tax and percentage used, follow these steps.

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax codes**, and follow these steps for each record in the list:
   1. Select the record and then go to **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application id** field, select the code that is used for Colombian electronic invoicing.
   1. In the **Income tax code** field, enter the code that identifies the tax type according to the Colombian normative.
   1. In the **Code regime** field, enter the tax name according to the Colombian normative.
   1. In the **User-defined field 2** enter the tax percentage according to the tax codes of the Colombian normative.

## Configure electronic document references

When you issue an electronic document that has an associated document or period, you must select **References** on the posting page and add the associated document or period.

### Reference a document
To reference a document, follow these steps.

1. In the **Reference code** field enter the number code for reference reason according to the Colombian normative.
1. Complete the **Reference date** field.
1. Complete the **Reference document number** field with the complete document number referenced.
1. Complete the **Reference reason** with a motive (not mandatory).

> [!NOTE] 
> The referenced document must be already validated/approved by the fiscal authority and the XML response attached in the invoice journal.

### Reference a period

When referencing a period enter two lines of references completing in the first line the **Reference date** field with the starting date of the period and in the second line with the ending date of the period.

Also complete the field **Reference reason** with the phrase **StartDate** in the first line and **EndDate** in the second line to indicate which is the starting and ending date of the period.

Learn more in [Configure electronic document references](ltm-electronic-doc-references.md).

## Configure lookups

You must configure the required lookups to be able to issue an electronic document. To configure lookups, follow these steps.

1. Go to **Organization administration > Electronic reporting > Configurations**.
1. Select the report to configure on the left menu.
1. Go to **Application specific parameters** setup in the top menu.
1. Select the report version to configure.
1. In the **Lookups** section select the **VAT/WithholdingTax** lookup.
1. In the **Conditions section** add the required **Lookup results** and select the corresponding tax codes for each one.
1. In the **Conditions section** add the **N/A** lookup result for taxes that should not appear in the electronic document submission such as self-withholdings.

> [!NOTE] 
> To ensure that the report shows the transactions that meet the configured conditions, complete the Lookup result field as Not Applicable with blank and not-blank conditions.

## Configure SSRS Reports / Services references

For electronic invoicing you must configure the **SSRS Reports / Services references**. To configure  SSRS Reports / Services references follow these steps.

1. Go to Organization administration **Setup > LATAM > SSRS Reports / Services references**.
1. Create a new record.
1. Complete the **Report/Service Id** and **Report/Service name** with a code and description.
1. In **Settings** tab select **Service** for the **Report/Service type** field.
1. In the **Sales point type** select **Pre-printed** (it must match the sales point type used for electronic invoicing.
1. In **Parameter** section add the following lines:
    1. **Name:** TaxApplicationId - **Value:** COFE (this code must match the tax application used for electronic invoicing)
    1. **Name:** Environment - **Value:** 2 or 1 (this code defines if the environment is for 2: Testing or 1: Production)
    1. **Name:** TechnicalKey - **Value:** (it is defined for each company, this code is the technical key used for electronic invoicing circuit)

> [!NOTE] 
> This configuration will be applied to all sales points used for every Invoice, Credit note and Debit note.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
