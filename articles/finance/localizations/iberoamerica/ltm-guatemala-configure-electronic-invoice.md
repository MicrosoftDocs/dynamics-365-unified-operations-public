---
title: Configure electronic invoice parameters for Guatemala
description: Learn how to configure the information required to generate the electronic invoice XML for Guatemala.
author: Nahuel306
ms.topic: how-to
ms.date: 09/29/2025
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-ssolveira
---

# Configure electronic invoice parameters for Guatemala

[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to configure the information that you need to generate the electronic invoice XML for Guatemala.

## Prerequisites

Before you complete the procedures in this article, make sure that you meet the following prerequisites:

- Enable both the country/region-specific Latin Americans (LATAM) feature for Guatemala and the general LATAM feature.
- Set the company's address to Guatemala.
- Download the specific report configurations from the Dataverse configuration repository for Guatemala Electronic Invoices:

| Element |                    Format name                                           |
| ------- | -------------------------------------------------                        |   
| Model   | :::no-loc text="Invoice Model LATAM":::                                  |
| Mapping | :::no-loc text="(Invoice Model LATAM) Invoice Model mapping LATAM":::    |
| Format  | :::no-loc text="Inventory e-invoice(GT)":::                              |
| Format  | :::no-loc text="Project e-invoice(GT)":::                                |

Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).
- Configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- Configure all the LATAM extensions before continuing with the configuration in this article.

## Configuration required for Guatemala electronic invoices

The following configurations are required for Guatemala electronic invoices:

- Configure the tax application
- Configure the legal entity
- Configure the document classes
- Configure the sales point configuration
- Configure the sales point prefix
- Configure the field master lists
- Configure the fiscal information
- Configure the addresses
- Configure other tax applications
- Configure Taxes

Each configuration is described in the following sections.

### Tax application configuration

Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax application** and select **New** to create a tax application record that has the code **GTFE** (Guatemala electronic invoice). Use this tax application record to assign the fiscal codification to each element in Microsoft Dynamics 365 Finance as required.

### Legal entity configuration

To configure the legal entity, follow these steps:

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
1. Select the legal entity that you want to work with.
1. Enter the address with country/region, state, and county.            
1. Enter the contact information with the email address and set it to **Primary**.
1. In the LATAM section, select the **Taxpayer type** that represents organizations.
1. Enter **GT** for the **Based in country/region**.
1. Select the option that represents the identification document type used by the organization for the **Country/region document type**.
1. In the LATAM section, enter the company ID number with the verification code at the end separated with a middle hyphen (1234567-8) in the **Country/region identification number** field.

### Document classes configuration

This configuration applies to invoices, credit notes, and debit notes.

To configure document classes, follow these steps:

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**. 
1. For each **Document class** that you want to use in electronic invoicing:
   1. Select the record and then go to **Tax application**.
   1. On the **Tax application** page, enter the ID that is used for Guatemala electronic invoicing in the **Tax application id** field.
   1. Enter the code according to the Guatemala normative in the **Tax application code** field.
   1. Enter **R** for debit and credit notes in the **Letter code** field to enable the **Reference code** field when posting a transaction.
   1. Enter the electronic document description in the **Legal Description** field.
   1. Set the **Use reference document** slider to No for invoices and set the **Use reference document** slider to Yes for debit notes and credit notes.
   1. Set the **voucher with taxes** slider to Yes.

### Sales point prefix configuration

To configure the sales point prefix, follow these steps:

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Sales point prefix** and for the sales point used for electronic invoicing follow these steps: 
1. Enter the authorized prefix code for electronic invoicing in the **Prefix** field.
1. In the **Report/Service Id** field, select the **SSRS Reports / Services references** configured for electronic invoicing. Learn more in [Configure SSRS Reports and Services references](#configure-ssrs-reports-and-services-references).

### Field master lists configurations

To configure field master lists, follow these steps:

1. Go to **Organization administration > Setup > LATAM > Fields master List**.
1. In the **LIST 1** field, configure the codes for operation types and for credit and debit note types.

Learn more in [Field list configuration for Latin America](ltm-core-field-master-lists.md).

### Fiscal information configuration

To configure fiscal information, follow these steps:

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax ID type**, and follow these steps for each record in the list:
1. Select the record, then select **Tax application**.
1. On the **Tax application** page, in the **Tax application id** field, enter the code that's used for Guatemala electronic invoicing.
1. In the **Tax application code** field, enter the code for tax IDs according to the Guatemala normative.
1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Taxpayer type**. In the records that you use, go to the **Tax application** menu, then follow these steps:
1. Create a record that has the tax application code that's used for Guatemala electronic invoicing.
1. In the **Tax application code** field, enter the code of the taxpayer responsibility according to the Guatemala normative.

Learn more in [Taxpayer types for Latin America](ltm-core-taxpayer-type.md) and [Tax ID types for Latin America](ltm-core-tax-id-type.md).

### Addresses configurations

To configure addresses, follow these steps:

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**. 
1. For each record (Country/Region, State, and County) used in electronic invoicing, go to **LATAM** \> **Tax application** to assign the tax application codes according to the Guatemala normative.

Learn more in [Address setup for Latin America](ltm-core-address-setup.md).

## Other tax application configurations

#### Configure released products

To configure released products, follow these steps:

1. Go to **Product information management** > **Products** > **Released products**.
1. For each record in the list, follow these steps:
   1. Select the record and in the top menu go to **LATAM > **Tax application**.
   1. Create a new record.
   1. In the **Tax application Id** field, select the one used for Guatemala electronic invoicing.
   1. In the **Tax application code** field, enter the code that identifies the product or service.

#### Currencies configuration

To configure currencies, follow these steps:

1. Go to **General ledger** > **Currencies** > **Currencies**.
1. For each record in the list, follow these steps:
   1. Select the record and then go to **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application id** field, select the code that's used for Guatemala electronic invoicing.
   1. In the **Tax application code** field, enter the currency code according to the Guatemala normative.

### Configure taxes

To configure the taxes for each tax and percentage used, follow these steps:

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax codes**.
1. Follow these steps for each record on the list:
   1. Select the record and then go to **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application id** field, select the code that's used for Guatemala electronic invoicing.
   1. In the **Income tax code** field, enter the code that identifies the tax type according to the Guatemala normative.
   1. In the **Code regime** field, enter the tax name according to the Guatemala normative.
  
> [!NOTE]
> The electronic invoice format includes VAT.

## Configure electronic document references

When you issue an electronic document that has an associated document, you must select **References** on the posting page and add the associated document.

To configure electronic document references, follow these steps:

1. Go to **organization administration**\>**Setup**\>**LATAM**\>**Electronic document references**
1. In the Tax application id field, enter the ID that is used for Guatemala electronic invoices.

> [!NOTE]
> For Debits and Credits notes, you must select **References** on the posting page and add the associated document.

### Steps to reference a document

In the references page, in the general tab, select **source vouchers**. From the list of documents, select the document to associate.

1. In the Reference code field, enter the number code for reference reason according to the Guatemala normative.
1. Complete the **Reference date** field.
1. Complete the **Reference document number** field with the complete document number referenced.
1. Complete the **Reference reason** field with a motive (not mandatory).

> [!NOTE]
> The referenced document must be already validated or approved by the fiscal authority and the XML response attached in the invoice journal.

Learn more in [Configure electronic document references](ltm-electronic-doc-references.md).

## Configure SSRS Reports and Services references

For electronic invoicing, you must configure the **SSRS Reports / Services references** following these steps.

1. Go to **Organization administration > Setup > LATAM > SSRS Reports / Services references**.
1. Create a new record.
1. Complete the **Report/Service Id** and **Report/Service name** with a code and description.
1. In the Settings tab, select **Service** for the **Report/Service type** field.
1. In the **Sales point type** select **Pre-printed** (it must match the sales point type used for electronic invoicing).
1. In the Parameter section, add the following lines:
    1. **Name:** TaxApplicationId - **Value:** GTFE (this code must match the tax application used for electronic invoicing)
   
> [!NOTE]
> This configuration applies to all sales points used for every Invoice, Credit note, and Debit note.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
