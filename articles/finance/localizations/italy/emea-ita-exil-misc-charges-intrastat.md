---
title: Miscellaneous charges per kilogram in an Intrastat declaration
description: Learn how to turn on, set up, and use the feature for miscellaneous charges per kilogram in an Intrastat declaration, including prerequisites.
author: mrolecki
ms.author: johnmichalak
ms.topic: article
ms.date: 12/16/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Italy
ms.search.validFrom: 2019-11-29
ms.search.form: 
ms.dyn365.ops.version: 10.0.8
---

# Miscellaneous charges per kilogram in an Intrastat declaration

[!include [banner](../../includes/banner.md)]

Intrastat is the system that collects information and generates statistics about the trade of goods among countries and regions in the European Union (EU). For more information, see [Intrastat overview](../europe/emea-intrastat.md).

Among other reporting elements, an Intrastat declaration contains information about miscellaneous charges. You usually calculate miscellaneous charges as a percentage of the invoice amount. However, in Italy, you often calculate them by multiplying the cost of each kilogram by the weight of goods in kilograms.

## Prerequisites

- The primary address of the legal entity is in Italy.
- In the **Feature management** workspace, turn on the **Miscellaneous charges per kilogram in Intrastat declaration** feature. For more information, see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Set up miscellaneous charges per kilogram

On the **Released products master data** page, on the **Foreign trade** FastTab, in the **Intrastat** section, in the **Charges per kilogram** field, enter the amount of the charges per kilogram.

:::image type="content" source="../media/emea-ita-exil-misc-charge-kg-pic1.jpg" alt-text="Screenshot of the Charges per kilogram field.":::

> [!NOTE]
> Verify that the product weight is defined in kilograms.

## Calculation of miscellaneous charges

When you transfer transactions to an Intrastat declaration, the system calculates the **Statistical charges amount** value by using the following formula:

*Statistical charges amount* = *Cost of each kilogram* × *Net weight (in kilograms)*

If you enter a **Charges percentage** value, the calculation uses both types of miscellaneous charges:

*Statistical charges amount* = (*Invoice amount* × *Charges percentage*) + (*Cost of each kilogram* × *Net weight [in kilograms]*)

:::image type="content" source="../media/emea-ita-exil-misc-charge-kg-pic2.jpg" alt-text="Screenshot of the charges calculation.":::

For more information, see [Transfer transactions to the Intrastat](../europe/transfer-transactions-intrastat.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
