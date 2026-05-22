---
title: Basis change in ICMS-DIF tax calculations for products from suppliers in other states
description: Learn about the configuration for calculations of the ICMS-DIF tax type when a fiscal document is received in the Brazilian state of Rio Grande do Sul or São Paulo.
author: Kai-Cloud
ms.author: kailiang
ms.topic: how-to
ms.date: 03/05/2026
ms.custom:
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2022-1-17
---

# Basis change (dual base) in ICMS-DIF tax calculations for products from suppliers in other states

This article describes the configuration for calculations of the **ICMS-DIF** tax type when you receive a fiscal document in the Brazilian state of Rio Grande do Sul (RS) or São Paulo (SP).

According to the definition in the state law, the Imposto sobre Circulação de Mercadorias e Serviços (ICMS) that you collect must follow this rule:

*ICMS to collect* = ([(*Operation amount* – *ICMS from source*) ÷ (1 – *ICMS % internal*)] × *ICMS % internal*) – *ICMS amount from source*

## Example

A Brazilian company in the RS state receives a fiscal document for a purchase from a vendor in the SP state. The company must collect the percentage difference of ICMS between the RS state (18 percent) and the SP state (12 percent). However, the base must be calculated according to the preceding rule.

- **Operation amount:** 1,000.00 Brazilian reals (R$ 1,000.00)
- **ICMS interstate:** R$ 120.00
- **ICMS percentage in the RS state:** 18 percent
- **ICMS to collect in the RS state:** (\[(1,000 – 120) ÷ (1 – 0.18)\] × 0.18 ) – 120 = R$ 73.17 

## Resolution

To calculate differential ICMS (ICMS-DIF) according to the rules of the RS state, set up sales tax codes and a sales tax group in the following way:

1. Create a sales tax code to receive the 12-percent ICMS (for the other state). Use this code to register the tax receivable amount from the vendor.
1. Create a sales tax code to collect the ICMS-DIF. This sales tax code should have a percentage amount of 18 percent (for your own state) to define the difference between 18 percent and 12 percent. Set the tax type to **ICMS-DIF**. Define this sales tax code in the following way in the calculation parameters:

    - In the **Origin** field, select **Percentage of gross amount**.
    - In the **Marginal base** field, select **Net amount per line**.
    - Define the taxation code so that it has a fiscal value of **3**. By using this value, the adjustment transaction is automatically created when you enable the **Fiscal books** module.
    - In the configuration of the sales tax group, select the **Use tax** option for the **ICMS-DIF** sales tax code.

### Use the delta tax rate in the configuration of dual-base ICMS-DIF sales tax codes

When you use the previously described settings, the system calculates the **ICMS-DIF** sales tax code using the dual base rule. However, the nominal tax rate is 18 percent, which differs from the 6-percent rate in the simple base rule. This difference causes inconsistency problems in fiscal document and tax reporting. As of Microsoft Dynamics 365 Finance version 10.0.29, you can enable the **(Brazil) Configure the delta tax rate in ICMS-DIF tax code for the dual base case** feature in **Feature management** to remove the inconsistency.

- In addition to completing the steps in the previous section, select the **ICMS 12** sales tax code in the **Sales tax on sales tax** field.
- Set the tax rate of the **ICMS-DIF** sales tax code to 18 percent. The **Percentage/Amount** field shows the nominal tax rate as 6 percent.

> [!NOTE]
> You must assign the **ICMS-DIF** and **ICMS 12** sales tax codes in the same sales tax group.

## Basis change (dual base) in ICMS-DIF tax calculations for products to non-taxpayer consumers (DIFAL) in other states

Enable the **(Brazil) Dual base calculation for ICMS-DIFAL in sales transactions** feature in **Feature management** to support the basis-change ICMS-DIF on trading to non-taxpayer consumers from another state. The sample ICMS-DIF sales tax code becomes effective in sales order and free text invoice transactions.

Enable the **(Brazil) Dual base calculation for ICMS-DIFAL for IPI cases** feature in **Feature management** to support scenarios where trading to non-taxpayer consumers from another state is also liable for Imposto sobre Produtos Industrializados (IPI). The system recognizes and applies the tax amount of the IPI sales tax code in the ICMS-DIFAL tax base.

- On the header of the sales order or free text invoice, set the **Final user** option to **Yes** on the **Fiscal information** FastTab.
- On the header of the purchase order or vendor invoice, set the **Use and consumption** option to **Yes** on the **Fiscal information** FastTab.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]