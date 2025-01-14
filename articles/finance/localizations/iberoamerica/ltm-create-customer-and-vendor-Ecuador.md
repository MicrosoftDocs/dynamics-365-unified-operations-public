---
title: Create customer and vendor records with an address in Ecuador
description: This topic provides information about creation Customers and Vendors records with an address in Ecuador. 
author: Cpicon85
ms.date: 01/14/2025
ms.topic: Article
ms.reviewer: johnmichalak
ms.author: v-cpicon
ms.custom: bap-template
---

The Ecuatorian customer and vendor configuration contains the fiscal information that's required by the fiscal authorities. The configuration also includes a reference to the document classes that can be used in transactions with customers and vendors.

# Prerequisites
Before you create records for customers and vendors who are located in Ecuador, the following setup must be completed:
- Address formats that are specific to Ecuador. These formats must use country as Ecuador and states/province for provinces.
- Create the tax codes that will be used for value-added tax (VAT), including VAT  13%, VAT 0%, etc.
- Sales tax groups that contain the tax codes that were created.
- Item sales tax groups that contain the tax codes that were created.
- Create Document classes to use with customer and vendor invoices, credit notes, debit notes, packing slips, and so on.  For more information, see [Configure sales and purchase invoices for Ecuador](ltm-configure-invoices-Ecuador.md).
- A customer and vendor set that contains all the document classes that will be used.
- A tax ID for each type of tax identification that your customers and vendors have.
- A taxpayer type for each type of taxpayer that your customers and vendors have.
# Create a record for a customer in Ecuador

1. Go to **Accounts receivable > Customers > All customers**, and select **New**.
2. In the **Type** field, select **Organization** for **Sociedad** or **Person** for **Persona natural**.
3. In the **Customer group** field, select a local group.
4. In the **Address** section, select **New**, and provide a name for the address.
5. In the **Country/región** field, select **Ecuador**.
6. Enter the street and street number.
7. Select a state/province, and mark the address as primary.
8. In the **Contact information** section, select **New** to create a record for the company phone number.
9. In the **Sales demographic** section, set the currency to **USD** (Legal currency).
10. Configure the terms of payments and the invoice account.
11. Set the delivery terms, mode of delivery, and delivery reason.
12. Select a sales tax group that contains all the tax codes that can have transactions with this customer.
13. In the **LATAM** section, enter the following information:
- In the **Customer set** field, select a set that contains the document classes to use with the customer.
- In the **Taxpayer type** field, select a taxpayer that represents an organization. 
- In the **Based in country/región** field, select **Ecuador**.
- In the **Country document type** field, select a tax ID type. For example, select **RUC** (Unique Taxpayer Registry).
- Complete the **Country document number** field with the customer's tax ID number.

> These are the main settings required for localization, you may fill in other fields of this form required for other Dynamics 365 Finance features you need to use.
> 
# Create a record for a vendor in Ecuador

1. Go to **Accounts payable > Vendors > All vendors**, and select **New**.
2. In the **Type** field, select **Organization** for **Sociedad** or **Person** for **Persona natural**.
3. In the **Vendor group field**, select a local group.
4. In the **Address** section, select **New**, and provide a name for the address.
5. In the **Country/región** field, select **Ecuador**.
6. Enter the street and street number.
7. Select a state/province, and mark the address as primary.
8. In the **Contact information** section, select **New** to create a record for the company phone number.
9. In the **Sales demographic** section, set the currency to **USD** (Legal currency).
10. Configure the terms of payments and the invoice account.
11. Set the delivery terms, mode of delivery, and delivery reason.
12. Select a sales tax group that contains all the tax codes that can have transactions with this vendor.
13. In the **LATAM** section, enter the following information:
- In the **Vendor set** field, select a set that contains the document classes to use with the vendor.
- In the **Taxpayer type** field, select a taxpayer that represents the organization. 
- In the **Based in country/región** field, select **Ecuador**.
- In the **Country document type** field, select a tax ID type. For example, select **RUC**.
- Complete the **Country document number** field with the vendor's tax ID number.

>These are the main settings required for localization, you may fill in other fields of this form required for other Dynamics 365 Finance features you need to use.
>
