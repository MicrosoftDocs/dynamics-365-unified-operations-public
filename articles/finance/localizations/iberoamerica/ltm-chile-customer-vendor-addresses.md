---
title: Create customer and vendor records with an address in Chile
description: This topic provides information about how to set up records for customers and vendors located in Chile. 
author: Fhernandez0088
ms.date: 09/21/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---

# Create customer and vendor records with an address in Chile

[!include[banner](../../includes/banner.md)]

The Latin American customer and vendor configuration contains the fiscal information required by the fiscal authorities. The configuration also includes a reference to the document classes that can be used in transactions with customers and vendors.

## Prerequisites
Before you canconfigure customer and vendor records who have an address in Chile, the following prerequisites must be met:

- Create regions, provinces, and communes from Chile using states, counties, and cities in the address setup.
- Create tax codes for VAT that will be used, including IVA 19, IVA exento, IVA no afecto, and Retenciones.
- Create sales tax groups that contain the tax codes you created.
- Create item sales tax groups that contain the tax codes you created.
- Create document classes to use with customers and vendors for invoices, credit notes, debit notes, and packing slips. To learn more, see [Configure sales and purchase invoices](ltm-chile-configure-sales-purchase-invoices.md).
- Create a customer and vendor set that contains all the document classes that will be used.
- Create the Tax ID type, **RUT**.
- Create the taxpayer type, **Persona Juridica**.

## Customer configuration

Complete the following steps to configure a record for a customer with an address in Chile. 

1. Go to **Accounts receivable** > **Customers** > **All customers** and select **New** to create a new customer.
2. Enter a name and brief description for the customer and in the **Type** field, select **Organization**.
3. In the **Customer group** field, select a local group.
4. In the **Address** section, create a new address and name it.
5. Set the country/region to Chile.
6. Complete the street and street number.
7. Select a state, county, and city. 
8. Set the address as primary.
9. In the **Contact information** section, create a new record for the company phone number. 
10. In the **Sales demographic** section, set the currency to **Chilean peso**.
11. Configure the terms of payments.
12. Configure the invoice account.
13. Set the delivery terms, mode of delivery, and delivery reason.
14. Select a sales tax group that contains all the tax codes that can have transactions with this customer.
15. In the **LATAM** section, from the **Legal entity** page, complete the information as follows:

    - **Customer set**: Select the set that contains the document classes to be used with the customer.
    - **Taxpayer type**: Select the **Persona juridica** that represents the organization.
    - **Based in country/region**: Select Chile.
    - **Country document type**: Select **RUT** (Registro Unico Tributario).
    - Complete the **Country document number** with the RUT number of the company.

## Vendor configuration

Complete the following steps to configure a record for a vendor with an address in Chile. 

1. Go to **Accounts payable** > **Vendors** > **All vendors** and select **New** to create a new vendor.
2. Enter a name and brief description for the vendor and in the **Type** field, select **Organization**.
3. In the **Vendor group** field, select a local group.
4. In the **Address** section create a new address and name it.
5. Set the country/region to Chile.
6. Complete the street and street number.
7. Select a state, county, and city. 
8. Set the address as primary.
9. In the **Contact information** section, create a new record for the company phone number. 
10. In the **Sales demographic** section, set the currency to **Chilean peso**.
11. Configure the terms of payments.
12. Configure the invoice account.
13. Set the delivery terms, mode of delivery, and delivery reason.
14. Select a sales tax group that contains all the tax codes that can have transactions with this vendor.
15. In the **LATAM** section, from the **Legal entity** page, complete the information as follows:

    - **Vendor set**: Select the set that contains the document classes to be used with the vendor.
    - **Taxpayer type**: Select the **Persona juridica** that represents an organization.
    - **Based in country/region**: Select Chile.
    - **Country document type**: Select **RUT** (Registro Unico Tributario).
    - Complete the **Country document number** with the RUT number of the company.







[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
