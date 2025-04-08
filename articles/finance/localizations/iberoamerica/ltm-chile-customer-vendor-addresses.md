---
title: Create customer and vendor records with an address in Chile
description: Learn how to set up records for customers and vendors that are located in Chile, including prerequisites and an outline on customer configuration.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: article
ms.date: 09/21/2023
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Create customer and vendor records with an address in Chile

[!include[banner](../../includes/banner.md)]

The Latin American (LATAM) customer and vendor configuration contains the fiscal information that's required by the fiscal authorities. In addition, it includes a reference to the document classes that can be used in transactions with customers and vendors.

## Prerequisites

Before you can configure records for customers and vendors who have an address in Chile, the following prerequisites must be met:

- Create regions, provinces, and communes in Chile by using states, counties, and cities in the address setup.
- Create the tax codes that will be used for value-added tax (VAT), including IVA 19, IVA exento, IVA no afecto, and Retenciones.
- Create sales tax groups that contain the tax codes that you created.
- Create item sales tax groups that contain the tax codes that you created.
- Create document classes to use with customers and vendors for invoices, credit notes, debit notes, and packing slips. For more information, see [Configure sales and purchase invoices](ltm-chile-configure-sales-purchase-invoices.md).
- Create a customer and vendor set that contains all the document classes that will be used.
- Create the **RUT** tax ID type. (RUT is short for "Registro Único Tributario.")
- Create the **Persona Juridica** taxpayer type.

## Customer configuration

Follow these steps to configure a record for a customer who has an address in Chile.

1. Go to **Accounts receivable** \> **Customers** \> **All customers**, and select **New** to create a customer.
2. Enter a name and a brief description for the customer.
3. In the **Type** field, select **Organization**.
4. In the **Customer group** field, select a local group.
5. In the **Address** section, create an address, and name it.
6. Set the country/region to Chile.
7. Complete the street and street number.
8. Select a state, county, and city.
9. Set the address as primary.
10. In the **Contact information** section, create a record for the company's phone number.
11. In the **Sales demographic** section, set the currency to **Chilean peso**.
12. Configure the terms of payment.
13. Configure the invoice account.
14. Set the delivery terms, mode of delivery, and delivery reason.
15. Select a sales tax group that contains all the tax codes that can have transactions with the customer.
16. In the **LATAM** section, from the **Legal entity** page, complete the information in the following way:

    - In the **Customer set** field, select the set that contains the document classes to use with the customer.
    - In the **Taxpayer type** field, select the **Persona Juridica** type that represents the organization.
    - In the **Based in country/region** field, select **Chile**.
    - In the **Country document type** field, select **RUT**.
    - Complete the **Country document number** field with the RUT number of the company.

## Vendor configuration

Follow these steps to configure a record for a vendor who has an address in Chile.

1. Go to **Accounts payable** \> **Vendors** \> **All vendors**, and select **New** to create a vendor.
2. Enter a name and a brief description for the vendor.
3. In the **Type** field, select **Organization**.
4. In the **Vendor group** field, select a local group.
5. In the **Address** section, create an address, and name it.
6. Set the country/region to Chile.
7. Complete the street and street number.
8. Select a state, county, and city.
9. Set the address as primary.
10. In the **Contact information** section, create a record for the company's phone number.
11. In the **Sales demographic** section, set the currency to **Chilean peso**.
12. Configure the terms of payment.
13. Configure the invoice account.
14. Set the delivery terms, mode of delivery, and delivery reason.
15. Select a sales tax group that contains all the tax codes that can have transactions with the vendor.
16. In the **LATAM** section, from the **Legal entity** page, complete the information in the following way:

    - In the **Vendor set** field, select the set that contains the document classes to use with the vendor.
    - In the **Taxpayer type** field, select the **Persona Juridica** type that represents an organization.
    - In the **Based in country/region** field, select **Chile**.
    - In the **Country document type** field, select **RUT**.
    - Complete the **Country document number** field with the RUT number of the company.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
