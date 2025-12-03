---
title: Configure electronic invoice parameters for Costa Rica
description: Learn how to configure the information required to generate the electronic invoice XML for Costa Rica, including an outline on the required configuration.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: how-to
ms.date: 10/03/2025
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Configure electronic invoice parameters for Costa Rica

[!include [banner](../../includes/banner.md)]

This article describes the main configuration settings required to issue electronic invoices in Costa Rica by using Microsoft Dynamics 365 Finance.

> [!NOTE]
> In addition to these settings, you might need to configure other fields that are related to other system features. To ensure a complete and accurate implementation of the Costa Rican localization, review the rest of the available documentation for country/region-specific configurations.
> Learn more in [Costa Rica overview](costa-rica.md).

## Prerequisites

Before you complete the procedures in this article, make sure you meet the following prerequisites:

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

The following sections describe each configuration.

### Configure the tax application

To configure the tax application, go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax application**, and select **New** to create a tax application record with the code **CRFE** (Costa Rican electronic invoice). Use this tax application record to assign the fiscal codification to each element in Microsoft Dynamics 365 Finance as required.

### Configure the legal entity

To configure the legal entity, follow these steps.

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
1. Select the legal entity that you want to work with.
1. Complete the address fields with the country/region, state, county, and city.
1. Enter the email address in the contact information and set it to **Primary**.
1. In the LATAM section, complete the **Taxpayer type** with an option that represents the organization.
1. In the **Based in country/region** field, enter **CRI**.
1. In the **Country/region document type** field, select the option that represents the identification document type used by the organization.
1. In the LATAM section, in the **Country/region identification number** field, enter the company ID number (for example, 1-123-45678901).
1. In the LATAM section, in the **Free Text 1** field, enter the company activity code number.

### Configure customers

To configure customers, follow these steps.

1. Go to **Accounts receivable** \> **Customers** \> **All customers**.
1. For each customer used in transactions:
   1. Complete the address fields with the country/region, state, county, and city.
   1. Complete the contact information with the email address and set it to **Primary**.
   1. In the LATAM section, complete the **Taxpayer type** with an option that represents the customer.
   1. In the **Based in country/region** field, select an option that represents the customer.
   1. In the **Country/region document type** field, select the option that represents the customer.
   1. In the LATAM section, in the **Country/region identification number** field, enter the customer ID number (for example, 1-123-45678901).
   1. In the top menu, go to **General** \> **Business classification**.
   1. Create a new record.
   1. In the **Business classifications** field, enter the customer activity code number.
  
### Configure vendors

To configure vendors, follow these steps.

1. Go to **Accounts payable** \> **Vendors** \> **All vendors**.
1. For each vendor used in transactions:
   1. Complete the address fields with the country/region, state, county, and city.
   1. Complete the contact information with the email address and set it to **Primary**.
   1. In the LATAM section, complete the **Taxpayer type** with an option that represents the vendor.
   1. In the **Based in country/region** field, select an option that represents the vendor.
   1. In the **Country/region document type** field, select the option that represents the vendor.
   1. In the LATAM section, complete the **Country/region identification number** field, enter the vendor ID number.

### Configure the document classes

This configuration applies to invoices, credit notes, debit notes, purchase invoices, and payment receipts.

To configure document classes, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**.
1. For each **Document class** that you want to use in Electronic Invoicing:
   1. Select the record and then go to **Tax application**.
   1. On the **Tax application** page, enter the ID that is used for Costa Rican electronic invoicing in the **Tax application id** field.
   1. In the **Tax application code** field, enter the code according to the Costa Rican normative.
   1. In the **Letter code** field, enter **R** for debit notes, credit notes, and purchase invoices to enable the **Reference code** field when posting a transaction.
   1. In the **User-defined field 2** field, enter the status code of the electronic document according to the Costa Rican normative.
   1. Set the **Use reference document** slider to **Yes** for debit notes, credit notes, and purchase invoices to enable the **Invoice posting references** section when posting a transaction.

### Configure the sales point prefix

To configure the sales point prefix, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Sales point prefix**, and for the sales point used for electronic invoicing, follow these steps:
1. Enter the sales point code in the **Prefix** field.
1. On the **Tax application** page, enter the ID that is used for Costa Rican electronic invoicing in the **Tax application id** field.
1. Enter the branch or head office code in the **Tax application code** field.
1. In the **Report/Service Id** field, select the **SSRS Reports / Services references** configured for electronic invoicing. [Configure SSRS Reports / Services references](#configure-ssrs-reports-and-services-references).

### Configure the field master lists

To configure field master lists, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Fields master List**.
1. In **LIST 9**, configure a document type code for reference according to the Costa Rican normative.
1. In **LIST 10**, configure the codes for reference reasons for credit notes, debit notes, and purchase invoices according to the Costa Rican normative.

Learn more in [Field list configuration for Latin America](ltm-core-field-master-lists.md).

### Configure the fiscal information

To configure fiscal information, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax ID type**, and for each record in the list, follow these steps:
1. Select the record, then select **Tax application**.
1. On the **Tax application** page, enter the code that is used for Costa Rican electronic invoicing in the **Tax application id** field.
1. Enter the code for tax IDs according to the Costa Rican normative in the **Tax application code** field.

### Configure the addresses

To configure addresses, follow these steps.

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**.
1. For each record (State, County, and City) used in electronic invoicing, in the **Description** field, enter the information according to the Costa Rican normative.
1. For each record (State, County, and City) used in electronic invoicing, go to **LATAM** \> **Tax application** to assign the tax application codes according to the Costa Rican normative.

Learn more in [Address setup for Latin America](ltm-core-address-setup.md).

### Other configurations

#### Method of payments

To configure the method of payments, follow these steps.

1. For customers, go to **Accounts receivable** \> **Payments setup** \> **Methods of payment**.
1. For each record in the list:
   1. Select the record, and then go to **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application id** field, enter the code that you use for Costa Rican electronic invoicing.
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
   1. In the **Tax application id** field, enter the code that you use for Costa Rican electronic invoicing.
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
   1. In the top menu, go to **Manage inventory** \> **GTIN codes**.
   1. Create a new record.
   1. In the **GTIN** field, enter the commercial code that identifies the product according to the Costa Rican normative.

> [!NOTE]
> When you post transactions by using Free Text Invoice or Project on Account Invoice for sales, or Invoice Journal for purchases, consider the following points:
> 1. The description of the service sold comes from the name of the ledger account used in the transaction.
> 1. The product or service identification code comes from the line description entered.
> 1. The transaction type code defaults to "01."

#### Configure Units

To configure Units, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **Units** \> **Units**.
1. For each record in the list:
   1. Select the record, then select **Tax application**.
   1. Create a new record.
   1. In the **Tax application id** field, enter the code that you use for Costa Rican electronic invoicing.
   1. In the **Tax application code** field, enter the unit code according to the Costa Rican normative.

> [!NOTE]
> When you post transactions by using Free Text Invoice or Project on Account Invoice for sales, or Invoice Journal for purchases, the unit defaults to "Unid."

#### Currencies configuration

To configure currencies, follow these steps.

1. Go to **General ledger** \> **Currencies** \> **Currencies**.
1. For each record in the list:
   1. Select the record and then go to **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application id** field, select the code that you use for Costa Rican electronic invoicing.
   1. In the **Tax application code** field, enter the currency code according to the Costa Rican normative.

### Configure charges and discounts

This section explains how to configure global charges and line discounts.

> [!NOTE]
> To apply a line discount, configure a line charge with a negative amount.
> Tax groups must be included in the charge.

To configure global charges and line discounts, follow these steps.

1. Go to **Accounts receivable** \> **Charges setup** \> **Charges code**.
1. For each record that you want to use as a global charge, follow these steps:
   1. Select a record and go to **LATAM** \> **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application Id** field, select the one used for Costa Rican Electronic Invoice.
   1. In the **Tax application code** field, enter the code according to the Costa Rican normative.
   1. In the **Description** field, enter the charge motive.

1. For each record that you want to use as a line discount, follow these steps:
   1. Select a record and go to **LATAM** \> **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application Id** field, select the one used for Costa Rican Electronic Invoice.
   1. In the **Tax application code** field, enter the discount code according to the Costa Rican normative.
   
### Configure taxes

To configure the taxes for each tax and percentage, follow these steps.

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax codes**.
1. For each record in the list:
   1. Select the record and then go to **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application id** field, select the code that you use for Costa Rican electronic invoicing.
   1. In the **Income tax code** field, enter the VAT rate code according to the Costa Rican normative.
   1. In the **Code regime** field, enter the tax code according to the Costa Rican normative.

## Configure electronic document references

To configure electronic document references, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Electronic documents references**.
1. In the **Tax application Id** field, enter the ID that you use for Costa Rican electronic invoices.

### Steps to reference a document

When you issue an electronic document that has an associated document, select **References** on the posting page, and add the associated document.

To reference a document for sales invoices, follow these steps.

1. Go to the **General** tab, select **Source Vouchers**, and from the list of documents, select the document to associate.
1. In the **Reference code** field, enter a number code for the reference reason.
1. Complete the **Reference reason** field with a motive.

To reference a document for purchase invoices, follow these steps.

1. In the **Reference code** field, enter the number code for the reference reason according to Costa Rican regulations.
1. Enter the date in the **Reference date** field.
1. Enter the complete document number in the **Reference document number** field.
1. Enter the document type code of the referenced transaction in the **Reference document type** field.
1. Complete the **Reference reason** field with a motive.

## Configure lookups

Configure the required lookups to create an electronic document.

To configure lookups, follow these steps:

1. Go to **Organization administration** \> **Electronic reporting** \> **Configurations**.
1. Select the report to configure in the left menu.
1. Go to **Application specific parameters** in the top menu.
1. Select the report version to configure.
1. In the **Lookups** section, select the **TaxType** lookup.
1. In the **Conditions** section, add the required **Lookup results**, and select the corresponding tax codes for each one.

> [!NOTE]
> To ensure the report shows transactions that meet the configured conditions, complete the Lookup result field as N/A with Blank and Not blank conditions.

## Configure SSRS reports and services references

For electronic invoicing, you must configure the **SSRS Reports / Services references**.

To configure SSRS reports and services references, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **SSRS Reports / Services references**.
1. Create a new record.
1. Enter a code and description in the **Report/Service ID** and **Report/Service name** fields.
1. In the **Settings** tab, select **Service** for the **Report/Service type** field.
1. In the **Sales point type** field, select **Pre-printed** (this selection must match the sales point type used for electronic invoicing).
1. In the **Parameter** section, add the following line:
   1. **Name:** TaxApplicationId.
   1. **Value:** CRFE (this code must match the tax application used for electronic invoicing).

> [!NOTE]
> This configuration applies to all sales points used for every invoice, credit note, debit note, purchase invoice, and payment receipt.

## Configure bundled item

Bundle items, composed of subitems with specific details captured in the transaction, are represented using a bill of materials (BOM) structure.
Learn more in [bills of materials and formulas](/dynamics365/supply-chain/production-control/bill-of-material-bom).

> [!NOTE]
> The transactional quantity is defined based on the value in the **From qty.** field within the BOM record's **Header** section. Each transaction references only one BOM.

## Purchase invoice

Learn more about purchase invoice posting in Latin America in [Purchase invoice posting for Latin America](ltm-core-purchase-invoice-posting.md).

## Electronic payment receipt

The LATAM extension represents the electronic payment receipt in customer payment journals.

For more information, see [Use the LATAM extension in customer payment journals](ltm-latam-in-customer-payment.md).

> [!NOTE]
> This functionality supports only full customer payments.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
