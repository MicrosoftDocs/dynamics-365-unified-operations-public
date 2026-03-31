---
title: Set up warehouse spatial locations (preview)
description: Learn how to assign coordinates to warehouse locations and configure sorting algorithms to optimize picking routes.
author: ismailjad
ms.author: ismailjad
ms.reviewer: kamaybac
ms.search.form: InventLocation, WMSLocation, WHSWaveTemplateTable, WHSWavePostMethodTaskConfig
ms.topic: how-to
ms.date: 03/31/2026
ms.custom:
  - bap-template
---

# Set up warehouse spatial locations (preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article explains how to assign coordinates to warehouse locations, configure the sorting algorithms that optimize picking routes, add the sorting step to wave processing, and configure batch processing for large-volume warehouses.

## Prerequisites

Before you set up warehouse spatial locations, the following prerequisites must be met:

- The **Warehouse spatial location** feature must be enabled in the **Feature management** workspace. For more information, see [Warehouse spatial location](warehouse-spatial-location.md).
- Warehouse locations must already be defined for your warehouse.

## Configure warehouse-level sorting settings

Before you assign coordinates to individual locations, configure the sorting algorithms and strategies at the warehouse level.

To configure warehouse-level spatial location settings, follow these steps.

1. Go to **Warehouse management \> Setup \> Warehouse \> Warehouses**.
1. Select the warehouse that you want to configure.
1. On the **Warehouse** FastTab, in the **Warehouse coordinates configuration** section, set the following fields.

### Distance calculation strategy

Select the method that the system uses to calculate the distance between two locations. The choice affects how distances are measured, which in turn affects the sort order of pick work lines. For more information about how each strategy calculates distance, see [Distance calculation strategies](warehouse-spatial-location.md#distance-calculation-strategies).

- **Straight Line** – Calculates the direct distance between two points, assuming the worker can move freely in any direction. Use this strategy for open warehouse layouts where workers can walk diagonally.
- **City Block** – Calculates the distance along a grid-like path (walking along one axis and then another), assuming the worker must follow aisles. Use this strategy for warehouses with aisle-based layouts where workers can't cut across aisles.

### Coordinate retrieval strategy

Select the method that the system uses to retrieve a location's coordinates.

- **Location coordinates** – Retrieves the X, Y, and Z coordinate values directly from the fields on the location record.

### Location sorting algorithm

Select the algorithm that the system uses to sort pick work lines. Both algorithms sort picks so that the worker starts at the farthest location from the put (destination) location and finishes at the nearest. For more information about how each algorithm works, see [Sorting algorithms](warehouse-spatial-location.md#sorting-algorithms).

- **Fast calculation** – Builds a route by repeatedly selecting the nearest unvisited location, then reverses it. Generates a route quickly and produces good results in most scenarios. Recommended for high-volume wave processing where calculation speed is the priority.
- **Optimized route** – Starts with the same route as fast calculation, then improves it by checking whether rearranging segments produces a shorter path. Recommended when minimizing travel distance is the priority. This option may take slightly longer to calculate but can produce noticeably shorter routes for complex pick patterns.

## Assign coordinates to warehouse locations

After you configure the warehouse-level settings, assign X, Y, and Z coordinates to each warehouse location. The system uses these coordinates to calculate distances between locations and determine the optimal pick route.

To assign coordinates to warehouse locations, follow these steps.

1. Go to **Warehouse management \> Setup \> Warehouse \> Locations**.
1. Select a location record.
1. Set the following fields.

- **X coordinate** – The position of the location along the X axis of the warehouse. This value typically represents the aisle or horizontal position.
- **Y coordinate** – The position of the location along the Y axis of the warehouse. This value typically represents the position within an aisle (depth).
- **Z coordinate** – The position of the location along the Z axis of the warehouse. This value typically represents the vertical level (for example, the shelf or rack level). Set this to 0 for ground-level locations to exclude vertical distance from calculations.

> [!TIP]
> Use a consistent coordinate system across all locations in a warehouse. For example, you might use the aisle number for X, the bay number for Y, and the shelf level for Z.

## Add the sort picking work lines step to a wave template

To use spatial location sorting during wave processing, add the **Sort picking work lines** step to your wave template.

To add the wave step, follow these steps.

1. Go to **Warehouse management \> Setup \> Waves \> Wave templates**.
1. Select the wave template that you want to modify.
1. On the **Methods** FastTab, find **Sort picking work lines** in the **Remaining methods** list.
1. Select the **Right arrow** button to move it to the **Selected methods** list.
1. Position the step after the work creation steps (such as **createWork**) and before the release step. The sort must run after work is created so that there are pick lines to sort.

> [!NOTE]
> The **Sort picking work lines** method only appears in the available methods list after the **Warehouse spatial location** feature is enabled in the **Feature management** workspace. If the method still doesn't appear, go to **Warehouse management \> Setup \> Waves \> Wave process methods**, and select **Regenerate methods**.

## Configure batch processing for sort picking work lines

By default, the **Sort picking work lines** step runs synchronously during wave processing. For high-volume warehouses, you can improve performance by configuring the step to run as parallel batch tasks. When batch processing is enabled, the system splits work across multiple parallel batch tasks, which can significantly reduce sorting time during wave processing.

To configure batch processing, follow these steps.

1. Go to **Warehouse management \> Setup \> Waves \> Wave process methods**.
1. Select the **sortPickingWorkLines** method in the list.
1. On the Action Pane, select **Task configuration**.
1. On the **Wave post method task configuration** page, select **New** to add a configuration row.
1. In the **Warehouse** field, select the warehouse that you want to configure batch processing for.
1. Set the following fields.

- **Maximum number of batch tasks** – The maximum number of parallel batch tasks that the system creates to process the sort step. The actual number of tasks is the lesser of this value and the number of works to sort. A higher value allows more parallel processing but uses more batch server capacity.
- **Wave processing batch group** – The batch group to use for the sorting batch tasks. If you leave this field blank, the system uses the default wave processing batch group that is configured in **Warehouse management parameters**.

> [!TIP]
> Start with a small number of batch tasks (for example, 2-4) and increase the value based on your wave volume and batch server capacity. Each batch task processes one work at a time from a shared queue, so the work is automatically distributed across available tasks.

> [!IMPORTANT]
> Batch processing is only used when a task configuration record exists for the warehouse. If no configuration is set up, the sort step runs synchronously during wave execution.

## Example scenario

This scenario shows how spatial location sorting reorders pick work lines to reduce travel distance, and how the distance calculation strategy affects the results.

### Set up

1. Configure a warehouse with the following settings:
   - **Distance calculation strategy**: *Straight Line*
   - **Coordinate retrieval strategy**: *Location coordinates*
   - **Location sorting algorithm**: *Fast calculation*

1. Create four pick locations with the following coordinates:

   | Location | X  | Y | Z | Description                              |
   |----------|----|---|---|------------------------------------------|
   | PICK-001 | 3  | 2 | 1 | Near the bay door, ground level          |
   | PICK-002 | 10 | 8 | 1 | Far side of warehouse, ground level      |
   | PICK-003 | 6  | 5 | 1 | Middle of warehouse, ground level        |
   | PICK-004 | 10 | 8 | 3 | Far side of warehouse, shelf level 3     |

1. Create a bay door (put) location at coordinates (1, 1, 1). This is where the worker delivers the picked items.

1. Add the **Sort picking work lines** step to the wave template, positioned after the
   work creation step.

### Process

1. Create a sales order that requires items from all four pick locations.
1. Process the wave. The system creates a work with four pick lines and one put line.
1. The **Sort picking work lines** step runs and reorders the pick lines.

### Result

**Before sorting**, the pick work lines are in the order the system created them, which doesn't consider location proximity:

| Line | Type | Location | Coordinates |
|------|------|----------|-------------|
| 1    | Pick | PICK-002 | (10, 8, 1)  |
| 2    | Pick | PICK-001 | (3, 2, 1)   |
| 3    | Pick | PICK-004 | (10, 8, 3)  |
| 4    | Pick | PICK-003 | (6, 5, 1)   |
| 5    | Put  | BAY-DOOR | (1, 1, 1)   |

With this order, the worker would zigzag across the warehouse: far side → near the door → far side again → middle → bay door.

**After sorting**, the system calculates the distance from the put location to each pick location and reorders the pick lines so the worker starts at the farthest location and works back toward the bay door:

**Distances from the put location (1, 1, 1) using straight-line strategy:**

| Location | Coordinates | Calculation                                                                                     | Distance from put |
|----------|-------------|-------------------------------------------------------------------------------------------------|-------------------|
| PICK-001 | (3, 2, 1)   | $\sqrt{(3-1)^2 + (2-1)^2 + (1+1)^2} = \sqrt{4 + 1 + 4}$              | 3.00              |
| PICK-003 | (6, 5, 1)   | $\sqrt{(6-1)^2 + (5-1)^2 + (1+1)^2} = \sqrt{25 + 16 + 4}$            | 6.71              |
| PICK-002 | (10, 8, 1)  | $\sqrt{(10-1)^2 + (8-1)^2 + (1+1)^2} = \sqrt{81 + 49 + 4}$           | 11.58             |
| PICK-004 | (10, 8, 3)  | $\sqrt{(10-1)^2 + (8-1)^2 + (3+1)^2} = \sqrt{81 + 49 + 16}$          | 12.08             |

The sorted work now looks like this:

| Line | Type | Location | Distance from put |
|------|------|----------|-------------------|
| 1    | Pick | PICK-004 | 12.08 (farthest)  |
| 2    | Pick | PICK-002 | 11.58             |
| 3    | Pick | PICK-003 | 6.71              |
| 4    | Pick | PICK-001 | 3.00 (nearest)    |
| 5    | Put  | BAY-DOOR | --                |

The worker now follows an efficient path: far shelf → far ground → middle → near the door → bay door. Each pick is closer to the destination than the previous one, eliminating the back-and-forth travel.

> [!NOTE]
> The put line (line 5) isn't moved by the sorting step. Only the pick lines before the first put are reordered. If the work contained additional pick/put cycles after the first put, those lines would also remain in their original positions.

### How the distance strategy changes the result

If you change the **Distance calculation strategy** to *City Block*, the distances are calculated differently. The city-block strategy assumes workers follow aisles instead of walking diagonally:

**Distances from the put location (1, 1, 1) using city-block strategy:**

| Location | Coordinates | Calculation                                                  | Distance from put |
|----------|-------------|--------------------------------------------------------------|-------------------|
| PICK-001 | (3, 2, 1)   | $\lvert 3-1 \rvert + \lvert 2-1 \rvert + \lvert 1 \rvert + \lvert 1 \rvert = 2 + 1 + 1 + 1$   | 5                 |
| PICK-003 | (6, 5, 1)   | $\lvert 6-1 \rvert + \lvert 5-1 \rvert + \lvert 1 \rvert + \lvert 1 \rvert = 5 + 4 + 1 + 1$   | 11                |
| PICK-002 | (10, 8, 1)  | $\lvert 10-1 \rvert + \lvert 8-1 \rvert + \lvert 1 \rvert + \lvert 1 \rvert = 9 + 7 + 1 + 1$  | 18                |
| PICK-004 | (10, 8, 3)  | $\lvert 10-1 \rvert + \lvert 8-1 \rvert + \lvert 3 \rvert + \lvert 1 \rvert = 9 + 7 + 3 + 1$  | 20                |

**Sorted pick order (farthest first):** PICK-004 → PICK-002 → PICK-003 → PICK-001 → Put

In this example, both strategies produce the same sorted order because the relative distances between locations are similar. However, the city-block distances are larger because they account for aisle-following movement. Notice that the gap between PICK-004 (distance 20) and PICK-002 (distance 18) is larger with city block than with straight line (12.08 vs 11.58). This is because the city-block strategy adds the full shelf height at both levels (level 3 + level 1 = 4) as a separate cost, whereas the straight-line strategy combines vertical and horizontal distance into a single direct measurement.

> [!TIP]
> The distance strategy doesn't always change the sorted order, but it can. When pick locations have similar horizontal positions but different shelf levels, the city-block strategy gives more weight to vertical distance, which can cause the sort order to differ from the straight-line strategy. Choose the strategy that best reflects how workers actually move through your warehouse.

## Related information

- [Warehouse spatial location](warehouse-spatial-location.md)
- [Wave processing](wave-processing.md)
- [Wave templates](wave-templates.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
