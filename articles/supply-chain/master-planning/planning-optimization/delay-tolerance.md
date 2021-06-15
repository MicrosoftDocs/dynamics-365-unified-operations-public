---
title: Delay tolerance (Negative days)
description: This topic provides information about delay tolerance calculation and how it affects planned orders creation in Planning Optimization.
author: crytt
ms.date: 6/15/2021
ms.topic: article
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: crytt
ms.search.validFrom: 2021-06-15
ms.dyn365.ops.version: AX 7.0.0
---

# Delay tolerance (Negative days)

[!include [banner](../../includes/banner.md)]

Delay tolerance feature enables Planning Optimization to consider the **Negative days** parameter defined on coverage groups. The functionality is used to extend delay tolerance period applied during master planning. This can be used to avoid creation of new supply orders, when existing supply can cover the demand with a small delay. Basically, the purpose is to determine if it makes sense to create a new supply order for a given demand.

## Enable delay tolerance feature

To make delay tolerance functionality available in your system, go to [Feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md), and turn on the *Negative days for Planning Optimization* feature.

## Delay tolerance in Planning Optimization

Delay tolerance represents the number of days that you are willing to wait, beyond the lead time, before you order new replenishment when you have existing supply planned. Delay tolerance is not tied to the working times calendars, it is number of calendar days.

At the time of master planning, when the system calculates the delay tolerance, it takes into account the **Negative days** parameter. You can specify the **Negative days** value on the **Coverage groups** page or **Item coverage** page.

The system ties the delay tolerance calculation to the *earliest replenishment date*, that is a sum of *Today’s date* and *Lead time*. The delay tolerance is calculated by using following formula: *max(Earliest replenishment date, Demand Due date) - Demand Due date + Negative days*, where *max* finds the larger of two values.

This formula ensures that master planning does not create new supply orders, when sufficient supply exists within the product lead time.

> [!NOTE]
> Delay tolerance calculation in Planning Optimization uses the dynamic negative days calculation from built-in master planning.  This is done regardless of the **Use dynamic negative days** setting on the **Master planning parameters** page.

If the existing supply implies the demand delay that is less or equal to the calculated delay tolerance, Planning Optimization will peg existing supply with the demand. In some cases, it is better to delay the demand than end up with oversupply.

Let us review how delay tolerance affects creation of planned orders in Planning Optimization.

### Example 1

A product has the following configuration:

- **Lead time:** *10* 
- **Negative days:** *2*

There is a demand for today: a sales order for a quantity of 10 of the product.  
There is a supply in 12 days: a purchase order for a quantity of 10 of the product.

When master planning runs, no planned orders are created because existing supply can cover the demand with delay of 12 days, that is equal to the delay tolerance.

### Example 2

A product has the following configuration:

- **Lead time:** *10* 
- **Negative days:** *0*

There is a demand for today: a sales order for a quantity of 10 of the product.  
There is a supply in 12 days: a purchase order for a quantity of 10 of the product.

When master planning runs, a planned order for a quantity of 10 is created, because existing supply can only cover the demand with delay of 12 days, while the delay tolerance is 10 days.

### Example 3
A product has the following configuration:

- **Lead time:** *10* 
- **Negative days:** *2*

There is a demand in 11 days: a sales order for a quantity of 10 of the product.  
There is a supply in 14 days: a purchase order for a quantity of 10 of the product.

When master planning runs, a planned order for a quantity of 10 is created because existing supply can only cover the demand with delay of three days, while the delay tolerance is two days. In this case the demand date is after the product lead time and therefore not included in the delay tolerance. Hence, the delays tolerance in this case only includes the negative days of two days.



