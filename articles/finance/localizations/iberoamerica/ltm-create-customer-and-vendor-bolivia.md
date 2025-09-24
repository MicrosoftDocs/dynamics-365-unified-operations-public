---
title: Create customer and vendor records with an address in Bolivia
description: Learn how to create customer and vendor records that have an address in Bolivia.
author: Cpicon85
ms.date: 02/18/2025
ms.topic: how-to
ms.reviewer: johnmichalak
ms.author: v-cpicon
ms.custom: bap-template
---

# Create customer and vendor records with an address in Bolivia

[!include [banner](../../includes/banner.md)]

The Bolivian customer and vendor configuration contains the fiscal information that the fiscal authorities require. It also contains a reference to the document classes that can be used in transactions with customers and vendors.

## Prerequisites

Before you create records for customers and vendors who are located in Bolivia, the following setup must be completed:

- Configure address formats that are specific to Bolivia. The address formats must use the structure country, state, county, and so on. Learn more in [Address setup](../../../fin-ops-core/dev-itpro/organization-administration/global-address-book-address-setup.md).
- Create the tax codes to use for value-added tax (VAT), including VAT 13% and VAT 0%. Learn more in [Sales tax calculation methods in the Origin field](../../general-ledger/sales-tax-calculation-methods-origin-field.md).
- Create sales tax groups that contain the tax codes that were created.
- Create item sales tax groups that contain the tax codes that were created.
- Create document classes to use with documents such as customer and vendor invoices, credit notes, debit notes, and packing slips. Learn more in [Configure sales and purchase invoices for Bolivia](ltm-configure-invoices-Bolivia.md).
- Create a customer and vendor set that contains all the document classes that will be used.
- Create a tax ID for each type of tax identification that your customers and vendors have.
- Create a taxpayer type for each type of taxpayer that your customers and vendors have.

## Create a record for a customer in Bolivia

To create a record for a customer in Bolivia, follow these steps.

1. Go to **Accounts receivable** \> **Customers** \> **All customers**, and select **New**.
1. In the **Type** field, select **Organization** for **Persona Juridica** or **Person** for **Persona natural**.
1. In the **Customer group** field, select a local group.
1. In the **Address** section, select **New**, and enter a name for the address.
1. In the **Country/region** field, select **Bolivia**.
1. Enter the street and street number.
1. Select a state/province.
1. Mark the address as primary.
1. In the **Contact information** section, select **New** to create a record for the company's phone number.
1. In the **Sales demographic** section, set the currency to **BOB** (legal currency).
1. Configure the terms of payments and the invoice account.
1. Set the delivery terms, mode of delivery, and delivery reason.
1. Select a sales tax group that contains all the tax codes that can have transactions with this customer.
1. In the **LATAM** section, enter the following information:

    - In the **Customer set** field, select a set that contains the document classes to use with the customer.
    - In the **Taxpayer type** field, select a taxpayer that represents an organization. 
    - In the **Based in country/region** field, select **Bolivia**.
    - In the **Country document type** field, select a tax ID type. For example, select **NIT** (Unique Taxpayer Registry).
    - Complete the **Country document number** field with the customer's tax ID number.

> [!NOTE]
> This procedure describes the main settings that are required for localization. You can set other fields that are required for other Microsoft Dynamics 365 Finance features that you must use.

## Create a record for a vendor in Bolivia

To create a record for a vendor in Bolivia, follow these steps.

1. Go to **Accounts payable** \> **Vendors** \> **All vendors**, and select **New**.
1. In the **Type** field, select **Organization** for **Persona juridica** or **Person** for **Persona natural**.
1. In the **Vendor group** field, select a local group.
1. In the **Address** section, select **New**, and enter a name for the address.
1. In the **Country/region** field, select **Bolivia**.
1. Enter the street and street number.
1. Select a state/province.
1. Mark the address as primary.
1. In the **Contact information** section, select **New** to create a record for the company's phone number.
1. In the **Sales demographic** section, set the currency to **BOB** (legal currency).
1. Configure the terms of payments and the invoice account.
1. Set the delivery terms, mode of delivery, and delivery reason.
1. Select a sales tax group that contains all the tax codes that can have transactions with this vendor.
1. In the **LATAM** section, enter the following information:

    - In the **Vendor set** field, select a set that contains the document classes to use with the vendor.
    - In the **Taxpayer type** field, select a taxpayer that represents the organization. 
    - In the **Based in country/region** field, select **Bolivia**.
    - In the **Country document type** field, select a tax ID type. For example, select **NIT**.
    - Complete the **Country document number** field with the vendor's tax ID number.

> [!NOTE]
> This procedure describes the main settings that are required for localization. You can set other fields that are required for other Dynamics 365 Finance features that you must use.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
