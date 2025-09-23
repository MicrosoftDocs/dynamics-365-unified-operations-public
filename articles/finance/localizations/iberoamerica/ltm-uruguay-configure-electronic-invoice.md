---
title: Configure electronic invoice parameters for Uruguay
description: Learn how to configure the information required to generate the electronic invoice XML for Uruguay.
author: SandraYamamoto0602
ms.topic: how-to
ms.date: 09/23/2025
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-sandraya
---

# Configure electronic invoice parameters for Uruguay

This article explains how to configure the information that is required to generate the electronic invoice XML for Uruguay.

## Prerequisites

Before completing the procedures in this article, ensure the following prerequisites are met:

- Enable both the country/region-specific Latin American (LATAM) feature for Uruguay and the general LATAM feature must be enabled.
- Set the company's address to Uruguay.
- You must download the specific report configurations from the Dataverse configuration repository for Uruguay Electronic Invoices:

| Element |                    Format name                    |
|:-------:|:-------------------------------------------------:|
| Model   | :::no-loc text="Invoice Model LATAM":::                              |
| Mapping |  :::no-loc text="(Invoice Model LATAM) Invoice Model mapping LATAM"::: |
| Format  | :::no-loc text="Inventory e-Invoice (UY)":::                   |
| Format  | :::no-loc text="e-Packing Slip (UY)":::                       |
| Format  | :::no-loc text="Export e-Packing Slip (UY)":::                        |
| Format  | :::no-loc text="Inventory e-Invoice":::                               |
| Format  | :::no-loc text="Inventory Export e-Invoice (UY)":::                     |
| Format  | :::no-loc text="Project e-Invoice (UY)":::                         |
| Format  | :::no-loc text="Project e-Invoice":::                          |
| Format  | :::no-loc text="Project Export e-Invoice (UY)":::                            |


> [!NOTE] 
> The format of the e- Packing slip and Export e-Packing Slip are the same for inventory and project, and both are generated from inventory.

Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).
- Configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- Configure all the LATAM extensions before continuing with the configuration in this article.

## Configuration required for Uruguay electronic invoices.
The following configurations are required for Uruguay electronic invoices:

- Configure the tax application
- Configure the legal entity
- Configure the document classes
- Configure the sales point prefix
- Configure the document class sales point 
- Configure the field master lists
- Configure the fiscal information
- Configure the addresses
- Configure other tax applications
- Configure Taxes

### Configure the Tax application.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax application** and select **New** to create a tax application record that has the code **UYFE** (Uruguayan electronic invoice). Use this tax application record to assign the fiscal codification to each element in Microsoft Dynamics 365 Finance as required.

### Configure the Legal entity

To configure the legal entity, follow these steps:

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
1. Select the legal entity that you want to work with.
1. Complete the address with country, state, and city.            
1. In the LATAM section complete the **Taxpayer type** with an option that represents organizations.
1. Complete the **Based in country/region** with **URY**.
1. Complete the **Country document type** with the option that represents the identification document type used by the organization.
1. Complete the **Country identification number** field, enter the company ID number. 

### Configure the Document classes

This configuration applies to Invoices, Credit notes, Debit notes and Packing slips where the transfer type is defined as sale.

To configure document classes, follow these steps:

1.	Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**.
1.	For each **Document class** that you want to use in Electronic Invoices:
   1. Select the record and then go to **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application id** field, enter the ID that is used for Uruguayan electronic invoices.
   1. In the **Tax application code** field, enter the code according to the Uruguayan regulations.
   1. In the **Letter code** field, enter **R** for debit and credit notes to enable the **Reference code** field when posting a transaction.
   1. In the document class configuration for Debit notes and credit notes set the **use reference document** slider to yes.

### Configure the Sales point prefix

To configure sales point prefix, follow these steps:

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Sales point prefix**.
1. For each **Sales point prefix** that you want to use in Electronic Invoices:
   1. Complete the **Prefix** field with the authorized prefix code for electronic invoices.
   1. In the field **Report/Service Id** select the **SSRS Reports / Services references** configured for electronic invoices (see #Configure SSRS Reports / Services references).
   1. On the **Tax application** page, in the **Tax application id** field, enter the numeric code provided by the DGI that identifies the parent company or the branch from where the operation takes place.

### Configure Document class sales point

To configure sales point address, follow these steps:

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class sales point**.
1. For each Sales point prefix, in the Printing Collapsible tab, configure the address in Printing Concept 1, City in Printing Concept 2 and Department in Printing Concept 3. 

### Configure Field master lists

1. Go to **Organization administration > Setup > LATAM > Fields master List**.
1. In the **LIST 10** configure the codes for reference reasons for credit and debit notes.

For more information see [Field list configuration for Latin America](ltm-core-field-master-lists.md)

### Configure Fiscal information

To configure fiscal information, follow these steps:

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax ID type**.
1. For each **Tax Id type** that you want to use in Electronic Invoices:
   1. Select the record, and then select **Tax application**.
   1. On the **Tax application** page, in the **Tax application id** field, enter the code that is used for Uruguayan electronic invoices.
   1. In the **Tax application code** field, enter the code for tax IDs according to the Uruguayan regulations.

### Configure Addresses 

To configure addresses, follow these steps:

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**. 
1. For each record in Country/Region used in electronic invoices go to **LATAM** \> **Tax application** to assign the tax application codes for according to the Uruguayan regulations.

Learn more in [Address setup for Latin America](ltm-core-address-setup.md).

### Other tax application configurations

#### Configure Terms of payments

To configure terms of payments, follow these steps:

1. Go to **Accounts receivable** \> **Payments setup** \> **Terms of payment**.
1. For each **Term of payment** that you want to use in Electronic Invoices:
   1. Select the record and then go to **Tax application** in the LATAM tab in the top menu.
   1. Create a new record.
   1. In the **Tax application id** field, enter the code that is used for Uruguayan electronic invoices.
   1. In the **Tax application code** field, enter the code for the term of payment according to the Uruguayan regulations (cash or credit).

#### Configure Currencies 

To configure currencies, follow these steps:

1. Go to **General ledger** \> **Currencies** \> **Currencies**.
1. For each **Currency** that you want to use in Electronic Invoices:
   1. Select the record and then go to **Tax application** in the LATAM tab in the top menu.
   1. In the **Tax application id** field, enter the code that is used for Uruguayan electronic invoices.
   1. In the **Tax application code** field, enter the code for each currency according to the Uruguayan regulations.

#### Configure Reasons for delivery

To configure mode of sales in reasons for delivery, follow these steps:

1. Go to **Sales and marketing** \> **Setup** \> **Distribution** \> **Reasons for delivery**.
1. Create **Mode of sale** to be used according to the Uruguayan regulations.
1. For each **Mode of sale** that you want to use in Electronic Invoices:
   1. Go to **Tax application** in the LATAM tab in the top menu.
   1. Create a record.
   1. On the **Tax application** page, in the **Tax application id** field, enter the ID that is used for Uruguayan electronic invoices.
   1. In the **Tax application code** field, enter the code according to the Uruguayan regulations.

#### Configure Mode of delivery

To configure mode of delivery, follow these steps:

1. Go to **Sales and marketing** \> **Setup** \> **Distribution** \> **Modes of delivery**.
1. Create **Transportation method** to be used according to the Uruguayan regulations.
1. For each **Transportation method** that you want to use in Electronic Invoices:
   1. Go to **Tax application** in the LATAM tab in the top menu.
   1. Create a record.
   1. On the **Tax application** page, in the **Tax application id** field, enter the ID that is used for Uruguayan electronic invoices.
   1. In the **Tax application code** field, enter the code according to the Uruguayan regulations.

### Configure Taxes

For each tax and percentage used you must follow these steps:

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax codes**.
1. For each **Sales tax code** that you want to use in Electronic invoices:
    1. Go to **Tax application** in the LATAM tab in the top menu.
    1. Create a new record.
    1. In the **Tax application id** field, select the code that is used for Uruguayan electronic invoices.
   1. In the **Income tax code** field, enter the code that identifies the tax type according to the Uruguayan regulations.

## Configure electronic document references

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Electronic documents references** and follow these steps:
1. In the **Tax application id** field, enter the ID that is used for Uruguayan electronic invoices.
1. Complete the Max amount of packing slips.

For debits and credits notes, you must select **References** on the posting page and add the associated document.

### Steps to reference a document:

1. In references page go to the General tab, click on **Source Vouchers** and from the list of documents, select the document to be associated.
1. In the **Reference code** field enter a number code for reference reason.
1. Complete the **Reference reason** with a motive (not mandatory).

Learn more in [Configure electronic document references](ltm-electronic-doc-references.md).

## Lookups configuration

You must configure the required lookups to be able to issue an electronic document following these steps:

1. Go to **Organization administration > Electronic reporting > Configurations**.
1. Select the report to configure on the left menu.
1. Go to **Application specific parameters** setup in the top menu.
1. Select the report version to configure.
1. In the **Lookups** section select the **TaxType** lookup.
1. In the **Conditions section** add the required **Lookup results** and select the corresponding tax codes for each one.

> [!NOTE] 
> To ensure that the report shows the transactions that meet the configured conditions, complete the Lookup result field as Not Applicable with blank and not-blank conditions.

## Configure SSRS Reports / Services references

For electronic invoices you must configure the **SSRS Reports / Services references** following these steps:

1. Go to Organization administration **Setup > LATAM > SSRS Reports / Services references**.
1. Create a new record.
1. Complete the **Report/Service Id** and **Report/Service name** with a code and description.
1. In **Settings** tab select **Service** for the **Report/Service type** field.
1. In the **Sales point type** select **Pre-printed** (it must match the sales point type used for electronic invoices.
1. In **Parameter** section add the following lines:
    1. **Name:** TaxApplicationId - **Value:** UYFE (this code must match the tax application used for electronic invoices).

> [!NOTE] 
> This configuration will be applied to all sales points used for every Invoice, Credit note, Debit note and Packing slips.
