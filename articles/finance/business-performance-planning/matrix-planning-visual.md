---
title: Matrix planning visual performance considerations
description: Learn the capabilities, how to use and configure the Matrix planning visual in Business Performance Planning.
ms.author: romainpham
author: ShielaSogge
ms.author: twheeloc
ms.topic: article
ms.date: 12/07/2023
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-12-03
ms.search.form: 
ms.dyn365.ops.version:
---

# Matrix planning visual performance considerations

The **Matrix planning visual** in Business Performance Planning (BPP) provides interactive data entry and write-back capabilities directly in Power BI.  
Because the visual handles both data rendering and user interactions, performance can vary depending on report design, data model size, and configuration choices.

This article describes recommended practices to improve performance and responsiveness when using the Matrix planning visual.

---

## Optimize data loading

### Use a Filter Measure

Always include a **Filter Measure** when configuring the Matrix planning visual.  
Without a Filter Measure, Power BI can’t pass filter context to the visual. This forces the visual to retrieve **all data** from the dataset before applying filters, significantly increasing load times.

A Filter Measure ensures that only the relevant subset of data is retrieved from Dataverse before rendering.

> [!TIP]
> A simple Filter Measure (for example, `SUM(FactTable[Amount])`) is sufficient to enable Power BI to push filters efficiently.

---

## Manage subtotals and hierarchies

Each subtotal displayed in the visual is calculated on the fly.  
As the number of subtotals and hierarchical levels increases, the visual needs to perform more computations, which can slow rendering.

To optimize:
- Limit the number of subtotal levels (ideally 2–3).
- Avoid showing totals at every hierarchy level.
- Disable unused totals in the **Format** pane.

> [!NOTE]
> 50 records grouped under one parent load faster than the same 50 records spread across multiple parent lines.

---

## Conditional formatting and cell locking

Conditional formatting and cell lock rules are applied after data is loaded but before rendering completes.  
These features can increase rendering time, especially when applied to many measures or complex hierarchies.

To improve performance:
- Apply formatting selectively to key KPIs only.  
- Avoid combining multiple nested conditions or rules in the same column.  
- Use static color schemes where possible.

---

## Edit validation and comments

- **Edit validation** rules don’t impact initial rendering because they’re triggered only when users edit data.  
- **Comments** are retrieved through a separate service call in parallel with the data load, so they have minimal impact on render time.

Both features are optimized for interactive performance.

---

## Authentication and connectivity

Use **Microsoft Entra ID (Azure Active Directory)** authentication instead of API-based authentication for all BPP visuals.

With Entra ID authentication:
- Each visual uses the signed-in user’s Power BI credentials.  
- No additional API keys or user mappings are required.  
- Single sign-on (SSO) improves both security and performance, as visuals no longer need to reauthenticate on every refresh.

This configuration applies to both **Power BI Desktop** and **Power BI Service** environments.

---

## General optimization recommendations

To maximize performance of your Matrix planning reports:

- Keep cube design and data models **simple** — avoid unnecessary columns or unused relationships.  
- Avoid large **multi-select entries** that update thousands of rows at once.  
- Limit **conditional formatting** and **cell locks** to critical measures only.  
- Minimize use of **complex calculated measures** inside visuals.  
- Use **DirectQuery to Dataverse** for transactional scenarios that need near real-time results.  
- Use **Import mode** for high-volume planning datasets when frequent recalculation isn’t required.  
- Test on **production-sized datasets** to validate end-user experience before rollout.

---

## Troubleshooting tips

If users experience slow rendering or timeout issues:

| Symptom | Possible cause | Recommended action |
|----------|----------------|--------------------|
| Visual loads slowly | Missing Filter Measure | Add a Filter Measure to limit data scope. |
| Delayed edit response | Large data volume or complex validations | Reduce edit scope or simplify rules. |
| Frequent timeouts | Excessive subtotals or conditional formatting | Disable totals and simplify formatting logic. |
| UI freezing in edit mode | Too many concurrent cell locks or updates | Reduce concurrency and batch updates. |

---

## Related links

- [Matrix planning visual overview](matrix-planning.md)  
- [Graphical planning visual](graphical-planning.md)  
- [Write-back and allocation in BPP](write-back.md)

