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

This article provides information about how to add the tax and legal information that you can use to comply with company and fiscal legislation. The attributes you can configure in includes tax identification in different levels, taxpayer classification per country, and different customizable concepts that can be filed manually.
The fields for this information are located on the **LATAM** FastTab on the following pages:

  - **Legal entity**
  - **Customer**
  - **Vendor**
  - **Bank groups**
  - **Employee**
  - **Shipping carriers**

The field information is also availalbe on the **LATAM** tab, on the Action Pane, of the **Contact** page. 

## Prerequisites
To enable the **LATAM tax and legal** functionality, first enable the **LATAM Globalization** feature and one other country-specific feature.
Next, set the company address in a LATAM country where the globalization feature is enabled.	

## Set up the LATAM tax and legal information
1. Open one of the following pages that have the LATAM functionality enabled:

  - **Organization administration** > **Organizations** > **Legal entities**
  - **Accounts receivable** > **Customers** > **All customers**
  - **Accounts payable** > **Vendors** > **All vendors**
  - **Warehouse management** > **Setup** > Shipping > **Shipping carriers**
  - **Cash and bank management** > **Setup** > **Bank groups**
  - **Human resources** > **Workers** > **Employees**
  - **Sales and marketing** > **Relationships** > **Contacts** > **All contacts**

2. In the LATAM section, complete the following fields:

| Field                         | Description                                                                                                                                                                                     |
|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Customer/Vendor set           | Select a customer/vendor set that contains the document classes that will be used by the customer/vendor. This field is only available on customer and vendor pages. |
| Taxpayer type                 | Select the taxpayer type that matches the company classification.     |
| Based in Country              | Select the country where the company is located.         |
| Country document type         | Select the country tax ID types added to the country LATAM configuration that you selected in the **Based in Country** field.     |
| Country identification number | Enter the company Tax ID number.    |
| Jurisdiction registered       | Select a state or province.              |
| State document type           | Select the document types for the company added in the taxpayer configuration in a State/Province level.                |
| State identification number   | Enter the company Tax ID number for the State/Province.     |
| Activities start date         | Enter the company commercial activity start date. This date is usually stipulated in the company statute. This field is only available on the **Legal entities** page.     |

3. Enter any remaining necessary field information. 


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
