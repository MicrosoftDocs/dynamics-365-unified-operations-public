---
title: Delay tolerance (negative days)
description: This topic provides information about the delay tolerance calculation and how it affects planned order creation in Planning Optimization.
author: crytt
ms.date: 07/30/2021
ms.topic: article
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: crytt
ms.search.validFrom: 2021-07-30
ms.dyn365.ops.version: 10.0.21
---

# Delay tolerance (negative days)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](../../includes/preview-banner.md)]

The delay tolerance feature enables Planning Optimization to consider the **Negative days** setting defined on coverage groups. The functionality is used to extend the delay tolerance period applied during master planning. This can be used to avoid creating new supply orders when existing supply can cover the demand with a small delay. The purpose is to determine whether it makes sense to create a new supply order for a given demand.

## Enable the delay tolerance feature on your system

To make delay tolerance functionality available on your system, go to [Feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) and turn on the *Negative days for Planning Optimization* feature.

## Delay tolerance in Planning Optimization

Delay tolerance represents the number of days that you are willing to wait, beyond the lead time, before you order new replenishment when you have existing supply planned. Delay tolerance is defined using calendar days, not business days.

At the time of master planning, when the system calculates the delay tolerance, it takes into account the **Negative days** setting. You can specify the **Negative days** value on the **Coverage groups** page or on the **Item coverage** page.

The system ties the delay tolerance calculation to the *earliest replenishment date*, which is *today's date* plus the *lead time*. The delay tolerance is calculated by using following formula: *max(Earliest Replenishment Date, Demand Due Date) – Demand Due Date + Negative Days*, where *max()* finds the larger of two values.

This formula ensures that master planning does not create new supply orders when sufficient supply exists within the product lead time.

> [!NOTE]
> The delay tolerance calculation in Planning Optimization uses the dynamic negative days calculation from built-in master planning.  This is done regardless of the **Use dynamic negative days** setting on the **Master planning parameters** page.

If the existing supply implies a demand delay that is less than or equal to the calculated delay tolerance, Planning Optimization will peg existing supply with the demand. In some cases, it is better to delay the demand than end up with oversupply.

The following subsections provide examples of how delay tolerance affects the creation of planned orders in Planning Optimization.

### Example 1

A product has the following configuration:

- **Lead time:** *10*
- **Negative days:** *2*

The following supply and demand exist for the product:

- **Demand for today:** A sales order for a quantity of 10
- **Supply in 12 days:** A purchase order for a quantity of 10

When master planning runs, no planned orders will be created because existing supply can cover the demand within 12 days, which is equal to the delay tolerance.

### Example 2

A product has the following configuration:

- **Lead time:** *10*
- **Negative days:** *0*

The following supply and demand exist for the product:

- **Demand for today:** A sales order for a quantity of 10
- **Supply in 12 days:** A purchase order for a quantity of 10

When master planning runs, a planned order for a quantity of 10 will be created because existing supply can only cover the demand after 12 days, while the delay tolerance is 10 days.

### Example 3

A product has the following configuration:

- **Lead time:** *10*
- **Negative days:** *2*

The following supply and demand exist for the product:

- **Demand in 11 days:** A sales order for a quantity of 10
- **Supply in 14 days:** A purchase order for a quantity of 10

When master planning runs, a planned order for a quantity of 10 will be created because existing supply can only cover the demand after three days, while the delay tolerance is two days. In this case, the demand date is after the product lead time and therefore isn't included in the delay tolerance. Hence, the delay tolerance only includes the negative days of two days.
