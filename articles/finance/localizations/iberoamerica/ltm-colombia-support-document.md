---
title: Configure the Colombia support document and adjustment note
description: Learn how to configure the support document (documento soporte) and adjustment note (nota de ajuste) for Colombia in Microsoft Dynamics 365 Finance.
author: MatiasPizmeny01
ms.author: v-mpizmeny
ms.date: 09/08/2026
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.search.region: Colombia
---

# Configure the Colombia support document and adjustment note

[!INCLUDE [banner](../../includes/banner.md)]

This article explains how to configure the **support document** (*documento soporte*) and the **adjustment note** (*nota de ajuste al documento soporte*) for Colombia in Microsoft Dynamics 365 Finance.

The support document is an electronic document issued by buyers who acquire goods or services from vendors that aren't obligated to issue invoices. The adjustment note is its corresponding correction document. DIAN regulates both documents in accordance with the UBL 2.1 standard.

## Prerequisites

Before you begin, ensure you meet the following prerequisites:

- The legal entity has an address in Colombia.
- Enable the **Colombian electronic invoicing** feature and the general **LATAM** feature in the **Feature management** workspace.
- Download the specific report configurations from the Microsoft Dataverse configuration repository for Colombian electronic invoicing:

| Element |                    Format name                    |
| ------- | ------------------------------------------------- |
| Model   | :::no-loc text="Invoice model":::                 |
| Model   | :::no-loc text="Invoice Model LATAM":::           |
| Mapping | :::no-loc text="Invoice model mapping":::         |
| Mapping | :::no-loc text="(Invoice Model LATAM) Invoice Model mapping LATAM"::: |
| Format  | :::no-loc text="Support Document format (CO)":::  |
| Format  | :::no-loc text="Adjustment Note (CO)":::          |
| Format  | :::no-loc text="Support Document (CO)":::         |

Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

- Configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- Configure all the LATAM extensions before continuing with the configuration in this article.

## Configuration required for Colombian electronic invoicing

The following configurations are required for Colombian electronic invoicing.

- Configure the tax application
- Configure the fiscal information
- Configure addresses
- Configure the legal entity
- Configure vendors
- Configure field master lists
- Configure document classes
- Configure the sales point prefix
- Configure CUFE parameters
- Configure other tax applications
- Configure charges and discounts
- Configure taxes
- Configure electronic document references
- Configure SSRS reports and services references

Each configuration is described in the following sections.

### Configure the tax application

The tax application assigns the corresponding fiscal codification to each element in Finance as required. To configure the tax application, follow these steps:

1. Go to **Organization administration** > **Setup** > **LATAM** > **Tax application**.
1. Select **New** to create a tax application record.
1. In the **Tax application Id** field, enter an identifier, such as COFE (Colombian electronic invoice).
1. In the **Tax application description** field, enter a descriptive name.

### Configure the fiscal information

To configure fiscal information, follow these steps:

1. Go to **Organization administration** > **Setup** > **LATAM** > **Tax ID type**. For each record, go to the **Tax application** menu.
1. On the **Tax application** page, in the **Tax application id** field, enter the code created for Colombian electronic invoicing.
1. In the **Tax Application Code** field, enter the code for tax IDs according to the Colombian normative.
1. Go to **Organization administration** > **Setup** > **LATAM** > **Taxpayer type**. For each record, go to the **Tax application** menu.
1. On the **Tax application** page, in the **Tax application id** field, enter the code created for Colombian electronic invoicing.
1. In the **Tax Application Code** field, enter the code of the taxpayer responsibility according to the Colombian normative.

Learn more in [Taxpayer types for Latin America](ltm-core-taxpayer-type.md) and [Tax ID types for Latin America](ltm-core-tax-id-type.md).

### Configure addresses

To configure addresses, follow these steps:

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**.
1. For each record (Country/region, state, and county) used in electronic invoicing, go to **LATAM** \> **Tax application** to assign the tax application codes according to the Colombian regulations.

Learn more in [Address setup for Latin America](ltm-core-address-setup.md).

### Configure the legal entity

To configure the legal entity, follow these steps:

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
1. Select the legal entity that you want to work with.
1. Complete the address fields with the country/region, state, and county.
1. In the LATAM section, complete the **Taxpayer type** with an option that represents organizations.
1. Enter **COL** in the **Based in country/region** field.
1. Complete the **Country/region document type** field with the option that represents the identification document type used by the organization.
1. In the LATAM section, in the Country/region identification number field, enter the company ID number with the verification code at the end separated by a middle hyphen (for example, 123456789-0).

### Configure vendors

To configure vendors, follow these steps:

1. Go to **Accounts payable** \> **Vendors** \> **All vendors** and select a vendor.
1. Complete the address fields with the **country/region**, **state**, **county**, and **zip code**.
1. In the LATAM section, select a **Taxpayer type** option that represents the vendor.
1. Complete the **Based in country/region** field with **COL**.
1. Select an option for the **Country/region document type** field that represents the identification document type used by the vendor.
1. In the LATAM section, enter the vendor ID number in the **Country/region identification number** field with the verification code at the end separated by a middle hyphen (for example, 123456789-0).

### Configure field master lists

To configure field master lists, follow these steps:

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Fields master List**.
1. In **LIST 1**, configure the codes for operation types and for credit and debit note types.
1. In **LIST 9**, configure a document type for reference (not mandatory).
1. In **LIST 10**, configure the codes for reference reasons for credit and debit notes according to the Colombian normative.

Learn more in [Field list configuration for Latin America](ltm-core-field-master-lists.md).

### Configure document classes

This configuration applies to **support document** and **adjustment note**.

To configure document classes, follow these steps:

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**.
1. For each **Document class** that you want to use in Electronic Invoicing:
   1. Select the record and then go to **Tax application**.
   1. On the **Tax application** page, in the **Tax application id** field, enter the ID that's used for Colombian electronic invoicing.
   1. In the **Tax application Code** field, enter the code according to the Colombian normative.
   1. In the **Letter code** field, enter **R** for **adjustment notes** to enable the **Reference code** field when posting a transaction.
   1. In the **Legal Description** field, enter the electronic document description.
   1. Set the **Require CA number** slider to **Yes**.
   1. Set the **Use reference document** slider to **Yes**.
   1. In the **Additional data** section, set the list 1 field to **Required**.
1. In the **Document mask** section, set the entry parameter for the **Vendor** record to **Auto**.

### Configure the sales point prefix

To configure the sales point prefix, follow these steps:

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Sales point prefix**. For the sales point used for electronic invoicing, follow these steps:
1. Enter the authorized prefix code for electronic invoicing in the **Prefix** field.
1. Set the **Validate CA** slider to **Yes**.
1. In the **Report/Service Id** field, select the **SSRS Reports / Services references** configured for electronic invoicing (see #Configure SSRS Reports / Services references).

### Configure CUFE parameters

To configure the CUFE parameters, follow these steps:

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **LATAM parameters**.
1. On the navigation pane, go to **Functionalities**.
1. Set the **Enable additional authorization code** slider to **Yes**.
1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class sales point** and for the sales point and document class used for electronic invoicing follow these steps:
1. Select the **Sales CA** button on the top menu and create a record.
1. Enter the **Resolution number** in the **Authorization code (CA)** field.
1. Enter the **Technical key** in the **Additional CA** field.
1. Enter the valid date range of the resolution in the **Date from** and **Date to** fields.
1. Enter the folio range in the **From voucher number** and **To voucher number** fields.

### Other tax application configurations

#### Methods of payment

To configure the methods of payment, follow these steps:

1. Go to **Accounts payable** \> **Payments setup** \> **Methods of payment**.
1. For each record in the list:
   1. Select the record, and then go to **Local instrument**.
   1. Create a new record.
   1. Enter the **Code** field used for Colombian electronic invoicing.

#### Terms of payment

To configure the terms of payment, follow these steps:

1. Go to **Accounts payable** \> **Payments setup** \> **Terms of payment**.
1. For each record in the list:
   1. Select the record, and then go to **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application id** field, enter the code that is used for Colombian electronic invoicing.
   1. In the **Tax application Code** field, enter the code for the term of payment according to the Colombian normative (cash or credit).

#### Configure released products

To configure released products, follow these steps:

1. Go to **Product information management** \> **Products** \> **Released products**.
1. For each record in the list:
   1. Select the record and in the top menu go to **LATAM** \> **Tax application**.
   1. Create a new record.
   1. In the **Tax application Id** field, select the one used for Colombia electronic invoicing.
   1. In the **Tax application Code** field, enter the code that identifies the product or service.
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

#### Currencies configuration

To configure currencies, follow these steps:

1. Go to **General ledger** \> **Currencies** \> **Currencies**.
1. For each record in the list:
   1. Select the record and then go to **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application id** field, select the code that's used for Colombian electronic invoicing.
   1. In the **Tax application Code** field, enter the currency code according to the Colombian normative.

### Configure charges and discounts

This section explains how to configure global and line charges and discounts.

#### Configure global and line charges

To configure global and line charges, follow these steps:

1. Go to **Accounts payable** \> **Charges setup** \> **Charges code**.
1. For each record that you use as a global or line charge, follow these steps:
   1. Select a record and go to **LATAM** \> **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application Id** field, select the one used for Colombian electronic invoicing.
   1. In the **Tax application code** field, enter the code according to the Colombian normative.

#### Configure global discounts

To configure global discounts, follow these steps:

1. Go to **Accounts receivable** \> **Charges setup** \> **Charges code**.
1. For each record that you use as a global discount, follow these steps:
   1. Select a record and go to **LATAM** \> **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application Id** field select the one used for Colombian electronic invoicing.
   1. In the **Tax application code** field enter the code according to the Colombian normative.

#### Line discounts

To use line discounts in the Colombian electronic invoice, use the Finance and Operations apps line discount feature.

> [!NOTE]
> To enter a global discount, use the **Maintain charges** button in the sales orders, enter the amount as a negative value, and set the tax code for the global discount to **Excluded**.

> [!NOTE]
> The charge code description is used in the discount or charge reason description of the invoice.

### Configure taxes

To configure the taxes for each tax and percentage used, follow these steps:

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax codes**.
1. For each record in the list:
   1. Select the record and then go to **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application id** field, select the code that is used for Colombian electronic invoicing.
   1. In the **Income tax code** field, enter the code that identifies the tax type according to the Colombian normative.
   1. In the **Code regime** field, enter the tax name according to the Colombian normative.
   1. In the **User-defined field 2**, enter the tax percentage according to the tax codes of the Colombian normative.

### Configure electronic document references

When you issue an electronic document that has an associated document, select **References** on the posting page and add the associated document.

#### Reference a document

To reference a document, follow these steps:

1. In the **Reference code** field, enter the number code for reference reason according to the Colombian normative.
1. Complete the **Reference date** field.
1. Complete the **Reference document number** field with the complete document number referenced.
1. Complete the **Reference reason** field with a motive (not mandatory).

> [!NOTE]
> The referenced document must be validated and approved by the fiscal authority and the XML response attached in the invoice journal.

### Configure SSRS reports and services references

For electronic invoicing, you must configure the **SSRS Reports / Services references**.

To configure SSRS reports and services references, follow these steps:

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **SSRS Reports / Services references**.
1. Create a new record.
1. Enter a code and description in the **Report/Service Id** and **Report/Service name** fields.
1. In the **Settings** tab, select **Service** for the **Report/Service type** field.
1. In the **Sales point type**, select **Pre-printed** (it must match the sales point type used for electronic invoicing).
1. In the **Parameter** section, add the following lines:
    1. **Name:** TaxApplicationId - **Value:** COFE (this code must match the tax application used for electronic invoicing).
    1. **Name:** Environment - **Value:** 2 or 1 (this code defines if the environment is for 2: Testing or 1: Production).
