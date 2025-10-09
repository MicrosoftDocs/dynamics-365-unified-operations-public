---
title: Configure electronic invoice parameters for Peru
description: Learn how to configure the information required to generate the electronic invoice XML for Peru.
author: SandraYamamoto0602
ms.topic: how-to
ms.date: 10/09/2025
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-sandraya
---

# Configure electronic invoice parameters for Peru.

This article explains how to configure the information that is required to generate the electronic invoice XML for Peru.

> [!NOTE]
> In addition to these settings, you might need to configure other fields that are related to other system features. To ensure a complete and accurate implementation of the Peruvian localization, review the rest of the available documentation for country/region-specific configurations.
> Learn more in [Peru overview](ltm-Peru_Overview.md).

## Prerequisites

Before completing the procedures in this article, make sure that the following prerequisites are met:

- Enable both the country/region-specific Latin American (LATAM) feature for Peru and the general LATAM feature must be enabled.
- Set the company's address to Peru.
- You must download the specific report configurations from the Dataverse configuration repository for Peru Electronic Invoices:

| Element |                    Format name                    |
|:-------:|:-------------------------------------------------:|
| Model   | :::no-loc text="Invoice Model LATAM":::                              |
| Mapping |  :::no-loc text="(Invoice Model LATAM) Invoice Model mapping LATAM"::: |
| Format  | :::no-loc text="Inventory e-Invoice format (PE)":::                   |
| Format  | :::no-loc text="Inventory e-CreditNote (PE)":::                       |
| Format  | :::no-loc text="Inventory e-DebitNote (PE)":::                        |
| Format  | :::no-loc text="Inventory e-Invoice (PE)":::                               |
| Format  | :::no-loc text="Project e-Invoice format (PE)":::                     |
| Format  | :::no-loc text="Project e-CreditNote (PE)":::                         |
| Format  | :::no-loc text="Project e-DebitNote (PE)":::                          |
| Format  | :::no-loc text="Project e-Invoice (PE) ":::                            |

Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).
- Configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- Configure all the LATAM extensions before continuing with the configuration in this article.

## Configuration required for Peruvian electronic invoices.
The following configurations are required for Peruvian electronic invoices:

- Configure the tax application
- Configure the document classes
- Configure the sales point prefix
- Configure the field master lists
- Configure the fiscal information
- Configure the addresses
- Configure other tax applications
- Configure charges and discounts
- Configure taxes

### Configure the Tax application.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax application** and select **New** to create a tax application record that has the code **PEFE** (Peruvian electronic invoice). Use this tax application record to assign the fiscal codification to each element in Microsoft Dynamics 365 Finance as required.

### Configure the Document classes

This configuration applies to Invoices, Credit notes and Debit notes.

To configure document classes, follow these steps:

1.	Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**.
1.	For each **Document class** that you want to use in Electronic Invoices:
1. Select the record, then go to **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application id** field, enter the ID that is used for Peruvian electronic invoices.
   1. In the **Tax application code** field, enter the code according to the Peruvian regulations.
   1. In the document class configuration for Debit notes and credit notes set the **use reference document** slider to yes.
1. For **Invoices**, in **additional data**, configure Field list 9 as required to allow the selection of transaction type. 
1. For **Debit notes** and **Credit notes**, in additional data, configure Field list 8 as required to allow the selection of references. 

### Configure the Sales point prefix

To configure sales point prefix, follow these steps:

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Sales point prefix**.
1. For each **Sales point prefix** that you want to use in Electronic Invoices:
   1. Complete the **Prefix** field. 
   1. Select the record, then go to **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application** page, in the **Tax application id** field, enter the code that is used for Peruvian electronic invoices.
   1. In the **Tax application code** field, enter the Address code that identifies the establishment.
   1. In the field **Report/Service Id** select the **SSRS Reports / Services references** configured for electronic invoices [Configure SSRS Reports / Services references](#configure-ssrs-reports-and-services-references).

### Configure Field master lists

1. Go to **Organization administration > Setup > LATAM > Fields master List**.
1. In the **List 8** configure the codes for credit notes and debit notes.
1. In the **LIST 9** configure the codes for transaction type.
1. For each **Reference code** configured in the **Fields master list** section,
 follow these steps: 
   1. Select the record, then go to **Tax application** under the **LATAM** tab in the top menu.
   1. Create a new record.
   1. In the **Tax application id** field, enter the ID that is used for Peruvian electronic invoices.
   1. In the **Tax application code** field, enter the same code of each reference.

For more information see [Field list configuration for Latin America](ltm-core-field-master-lists.md)

### Configure Fiscal information

To configure fiscal information, follow these steps:

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax ID type**.
1. For each **Tax Id type** that you want to use in Electronic Invoices:
   1. Select the record, then go to Tax application in the top menu. 
   1. Create a new record.
   1. On the **Tax application** page, in the **Tax application id** field, enter the code that is used for Peruvian electronic invoices.
   1. In the **Tax application code** field, enter the code for tax IDs according to the Peruvian regulations.

### Configure Addresses 

To configure addresses, follow these steps:

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**. 
1. For each record in Country/Region that you want to use in Electronic Invoices:
   1. Select the record, then go to **Tax application** under the **LATAM** tab in the top menu.
   1. Create a record.
   1. In the **Tax application id** field, enter the code that is used for Peruvian electronic invoices.
   1. In the **Tax application code** field, enter the code for each country according to the Peruvian regulations.

Learn more in [Address setup for Latin America](ltm-core-address-setup.md).

### Other tax application configurations

#### Configure Currencies 

To configure currencies, follow these steps:

1. Go to **General ledger** \> **Currencies** \> **Currencies**.
1. For each **Currency** that you want to use in Electronic Invoices:
   1. Select the record, then go to **Tax application** under the **LATAM** tab in the top menu.
   1. Create a record.
   1. In the **Tax application id** field, enter the code that is used for Peruvian electronic invoices.
   1. In the **Tax application code** field, enter the code for each currency according to the Peruvian regulations.

### Configure charges and discounts

#### Configure global or line charges

To configure global or line charges, follow these steps.

1. Go to **Accounts receivable \> Charges setup \> Charges code**.
1. For each **Charge** that you want to use in Electronic Invoices, follow these steps:
   1. Select the record, then go to **Tax application** under the **LATAM** tab in the top menu.
   1. Create a new record.
   1. In the **Tax application Id** field enter the code that is used for Peruvian electronic invoices.
   1. In the **Tax application code** field enter the code according to the Peruvian regulations.

#### Configure global or line discounts

To configure global or line discounts, follow these steps.

1. Go to **Accounts receivable > Charges setup > Charges code**.
1. For each **Discount** that you want to use in Electronic Invoices, follow these steps:
1. For each record that is used as a global or line discount, follow these steps:
   1. Select the record, then go to **Tax application** under the **LATAM** tab in the top menu.
   1. Create a new record.
   1. In the **Tax application Id** field enter enter the code that is used for Peruvian electronic invoices.
   1. In the **Tax application code** field enter the code according to the Peruvian normative.

> [!NOTE] 
> To enter a global or line discount, use the Maintain charges button in the sales orders, enter the amount in negative.

To configure Units, follow these steps:

Go to **Organization administration** \> **Setup** \> **Units** \> **Units**, and follow these steps for each record in the list:
   1. Select the record, then go to **Tax application** under the **LATAM** tab in the top menu.
   1. Crate a new record.
   1. In the **Tax application id** field, enter the code that is used for Peruvian electronic invoices.
   1. In the **Tax code** field, enter the code according to the Peruvian regulations.

### Configure Taxes

For each tax and percentage used you must follow these steps:

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax codes**.
1. For each **Sales tax code** that you want to use in Electronic invoices:
    1. Select the record, then go to Tax application in the top menu.
    1. Create a new record.
    1. In the **Tax application id** field, select the code that is used for Peruvian electronic invoices.
   1. In the **Income tax code** field, enter the code that identifies the tax type according to the Peruvian regulations.
   1. In the **Code Regime** field, enter the name code. 
   1. In the **User-defined field 2** field, Enter the code that represents its tax condition according the UN/ECE 5153 regulation.
   1. In the **User-defined field 4** field, enter the letter of tax category identifier according the UN/ECE 5305 regulation.

## Configure electronic document references

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Electronic documents references** and follow these steps:
1. In the **Tax application id** field, enter the ID that is used for Peruvian electronic invoices.
1. Complete the **Max amount of packing slips** field.

For debits and credits notes, you must select **References** on the posting page and complete all fields required. 

#### Steps to reference a document

1. In references page go to the General tab, click on **Source Vouchers** and from the list of documents, select the document to be associated.
1. Complete the **Reference reason** with a motive (not mandatory).

Learn more in [Configure electronic document references](ltm-electronic-doc-references.md).

## Configure SSRS Reports and Services references.

For electronic invoices you must configure the **SSRS Reports / Services references** following these steps:

1. Go to Organization administration **Setup > LATAM > SSRS Reports / Services references**.
1. Create a new record.
1. Complete the **Report/Service Id** and **Report/Service name** with code and description.
1. In **Settings** tab select **Service** for the **Report/Service type** field.
1. In the **Sales point type** select **Pre-printed** (it must match the sales point type used for electronic invoices.
1. In **Parameter** section add the following lines.
    1. **Name:** TaxApplicationId - **Value:** PEFE (this code must match the tax application used for electronic invoices).

> [!NOTE] 
> This configuration will be applied to all sales points used for every Invoice, Credit note and Debit note.


