---
title: Create a work class
description: Learn what work classes do in warehouse management and how to create one, including work order types and valid put location types.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ai-usage: ai-assisted
ms.search.form: WHSWorkClass
ms.topic: how-to
ms.date: 09/09/2026
ms.custom:
  - bap-template
---

# Create a work class

[!INCLUDE [banner](../../includes/banner.md)]

A work class directs and limits the type of work order lines that a warehouse worker can process on a mobile device. It can also validate the location where a worker puts items after picking them.

Work classes are a small setup entity, but they sit between several larger ones. Work templates assign a work class to each work line they create, mobile device menu items list the work classes that their workers are allowed to process, and the work class itself can restrict the put locations that those workers can use. A warehouse manager typically creates work classes.

## How work classes control work

A work class connects three parts of the warehouse configuration:

- **Work templates assign the class** – When a work template creates work, each work line receives the work class that is specified on the corresponding work template line.
- **Mobile device menu items filter by the class** – Each menu item lists the work classes that it can process. A worker sees a work line only when one of the menu items that they can reach lists that line's work class. This behavior is how you keep, for example, picking work and counting work in separate mobile device flows.
- **The class can validate put locations** – If you list one or more valid put location types on the work class, a worker who processes a *Put* line for that class can put the items only in a location whose location profile uses one of those location types. If the worker enters another location, or a location directive resolves to one, the operation fails with the message "Location type is invalid."

The last point has an important default. If you don't list any valid put location types, no put location restriction applies at all. The restriction takes effect only after you add at least one location type, and adding one immediately excludes every type that you don't list.

The work order type that you select also has a consequence beyond categorization. When you select a work class elsewhere in the system, the lookup is filtered by work order type. A work class therefore appears only where its work order type matches, so a class that has the wrong work order type silently never appears in the list that you expect.

## Prerequisites

Before you begin, ensure that you meet the following prerequisites:

- The warehouse is enabled for warehouse management processes.
- If you plan to restrict put locations, the location types that you want to use already exist. You can create them at **Warehouse management** > **Setup** > **Warehouse** > **Location types**. Location types are assigned to locations through location profiles.

## Create a work class

To create a work class, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Work** > **Work classes**.
1. On the Action Pane, select **New**.
1. Set the following fields:
    - **Work class ID** – Enter a unique identifier for the work class. If you enter an identifier that already exists, you receive the message "A work class with the same Id already exists."
    - **Description** – Enter a description that explains what the work class is used for.
    - **Work order type** – Select the type of work that this class applies to, such as *Sales orders*, *Purchase orders*, or *Cycle counting*. Select the value carefully, because it determines where the work class can later be selected.

1. On the Action Pane, select **Save**.

## Restrict the put locations for the work class

This step is optional. Complete it when workers who process this class must put items only in specific kinds of locations, such as a bay door or a staging area. To restrict the put locations, follow these steps:

1. On the **Valid put location types** FastTab toolbar, select **New**.
1. In the **Location type** field, select a location type.
1. Repeat the previous two steps for each additional location type that you want to allow.
1. On the Action Pane, select **Save**.

> [!NOTE]
> The restriction applies to *Put* work lines only, and it's enforced both when a warehouse worker enters a location manually on a mobile device and when a location directive resolves the location. Leave the FastTab empty if you don't want any restriction.

## Related information

- [Create and configure mobile device menu items](../configure-mobile-devices-warehouse.md)
- [Control warehouse work by using work templates and location directives](../control-warehouse-location-directives.md)
- [Dynamic work classification](../dynamic-work-classification.md)
- [Work policies](../warehouse-work-policies.md)
- [Movement of inventory with associated work in Warehouse management](../move-inventory-associated-work.md)
