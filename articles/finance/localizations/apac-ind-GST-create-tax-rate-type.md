---
# required metadata

title: Define a tax rate type and assign it to relevant master data  
description: This topic explains how to define the tax rate type and assign it to the relevant master data. 
author: yijialuan 
manager: kfend
ms.date: 02/24/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: riluan
ms.search.validFrom: 2019-10-01
ms.dyn365.ops.version: 10.0.5

---

# Define tax rate type

[!include [banner](../includes/banner.md)]

This topic provides information about how to define the tax rate type and assign it to the relevant master data. This task is part of the master data setup that is required to make the India localization solution for Goods and Services Tax (GST) available.

To make the India localization solution GST in Dynamics 365 Finance available, you must complete the following master data setup:

- Define a business vertical
- Update the state code and union territory
- Create a Goods and Services Tax Identification Number (GSTIN) master
- Define GSTINs for the legal entity, warehouse, vendor, or customer masters
- Define Harmonized System of Nomenclature (HSN) codes and Service Accounting Codes (SACs)
- Define tax rate type
- Create main accounts for the GST posting type
- Create a tax settlement period
- Attach the GSTIN to a tax registration group

## Tax rate type

In most taxation systems, there is the concept of a tax rate type, such as standard tax rate, reduced tax rate and super reduced tax rate. In India GST, there are following five types:

| Rates | Type      | Products                                                                                                                                                                                                      |
| ----- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 0%    | Nil       | Basic foods including fish, meat, dairy, vegetables, bread, and salt. Postal services. Books and newspapers. Accomodiation below Rs 999 per night.                                                          |
| 5%    | Low       | Household necessities such as consumable oil, sugar, spices, tea, and coffee (except instant) are included. Coal, Mmishti/mithai (Indian sweets), and life-saving drugs are also covered. |
| 12%   | Standard1 | This includes computers and processed food.                                                                                                                                                                    |
| 18%   | Standard2 | Hair oil, toothpaste and soaps, capital goods. and industrial intermediaries.                                                                                                        |
| 28%   | High      | Luxury items such as small cars, consumer durables like AC and refrigerators, premium cars, cigarettes, carbonated beverages, and high-end motorcycles.                                     |

## When to use tax rate type

It's not mandatory to set up the tax rate type. In the standard GST configuration, HSN/SAC is used to determne the GST rate. For users who maintain multiple [HSN/SAC](apac-ind-GST-hsn-service-accounting-codes.md), it's time consuming to complete [tax setup](apac-ind-GST-set-up-rate-percentage-tables.md), and it also takes longer for the tax engine to pick up the tax rate.

With the tax rate type, ideally the tax setup for the GST rate can be simplied into just a few records. There might a bit more records if you consider the scenarios of tax exemptation and reverse charge, but it is still much lesser than setting up rate by HSN/SAC.

| Tax rate type | Rate |
| ------------- | ---- |
| Nil           | 0%   |
| Low           | 5%   |
| Standard1     | 12%  |
| Standard2     | 18%  |
| High          | 28%  |

> [!NOTE]
> Using the tax rate type does not mean that you do not need to define HSN/SAC. This definition is still mandatory from the GSTR perspective. 

## Define a tax rate type

1. Go to **Product information management** \> **Products** \> **Released products**.
2. Select and open a released product and on the **General** fasttab, find the **Tax rate type** field.
4. Right-click the field and select **View details**.
5. Enter the name and description of the tax rate type you want to add.

![Define tax rate type](media/IND-define-tax-rate-type.png)

You can also import the tax rate type vby using its data entity, **Tax rate type**.

## Assign a tax rate type to relevant taxable master data

You can associate the tax rate type to the following taxable master data where it will all be supported by data entity.

- Released product
- Procurement/Sales categories
- Charge code
