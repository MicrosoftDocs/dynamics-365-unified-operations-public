---
title: Create customer and vendor records with an address in Costa Rica
description: This article explains how to set up records for customers and vendors located in Costa Rica. 
author: Cpicon85
ms.date: 10/09/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-cpicon
ms.custom: bap-template
---

# Create customer and vendor records with an address in Costa Rica

[!include [banner](../../includes/banner.md)]

The Costa Rican customer and vendor configuration contains the fiscal information required by the fiscal authorities. The configuration also includes a reference to the document classes that can be used in transactions with customers and vendors.

## Prerequisites
Before you create records for customers and vendors who are located in Costa Rica, the following must be set up:

- Address formats specific to Costa Rica. This includes using States, Counties, and Cities for Regions, Provinces, and Communes, respectively.
- Tax codes for the VAT tax (value added tax) that will be used (VAT general rate, exempt, etc).
- Sales tax groups that contain the tax codes created.
- Item sales tax groups that contain the tax codes created.
- Document classes to use with customer and vendor invoices, credit notes, debit notes, and packing slips. For more details, see [Configure sales and purchase invoices for Costa Rica](ltm-configure-invoices-costa-rica.md).
- A customer and vendor set that contains all the document classes that will be used.
- A tax ID for each type of tax identification that your customers and suppliers have.
- A taxpayer type for each type of taxpayer that your customers and suppliers have.

## Create a record for a customer in Costa Rica

1. Go to **Accounts receivable** > **Customers** > **All customers** and select **New**.
2. In the **Type** field, select **Organization**.
3. In the **Customer group** field, select a local group.
4. In the **Address** section, select **New** and provide a name for the address.
5. In the **Country/region** field, select **Costa Rica**.
6. Enter the street and street number.
7. Select a state, county, and city, and mark the address as primary. 
8. In the **Contact information** section, select **New** to create a new record for the company phone number. 
9. In the **Sales demographic** section set the currency to **CRC** (Costa Rican Colon).
10. Configure the terms of payments and the invoice account.
11. Set the delivery terms, mode of delivery, and delivery reason.
12. Select a sales tax group that contains all the tax codes that can have transactions with this customer.
13. In the **LATAM** section, enter the following field information:

    - **Customer set** - Select a set that contains the document classes to be used with the customer.
    - **Taxpayer type** - Select a taxpayer that represents an organization. For example **persona juridica**.
    - **Based in country/region** - Select **Costa Rica**.
    - **Country document type** - Select a tax ID type. For example, **CJ** (cedula juridica).
    - Complete the **Country document number** with the customer's tax ID number.

## Create a record for a vendor in Costa Rica

1. Go to **Accounts payable** > **Vendors** > **All vendors** and select **New**.
2. In the **Type** field, select **Organization**.
3. In the **Vendor group** field, select a local group.
4. In the **Address** section, select **New** and provide a name for the address.
5. In the **Country/region** field, select **Costa Rica**.
6. Enter the street and street number.
7. Select a state, county, and city, and mark the address as primary. 
8. In the **Contact information** section, select **New** to create a new record for the company phone number. 
9. In the **Sales demographic** section set the currency to **CRC** (Costa Rican Colon).
10. Configure the terms of payments and the invoice account.
11. Set the delivery terms, mode of delivery, and delivery reason.
12. Select a sales tax group that contains all the tax codes that can have transactions with this vendor.
13. In the **LATAM** section, enter the following field information:

    - **Vendor set** - Select a set that contains the document classes to be used with the vendor.
    - **Taxpayer type** - Select a taxpayer that represents the organization. For example, **persona juridica**.
    - **Based in country/region** - Select **Costa Rica**.
    * **Country document type** - Select a tax ID type. For example, **CJ** (cedula juridica).
    * Complete the **Country document number** with the Vendor's tax ID number.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
