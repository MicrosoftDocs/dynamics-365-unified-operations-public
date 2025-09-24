---
title: Configure electronic invoice parameters for Uruguay
description: Learn how to configure the information required to generate the electronic invoice XML for Uruguay.
author: SandraYamamoto0602
ms.topic: how-to
ms.date: 09/24/2025
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-sandraya
---

# Configure electronic invoice parameters for Uruguay

This article explains how to set up the information required to generate the electronic invoice XML for Uruguay.

## Prerequisites

Before completing the procedures in this article, ensure the following prerequisites are met:

- Enable both the country/region-specific Latin American (LATAM) feature for Uruguay and the general LATAM feature.
- Set the company's address to Uruguay.
- Download the specific report configurations from the Dataverse configuration repository for Uruguay Electronic Invoices:

| Element | Format name |
|---------|-------------|
| Model   | :::no-loc text="Invoice model LATAM"::: |
| Mapping | :::no-loc text="(Invoice model LATAM) Invoice model mapping LATAM"::: |
| Format  | :::no-loc text="Inventory e-Invoice (UY)"::: |
| Format  | :::no-loc text="e-Packing Slip (UY)"::: |
| Format  | :::no-loc text="Export e-Packing Slip (UY)"::: |
| Format  | :::no-loc text="Inventory e-Invoice"::: |
| Format  | :::no-loc text="Inventory Export e-Invoice (UY)"::: |
| Format  | :::no-loc text="Project e-Invoice (UY)"::: |
| Format  | :::no-loc text="Project e-Invoice"::: |
| Format  | :::no-loc text="Project Export e-Invoice (UY)"::: |


> [!NOTE] 
> The format of the e-packing slip and export e-packing slip is the same for inventory and project, and both are generated from inventory.

Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../../../global/workspace/gsw-import-er-config-dataverse.md).
- Configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- Configure all LATAM extensions before continuing with the configuration in this article.

## Configuration required for Uruguay electronic invoices

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

### Configure the tax application

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax application** and select **New** to create a tax application record that has the code **UYFE** (Uruguayan electronic invoice). Use this tax application record to assign the fiscal codification to each element in Microsoft Dynamics 365 Finance as required.

### Configure the legal entity

To configure the legal entity, follow these steps.

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
1. Select the legal entity that you want to work with.
1. Complete the address with the country/region, state, and city.
1. In the LATAM section, complete the **Taxpayer type** with an option that represents organizations.
1. Complete the **Based in country/region** field with **URY**.
1. Complete the **Country/region document type** field with the option that represents the identification document type used by the organization.
1. Complete the **Country/region identification number** field by entering the company ID number.

### Configure the document classes

This configuration applies to Invoices, Credit notes, Debit notes, and Packing slips where the transfer type is defined as sale.

To configure document classes, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**.
1. For each **Document class** that you want to use in Electronic Invoices:
   1. Select the record and then go to **Tax application** in the top menu.
   1. Create a new record.
1. In the **Tax application id** field, enter the ID used for Uruguayan electronic invoices.
   1. In the **Tax application code** field, enter the code according to the Uruguayan regulations.
   1. In the document class configuration for debit notes and credit notes, set the **use reference document** slider to yes.

### Configure the sales point prefix

To configure sales point prefix, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Sales point prefix**.
1. For each **Sales point prefix** that you want to use in Electronic Invoices:
   1. Complete the **Prefix** field with the authorized prefix code for electronic invoices.
   1. On the **Tax application** page, in the **Tax application id** field, enter the numeric code provided by the DGI that identifies the parent company or the branch from where the operation takes place.

### Configure document class sales point

To configure sales point address, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class sales point**.
1. For each sales point prefix, in the **Printing Collapsible** tab, configure the address in **Printing Concept 1**, city in **Printing Concept 2**, and department in **Printing Concept 3**.

### Configure field master lists

To configure field master lists, follow these steps.

1. Go to **Organization administration > Setup > LATAM > Fields master List**.
1. In the LIST 10,** configure the codes for reference reasons for credit and debit notes.

Learn more in [Field list configuration for Latin America](ltm-core-field-master-lists.md)

### Configure fiscal information

To configure fiscal information, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax ID type**.
1. For each **Tax Id type** that you want to use in Electronic Invoices:
   1. Select the record, then select **Tax application**.
   1. In the **Tax application code** field, enter the code for tax IDs according to the Uruguayan regulations.

### Configure addresses

To configure addresses, follow these steps.

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**.
1. For each record in Country/Region used in electronic invoices, go to **LATAM** \> **Tax application** to assign the tax application codes according to the Uruguayan regulations.

Learn more in [Address setup for Latin America](ltm-core-address-setup.md).

## Other tax application configurations

### Configure terms of payment

To configure terms of payment, follow these steps.

1. Go to **Accounts receivable** \> **Payments setup** \> **Terms of payment**.
1. For each **Term of payment** that you want to use in Electronic Invoices:
   1. Select the record and then go to **Tax application** in the LATAM tab in the top menu.
   1. Create a new record.
   1. In the **Tax application id** field, enter the code that is used for Uruguayan electronic invoices.
   1. In the **Tax application code** field, enter the code for the term of payment according to the Uruguayan regulations (cash or credit).

### Configure currencies 

To configure currencies, follow these steps.

1. Go to **General ledger** \> **Currencies** \> **Currencies**.
1. For each **Currency** that you want to use in Electronic Invoices:
   1. Select the record and then go to **Tax application** in the LATAM tab in the top menu.
   1. In the **Tax application id** field, enter the code that is used for Uruguayan electronic invoices.
   1. In the **Tax application code** field, enter the code for each currency according to the Uruguayan regulations.

### Configure reasons for delivery

To configure the mode of sales in reasons for delivery, follow these steps.

1. Go to **Sales and marketing** \> **Setup** \> **Distribution** \> **Reasons for delivery**.
1. Create **Mode of sale** to use according to the Uruguayan regulations.
1. For each **Mode of sale** that you want to use in Electronic Invoices:
   1. Go to **Tax application** in the LATAM tab in the top menu.
   1. Create a record.
   1. On the **Tax application** page, in the **Tax application id** field, enter the ID that Uruguayan electronic invoices use.
   1. In the **Tax application code** field, enter the code according to the Uruguayan regulations.

### Configure mode of delivery

To configure the mode of delivery, follow these steps.

1. Go to **Sales and marketing** \> **Setup** \> **Distribution** \> **Modes of delivery**.
1. Create **Transportation method** to use according to the Uruguayan regulations.
1. For each **Transportation method** that you want to use in Electronic Invoices:
   1. Go to **Tax application** in the LATAM tab in the top menu.
   1. Create a record.
   1. On the **Tax application** page, in the **Tax application id** field, enter the ID that Uruguayan electronic invoices use.
   1. In the **Tax application code** field, enter the code according to the Uruguayan regulations.

### Configure taxes

For each tax and percentage you use, follow these steps.

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax codes**.
1. For each **Sales tax code** that you want to use in Electronic invoices:
    1. Go to **Tax application** in the LATAM tab in the top menu.
    1. Create a new record.
    1. In the **Tax application id** field, select the code that is used for Uruguayan electronic invoices.
   1. In the **Income tax code** field, enter the code that identifies the tax type according to the Uruguayan regulations.

## Configure electronic document references

To configure electronic document references, follow these steps.

1. Go to **Organization administration** > **Setup** > **LATAM** > **Electronic documents references**, and follow these steps:
1. In the **Tax application id** field, enter the ID that is used for Uruguayan electronic invoices.
1. Complete the **Max amount of packing slips** field.

For debit and credit notes, select **References** on the posting page, and add the associated document.

### Reference a document

To reference a document, follow these steps.

1. On the references page, go to the General tab, select **Source Vouchers**, and from the list of documents, select the document to associate.
1. In the **Reference code** field, enter a numeric code for the reference reason.
1. Complete the **Reference reason** field with a reason (optional).

Learn more in [Configure electronic document references](ltm-electronic-doc-references.md).

## Lookups configuration

To configure the required lookups to issue an electronic document, follow these steps.

1. Go to **Organization administration > Electronic reporting > Configurations**.
1. Select the report to configure from the left menu.
1. Go to the **Application specific parameters** set up in the top menu.
1. Select the report version to configure.
1. In the **Lookups** section, select the **TaxType** lookup.
1. In the **Conditions** section, add the required **Lookup results** and select the corresponding tax codes for each one.

> [!NOTE]
> To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** field as Not Applicable with blank and not-blank conditions.

## Configure SSRS reports and services references

To configure the **SSRS Reports / Services references** for electronic invoices, follow these steps.

1. Go to Organization administration, and select **Setup > LATAM > SSRS Reports / Services references**.
1. Create a new record.
1. Complete the **Report/Service Id** and **Report/Service name** with a code and description.
1. On the **Settings** tab, select **Service** for the **Report/Service type** field.
1. In the **Sales point type**, select **Pre-printed** (this type must match the sales point type used for electronic invoices).
1. In the **Parameter** section, add the following lines:
    1. **Name:** TaxApplicationId - **Value:** UYFE (this code must match the tax application used for electronic invoices).

> [!NOTE]
> This configuration applies to all sales points used for every invoice, credit note, debit note, and packing slip.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
