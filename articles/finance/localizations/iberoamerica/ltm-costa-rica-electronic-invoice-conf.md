---
title: Configure electronic invoice parameters for Costa Rica
description: Learn how to configure the information required to generate the electronic invoice XML for Costa Rica, including an outline on the required configuration.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: how-to
ms.date: 09/29/2025
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Configure electronic invoice parameters for Costa Rica

[!include [banner](../../includes/banner.md)]

This article describes the main configuration settings required to issue electronic invoices in Costa Rica using Microsoft Dynamics 365 Finance.

> [!NOTE]
> In addition to these settings, you may need to configure other fields that are related to additional system features. To ensure a complete and accurate implementation of the Costa Rican localization, it's recommended that you review the rest of the available documentation for country-specific configurations.
> Learn more in [Costa Rica overview](costa-rica.md).

## Prerequisites

Before you complete the procedures in this article, make sure the following prerequisites are met:

- Enable the country/region-specific Latin American (LATAM) feature for Costa Rica, and the general LATAM feature.
- Set the company's address to Costa Rica.
- Download the specific report configurations from the Dataverse configuration repository for Costa Rican Electronic Invoices:

| Element |                    Format name                    |
|:-------:|:-------------------------------------------------:|
| Model   | :::no-loc text="Invoice Model LATAM":::                               |
| Mapping | :::no-loc text="(Invoice Model LATAM) Invoice Model mapping LATAM"::: |
| Format  | :::no-loc text="Inventory e-invoice (CRI)":::                   |
| Format  | :::no-loc text="Inventory Credit Note (CRI)":::                       |
| Format  | :::no-loc text="Inventory Debit Note (CRI)":::                        |
| Format  | :::no-loc text="Inventory e-invoice (CR)":::                          |
| Format  | :::no-loc text="Inventory Export e-Invoice (CRI)":::                     |
| Format  | :::no-loc text="Payment Receipt (CRI)":::                         |
| Format  | :::no-loc text="Project e-invoice (CRI)":::                          |
| Format  | :::no-loc text="Project Credit Note (CRI)":::                            |
| Format  | :::no-loc text="Project Debit Note (CRI)":::                            |
| Format  | :::no-loc text="Project e-invoice (CR)":::                            |
| Format  | :::no-loc text="Project Export e-Invoice (CRI)":::                            |
| Format  | :::no-loc text="Purchase e-invoice (CRI)":::                            |

Learn more in [Import electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).
- Configure the electronic reporting (ER) parameters. Learn more in [Configure the electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- Configure all the LATAM extensions before you continue with the configuration in this article.

## Configuration required for Costa Rica electronic invoices

These configurations are required for Costa Rican electronic invoices.

- Set up the tax application
- Set up the legal entity
- Set up customers
- Set up vendors
- Set up the document classes
- Set up the sales point prefix
- Set up the field master lists
- Set up the fiscal information
- Set up the addresses
- Set up other configurations
- Set up charges and discounts
- Set up taxes

Each configuration is described in the sections that follow.

### Configure the tax application

To configure the tax application, go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax application**, and select **New** to create a tax application record with the code **CRFE** (Costa Rican electronic invoice). Use this tax application record to assign the fiscal codification to each element in Microsoft Dynamics 365 Finance as required.

### Configure the legal entity

To configure the legal entity, follow these steps.

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
1. Select the legal entity that you want to work with.
1. Complete the address fields with the country/region, state, county, and city.
1. Enter the email address in the contact information and set it to **Primary**.
1. In the LATAM section, complete the **Taxpayer type** with an option that represents the organization.
1. Complete the **Based in country/region** field with **CRI**.
1. Complete the **Country/region document type** field with the option that represents the identification document type used by the organization.
1. In the LATAM section, complete the **Country/region identification number** field, enter the company ID number (for example, 1-123-45678901).
1. In the LATAM section, complete the **Free Text 1** field with the company activity code number.

### Configure customers

To configure customers, follow these steps.

1. Go to **Accounts receivable** \> **Customers** \> **All customers**.
1. For each customer used in transactions:
   1. Complete the address fields with the country/region, state, county and city.
   1. Complete the contact information with the email address and set it to **Primary**.
   1. In the LATAM section, complete the **Taxpayer type** with an option that represents the customer.
   1. Complete the **Based in country/region** with an option that represents the customer.
   1. Complete the **Country/region document type** field with the option that represents the customer.
   1. In the LATAM section, complete the **Country/region identification number** field, enter the customer ID number (for example, 1-123-45678901).
   1. In the top menu go to **General** \> **Business classification**.
   1. Create a new record.
   1. Complete the **Business classifications** field with the customer activity code number.
  
### Configure vendors

To configure vendors, follow these steps.

1. Go to **Accounts payable** \> **Vendors** \> **All vendors**.
1. For each vendor used in transactions:
   1. Complete the address fields with the country/region, state, county and city.
   1. Complete the contact information with the email address and set it to **Primary**.
   1. In the LATAM section, complete the **Taxpayer type** with an option that represents the vendor.
   1. Complete the **Based in country/region** with an option that represents the vendor.
   1. Complete the **Country/region document type** field with the option that represents the vendor.
   1. In the LATAM section, complete the **Country/region identification number** field, enter the vendor ID number.

### Configure the document classes

This configuration applies to Invoices, Credit notes, Debit notes, Purchase invoices and Payment receips.

To configure document classes, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**.
1. For each **Document class** that you want to use in Electronic Invoicing:
   1. Select the record and then go to **Tax application**.
   1. On the **Tax application** page, in the **Tax application id** field, enter the ID that is used for Costa Rican electronic invoicing.
   1. In the **Tax application code** field, enter the code according to the Costa Rican normative.
   1. In the **Letter code** field, enter **R** for debit notes, credit notes and purchase invoices to enable the **Reference code** field when posting a transaction.
   1. In the **User-defined field 2** field, enter the status code of the electronic document according to the Costa Rican normative.
   1. Set the **Use reference document** slider to **Yes** for debit notes, credit notes and purchase invoices to enable the **Invoice posting references** section when posting a transaction.

### Configure the sales point prefix

To configure the sales point prefix, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Sales point prefix** and for the sales point used for electronic invoicing follow these steps:
1. Complete the **Prefix** field with the sales point code.
1. On the **Tax application** page, in the **Tax application id** field, enter the ID that is used for Costa Rican electronic invoicing.
1. In the **Tax application code** field, enter the branch or head office code.
1. In the field **Report/Service Id**, select the **SSRS Reports / Services references** configured for electronic invoicing [Configure SSRS Reports / Services references](#configure-ssrs-reports-and-services-references).

### Configure the field master lists

To configure field master lists, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Fields master List**.
1. In the **LIST 9**, configure a document type code for reference according to the Costa Rican normative.
1. In the **LIST 10**, configure the codes for reference reasons for credit notes, debit notes and purchase invoices according to the Costa Rican normative.

Learn more in [Field list configuration for Latin America](ltm-core-field-master-lists.md).

### Configure the fiscal information

To configure fiscal information, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax ID type**, and follow these steps for each record in the list:
1. Select the record, and then select **Tax application**.
1. On the **Tax application** page, in the **Tax application id** field, enter the code that is used for Costa Rican electronic invoicing.
1. In the **Tax application code** field, enter the code for tax IDs according to the Costa Rican normative.

### Configure the addresses

To configure addresses, follow these steps.

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**.
1. For each record (State, County and City) used in electronic invoicing go to **LATAM** \> **Tax application** to assign the tax application codes according to the Costa Rican normative.
1. For each record (State, County and City) used in electronic invoicing complete the description field according to the Costa Rican normative.

Learn more in [Address setup for Latin America](ltm-core-address-setup.md).

### Other configurations

#### Method of payments

To configure the method of payments, follow these steps.

1. For customers, go to **Accounts receivable** \> **Payments setup** \> **Methods of payment**.
1. For each record in the list:
   1. Select the record, and then go to **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application id** field, enter the code that is used for Costa Rican electronic invoicing.
   1. In the **Tax application code** field, enter the code for the payment method according to the Costa Rican normative.

1. For vendors, go to **Accounts payable** \> **Payments setup** \> **Methods of payment**.
1. For each record in the list:
   1. Select the record, and then go to **Local instrument**.
   1. Create a new record.
   1. Enter the **Code** field used for Costa Rican electronic invoicing.

#### Terms of payments

To configure the terms of payment, follow these steps.

1. Go to **Accounts receivable** \> **Payments setup** \> **Terms of payment**.
1. For each record in the list:
   1. Select the record, and then go to **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application id** field, enter the code that is used for Costa Rican electronic invoicing.
   1. In the **Tax application code** field, enter the code for the sales condition according to the Costa Rican normative.
   1. In the **Days** field, enter the credit term (if applicable).

#### Configure released products

To configure released products, follow these steps.

1. Go to **Product information management** \> **Products** \> **Released products**.
1. For each record in the list:
   1. Select the record and in the top menu go to **LATAM** \> **Tax application**.
   1. Create a new record.
   1. In the **Tax application Id** field, select the one used for Costa Rican electronic invoicing.
   1. In the **Tax application code** field, enter the code that identifies the product/service.
   1. In the **User-defined field 1** field, enter the transaction type code according to the Costa Rican normative.
   1. In the **User-defined field 3** field, enter the tariff heading code according to the Costa Rican normative.
   1. In the top menu go to **Manage inventory** \> **GTIN codes**.
   1. Create a new record.
   1. In the **GTIN** field, enter the comercial code that identifies the product according to the Costa Rican normative.

> [!NOTE]
> When posting transactions using Free Text Invoice or Project on Account Invoice for sales, or Invoice Journal for purchases, the following points must be considered:
> 1. The description of the service sold will be taken from the name of the ledger account used in the transaction.
> 1. The product/service identification code will be derived from the line description entered.
> 1. The transaction type code will default to "01".

#### Configure Units

To configure Units, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **Units** \> **Units**.
1. For each record in the list:
   1. Select the record, and then select **Tax application**.
   1. Create a new record.
   1. In the **Tax application id** field, enter the code that is used for Costa Rican electronic invoicing.
   1. In the **Tax application code** field, enter the unit code according to the Costa Rican normative.

> [!NOTE]
> When posting transactions using Free Text Invoice or Project on Account Invoice for sales, or Invoice Journal for purchases, the unit used will default to "Unid" 

#### Currencies configuration

To configure currencies, follow these steps.

1. Go to **General ledger** \> **Currencies** \> **Currencies**.
1. For each record in the list:
   1. Select the record and then go to **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application id** field, select the code that is used for Costa Rican electronic invoicing.
   1. In the **Tax application code** field, enter the currency code according to the Costa Rican normative.

### Configure charges and discounts

This section explains how to configure global charges and line discounts.

> [!NOTE] 
> To apply a line discount, configure a line charge with a negative amount.
> Tax groups must be included in the charge.

To configure global charges and line discounts, follow these steps.

1. Go to **Accounts receivable** \> **Charges setup** \> **Charges code**.
1. For each record that is used as a global charge, follow these steps:
   1. Select a record and go to **LATAM** \> **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application Id** field select the one used for Costa Rican Electronic Invoice.
   1. In the **Tax application code** field enter the code according to the Costa Rican normative.
   1. In the **Description** field, enter the charge motive.

1. For each record that is used as a line discount, follow these steps:
   1. Select a record and go to **LATAM** \> **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application Id** field select the one used for Costa Rican Electronic Invoice.
   1. In the **Tax application code** field enter the discount code according to the Costa Rican normative.
   
### Configure Taxes

To configure the taxes for each tax and percentage used, follow these steps.

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax codes**.
1. For each record in the list:
   1. Select the record and then go to **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application id** field, select the code that is used for Costa Rican electronic invoicing.
   1. In the **Income tax code** field, enter the VAT rate code according to the Costa Rican normative.
   1. In the **Code regime** field, enter the tax code according to the Costa Rican normative.

## Configure electronic document references

When you issue an electronic document that has an associated document, you must select **References** on the posting page and add the associated document.

### Reference a document

To reference a document, follow these steps.

1. In the **Reference code** field, enter the number code for the reference reason according to the Costa Rican normative.
1. Enter the date in the **Reference date** field.
1. Enter the complete document number in the **Reference document number** field.
1. Enter the document type code of the referenced transaction in the **Reference document type** field.
1. Enter a reason in the **Reference reason** field.

## Configure lookups

Configure the required lookups to issue an electronic document.

Follow these steps to configure lookups.

1. Go to **Organization administration** \> **Electronic reporting** \> **Configurations**.
1. Select the report to configure in the left menu.
1. Go to **Application specific parameters** in the top menu.
1. Select the report version to configure.
1. In the Lookups section, select the **TaxType** lookup.
1. In the **Conditions section**, add the required **Lookup results**, and select the corresponding tax codes for each one.

> [!NOTE] 
> To ensure the report shows transactions that meet the configured conditions, complete the Lookup result field as N/A with Blank and Not blank conditions.

## Configure SSRS reports and services references

For electronic invoicing, you must configure the **SSRS Reports / Services references**.

To configure SSRS reports and services references, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **SSRS Reports / Services references**.
1. Create a new record.
1. Complete the Report/Service Id and Report/Service name with a code and description.
1. In Settings tab, select Service for the Report/Service type field.
1. In the **Sales point type** field, select **Pre-printed** (This selection must match the sales point type used for electronic invoicing).
1. In **Parameter** section, add the following line:
   1. **Name:** TaxApplicationId.
   1. **Value:** CRFE (this code must match the tax application used for electronic invoicing).

> [!NOTE] 
> This configuration applies to all sales points used for every invoice, credit note, debit note, purchase invoice, and payment receipt.

## Configure bundled item

Bundle items, composed of sub-items with specific details captured in the transaction, are represented using a bill of materials (BOM) structure.
Learn more in [bills of materials and formulas](/dynamics365/supply-chain/production-control/bill-of-material-bom).

> [!NOTE] 
> The transactional quantity is defined based on the value in the **From qty.** field within the BOM record's **Header** section. Each transaction references only one BOM.

## Purchase invoice

To explore more about purchase invoice posting in Latin America, please visit the link below.

[Purchase invoice posting for Latin America](ltm-core-purchase-invoice-posting.md).

## Electronic payment receipt

The electronic payment receipt is represented by the LATAM extension in customer payment journals.

Learn more in [Use the LATAM extension in customer payment journals](ltm-latam-in-customer-payment.md).

> [!NOTE] 
> This functionality supports only full customer payments.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
