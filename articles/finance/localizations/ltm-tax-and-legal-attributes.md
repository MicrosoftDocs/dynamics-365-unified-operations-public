---
title: Tax and legal attributes for Latin America
description: This article provides information about the document class type configuration for Latin America. 
author: Fhernandez0088
ms.date: 08/30/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---

# Tax and legal attributes for Latin America

[!include [banner](../includes/banner.md)]

This article explains how to add the tax and legal information that you can use to comply with company and fiscal legislation. The attributes that you can configure include the tax identification at different levels, the taxpayer classification per country, and different customizable concepts that can be manually filled. The fields for this information are located on the **LATAM** FastTab of the following pages:

- **Legal entities**
- **Customer**
- **Vendor**
- **Bank groups**
- **Employee**
- **Shipping carriers**

The field information is also available on the **LATAM** tab on the Action Pane of the **Contact** page.

## Prerequisites

To enable the **LATAM tax and legal** functionality, first enable the **LATAM Globalization** feature and one other country-specific feature. Then set the company address in a Latin American (LATAM) country where the globalization feature is enabled.	

## Set up the LATAM tax and legal information

1. Open one of the pages where the LATAM functionality is enabled:

    - **Organization administration** \> **Organizations** \> **Legal entities**
    - **Accounts receivable** \> **Customers** \> **All customers**
    - **Accounts payable** \> **Vendors** \> **All vendors**
    - **Cash and bank management** \> **Setup** \> **Bank groups**
    - **Human resources** \> **Workers** \> **Employees**
    - **Warehouse management** \> **Setup** \> **Shipping** \> **Shipping carriers**
    - **Sales and marketing** \> **Relationships** \> **Contacts** \> **All contacts**

2. On the **LATAM** FastTab, set the following fields.

    | Field | Description |
    |-------|-------------|
    | **Customers set**/**Vendors set** | Select a customer or vendor set that contains the document classes that the customer or vendor will use. This field is available only on the **Customer** and **Vendor** pages. |
    | **Taxpayer type** | Select the taxpayer type that matches the company classification. |
    | **Based in country/region** or **Country/region** (depending on the page) | Select the country where the company is located. |
    | **Country document type** | Select the country tax ID types that have been added to the country LATAM configuration that you selected in the **Based in country/region** field. |
    | **Country identification number** | Enter the company's tax ID number. |
    | **Jurisdiction registered** or **State** (depending on the page) | Select a state or province. |
    | **State document type** | Select the document types for the company that have been added in the taxpayer configuration at the state/province level. |
    | **State identification number** | Enter the company's tax ID number for the state or province. |
    | **Activities start date** | Enter the company's commercial activity start date. This date is usually stipulated in the company statute. This field is available only on the **Legal entities** page. |

3. Enter any remaining field information that's required.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
