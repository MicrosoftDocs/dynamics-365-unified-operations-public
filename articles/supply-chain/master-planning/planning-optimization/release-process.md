---
title: Planning Optimization release process and release history
description: This article provides information about the release process and release history for Planning Optimization.
author: t-benebo
ms.date: 02/20/2023
ms.topic: article
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2021-07-28
ms.dyn365.ops.version: 10.0.31
---

# Planning Optimization release process and release history

[!include [banner](../../includes/banner.md)]

Microsoft updates Planning Optimization on a monthly basis. However, based on business requirements, we occasionally release other updates between the scheduled releases.

Each release is published to the individual regions where Planning Optimization is available. The process typically takes three days.

While Planning Optimization is being updated, master planning might run a bit more slowly than usual.

Environments that use Planning Optimization automatically receive the latest release. No user action is required: the service is automatically updated. However, no breaking-change functionality is ever automatically pushed to environments. By default, any changes that are considered breaking are turned off and must be explicitly turned on by using [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). Therefore, those changes won't appear in environments until you choose to enable them.

Because notifications aren't shown when Planning Optimization is updated in your environment, you can review the release notes in the following table to determine when changes were released and what functionality they introduced. This table shows the changes that were released for Planning Optimization, whether those changes are associated with a feature from feature management, and the date of the release.

| Changes | Feature management details | Release dates |
|---|---|---|
| <p>BOM lines with rounding or multiple setups.</p><p>BOM/formula lines with negative quantity.</p><p>General performance, quality and stability improvements.</p> | No feature management required | May 22–31, 2023 |
| <p>General performance, quality and stability improvements.</p> | No feature management required | May 4–8, 2023 |
| <p>Process manufacturing support for Planning Optimization. This includes support for creating planned batch orders for formula products, co-products, and by-products, formula lines with formula measurement, and formula versions with yield, but doesn't include support for planning items or item substitutions (plan groups).</p><p>General performance, quality and stability improvements.</p> | No feature management required | April 17–21, 2023 |
| <p>General performance, quality and stability improvements.</p> | No feature management required | March 27–30, 2023 |
| <p>General performance, quality and stability improvements.</p> | No feature management required | March 13–17, 2023 |
| <p>General performance, quality and stability improvements.</p> | No feature management required | February 15–24, 2023 |
| <p>[Bills of material with constant scrap or variable scrap defined](../scrap-calculations.md)</p><p>Demand with specific BOM or route requirements defined</p><p>Calculated delays: Add the calculated delay to the requirement date settings on master plans</p> | No feature management required | January 10–15, 2023 |
| <p>[Batch disposition codes](../../inventory/batch-disposition-codes.md)</p><p>Include on-hand inventory and inventory transaction parameters on master plans</p><p>Released production orders that aren't started, where scheduled start date is earlier than today</p><p>General performance, quality, and stability improvements</p> | No feature management required | October 10–14, 2022 |
| <p>[Resource scheduling with finite capacity](finite-capacity.md)</p><p>General performance, quality, and stability improvements</p> | No feature management required | September 19–23, 2022 |
| <p>[Master planning for products with limited shelf life](shelf-life.md)</p><p>General performance, quality, and stability improvements</p> | No feature management required | August 29 to September 3, 2022 |
| <p>[Centralized calendar maintenance](../supply-chain-calendars-master-planning.md)</p><p>[Suggestions to optimize existing supply](../action-messages.md)</p><p>[Support for subcontracting](../../production-control/manage-subcontract-work-production.md)</p><p>General performance, quality, and stability improvements</p> | No feature management required | March 7–11, 2022 |
| Planning priority support for production orders | Available with version 10.0.25 as part of the feature named *Priority driven MRP support for Planning Optimization*. | November 12–18, 2021 |
| General performance, quality, and stability improvements | No feature management required | November 12–18, 2021 |
| <p>Support for process time calculation formulas, production route with overlap, and production operation number on requirement transactions</p><p>Enhanced error messages for production scheduling related to timeout, capacity couldn't be found, and cyclic route</p><p>Improved consistency when calculating receipt dates and issue dates on both planned orders and firmed orders</p><p>General performance, quality, and stability improvements</p> | Feature name: *Infinite capacity scheduling for Planning Optimization* | October 22–27, 2021 |
| <p>Support for considering scrap percentage in processing time calculation</p><p>Support for operation number and materials usage during scheduling</p> | Feature name: *Infinite capacity scheduling for Planning Optimization* | October 5–7, 2021 |
| <p>Support for production route job types: **Queue before**, **Queue after**, and **Transport time**</p><p>General performance, quality, and stability improvements</p> | Feature name: *Infinite capacity scheduling for Planning Optimization* | September 25–30, 2021 |
| <p>Support for master plans with **Scheduling method** set to *Operations scheduling*</p><p>On the **Route groups** page, respect settings for the **Activation**, **Working time**, and **Capacity** check boxes for rows with a **Route/job type** of *Setup* or *Process* </p><p>General performance, quality, and stability improvements</p> | <p>Operations scheduling is available in feature management as of version 10.0.20</p><p>Feature name: *Infinite capacity scheduling for Planning Optimization*</p> | September  9–17, 2021 |
| General performance, quality, and stability improvements | No feature management required | August 25–30, 2021 |
| <p>Added **Lead time** field to planned orders.</p><p>General performance, quality, and stability improvements.</p> | No feature management required | August 12–17, 2021 |
| <p>Added resource type requirements for infinite capacity scheduling</p><p>Improved resource efficiency and calendar efficiency for infinite capacity scheduling</p><p>For more information, see [Scheduling with infinite capacity](infinite-capacity-planning.md)</p> | <p>Available in feature management as of version 10.0.20</p><p>Feature name: *Infinite capacity scheduling for Planning Optimization*</p> | July 6–12, 2021 |
| General quality improvements | No feature management required | July 6–12, 2021 |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
