---
# required metadata

title: Define Tax Rate Type and assign it to relevant master data  
description: This topic explains how to define Tax Rate Type and assign it to the relevant master data. This task is part of the master data setup that is required to make the India localization solution for Goods and Services Tax (GST) available.
author: yijialuan 
manager: kfend
ms.date: 02/15/2020
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

To make the India localization solution for Goods and Services Tax (GST) in Microsoft Dynamics 365 Finance available, you must complete the following master data setup:

- Define a business vertical.
- Update the state code and union territory.
- Create a Goods and Services Tax Identification Number (GSTIN) master.
- Define GSTINs for the legal entity, warehouse, vendor, or customer masters.
- Define Harmonized System of Nomenclature (HSN) codes and Service Accounting Codes (SACs).
- Define Tax rate type
- Create main accounts for the GST posting type.
- Create a tax settlement period.
- Attach the GSTIN to a tax registration group.

## What is tax rate type

In most of the taxation systems, there is concept of tax rate type, like standard tax rate, reduced tax rate, super reduced tax rate, etc.. In India GST, there are following five slabs:

| Rates | Type      | Products                                                                                                                                                                                                      |
| ----- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 0%    | Nil       | Basic foods, including: fish, meat, dairy, vegetables, bread,   salt. Postal services. Books and newspapers. Accomodiation below Rs 999 per   night                                                           |
| 5%    | Low       | Household necessities such as edible   oil, sugar, spices, tea, and coffee (except instant) are included.   Coal , Mishti/Mithai (Indian Sweets) and Life-saving drugs are also covered   under this GST slab |
| 12%   | Standard1 | This includes computers and processed food                                                                                                                                                                    |
| 18%   | Standard2 | Hair oil, toothpaste and soaps, capital goods and industrial   intermediaries are covered in this slab                                                                                                        |
| 28%   | High      | Luxury items such as small cars , consumer durables like AC and   Refrigerators, premium cars, cigarettes and aerated drinks , High-end   motorcycles  are included here.                                     |

## When to use tax rate type

It's not mandatory to setup the Tax Rate Type. In the standard GST configuration, HSN/SAC is used to determne the GST rate. For users who maintain lots of [HSN/SAC](apac-ind-GST-hsn-service-accounting-codes.md), it's time consuming to do the [tax setup](apac-ind-GST-set-up-rate-percentage-tables.md), and it also takes longer time to for the tax engine to pick up the tax rate.

With the tax rate type, ideally the tax setup for the GST rate can be simplied into just a few records. There might a bit more records if consider the scenarios of tax exemptation, reverse charge, etc., but it is still much lesser than setting up rate rate by HSN/SAC.
| Tax Rate Type | Rate |
| ------------- | ---- |
| Nil           | 0%   |
| Low           | 5%   |
| Standard1     | 12%  |
| Standard2     | 18%  |
| High          | 28%  |

> [!NOTE]
> Use tax rate type does not mean you do not need to define HSN/SAC which is mandatory from GSTR perspective. 

## Define tax rate type

1. Go to **Product information management** \> **Products** \> **Released products**.
2. Open one released product.
3. In the **General** fasttab, find the Tax rate type.
4. Right click the arrow and click the context menu: **View details**.
5. Enter the name and description of the tax rate types you want to add.

![Define tax rate type](media/IND-define-tax-rate-type.png)

Users can also import the tax rate type via its data entity **Tax rate type**

## Assign tax rate type to relevant taxable master data

You can associate the Tax Rate Type to following taxable master data, and they are all supported by data entity.

- Released Product
- Procurement/Sales categories
- Charge code