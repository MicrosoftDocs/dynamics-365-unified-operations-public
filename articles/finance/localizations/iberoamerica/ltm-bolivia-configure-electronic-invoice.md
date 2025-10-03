---
title: Configure electronic invoice parameters for Bolivia
description: Learn how to configure the information required to generate the electronic invoice XML for Bolivia.
author: MatiasPizmeny01
ms.author: v-mpizmeny
ms.topic: how-to
ms.date: 10/03/2025
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Configure electronic invoice parameters for Bolivia

[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to set up the information required to generate the electronic invoice XML for Bolivia.

## Prerequisites

Before you complete the procedures in this article, make sure the following prerequisites are met:

- Enable the country/region-specific Latin American (LATAM) feature for Bolivia, and the general LATAM feature.
- Set the company's address to Bolivia.
- Download the specific report configurations from the Dataverse configuration repository for Bolivian Electronic Invoices:

| Element |                    Format name                    |
|:-------:|:-------------------------------------------------:|
| Model   | :::no-loc text="Invoice Model LATAM":::                               |
| Mapping | :::no-loc text="(Invoice Model LATAM) Invoice Model mapping LATAM"::: |
| Format  | :::no-loc text=" (Preview) Inventory e-Invoice (BO)":::                   |
| Format  | :::no-loc text=" (Preview) Inventory Discount e-CreditDebit Note (BO) ":::                       |
| Format  | :::no-loc text=" (Preview) Inventory e-CreditDebit Note (BO)":::                        |
| Format  | :::no-loc text=" (Preview) Inventory Export e-Invoice (BO)":::                          |
| Format  | :::no-loc text=" (Preview) Service export e-Invoice (BO) ":::                          |
| Format  | :::no-loc text=" (Preview) Zero Rate e-Invoice (BO) ":::                          |

Learn more in [Import electronic reporting (ER) configurations from Dataverse](gsw-import-er-config-dataverse.md).
- Configure the electronic reporting (ER) parameters. Learn more in [Configure the electronic reporting (ER) framework](electronic-reporting-er-configure-parameters.md).
- Configure all the LATAM extensions before you continue with the configuration in this article.

## Configuration required for Bolivia electronic invoices

Complete these configurations for Bolivia electronic invoices.

- Set up the tax application
- Set up the legal entity
- Set up customers
- Set up the document classes
- Set up the sales point prefix
- Set up the document class sales point
- Set up the fiscal information
- Set up the addresses
- Set up other configurations
- Set up domestic and international costs and expenses for export invoices
- Set up taxes

Each configuration is described in the sections that follow.

### Configure the tax application

To configure the tax application, go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax application**, and select **New** to create a tax application record with the code **BOFE** (Bolivian electronic invoice). Use this tax application record to assign the fiscal codification to each element in Microsoft Dynamics 365 Finance as required.

### Configure the legal entity

To configure the legal entity, follow these steps.

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
1. Select the legal entity that you want to work with.
1. Complete the address fields with the country/region, city, street, and street number.
1. Enter the phone number in the contact information and set it to **Primary**.
1. In the LATAM section, complete the **Taxpayer type** with an option that represents the organization.
1. Complete the **Based in country/region** field with **BOL**.
1. Complete the **Country/region document type** field with the option that represents the identification document type used by the organization.
1. In the LATAM section, in the **Country/region identification number** field, enter the company ID number.
1. In the LATAM section, complete the **Free Text 1** field with the company activity code number.

### Configure customers

To configure customers, follow these steps.

1. Go to **Accounts receivable** \> **Customers** \> **All customers**.
1. For each customer used in transactions:
   1. Complete the **organization number** field with the unique customer identification code.
   1. Complete the address fields with the country/region, city, street, and street number.
   1. In the LATAM section, complete the **Taxpayer type** with an option that represents the customer.
   1. Complete the **Based in country/region** with an option that represents the customer.
   1. Complete the **Country/region document type** field with the option that represents the customer.
   1. In the LATAM section, complete the **Country/region identification number** field. Enter the customer ID number.

### Configure the document classes

This configuration applies to invoices, credit notes, and debit notes.

To configure document classes, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**.
1. For each **Document class** that you want to use in electronic invoicing:
   1. Select the record and set the **Use reference document** slider to **Yes** for debit notes and credit notes to enable the **Invoice posting references** section when posting a transaction.
   1. Go to **Tax application**.
   1. On the **Tax application** page, in the **Tax application id** field, enter the ID that is used for Bolivian electronic invoicing.
   1. In the **Tax application code** field, enter the code according to the Bolivian normative.

### Configure the sales point prefix

To configure the sales point prefix, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Sales point prefix** and for the sales point used for electronic invoicing follow these steps:
1. Complete the **Prefix** field with the sales point code.
1. On the **Tax application** page, in the **Tax application id** field, enter the ID that is used for Bolivian electronic invoicing.
1. In the **Tax application code** field, enter the branch code.
1. In the field **Report/Service Id**, select the **SSRS Reports / Services references** configured for electronic invoicing [Configure SSRS Reports / Services references](#configure-ssrs-reports-and-services-references).

### Configure the document class sales point

To configure the document class sales point, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class sales point** and for the document class ID and sales point used for electronic invoicing follow these steps:
1. Enter **Customer** in the **Account type** field.
1. Enter a number sequence that represents the document class in the **Number sequence code** field.
1. Enter the registered branch address in the **Printing concept 1** field on the **Printing section**.

### Configure the fiscal information

To configure fiscal information, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax ID type**, and follow these steps for each record in the list:
1. Select the record, then select **Tax application**.
1. On the **Tax application** page, enter the code that is used for Bolivian electronic invoicing in the **Tax application id** field.
1. Enter the code for tax IDs according to the Bolivian normative in the **Tax application code** field.

### Configure the addresses

To configure addresses, follow these steps.

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**.
1. For each **Country** record used in electronic invoicing, go to **LATAM** \> **Tax application** to assign the tax application codes according to the Bolivian normative.
1. For each **City** record used in electronic invoicing, enter the description according to the Bolivian normative.

Learn more in [Address setup for Latin America](ltm-core-address-setup.md).

### Other configurations

#### Method of payments

To configure the method of payments, follow these steps.

1. Go to **Accounts receivable** \> **Payments setup** \> **Methods of payment**.
1. For each record in the list:
   1. Select the record, and then go to **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application id** field, enter the code that is used for Bolivian electronic invoicing.
   1. In the **Tax application code** field, enter the code for the payment method according to the Bolivian normative.
   1. If a card number is required, follow these steps:
   1. In the **Service level** field, create a new record.
   1. In the **Code** field, enter the card number according to the Bolivian normative (if applicable).

#### Terms of delivery

To configure terms of delivery, follow these steps.

1. Go to **Sales and marketing** \> **Setup** \> **Distribution** \> **Terms of delivery**.
1. Create a new record.
1. Complete the **Delivery terms** field.
1. Complete the **Description** field.

#### Configure released products

To configure released products, follow these steps.

1. Go to **Product information management** \> **Products** \> **Released products**.
1. For each record in the list:
   1. Select the record and in the top menu go to **LATAM** \> **Tax application**.
   1. Create a new record.
   1. In the **Tax application Id** field, select the one used for Bolivian electronic invoicing.
   1. In the **Tax application code** field, enter the code that identifies the product/service according to the Bolivian normative.
   1. In the **User-defined field 1** field, enter the NANDINA code according to current customs regulations.

#### Configure Units

To configure Units, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **Units** \> **Units**.
1. For each record in the list:
   1. Select the record, then select **Tax application**.
   1. Create a new record.
   1. In the **Tax application id** field, enter the code that is used for Bolivian electronic invoicing.
   1. In the **Tax application code** field, enter the unit code according to the Bolivian normative.

> [!NOTE]
> When posting transactions by using a product of type 'Service', code 58 automatically displays by default.

#### Currencies configuration

To configure currencies, follow these steps.

1. Go to **General ledger** \> **Currencies** \> **Currencies**.
1. For each record in the list:
   1. Select the record and then go to **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application id** field, select the code that is used for Bolivian electronic invoicing.
   1. In the **Tax application code** field, enter the currency code according to the Bolivian standard.

### Configure domestic and international costs and expenses for export invoices

This section explains how to configure domestic and international costs and expenses for export invoices.

1. Go to **Accounts receivable** \> **Charges setup** \> **Charges code**.
1. For each record that you use as a domestic cost and expense for export invoices, follow these steps:
   1. Select a record and go to **LATAM** \> **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application Id** field, select the one used for Bolivian Electronic Invoice.
   1. In the **Tax application code** field, enter **N** for national.
   1. In the **Description** field, enter the charge motive.

1. For each record that you use as an international cost and expense for export invoices, follow these steps:
   1. Select a record and go to **LATAM** \> **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application Id** field, select the one used for Bolivian Electronic Invoice.
   1. In the **Tax application code** field, enter **I** for international.
   1. In the **Description** field, enter the charge motive.
   
### Configure Taxes

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax codes**.
1. For each **VAT** tax you use:
   1. In the **Calculation parameters** section, in the **Origin** field, select **Calculated percentage of net amount**.
   1. Go to **Sales tax code** \> **Values** in the top menu.
   1. In the **Values** field, enter the tax rate according to the Bolivian normative.

## Configure electronic document references

To configure electronic document references, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Electronic documents references**.
1. In the **Tax application Id** field, enter the ID that you use for Bolivian electronic invoices.

### Steps to reference a document

When you issue an electronic document that has an associated document, you must select **References** on the posting page and add the associated document.

To reference a document, follow these steps.

1. Go to the General tab, select **Source Vouchers**, and from the list of documents, select the document to associate.
1. Complete the **Reference reason** with a motive (not mandatory).

## Configure lookups

Configure the required lookups to issue an electronic document.

Follow these steps to configure lookups.

1. Go to **Organization administration** \> **Electronic reporting** \> **Configurations**.
1. Select the report to configure in the left menu.
1. Go to **Application specific parameters** in the top menu.
1. Select the report version to configure.
1. In the Lookups section, select the **TaxType** lookup.
1. In the **Conditions section**, select **VAT** in the **Lookup result field** and assign the corresponding tax codes.

> [!NOTE] 
> To ensure the report shows transactions that meet the configured conditions, complete the Lookup result field as N/A with **Blank** and **Not blank** conditions.

## Configure SSRS reports and services references

For electronic invoicing, you must configure the **SSRS Reports / Services references**.

To configure SSRS reports and services references, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **SSRS Reports / Services references**.
1. Create a new record.
1. Enter a code and description in the Report/Service ID and Report/Service name fields.
1. In the Settings tab, select Service for the Report/Service type field.
1. In the **Sales point type** field, select **Pre-printed** (this selection must match the sales point type used for electronic invoicing).
1. In the **Parameter** section, add the following line:
   1. **Name:** TaxApplicationId.
   1. **Value:** BOFE (this code must match the tax application used for electronic invoicing).

> [!NOTE] 
> This configuration applies to all sales points used for every invoice, credit note, and debit note.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]