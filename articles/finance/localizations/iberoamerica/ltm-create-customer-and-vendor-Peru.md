---
title: Create customer and vendor records with an address in Peru
description: Learn how to create customer and vendor records that have an address in Peru in Microsoft Dynamics 365 Finance.
author: Fhernandez0088
ms.date: 04/17/2025
ms.topic: how-to
ms.reviewer: johnmichalak
ms.author: v-federicohe
ms.custom: bap-template
---

# Create customer and vendor records with an address in Peru

[!include [banner](../../includes/banner.md)]

This article explains how to create customer and vendor records that have an address in Peru in Microsoft Dynamics 365 Finance.

The Peruvian customer and vendor configuration contains the fiscal information that the fiscal authorities require. It also contains a reference to the document classes that can be used in transactions with customers and vendors.

## Prerequisites

Before you create records for customers and vendors who are located in Peru, the following setup must be completed:

1. Configure address formats that are specific to Peru. The address formats must use the structure of country, state, county, and so on. Learn more in [Address setup](../../../fin-ops-core/dev-itpro/organization-administration/global-address-book-address-setup.md).
1. Create the tax codes to use for value-added tax (VAT, or IGV in Peru), including VAT 18% and VAT 0%. Learn more in [Sales tax calculation methods in the Origin field](../../general-ledger/sales-tax-calculation-methods-origin-field.md).
1. Create sales tax groups that contain the tax codes that were created.
1. Create item sales tax groups that contain the tax codes that were created.
1. Create document classes to use with documents such as customer and vendor invoices, credit notes, debit notes, and packing slips. Learn more in [Configure sales and purchase invoices for Peru](ltm-configure-invoices-Peru.md).
1. Create a customer and vendor set that contains all the document classes that are used. Learn more in [Customer sets for Latin America](ltm-core-customers-set.md) and [Vendor sets for Latin America](ltm-core-vendors-set.md).
1. Create a tax ID for each type of tax identification that your customers and vendors have. Learn more in [Tax ID types for Latin America](ltm-core-tax-id-type.md).
1. Create a taxpayer type for each type of taxpayer that your customers and vendors have. Learn more in [Taxpayer types for Latin America](ltm-core-taxpayer-type.md).

## Create a record for a customer in Peru

To create a record for a customer in Peru, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable** \> **Customers** \> **All customers**, and select **New**.
1. In the **Type** field, select **Organization** for **Persona juridica** or **Person** for **Persona natural**.
1. In the **Customer group** field, select a local group.
1. In the **Address** section, select **New**, and then enter a name for the address.
1. In the **Country/region** field, select **Peru**.
1. Enter the street and street number.
1. Select a state/province.
1. Mark the address as primary.
1. In the **Contact information** section, select **New** to create a record for the company's phone number.
1. In the **Sales demographic** section, set the currency to **PEN** (legal currency).
1. Configure the terms of payments and the invoice account.
1. Set the delivery terms, mode of delivery, and delivery reason.
1. Select a sales tax group that contains all the tax codes that can have transactions with this customer.
1. In the **LATAM** section, enter the following information:

    1. In the **Customer set** field, select a set that contains the document classes to use with the customer.
    1. In the **Taxpayer type** field, select a taxpayer that represents an organization.
    1. In the **Based in country/region** field, select **Peru**.
    1. In the **Country document type** field, select a tax ID type. For example, select **RUC** (Unique Taxpayer Registry).
    1. In the **Country document number** field, enter the customer's tax ID number.

> [!NOTE]
> This procedure describes the main settings that are required for localization. You can set other fields that are required for other Dynamics 365 Finance features that you must use.

## Create a record for a vendor in Peru

To create a record for a vendor in Peru, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable** \> **Vendors** \> **All vendors**, and select **New**.
1. In the **Type** field, select **Organization** for **Persona juridica** or **Person** for **Persona natural**.
1. In the **Vendor group** field, select a local group.
1. In the **Address** section, select **New**, and then enter a name for the address.
1. In the **Country/region** field, select **Peru**.
1. Enter the street and street number.
1. Select a state/province.
1. Mark the address as primary.
1. In the **Contact information** section, select **New** to create a record for the company's phone number.
1. In the **Sales demographic** section, set the currency to **PEN** (legal currency).
1. Configure the terms of payments and the invoice account.
1. Set the delivery terms, mode of delivery, and delivery reason.
1. Select a sales tax group that contains all the tax codes that can have transactions with this vendor.
1. In the **LATAM** section, enter the following information:

    1. In the **Vendor set** field, select a set that contains the document classes to use with the vendor.
    1. In the **Taxpayer type** field, select a taxpayer that represents the organization.
    1. In the **Based in country/region** field, select **Peru**.
    1. In the **Country document type** field, select a tax ID type. For example, select **RUC**.
    1. In the **Country document number** field, enter the vendor's tax ID number.

> [!NOTE]
> This procedure describes the main settings that are required for localization. You can set other fields that are required for other Dynamics 365 Finance features that you must use.
