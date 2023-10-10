---
title: Create customer and vendor records with an address in Costa Rica
description: This topic provides information about how to set up records for customers and vendors located in Costa Rica. 
author: Cpicon85
ms.date: 10/09/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-cpicon
ms.custom: bap-template
---

# Create customer and vendor records with an address in Costa Rica

The Latin American customer and vendor configuration contains the fiscal information required by the fiscal authorities. The configuration also includes a reference to the document classes that can be used in transactions with customers and vendors.
## Prerequisites

* Create regions, provinces and communes from Costa Rica using states, counties, and cities from the address setup.
* Create tax codes for the VAT tax (value added tax) that will be used (VAT general rate, exempt, etc).
* Create sales tax groups containing the tax codes created.
* Create item sales tax groups containing the tax codes created.
* Create document classes that will be used with the vendors/customers (invoices, credit notes, debit notes, packing slips, etc.) See sales and vendor invoice for Costa Rica company configuration.
* Create a customer and vendor set that contains all the document classes that will be used.
* Create a Tax ID for each type of tax identification that your customers and suppliers have.
* Create a taxpayer type for each type of taxpayer that your customers and suppliers have.

## Customer configuration

1. Go to **Accounts receivable > Customers > All customers** create a new customer.
2. Set the type to “organization”.
3. Set the customer group to a local one.
4. In the **Address** section create a new one and give it a name.
5. Set the country/region to Costa Rica.
6. Complete the street and street number.
7. Select a state, county, and city. 
8. Set the address as primary.
9. In the **Contact information** section create a new record for the company phone number. 
10. In the **Sales demographic** section set the currency to **CRC** Costa Rican Colon.
11. Configure the terms of payments.
12. Configure the invoice account.
13. Set the delivery terms, mode of delivery and delivery reason.
14. Select a sales tax group that contains all the tax codes that can have the transactions with this customer.
15. In the **LATAM** section complete the information as follows:
    * **Customer set**: select a set created previously that contains the document classes to be used with the customer
    * **Taxpayer type**: select a taxpayer created before, for example “persona juridica” that represents an organization
    * **Based in country/region**: Costa Rica
    * **Country document type**: select one tax ID type created before, for example "CJ" (cedula juridica)
    * Complete the **Country document number** with the tax ID number the client

## Vendor configuration

1. Go to **Accounts payable > Vendors > All vendors** create a new vendor.
2. Set the type to “organization”.
3. Set the customer group to a local one.
4. In the **Address** section create a new one and give it a name.
5. Set the country/region to Costa Rica.
6. Complete the street and street number.
7. Select a state, county, and city. 
8. Set the address as primary.
9. In the **Contact information** section create a new record for the company phone number. 
10. In the **Sales demographic** section set the currency to **CRC** Costa Rican Colon
11. Configure the terms of payments.
12. Configure the invoice account.
13. Set the delivery terms, mode of delivery and delivery reason.
14. Select a sales tax group that contains all the tax codes that can have the transactions with this vendor.
15. In the **LATAM** section complete the information as follows:
      * **Vendor set**: select a set created previously that contains the document classes to be used with the vendor
      * **Taxpayer type**: select a taxpayer created before, for example “persona juridica” that represents an organization
    * **Based in country/region**: Costa Rica
    * **Country document type**: select one tax ID type created before, for example "CJ" (cedula juridica)
    * Complete the **Country document number** with the tax ID number the vendor
