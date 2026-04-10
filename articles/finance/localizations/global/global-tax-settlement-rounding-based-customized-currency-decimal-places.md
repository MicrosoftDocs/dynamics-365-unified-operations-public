---
title: Tax settlement rounding based on customized currency decimal places
description: Learn how to do tax settlement rounding that is based on customized currency decimal places, including outlines on requirements and the background.
author: shtao
ms.author: johnmichalak
ms.topic: article
ms.date: 01/21/2026
ms.custom:
ms.reviewer: johnmichalak
audience: Application User
ms.search.region:
ms.search.validFrom:
ms.search.form: 
ms.dyn365.ops.version: AX 10.0.23
---

# Tax settlement rounding based on customized currency decimal places

[!include [banner](../../includes/banner.md)]

This article explains how to do tax settlement rounding that is based on customized currency decimal places.

## Requirements

Before you can use the **Tax settlement rounding based on the customized currency decimal places** feature, your version of Microsoft Dynamics 365 Finance must be at least 10.0.23.

## Background

Because of the high value of the currency in Gulf countries/regions, developers usually extend the **amount** data type to three, four, or even more decimal places. (For more information, see [Extending decimal point precision for selected data types](../../../fin-ops-core/dev-itpro/extensibility/decimal-point-precision.md).) The tax settlement functionality at **Tax \> Declarations \> Sales tax \> Settle and post sales tax** must use the same precision for rounding. If the tax settlement doesn't use the same rounding precision as the customized currency, the tax settlement loses the accuracy of the amount. This loss causes a voucher imbalance.

## Functionality

Enable this feature when you customize decimal places. For example, enable it if you extend the **amount** data type to three or more decimal places. Tax settlements can use the same rounding precision. You can set the **Round-off** field to the corresponding precision when you configure sales tax authorities in the **Tax** module.

:::image type="content" source="../media/tax-settle-tax-authority-round-off.png" alt-text="Screenshot of Round-off field set to three decimal places for a sales tax authority on the Sales tax authorities page.":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
