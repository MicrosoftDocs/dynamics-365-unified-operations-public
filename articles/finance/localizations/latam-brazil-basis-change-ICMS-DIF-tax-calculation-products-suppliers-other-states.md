---
# required metadata

title: Basis change in ICMS-DIF tax calculation for products from suppliers in other states
description: This topic describes the configuration for ICMS-DIF tax type calculations when a fiscal document is received in the Brazilian state of Rio Grande do Sul (RS) or São Paulo (SP).
author: Kai-Cloud
ms.date: 1/20/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:
audience: Application user
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: kailiang
ms.search.validFrom: 2022-1-17
ms.dyn365.ops.version: 10.0.26
---

# Basis change in ICMS-DIF tax calculation for products from suppliers in other states

This topic describes the configuration for ICMS-DIF tax type calculation when a fiscal document is received in the state of Rio Grande do Sul (RS) or São Paulo (SP) in Brazil.

Per the state law definition, the ICMS to be collected must follow the rule:

ICMS to collect = (((Operation amount - ICMS from source ) / (1 - ICMS % internal) ) * ICMS % internal) - ICMS amount from source

## Example

A Brazilian company is located in the RS state and receives a fiscal document for purchase from a vendor located in the SP state. The company must collect the percentage difference of ICMS between RS, which is 18% and SP, which is 12%. However, the base must be calculated as mentioned in the previous calculation.

- Operation amount: R$ 1000.00
- ICMS interstate: R$ 120.00
- ICMS % in RS state: 18%
- ICMS to collect in RS state = (((1000 -120 ) / (1 - 0.18) ) * 0.18 ) - 120 = 73.17

## Resolution

To get the calculation of ICMS DIF following the RS state rules, sales tax codes and a sales tax group must be set up as follows.

1. Create a sales tax code to receive the ICMS 12% (other state). This is the code used to register the tax receivable amount from the vendor.
2. Create a sales tax code to collect the ICMS DIF, with a percentage amount of 18% (your own state) to define the difference between 18% - 12%. This sales tax code with tax type equal to **ICMS-DIF** must to be defined as follows in the calculation parameters:

- Origin: Select the option **Percentage of gross amount**.
- Marginal base: Net amount per line or Net amount of invoice balance
- The taxation code must be defined with a fiscal value of 3 to automatically create the adjustment transaction when the **Fiscal books** module is enabled.
- Sales tax group configuration: Use tax must be flagged for the ICMS-DIF sales tax code.
