---
title: Fixed asset allocation rules for Japan
description: Access answers some frequently asked questions about fixed asset allocation rules for Japan, including questions about dimension rules.
author: EricWangChen
ms.author: wangchen
ms.topic: article
ms.date: 12/08/2025
ms.reviewer: johnmichalak
audience: Application User 
ms.search.region: Japan
ms.search.validFrom: 2016-02-28
ms.search.form: AssetAllocationRuleSetup_CN
ms.dyn365.ops.version: AX 7.0.0
---

# Fixed asset allocation rules for Japan

[!include [banner](../../includes/banner.md)]

In Japan, an administrative department registers a fixed asset and allocates the depreciation amount among the usage departments. You can set up an allocation rule to allocate depreciation amounts to multiple financial dimensions by percentage. This article answers some frequently asked questions about the allocation rules for fixed assets.

You can set up an allocation rule to allocate depreciation costs for a fixed asset to a dimension of your legal entity. You can put fixed assets into service for multiple dimensions, such as departments or cost centers. When you depreciate a fixed asset, you post the depreciation cost to an offset account. By setting up an allocation rule, you can share the depreciation cost of the fixed asset between multiple dimensions of your legal entity.

## When I allocate depreciation costs, can the dimensions that are based on the allocation rule of the fixed asset model override the default dimensions in the journal header?

Yes. The dimensions that you specify in the allocation rule override the default dimensions that usually display in the journal header.

## What happens if I delete a dimension that is part of an allocation rule?

If you delete a financial dimension that is assigned to an allocation rule, you receive a message that states that the depreciation proposal can't be run. You must select another financial dimension for the allocation rule and run the depreciation proposal again.

## How does rounding the currency up or down affect the allocation rule?

After an allocation rule is applied to a fixed asset, the deprecation cost that is allocated to a legal entity dimension can be a whole amount or a fractional amount. If you set up rounding rules for your currency, the resulting allocated depreciation costs can be more than or less than the depreciation cost, in accordance with the allocation rule. Here are some examples that show how currency rounding can affect the allocation rule.

### Rounded-up currency

For this example, the depreciation cost amount of a fixed asset is 170 currency units. You set up an allocation rule to allocate 1 percent of the depreciation cost to each of the 100 dimensions of your legal entity. You also set up a rounding rule that indicates that fractional currency units that are more than halfway between two whole currency units are rounded up to the nearest whole currency unit. Here's how the depreciation cost per dimension is calculated in this scenario:

- Original depreciation cost per dimension = 1.70 currency units
- Rounded-up depreciation cost per dimension = 2.00 currency units
- Total rounded-up depreciation cost of the fixed asset = 2.00 × 100 = 200 currency units

### Rounded-down currency

In this example, the depreciation cost amount of a fixed asset is 120 currency units. You set up an allocation rule to allocate 1 percent of the depreciation cost to each of the 100 dimensions of your legal entity. You also set up a rounding rule that indicates that fractional currency units that are less than halfway between two whole currency units are rounded down to the nearest whole currency unit. Here's how the depreciation cost per dimension is calculated in this scenario:

- Original depreciation cost per dimension = 1.20 currency units
- Rounded-down depreciation cost per dimension = 1.00 currency units
- Total rounded-down depreciation cost of the fixed asset = 1.00 × 100 = 100 currency units

If the total rounded-down depreciation cost that you must allocate across each dimension is less than the rounding amount, the allocation rule isn't applied to the depreciation. Instead, the depreciation amount is either posted to the main account or offset by using the posting profile rules that you set up on the **Fixed asset posting profiles** page. To avoid these and similar scenarios, you can manually adjust the rounding rule for fixed asset depreciation on the **Currencies** page.

## Additional resources

- [Allocate carrying amount of shared asset and goodwill to cash generating units](allocate-carrying-amount.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
