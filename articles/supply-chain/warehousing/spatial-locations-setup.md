---
title: Set up warehouse spatial locations (preview)
description: Learn how to assign coordinates to warehouse locations and configure sorting algorithms to optimize picking routes.
author: ismailjad
ms.author: ismailjad
ms.reviewer: kamaybac
ms.search.form: InventLocation, WMSLocation, WHSWaveTemplateTable, WHSWavePostMethodTaskConfig
ms.topic: how-to
ms.date: 04/24/2026
ms.custom:
  - bap-template
---

# Set up warehouse spatial locations (preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: preview until further notice -->

Warehouse spatial location sorting optimizes picking routes by assigning X, Y, and Z coordinates to warehouse locations. You can configure the sorting algorithms, add the sorting step to wave processing, and set up batch processing for large-volume warehouses.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

To use warehouse spatial locations, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.48 or later.
- The feature named *Warehouse spatial location* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
- Warehouse locations must already be defined for your warehouse.

> [!NOTE]
> After you turn on the *Warehouse spatial location* feature, you can turn it off if needed. However, all coordinate values and configurations that you entered remain in the database.

## Configure warehouse-level sorting settings

Before you assign coordinates to individual locations, configure the sorting algorithms and strategies at the warehouse level.

To configure warehouse-level spatial location settings, follow these steps:

1. Go to **Warehouse management** \> **Setup** \> **Warehouse** \> **Warehouses**.
1. Select the warehouse that you want to configure.
1. On the **Warehouse** FastTab, in the **Warehouse coordinates configuration** section, make the following settings:

    - **Distance calculation strategy** – Select the method that the system uses to calculate the distance between two locations. The choice affects how distances are measured, which in turn affects the sort order of pick work lines. You can learn more about how each strategy calculates distance in [Distance calculation strategies](spatial-location-overview.md#distance-calculation-strategies). Choose one of the following options:
      - *Straight Line* – Calculates the direct distance between two points, assuming the worker can move freely in any direction. Use this strategy for open warehouse layouts where workers can walk diagonally.
      - *City Block* – Calculates the distance along a grid-like path (walking along one axis and then another), assuming the worker must follow aisles. Use this strategy for warehouses with aisle-based layouts where workers can't cut across aisles.
    - **Coordinate retrieval strategy** – Select the method that the system uses to retrieve a location's coordinates. Currently, only one setting is available and is selected by default:
        - *Location coordinates* – Retrieves the X, Y, and Z coordinate values directly from the fields on the location record.
    - **Location sorting algorithm** – Select the algorithm that the system uses to sort pick work lines. Both algorithms sort picks so that the worker starts at the farthest location from the put (destination) location and finishes at the nearest. You can learn more about how each algorithm works in [Sorting algorithms](spatial-location-overview.md#sorting-algorithms). Choose one of the following options:
        - *Fast calculation* – Builds a route by starting at the put location and repeatedly selecting the next nearest unvisited pick location, then reverses the result. Generates a route quickly and produces good results in most scenarios. Recommended for high-volume wave processing where calculation speed is the priority.
        - *Optimized route* – Starts with the same route as the fast calculation, then improves it by checking whether rearranging segments produces a shorter path. Recommended when minimizing travel distance is the priority. This option might take slightly longer to calculate but can produce noticeably shorter routes for complex pick patterns.

1. Repeat these steps for each warehouse where you want to use spatial location sorting. You can have different settings for different warehouses based on their layouts and operational priorities.

## Assign coordinates to warehouse locations

After you configure the warehouse-level settings, assign X, Y, and Z coordinates to each warehouse location. The system uses these coordinates to calculate distances between locations and determine the optimal pick route.

To assign coordinates to warehouse locations, follow these steps:

1. Go to **Warehouse management** \> **Setup** \> **Warehouse** \> **Locations**.
1. Select a location record.
1. Make the following settings:

    - **X coordinate** – Enter the position of the location along the X axis of the warehouse. This value typically represents the aisle or horizontal position.
    - **Y coordinate** – Enter the position of the location along the Y axis of the warehouse. This value typically represents the position within an aisle (depth).
    - **Z coordinate** – Enter the position of the location along the Z axis of the warehouse. This value typically represents the vertical level (for example, the shelf or rack level). Set this value to 0 for ground-level locations to exclude vertical distance from calculations.

1. Repeat these steps for each location in each warehouse where you want to use spatial location sorting.

> [!TIP]
> Use a consistent coordinate system across all locations in a warehouse. For example, you might use the aisle number for X, the bay number for Y, and the shelf level for Z.

## Add the *Sort picking work lines* step to your wave templates

To use spatial location sorting during wave processing, add the *Sort picking work lines* step to the relevant wave templates. Learn more about wave templates in [Wave templates](wave-templates.md).

To add the wave step, follow these steps:

1. Go to **Warehouse management** \> **Setup** \> **Waves** \> **Wave templates**.
1. Select the wave template that you want to modify.
1. On the **Methods** FastTab, in the **Remaining methods** list, find and select the method with **Name** *Sort picking work lines*.
1. Select the **Add** button (right arrow) to move it to the **Selected methods** list.
1. Use the **Move up** and **Move down** arrows to position the step after the work creation step (such as *Create work*) and before the release step (if there is one). The sort must run after work is created so that there are pick lines to sort.

> [!NOTE]
> The *Sort picking work lines* method only appears in the lists on the **Methods** FastTab after the *Warehouse spatial location* feature is turned on in **Feature management**. If the method still doesn't appear, go to **Warehouse management** \> **Setup** \> **Waves** \> **Wave process methods**, and select **Regenerate methods** from the Action Pane.

## Configure batch processing for *Sort picking work lines*

By default, the *Sort picking work lines* step runs synchronously during wave processing. For high-volume warehouses, you can improve performance by configuring the step to run as parallel batch tasks. When you enable batch processing, the system splits work across multiple parallel batch tasks, which can significantly reduce sorting time during wave processing.

To configure batch processing, follow these steps:

1. Go to **Warehouse management** \> **Setup** \> **Waves** \> **Wave process methods**.
1. Select the *sortPickingWorkLines* method in the list.
1. On the Action Pane, select **Task configuration**. The **Wave post method task configuration** page opens.
1. On the Action Pane, select **New** to add a configuration row.
1. In the **Warehouse** field, select the warehouse that you want to set up to use batch processing.
1. Make the following settings:

    - **Maximum number of batch tasks** – Enter the maximum number of parallel batch tasks that the system creates to process the sort step. The actual number of tasks is the lesser of this value and the number of work records to sort. A higher value allows more parallel processing but uses more batch server capacity.
    - **Wave processing batch group** – Enter the batch group to use for the sorting batch tasks. If you leave this field blank, the system uses the default wave processing batch group that you configure on the **Warehouse management parameters** page.

1. Repeat these steps for each warehouse where you want to use batch processing for the sort step.

> [!TIP]
> Start with a small number of batch tasks (for example, 2-4) and increase the value based on your wave volume and batch server capacity. Each batch task processes one work record at a time from a shared queue, so the work is automatically distributed across available tasks.

> [!IMPORTANT]
> The system uses batch processing only when a task configuration record exists for the warehouse. If you don't set up a configuration, the sort step runs synchronously during wave execution.

## Example scenario

This scenario shows how spatial location sorting reorders pick work lines to reduce travel distance, and how the distance calculation strategy affects the results.

### Set up the scenario

This scenario uses a warehouse with four pick locations and one bay door (put location). The pick locations are arranged so that without sorting, the worker would zigzag across the warehouse. After sorting, the pick lines are reordered so the worker starts at the farthest location and works back toward the bay door in a more efficient path.

To set up the scenario so you can run it, follow these steps to set up the warehouse and wave template:

1. Configure a warehouse with the following settings:
   - **Distance calculation strategy** – *Straight Line*
   - **Coordinate retrieval strategy** – *Location coordinates*
   - **Location sorting algorithm** – *Fast calculation*

1. Create four pick locations with the following coordinates:

   | Location | X  | Y | Z | Description                              |
   |----------|----|---|---|------------------------------------------|
   | PICK-001 | 3  | 2 | 1 | Near the bay door, ground level          |
   | PICK-002 | 10 | 8 | 1 | Far side of warehouse, ground level      |
   | PICK-003 | 6  | 5 | 1 | Middle of warehouse, ground level        |
   | PICK-004 | 10 | 8 | 3 | Far side of warehouse, shelf level 3     |

1. Create a bay door (put) location at coordinates (1, 1, 1). This location is where the worker delivers the picked items.

1. Add the *Sort picking work lines* step to the wave template, positioned after the
   work creation step.

### Run the scenario

To run the scenario, follow these steps:

1. Create a sales order that requires items from all four pick locations.
1. Process the wave. The system creates a work record with four pick lines and one put line.
1. The *Sort picking work lines* step runs and reorders the pick lines.

### Result

Before sorting, the pick work lines are in the order the system created them, which doesn't consider location proximity, as shown in the following table:

| Line | Type | Location | Coordinates |
|------|------|----------|-------------|
| 1    | Pick | PICK-002 | (10, 8, 1)  |
| 2    | Pick | PICK-001 | (3, 2, 1)   |
| 3    | Pick | PICK-004 | (10, 8, 3)  |
| 4    | Pick | PICK-003 | (6, 5, 1)   |
| 5    | Put  | BAY-DOOR | (1, 1, 1)   |

With this order, the worker would zigzag across the warehouse: *far side \> near the door \> far side again \> middle \> bay door*.

During sorting, the system calculates the distance from the put location to each pick location and reorders the pick lines so the worker starts at the farthest location and works back toward the bay door. The following table shows how the distances from the put location (1, 1, 1) are calculated using the *straight-line strategy*:

| Location | Coordinates | Calculation                                                 | Distance from put |
|----------|-------------|-------------------------------------------------------------|-------------------|
| PICK-001 | (3, 2, 1)   | $\sqrt{(3-1)^2 + (2-1)^2 + (1+1)^2} = \sqrt{4 + 1 + 4}$     | 3.00              |
| PICK-003 | (6, 5, 1)   | $\sqrt{(6-1)^2 + (5-1)^2 + (1+1)^2} = \sqrt{25 + 16 + 4}$   | 6.71              |
| PICK-002 | (10, 8, 1)  | $\sqrt{(10-1)^2 + (8-1)^2 + (1+1)^2} = \sqrt{81 + 49 + 4}$  | 11.58             |
| PICK-004 | (10, 8, 3)  | $\sqrt{(10-1)^2 + (8-1)^2 + (3+1)^2} = \sqrt{81 + 49 + 16}$ | 12.08             |

The sorted work now looks like this:

| Line | Type | Location | Distance from put |
|------|------|----------|-------------------|
| 1    | Pick | PICK-004 | 12.08 (farthest)  |
| 2    | Pick | PICK-002 | 11.58             |
| 3    | Pick | PICK-003 | 6.71              |
| 4    | Pick | PICK-001 | 3.00 (nearest)    |
| 5    | Put  | BAY-DOOR | --                |

The worker now follows an efficient path: *far shelf \> far ground \> middle \> near the door \> bay door*. Each pick is closer to the destination than the previous one, eliminating the back-and-forth travel.

> [!NOTE]
> The sorting step doesn't move the put line (line 5). It only reorders the pick lines before the first put. If the work contained additional pick and put cycles after the first put, those lines would also stay in their original positions.

### How the distance strategy changes the result

If you change the **Distance calculation strategy** to *City Block*, the system calculates distances differently. The city-block strategy assumes workers follow aisles instead of walking diagonally:

The following table shows how the city-block strategy calculates distances from the put location (1, 1, 1):

| Location | Coordinates | Calculation                                                                                  | Distance from put |
|----------|-------------|----------------------------------------------------------------------------------------------|-------------------|
| PICK-001 | (3, 2, 1)   | $\lvert 3-1 \rvert + \lvert 2-1 \rvert + \lvert 1 \rvert + \lvert 1 \rvert = 2 + 1 + 1 + 1$  | 5                 |
| PICK-003 | (6, 5, 1)   | $\lvert 6-1 \rvert + \lvert 5-1 \rvert + \lvert 1 \rvert + \lvert 1 \rvert = 5 + 4 + 1 + 1$  | 11                |
| PICK-002 | (10, 8, 1)  | $\lvert 10-1 \rvert + \lvert 8-1 \rvert + \lvert 1 \rvert + \lvert 1 \rvert = 9 + 7 + 1 + 1$ | 18                |
| PICK-004 | (10, 8, 3)  | $\lvert 10-1 \rvert + \lvert 8-1 \rvert + \lvert 3 \rvert + \lvert 1 \rvert = 9 + 7 + 3 + 1$ | 20                |

The sorted pick order (farthest first) is now:

| Line | Type | Location | Distance from put |
|------|------|----------|-------------------|
| 1    | Pick | PICK-004 | 20 (farthest)     |
| 2    | Pick | PICK-002 | 18                |
| 3    | Pick | PICK-003 | 11                |
| 4    | Pick | PICK-001 | 5 (nearest)       |
| 5    | Put  | BAY-DOOR | --                |

In this example, both strategies produce the same sorted order because the relative distances between locations are similar. However, the city-block distances are larger because they account for aisle-following movement. Notice that the gap between PICK-004 (distance 20) and PICK-002 (distance 18) is larger with city block than with straight line (12.08 vs 11.58). This difference exists because the city-block strategy adds the full shelf height at both levels (level 3 + level 1 = 4) as a separate cost, whereas the straight-line strategy combines vertical and horizontal distance into a single direct measurement.

> [!TIP]
> The distance strategy doesn't always change the sorted order, but it can. When pick locations have similar horizontal positions but different shelf levels, the city-block strategy gives more weight to vertical distance, which can cause the sort order to differ from the straight-line strategy. Choose the strategy that best reflects how workers actually move through your warehouse.

## Related information

- [Warehouse spatial location overview](spatial-location-overview.md)
- [Warehouse configuration overview](warehouse-configuration.md)
- [Wave processing](wave-processing.md)
- [Wave templates](wave-templates.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
