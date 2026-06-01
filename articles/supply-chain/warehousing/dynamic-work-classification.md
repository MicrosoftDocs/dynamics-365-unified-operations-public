---
title: Dynamic work classification (production-ready preview)
description: Learn how to use Power Fx formulas to dynamically assign work pools, priorities, location directive codes, and work classes to warehouse work.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form: WHSWorkTemplateClassificationRule
ms.topic: how-to
ms.date: 05/08/2026
ms.custom:
  - bap-template
ms.collection:
  - ai-assisted
---

# Dynamic work classification (production-ready preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Warehouse managers often need different work pools, priorities, or bay door assignments depending on the carrier, shipping deadline, or type of items being picked. Without dynamic classification, each combination requires its own work template, which can lead to a large and complex configuration.

[!INCLUDE [production-ready-preview-dynamics365](~/../shared-content/shared/preview-includes/production-ready-preview-dynamics365.md)]

Dynamic work classification lets you use Power Fx formulas to determine these work parameters at runtime instead of configuring them statically on each work template. A single work template combined with a classification rule can replace many static templates, making your configuration simpler to maintain and more adaptable to changing business requirements.

Dynamic work classification provides two main capabilities:

- **Classification at work creation** – When warehouse work is created, the system evaluates a Power Fx formula to override the work pool, work priority, location directive codes, and work classes on the generated work. The formula can look up values from the work header and associated records, including the load, shipment, wave, and transportation appointment.
- **Reclassification after load changes** – If a load changes after work has been created (for example, the carrier is reassigned), the system can reevaluate the formula and update the associated work. Work can also be reevaluated on a schedule if the formula depends on the current date or time.

To start using dynamic work classification, you must configure how loads trigger reclassification, create one or more classification rules that contain your Power Fx formulas, and associate each rule with the work templates that should use it.

## Prerequisites

To use the feature described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.48 or later.
- The feature named *(Production Ready Preview) Dynamic work classification* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Configure work reclassification on load update

To control whether dynamic work classification rules can reclassify work when loads change, configure the **Work classification on load update** option. Work is only reclassified by rules that are explicitly set to **Reclassify work on load update**, so you can choose which rules should apply when a load changes. The system always classifies work at creation if a rule is associated with the work template, regardless of this setting.

To configure this setting, follow these steps:

1. Go to **Warehouse management** \> **Setup** \> **Warehouse management parameters**.
1. On the **General** tab, open the **Work** FastTab.
1. Set the **Work classification on load update** field to one of the following values:
    - *Disabled* – No action is performed when a load is updated.
    - *Synchronous* – All work associated with an updated load is reclassified immediately after the load is updated.

> [!NOTE]
> When using synchronous reclassification, the user might experience a brief wait during load updates while the system processes all associated work headers.

## Create dynamic work classification rules

Classification rules define the Power Fx formulas that determine how work should be classified. Each rule specifies which fields to override and the logic for calculating the new values.

To create a rule, follow these steps:

1. Go to **Warehouse management** \> **Setup** \> **Work** \> **Dynamic work classification rules**.
1. Select **New** to create a rule.
1. Make the following settings in the header of the new rule:
    - **Dynamic work classification rule** – Enter a name for the rule.
    - **Description** – Enter a short description for the rule.
    - **Rule scope** – Specify when the rule's formulas run during work creation and which data they can reference. The scope determines whether classification is applied only at the work header level or also at the initial work line level. Choose one of the following values:
        - *Work* – The formula runs once, after the work header is created. Use this scope when classification depends only on header-level properties such as the carrier or shipping time.
        - *Work and initial work lines* – The formula runs twice. First, as the initial pick work line is selected, the system evaluates a separate *initial work line formula* and applies overrides to that line. Then, after all initial work lines are collected, the system runs the main formula against the work header. Use this scope when classification depends on item-level properties such as the pick zone.

1. On the **Recalculation** FastTab, make the following settings to control how and when the rule is reevaluated if a load changes after the initial work creation:
    - **Reclassification schedule ID** – This setting is reserved for future use and has no effect in the current release.
    - **Reclassify work on load update** – Set this option to *Yes* to run the classification again each time a load associated with the work header changes. This setting ensures that any updates to the load are reflected in the work classification. This setting only applies if the **Work classification on load update** parameter is set to allow reclassification (see the previous section).

1. On the **Power Fx formula** FastTab, enter a formula that returns a record with the fields you want to override. See the next sections for details on writing formulas.
1. If the **Rule scope** is set to *Work and initial work lines*, the page includes a **Initial work line formula** FastTab. This formula runs when the first work line is assigned to a new work record. See the next sections for details on writing formulas.

> [!TIP]
>
> - Use the **Copy** button on the Action Pane to duplicate an existing rule as a starting point for a new one.
> - Use the **Preview** button to test a rule against an existing work header and see the results without making changes.
> - The **Work reclassification schedules** button is reserved for future use and has no effect in the current release.

## Write work classification formulas

On the **Power Fx formula** FastTab of each classification rule, enter a formula that returns a record with one or more of the following fields.

The following table describes the fields that a work classification formula can return.

| Field | Type | Description |
|---|---|---|
| `WorkPoolId` | String | Overrides the work pool on the created work. |
| `DefaultWorkPriority` | Number | Overrides the priority on the created work. |
| `DirectiveCodeOverrides` | Record | A record where each field name is a location directive code to replace and the value is the new directive code. Applies to all pick/put pairs. |
| `WorkClassOverrides` | Record | A record where each field name is a work class to replace and the value is the new work class. Applies only to the second and subsequent pick/put pairs. To change the work class of the first pick/put pair, use the initial work line formula instead. |

The following example shows a formula that returns all four fields.

```powerfx
{
    WorkPoolId: "PoolA",
    DefaultWorkPriority: 100,
    DirectiveCodeOverrides: {
        BAYDOOR: "BAYDOOR-C1",
        STAGING: "STAGING-C1"
    },
    WorkClassOverrides: {
        'Standard Class': "Express Class"
    }
}
```

> [!IMPORTANT]
> Returning `Blank()` for a field (or omitting it) preserves the original value from the work template. Returning an empty string (`""`) actively clears the value. For example, returning `Blank()` for `WorkPoolId` keeps whatever work pool was set on the work template, while returning `""` removes the work pool entirely.

### Available data objects for work formulas

The following table lists the objects that you can reference in a work classification formula.

| Object | Description |
|---|---|
| `workTable` | The work header that was generated. |
| `workTable.Load` | The load record associated with the work header. |
| `workTable.Shipment` | The shipment record associated with the work header. |
| `workTable.Wave` | The wave record associated with the work header. |
| `workTable.Appointment` | The first transportation management (TMS) appointment associated with the load. |

## Write initial work line formulas

If you set the **Rule scope** to *Work and initial work lines*, enter an additional formula on the **Initial work line formula** FastTab. This formula runs as the first pick work line is assigned to a new work record and can override the following fields.

| Field | Type | Description |
|---|---|---|
| `WorkPoolId` | String | Overrides the work pool on the created work header. |
| `WorkClassId` | String | Overrides the work class of the initial pick/put work lines. |

### Available data objects for initial work line formulas

The following table lists the objects that you can reference in an initial work line formula.

| Object | Description |
|---|---|
| `workLine` | The initial pick work line that was generated. |
| `workLine.InventTable` | The item master record for the item being picked. |
| `workLine.WHSInventTable` | The warehouse item settings for the item being picked. |
| `workLine.Load` | The load record associated with the work line. |
| `workLine.LoadLine` | The load line associated with the initial pick line. |
| `workLine.Shipment` | The shipment record associated with the work line. |

## Associate rules with work templates

After creating a classification rule, associate it with the work template that should use it. During work creation, the system evaluates the rule's formula and applies the returned overrides to the generated work.

Go to **Warehouse management** \> **Setup** \> **Work** \> **Work templates**, select a template, and set the **Dynamic work classification rule** field to the rule you want to use for that template.

> [!NOTE]
> When you use dynamic work classification with a work template, make sure the template's grouping settings align with your formula logic. For example, if your formula classifies work based on zone, the work template should group work creation by zone so that each work header contains lines from only one zone.

## Examples

The following examples illustrate common scenarios where dynamic work classification can simplify your configuration.

### Example 1: Set work pool and priority by carrier

A warehouse uses three carriers that pick up shipments at different times during the day. The warehouse manager wants to route each carrier's work to a separate work pool and assign higher priority to the earliest pickup.

Without dynamic classification, this setup requires three work templates. Each template filters on a different carrier code, each with its own work pool and priority settings.

With dynamic classification, a single work template and one rule handle all three carriers.

```powerfx
Switch(workTable.Load.CarrierCode,
    "Carrier1", {WorkPoolId: "Carrier1", DefaultWorkPriority: 100},
    "Carrier2", {WorkPoolId: "Carrier2", DefaultWorkPriority: 50},
    "Carrier3", {WorkPoolId: "Carrier3", DefaultWorkPriority: 10}
)
```

If you later reassign the load to a different carrier, the system can automatically reclassify the work when reclassification on load update is turned on.

### Example 2: Direct put-away to carrier-specific bay doors

Building on example 1, the warehouse manager also wants outbound put lines directed to different bay doors depending on the carrier. With static configuration, each work template needs a different location directive code.

With dynamic classification, you can add directive code overrides to the same formula.

```powerfx
Switch(workTable.Load.CarrierCode,
    "Carrier1", {
        WorkPoolId: "Carrier1",
        DefaultWorkPriority: 100,
        DirectiveCodeOverrides: {BAYDOOR: "BAYDOOR-C1"}
    },
    "Carrier2", {
        WorkPoolId: "Carrier2",
        DefaultWorkPriority: 50,
        DirectiveCodeOverrides: {BAYDOOR: "BAYDOOR-C2"}
    },
    "Carrier3", {
        WorkPoolId: "Carrier3",
        DefaultWorkPriority: 10,
        DirectiveCodeOverrides: {BAYDOOR: "BAYDOOR-C3"}
    }
)
```

### Example 3: Prioritize work by shipping deadline

Instead of classifying by carrier, this example prioritizes work based on how close the load is to its scheduled shipping time. Loads with earlier deadlines receive higher priority, ensuring workers pick the most time-sensitive orders first.

The following formula converts the scheduled shipping time into a numeric priority. A shipment scheduled for 9:00 AM becomes priority 900, while a 3:00 PM shipment becomes priority 1500.

```powerfx
{
    DefaultWorkPriority:
        If(Not(IsBlank(workTable.Load.LoadSchedShipUTCDateTime)),
            If(IsToday(workTable.Load.LoadSchedShipUTCDateTime),
                Hour(workTable.Load.LoadSchedShipUTCDateTime) * 100
                    + Minute(workTable.Load.LoadSchedShipUTCDateTime),
                3000),
            Blank())
}
```

The formula assigns a priority of 3000 to loads scheduled for a future day (beyond the maximum time-based priority of 2359) and returns `Blank()` for loads with no scheduled date, which preserves the work template's default priority.

An alternative approach calculates priority based on the number of minutes remaining until the shipping deadline.

```powerfx
{
    DefaultWorkPriority:
        If(Not(IsBlank(workTable.Load.LoadSchedShipUTCDateTime)),
            If(IsToday(workTable.Load.LoadSchedShipUTCDateTime),
                Max(0, DateDiff(Now(), workTable.Load.LoadSchedShipUTCDateTime,
                    TimeUnit.Minutes)),
                24 * 60),
            Blank())
}
```

> [!IMPORTANT]
> The time-remaining approach requires the reclassification batch job to run on a recurring schedule (for example, every hour) to keep priorities current. Depending on the number of open work headers, this requirement can add load to the system. The time-of-day approach (first formula) is more efficient because work only needs reclassification when the load's scheduled shipping time changes.

### Example 4: Classify work by pick zone

This example assigns a different work class to the initial pick/put pair based on the zone where items are picked. For example, picks from a freezer zone can be restricted to workers with appropriate cold-weather gear.

To use this approach, set the **Rule scope** to *Work and initial work lines* and configure the work template to group work by zone. This configuration ensures each work header contains lines from only one zone.

The initial work line formula concatenates a prefix with the zone ID to create a zone-specific work class.

```powerfx
{
    WorkClassId: Concatenate("S-", workLine.ZoneId)
}
```

Alternatively, you can set the work pool instead of the work class.

```powerfx
{
    WorkPoolId: Concatenate("S-", workLine.ZoneId)
}
```

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
