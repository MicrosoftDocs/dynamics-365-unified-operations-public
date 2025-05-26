---
title: Create customer and vendor records with an address in the Dominican Republic
description: Learn how to create customer and vendor records that have an address in the Dominican Republic.
author: cpicon85
ms.date: 04/03/2025
ms.topic: how-to
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.author: v-cpicon

---

# Create customer and vendor records with an address in the Dominican Republic

[!INCLUDE[banner](../../../includes/banner.md)]

The Dominican Republic customer and vendor configuration contains the fiscal information that is required by the fiscal authorities. It also includes a reference to the document classes that can be used in transactions with customers and vendors.

## Prerequisites

Before you create records for customers and vendors who are located in the Dominican Republic, the following setup must be completed:

- Set up address formats that are specific to the Dominican Republic. Use the **Address setup** page to configure provinces, municipalities, sectors, and other information. Learn more in [Address setup for Latin America](ltm-core-address-setup.md).
- Create the tax codes that will be used for Tax on Transfers of Industrialized Goods and Services (ITBIS), including ITBIS 18% and ITBIS 0%.
- Set up sales tax groups that contain the tax codes that were created.
- Set up item sales tax groups that contain the tax codes that were created.
- Create document classes to use with customer and vendor invoices, credit notes, debit notes, packing slips, and other documents. Learn more in [Configure sales and purchase invoices for the Dominican Republic](ltm-configure-invoices-dominican-republic.md).
- Create a customer and vendor set that contains all the document classes that will be used.
- Create a tax ID for each type of tax identification that your customers and vendors have.
- Create a taxpayer type for each type of taxpayer that your customers and vendors have.

## Create a record for a customer in the Dominican Republic

To create a record for a customer in the Dominican Republic, follow these steps.

1. Go to **Accounts receivable** \> **Customers** \> **All customers**, and select **New**.
1. In the **Type** field, select **Organization** for Persona Jurídica or **Person** for Persona Natural.
1. In the **Customer group** field, select a local group.
1. In the **Address** section, select **New**, and provide a name for the address.
1. In the **Country/region** field, select **Dominican Republic**.
1. Enter the street and street number.
1. Select a state/province.
1. Mark the address as primary.
1. In the **Sales demographic** section, set the currency to **DOP** (Dominican peso).
1. Configure the terms of payment and the invoice account.
1. Select a sales tax group that contains all the tax codes that can have transactions with this customer.
1. In the **LATAM** section, enter the following information:

    - In the **Customer set** field, select a set that contains the document classes to use with the customer.
    - In the **Taxpayer type** field, select a taxpayer that represents an organization.
    - In the **Based in country/region** field, select **Dominican Republic**.
    - In the **Country document type** field, select a tax ID type. For example, select **RNC** (Registro Nacional de Contribuyentes).
    - Complete the **Country document number** field with the customer's tax ID number.

> [!NOTE]
> This procedure describes the main settings that are required for localization. You can set other fields that are required for other Microsoft Dynamics 365 Finance features that you must use.

## Create a record for a vendor in the Dominican Republic

To create a record for a vendor in the Dominican Republic, follow these steps.

1. Go to **Accounts payable** \> **Vendors** \> **All vendors**, and select **New**.
1. In the **Type** field, select **Organization** for Persona Jurídica or **Person** for Persona Natural.
1. In the **Vendor group** field, select a local group.
1. In the **Address** section, select **New**, and provide a name for the address.
1. In the **Country/region** field, select **Dominican Republic**.
1. Enter the street and street number.
1. Select a state/province.
1. Mark the address as primary.
1. In the **Sales demographic** section, set the currency to **DOP** (Dominican peso).
1. Configure the terms of payment and the invoice account.
1. Select a sales tax group that contains all the tax codes that can have transactions with this vendor.
1. In the **LATAM** section, enter the following information:

    - In the **Vendor set** field, select a set that contains the document classes to use with the vendor.
    - In the **Taxpayer type** field, select a taxpayer that represents the organization.
    - In the **Based in country/region** field, select **Dominican Republic**.
    - In the **Country document type** field, select a tax ID type. For example, select **RNC** (Registro Nacional de Contribuyentes).
    - Complete the **Country document number** field with the vendor's tax ID number.

> [!NOTE]
> This procedure describes the main settings that are required for localization. You can set other fields that are required for other Finance features that you must use.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
