---
title: Configure electronic invoice parameters for Dominican Republic
description: Learn how to configure the information required to generate the electronic invoice XML for Dominican Republic.
author: SandraYamamoto0602
ms.topic: how-to
ms.date: 10/01/2025
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-sandraya
---

# Configure electronic invoice parameters for Dominican Republic

This article explains how to configure the information required to generate the electronic invoice XML for Dominican Republic.

## Prerequisites

Before completing the procedures in this article, ensure the following prerequisites are met:

- Enable both the country/region-specific Latin American (LATAM) feature for Dominican Republic and the general LATAM feature. 
- Set the company's address to Dominican Republic.
- Download the specific report configurations from the Dataverse configuration repository for Dominican Republic Electronic Invoices:

| Element |                    Format name                    |
|:-------:|:-------------------------------------------------:|
| Model   | :::no-loc text="Invoice Model LATAM":::                              |
| Mapping |  :::no-loc text="(Invoice Model LATAM) Invoice Model mapping LATAM"::: |
| Format  | :::no-loc text="Inventory e-invoice (DO)":::                   |
| Format  | :::no-loc text="Project e-invoice (DO)":::                       |

Learn more in [Import Electronic reporting (ER) configurations from Dataverse](global/workspace/gsw-import-er-config-dataverse.md).
- Configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- Configure all the LATAM extensions before continuing with the configuration in this article.

## Configuration required for Dominican Republic electronic invoices
The following configurations are required Dominican Republic for electronic invoices:

- Configure the tax application
- Configure the document classes
- Configure the sales point prefix
- Configure the document class sales point 
- Configure the field master lists
- Configure other tax applications

### Configure the Tax application

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax application** and select **New** to create a tax application record that has the code **DOM** (Dominican Republic electronic invoice). Use this tax application record to assign the fiscal codification to each element in Microsoft Dynamics 365 Finance as required.

### Configure the Document classes

This configuration applies to Invoices, Credit notes and Debit notes.

To configure document classes, follow these steps:

1.	Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**.
1. For each **Document class** that you want to use in Electronic Invoices.
   1. Select the record and then go to **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application id** field, enter the ID that is used for Dominican Republic electronic invoices.
   1. In the **Tax application code** field, enter the code according to the Dominican Republic regulations.
   1. In the **Letter code** field, enter **R** for debit and credit notes to enable the **Reference code** field when posting a transaction.
   1. In the document class configuration for debit notes and credit notes set the **Use reference document** slider to yes.
   1. In **Require CA number** set slider to yes. 
   1. For **Invoices**, in additional data, configure as enable Field list 1 to allow the selection of income types. 
   1. For **Debit notes** and **Credit notes**, in additional data, configure as enable Field list 1 to allow the selection of income types on posting page and Field list 10 to allow the selection of references. 

### Configure the Sales point prefix

To configure sales point prefix, follow these steps:

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Sales point prefix**.
1. For each **Sales point prefix** that you want to use in Electronic Invoices.
   1. Complete the **Sales point** that will be part of the electronic fiscal document number.
   1. Complete the **Prefix** field with a prefix number.
   1. In **Validate CA** set slider to yes.
   1. In the field **Report/Service Id** select the **SSRS Reports / Services references** configured for electronic invoices [Configure SSRS Reports / Services references](#configure-ssrs-reports-and-services-references).

### Configure document class sales point

To configure Document class sales point, follow these steps:

1.. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class sales point**.
   1. Select **Sales point prefix** created in the previous step and add a number sequence code.
   1. In the Sales CA tab in the top menu, complete all mandatory fields, especially **Date to** field that indicate Sequence due date and **From voucher number** field and **To voucher number** field with the sequence numbers authorized by the DGII.
   
### Configure Field master lists

1. Go to **Organization administration > Setup > LATAM > Fields master List**.
   1. In the **LIST 1**, in reference code, configure the codes and descriptions for **Types of income**. 
   1. In the **LIST 10** in reference code, configure the codes and descriptions for **Reference reasons** for credit and debit notes. 
1. For each **Reference code** configured in Fields master list, follow these steps:
   1. Select the record and then go to **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application id** field, enter the ID that is used for Dominican Republic electronic invoices.
   1. In the **Tax application code** field, enter the same code of each reference.

For more information see [Field list configuration for Latin America](ltm-core-field-master-lists.md).

### Other tax application configurations

#### Configure Method of payments

To configure Method of payments, follow these steps:

1. Go to **Accounts receivable** \> **Payments setup** \> **Methods of payment**.
1. For each **Method of payment** that you want to use in Electronic Invoices:
   1. Select the record and then go to **Tax application** in the LATAM tab in the top menu.
   1. Create a new record.
   1. In the **Tax application id** field, enter the code that is used for Dominican Republic electronic invoices.
   1. In the **Tax application code** field, enter the code for types of payments according to the Dominican Republican regulations (cash, credit or free).

#### Configure Currencies

To configure currencies, follow these steps:

1. Go to **General ledger** \> **Currencies** \> **Currencies**.
1. For each **Currency** that you want to use in Electronic Invoices:
   1. Select the record and then go to **Tax application** in the LATAM tab in the top menu.
   1. Create a new record.
   1. In the **Tax application id** field, enter the code that is used for Dominican Republic electronic invoices.
   1. In the **Tax application code** field, enter the code for each currency according to the Dominican Republic regulations.

#### Configure electronic document references

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Electronic documents references** and follow these steps:
1. In the **Tax application id** field, enter the ID that is used for Dominican Republic electronic invoices.
1. Complete the **Max amount of packing slips**.

For debits and credits notes, you must select **References** on the posting page and add the associated document.

#### Steps to reference a document

1. In references page go to the General tab, click on **Source Vouchers** and from the list of documents, select the document to be associated.
1. In the **Reference code** field enter a number code for reference reason.
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
    1. **Name:** TaxApplicationId - **Value:** DOM (this code must match the tax application used for electronic invoices).
