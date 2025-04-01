---
title: Create customer and vendor records with an address in Dominican Republic
description: Learn about creation Customers and Vendors records with an address in Dominican Republic. 
author: cpicon85
ms.date: 03/24/2025
ms.topic: how-to
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.author: v-cpicon

---

# Create customer and vendor records with an address in Dominican Republic

[!INCLUDE[banner](../../../includes/banner.md)]

The Dominican Republic customer and vendor configuration contains the fiscal information that's required by the fiscal authorities. The configuration also includes a reference to the document classes that can be used in transactions with customers and vendors.

## Prerequisites

Before you create records for customers and vendors who are located in the Dominican Republic, the following setup must be completed:

- Set up address formats that are specific to the Dominican Republic. Use Address setup to configure provinces, municipalities, sectors, etc. Learn more in [Address setup](ltm-core-address-setup.md).
- Create the tax codes that will be used for Tax on Transfers of Industrialized Goods and Services (ITBIS), including ITBIS 18%, 0%, etc. 
- Sales tax groups that contain the tax codes that were created.
- Item sales tax groups that contain the tax codes that were created.
- Create Document classes to use with customer and vendor invoices, credit notes, debit notes, packing slips, and so on. Learn more in [Configure sales and purchase invoices for the Dominican Republic](ltm-Configure-invoices-Dominican Republic.md).
- A customer and vendor set that contains all the document classes that will be used.
- A tax ID for each type of tax identification that your customers and vendors have.
- A taxpayer type for each type of taxpayer that your customers and vendors have.

## Create a record for a customer in Dominican Republic

To create a record for a customer in Bolivia, follow these steps.

1. Go to **Accounts receivable > Customers > All customers**, and select **New**.
2. In the **Type** field, select Organization for Persona Jurídica or Person for Persona Natural.
3. In the **Customer group** field, select a local group.
4. In the **Address** section, select **New**, and provide a name for the address.
5. In the **Country/region** field, select **Dominican Republic**.
6. Enter the street and street number.
7. Select a state/province,  and mark the address as primary.
8. In the **Sales demographic** section, set the currency to **DOP** (Dominican Peso).
9. Configure the terms of payments and the invoice account.
10. Select a sales tax group that contains all the tax codes that can have transactions with this customer.
11. In the LATAM section, enter the following information:
     - In the **Customer set** field, select a set that contains the document classes to use with the customer.
     - In the **Taxpayer type** field, select a taxpayer that represents an organization.
     - In the **Based in country/region** field, select **Dominican Republic**.
     - In the **Country document type** field, select a tax ID type. For example, select **RNC** (Registro Nacional de Contribuyentes).
     - Complete the **Country document number** field with the customer's tax ID number.

> This procedure describes the main settings that are required for localization. You can set other fields that are required for other Microsoft Dynamics 365 Finance features that you must use..

## Create a record for a vendor in Dominican Republic

To create a record for a vendor in Dominican Republic, follow these steps.

1. Go to **Accounts payable > Vendors > All vendors**, and select **New**.
2. In the **Type** field, select Organization for Persona Jurídica or Person for Persona Natural
3. In the **Vendor group** field, select a local group.
4. In the **Address** section, select **New**, and provide a name for the address.
5. In the **Country/region** field, select **Dominican Republic**.
6. Enter the street and street number.
7. Select a state/province, and mark the address as primary.
8. In the **Sales demographic** section, set the currency to **DOP** (Dominican Peso).
9. Configure the terms of payments and the invoice account.
10. Select a sales tax group that contains all the tax codes that can have transactions with this vendor.
11. In the **LATAM** section, enter the following information:
    - In the **Vendor set** field, select a set that contains the document classes to use with the vendor.
    - In the **Taxpayer type** field, select a taxpayer that represents the organization.
    - In the **Based in country/region** field, select **Dominican Republic**.
    - In the **Country document type** field, select a tax ID type. For example, select **RNC**.
    - Complete the **Country document number** field with the vendor's tax ID number.

> This procedure describes the main settings that are required for localization. You can set other fields that are required for other Finance features that you must use..

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
