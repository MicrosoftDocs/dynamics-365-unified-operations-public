---
title: Parameters not used by Planning Optimization
description: Learn about the parameters that Planning Optimization doesn't currently consider during its operation with an outline on the master planning parameters page.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: ReqParameters, ReqGroup, ReqItemTable, ReqPlanSched, EcoResProductDetailsExtended, InventItemOrderSetup, WorkCalendarTable, PdsDispositionMaster
ms.topic: concept-article
ms.date: 09/30/2025
ms.custom:
  - bap-template
---

# Parameters not used by Planning Optimization

[!include [banner](../../includes/banner.md)]

This article lists the parameters that Planning Optimization doesn't currently consider during its operation. The planning service might skip a parameter because, for example, it doesn't yet support related functionality. Alternatively, functional changes might make the parameter obsolete.

The following sections list the parameters that Planning Optimization doesn't use on specific pages. They also explain why each parameter isn't used.

## Master planning parameters page

Planning Optimization doesn't use the following parameters or options on the **Master planning parameters** page:

- **General** tab:

    - **Current forecast plan** – Planning Optimization doesn't consider this parameter. Instead, create a master plan that specifies a forecast model.
    - **Copy the complete and updated static master plan to the dynamic master plan** – Planning Optimization doesn't support this option. You can run each plan independently, but results aren't copied between them.
    - **Start time for calculated delays** – Planning Optimization doesn't support this option.
    - **Use dynamic negative days** – Planning Optimization always uses the *Dynamic negative days* approach.
    - **Today's date calendar** – Planning Optimization doesn't support this option. Planning Optimization always uses current time rounded to the next whole hour.
    - **Use of cache** – Planning Optimization doesn't consider this parameter because it manages performance and scaling.  
    - **Number of tasks in helper task bundle** – Planning Optimization doesn't consider this parameter because it manages performance and scaling.
    - **Pre-processing: Automatically filter by items with direct demand** – Planning Optimization doesn't support this option.  
    - **Post-processing: Automatically filter by items with direct demand** – Planning Optimization doesn't support this option.
    - **Number of threads** – Planning Optimization doesn't consider this parameter because it manages performance and scaling.
    - **Planning process timeout in minutes** – In Planning Optimization, there's a fixed timeout of 1 hour.
    - **Scheduling start time** – Planning Optimization doesn't consider this parameter. With Planning Optimization, an explosion run is a run of the plan for the selected items.

- **Planned orders** tab:

    - **Receipt time** – Planning Optimization doesn't support this option. The receipt time exactly matches the demand time in Planning Optimization.

- **Number sequences** tab:

    - **Master scheduling planned order number** – Planning Optimization uses its own number sequence, which you can't select, so it doesn't consider this parameter.

## Coverage groups page

Planning Optimization doesn't use the following parameters or options on the **Coverage groups** page:

- **Other** FastTab:

    - **Freeze time fence (days)** – Freeze time fence is supported in Supply Chain Management version 10.0.40 and later. To use it, turn on the feature named *Freeze time fence support for Planning Optimization* in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
    - **Forecast plan time fence** – Planning Optimization doesn't support forecast plans. Instead, create a master plan that specifies a forecast model.

- **Delays** FastTab:

    - **Calculated delays** – Planning Optimization doesn't consider this parameter because it always calculates delays for the coverage group.
    - **Calculate delays time fence (days)** – Planning Optimization doesn't consider this parameter because it calculates delays for the **Coverage time fence (days)**.

## Item coverage page

Planning Optimization doesn't use the following parameters or options on the **Item coverage** page:

- **General** tab:

    - **Planned order type** – Planning Optimization supports all order types, including kanban. To use kanban, enable the *(Preview) Lean manufacturing for Planning Optimization* feature in Feature management. This is a preview feature in Supply Chain Management version 10.0.45 and is generally available as of version 10.0.46.
    - **Freeze time fence (days)** – Freeze time fence is supported in Supply Chain Management version 10.0.40 and later. To use it, turn on the feature named *Freeze time fence support for Planning Optimization* in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
    - **Fulfill minimum** – Planning Optimization doesn't support the *Today's date*, *First issue*, and *Coverage time fence* options. It always uses the *Today's date + procurement time* option.
    - **Minimum periods** – Planning Optimization doesn't support this parameter.
    - **Planning formula** – Pending. To use this formula, enable *Planning items support for Planning Optimization* in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Master plans page

Planning Optimization doesn't use the following parameters or options on the **Master plans** page:

- **General** FastTab:

    - **Include continuity plan** – Planning Optimization doesn't support this parameter.
    - **Capacity time fence for bottleneck resources** – Planning Optimization doesn't support this parameter because customers didn't use it.
    - **Planned orders** – Planning Optimization uses fixed number sequences.
    - **Session** – Planning Optimization uses fixed number sequences.
    - **Continuity plan** – Planning Optimization doesn't support this parameter.

- **Time fences in days** FastTab:

    - **Freeze** – Freeze time fence is supported in Supply Chain Management version 10.0.40 and later. To use it, turn on the *Freeze time fence support for Planning Optimization* feature in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
    - **Forecast plan** – Planning Optimization doesn't support this parameter.
    - **Continuity plan** – Planning Optimization doesn't support this parameter.
    - **Calculated delays** – Planning Optimization doesn't consider this parameter. Calculated delays are created for the **coverage time fence (days)**.

- **Calculated delays** FastTab:

    - **Ensure that the planned orders are not created prior to the master planning run date** – Planning Optimization doesn't support this parameter. Planning Optimization never creates planned orders in the past.
    - **Add the calculated delay to the requirement date** (in the **Planned kanban** section) – To use kanban, enable the *(Preview) Lean manufacturing for Planning Optimization* feature in Feature management. This is a preview feature in Supply Chain Management version 10.0.45 and is generally available as of version 10.0.46.

- **Action message** FastTab:

    - **Update postponed date as requirement date** – Planning Optimization discontinued this parameter.

## Scheduling parameters page

Planning Optimization doesn't use the following parameters or options on the **Scheduling parameters** page:

- **Schedule timeout enabled** – In Planning Optimization, schedule timeout is always enabled.
- **Maximum scheduling time per sequence** – Planning Optimization doesn't support this parameter.
- **Schedule optimization timeout enabled** – Planning Optimization doesn't support this parameter.
- **Optimization attempts timeout** – Planning Optimization doesn't support this parameter.
- **Keep production unit** – Planning Optimization doesn't support this parameter.
- **Keep warehouse from resource** – Planning Optimization doesn't support this parameter.
