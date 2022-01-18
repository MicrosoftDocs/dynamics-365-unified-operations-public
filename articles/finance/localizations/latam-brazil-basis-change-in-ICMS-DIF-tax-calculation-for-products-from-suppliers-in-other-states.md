---
# required metadata

title: Basis change in ICMS-DIF tax calculation for products from suppliers in other states
description: This topic describes the configuration for ICMS-DIF tax type calculation are available when fiscal document is received in state Rio Grande do Sul (RS) or São Paulo (SP) in Brazil.
author: Kai-Cloud
ms.date: 1/17/2022
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

[!include [banner](../../includes/banner.md)]

This topic describes the configuration for ICMS-DIF tax type calculation when fiscal document is received in state Rio Grande do Sul (RS) or São Paulo (SP) in Brazil.

As per the state law definition, the ICMS to be collected in concept of differential % , must follows the following rule:

ICMS to collect = ( (Operation amount - ICMS from source ) / (1 - ICMS % internal) ) * ICMS % internal) - ICMS amount from source

## Scenario example

A Brazil company is located in RS state and receives a fiscal document (purchase) from a vendor located in SP state. As per law definition, this company must collect the different % of ICMS between RS state (18%) and SP interstate % (12%), but the base must be calculated in a different way as is mentioned above.

- Operation amount: R$ 1000,00
- ICMS interstate: R$ 120,00
- ICMS % in RS state : 18%
- ICMS to collect in RS state => (((1000 -120 ) / (1 - 0,18) ) * 0,18 ) - 120 = 73,17

## Resolution

In order to get the calculation of ICMS DIF as per RS state rules, the user must be able to setup sales tax codes and sales tax group as follows:

1. Create a sales tax code to receive the ICMS 12% (other state), this is the code used to register the tax receivable amount from the vendor.
2. Create a sales tax code to collect the ICMS DIF, with percentage amount of 18% (Own state, example RS) instead to define the difference between 18% - 12%. This sales tax code with tax type = ICMS-DIF must to be defined as follows in the calculation parameters:

- Origin: Select the option Percentage of gross amount.
- Marginal base: Net amount per line or Net amount of invoice balance
- Taxation code must be defined as fiscal value = 3, in order to create automatically the adjustment transaction when Fiscal Books module is enabled.
- Sales tax group configuration: Use tax must flagged for the ICMS-DIF sales tax code.



 [!INCLUDE [footer-include](../../../includes/footer-banner.md)]