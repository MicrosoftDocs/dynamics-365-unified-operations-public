---
title: Delay tolerance (negative days)
description: This article provides information about the delay tolerance calculation and how it affects planned order creation in Planning Optimization.
author: t-benebo
ms.date: 08/09/2022
ms.topic: article
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2021-07-30
ms.dyn365.ops.version: 10.0.21
---

# Delay tolerance (negative days)
<!-- KFM: Split topic into PO and classic -->

[!include [banner](../../includes/banner.md)]

The delay tolerance functionality enables Planning Optimization to consider the **Negative days** value that is set for coverage groups, item coverage, and/or master plans. It's used to extend the delay tolerance period that is applied during master planning. In this way, you can avoid creating new supply orders if existing supply will be able to cover the demand after a short delay. The purpose of the functionality is to determine whether it makes sense to create a new supply order for a given demand.

## Turn delay tolerance features on or off

To make the delay tolerance functionality available in your system, go to [Feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md), and turn on the following features:

- *Negative days for Planning Optimization* – This feature enables negative days settings for coverage groups and item coverage. As of Supply Chain Management version 10.0.29, the feature is mandatory and can't be turned off.
- *Make-to-order supply automation* – This feature enables negative days settings for master plans. (As of Supply Chain Management version 10.0.32, it's turned on by default. As of Supply Chain Management version 10.0.36, the feature is mandatory and can't be turned off.) For more information, see [Make-to-order supply automation](../make-to-order-supply-automation.md).

## Delay tolerance in Planning Optimization

Delay tolerance represents the number of days beyond the lead time that you're willing to wait before you order new replenishment when existing supply is already planned. Delay tolerance is defined by using calendar days, not business days.

At the time of master planning, when the system calculates the delay tolerance, it considers the **Negative days** setting. You can set the **Negative days** value on the **Coverage groups** page, the **Item coverage** page, or the **Master plans** page. If negative days are assigned at more than one level, the system applies the following hierarchy to decide which setting to use:

- If negative days are enabled on the **Master plans** page, that setting overrides all other negative days settings when the plan runs.
- If negative days are configured on the **Item coverage** page, that setting overrides the coverage group setting.
- Negative days that are configured on the **Coverage groups** page apply only if negative days haven't been configured for a relevant item or plan.

The system links the delay tolerance calculation to the *earliest replenishment date*, which equals today's date plus the lead time. The delay tolerance is calculated by using the following formula, where *max()* finds the larger of two values:

*max(Earliest replenishment date, Demand due date)* – *Demand due date* + *Negative days*

This formula ensures that master planning doesn't create new supply orders when enough supply exists during the product lead time.

> [!NOTE]
> The delay tolerance calculation in Planning Optimization always uses the dynamic negative days calculation from the deprecated master planning engine. The **Use dynamic negative days** setting on the **Master planning parameters** page has no effect on this behavior.

If the existing supply implies a demand delay that is less than or equal to the calculated delay tolerance, Planning Optimization pegs existing supply with the demand. In some cases, it's better to delay the demand than to end up with oversupply.

The following subsections provide examples that show how delay tolerance affects the creation of planned orders in Planning Optimization.

### Example 1

A product has the following configuration:

- **Lead time:** *10*
- **Negative days:** *2*

The following supply and demand exist for the product:

- **Demand for today:** A sales order for a quantity of 10
- **Supply in 12 days:** A purchase order for a quantity of 10

Existing supply can cover the demand within 12 days, and that period equals the delay tolerance. Therefore, when master planning runs, no planned orders are created.

### Example 2

A product has the following configuration:

- **Lead time:** *10*
- **Negative days:** *0*

The following supply and demand exist for the product:

- **Demand for today:** A sales order for a quantity of 10
- **Supply in 12 days:** A purchase order for a quantity of 10

Existing supply can cover the demand only after 12 days. However, the delay tolerance is 10 days. Therefore, when master planning runs, a planned order for a quantity of 10 is created.

### Example 3

A product has the following configuration:

- **Lead time:** *10*
- **Negative days:** *2*

The following supply and demand exist for the product:

- **Demand in 11 days:** A sales order for a quantity of 10
- **Supply in 14 days:** A purchase order for a quantity of 10

Existing supply can cover the demand only after three days. However, the delay tolerance is two days. (In this case, the delay tolerance includes only the two negative days. The demand date isn't included because it's after the product lead time.) Therefore, when master planning runs, a planned order for a quantity of 10 is created.
