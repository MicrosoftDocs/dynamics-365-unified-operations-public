---
title: Warehouse spatial location (preview)
description: Learn how to assign coordinates to warehouse locations to optimize picking routes and reduce travel time.
author: ismailjad
ms.author: ismailjad
ms.reviewer: kamaybac
ms.search.form: InventLocation, WMSLocation
ms.topic: conceptual
ms.date: 03/31/2026
ms.custom:
  - bap-template
---

# Warehouse spatial location (preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The warehouse spatial location feature lets you assign X, Y, and Z coordinates to warehouse locations. The system uses these coordinates to calculate optimized picking routes that minimize the travel distance that warehouse workers spend moving between locations during pick work.

When this feature is enabled, the **Sort picking work lines** wave processing step reorders the pick work lines within a work so that workers follow an efficient route through the warehouse. The step uses the assigned coordinates, your selected distance calculation strategy, and your selected sorting algorithm to determine the optimal order.

## Key concepts

- **Spatial coordinates** – The X, Y, and Z values that represent a location's physical position in the warehouse. The X and Y axes represent the horizontal position, and the Z axis represents the vertical position (for example, a rack level).
- **Pick work line** – A line in a work that instructs a worker to pick items from a specific warehouse location. A work typically contains multiple pick work lines followed by a put work line.
- **Put work line** – A line in a work that instructs a worker to place (put) the picked items at a destination location, such as a bay door or staging area.
- **Location sorting algorithm** – The algorithm that determines the order in which pick work lines are sorted. You can choose between a fast calculation or an optimized route. Both algorithms produce a route that starts at the farthest pick location and ends at the pick location nearest to the put location.
- **Distance calculation strategy** – The method that the system uses to calculate the distance between two locations. You can choose between a straight-line calculation or a city-block calculation. The choice affects the relative distances between locations, which in turn affects the sort order.
- **Coordinate retrieval strategy** – The method that the system uses to retrieve coordinate values for a location. Currently, the only available method retrieves the X, Y, and Z values directly from the location record.
- **Sort picking work lines** – A wave processing step that reorders pick work lines based on the spatial coordinates of the locations involved. This step only sorts pick lines that appear before the first put line in a work.

## How sorting works

When the **Sort picking work lines** step runs during wave processing, the system performs the following steps for each work:

1. **Identifies the first put line** in the work. This is the destination where the worker delivers the picked items.
1. **Collects all pick lines before the first put line.** Only these lines are sorted. Any lines after the first put (such as additional pick/put cycles in the same work) remain in their original positions.
1. **Validates the work.** The system checks that there are at least two pick lines to sort, that the put location has valid coordinates, and that at least one pick location has valid coordinates. If validation fails, the work is skipped and the pick lines remain in their original order.
1. **Calculates distances** between locations using the warehouse's configured distance calculation strategy.
1. **Sorts the pick lines** using the warehouse's configured sorting algorithm so that the farthest pick location is first and the nearest pick location (closest to the put location) is last.
1. **Renumbers the sorted pick lines** in the database so that the new order is preserved when the work is executed.

## Sorting algorithms

The **Location sorting algorithm** setting controls how the system determines the order of pick work lines. Both algorithms produce a route where the worker starts at the farthest pick location from the put location and finishes at the nearest pick location, so the last pick is close to the put destination.

### Fast calculation

The fast calculation algorithm uses a nearest-neighbor approach:

1. Starting at the put location, the system finds the closest unvisited pick location.
2. From that location, it finds the next closest unvisited pick location.
3. This continues until all pick locations have been visited.
4. The resulting route visits locations from nearest-to-farthest (relative to the put). The system then reverses the route so that the worker starts at the farthest location and ends at the nearest.

This algorithm is fast because it makes a single pass through the pick locations. However, because it always chooses the next closest location, it can produce routes with crossing paths when locations are spread across the warehouse in complex patterns.

**Best for:** Warehouses that need quick route calculation with good (but not always optimal) results. Works well when pick locations are spread evenly or arranged in lines.

### Optimized route

The optimized route algorithm starts with the same nearest-neighbor route as fast calculation, and then improves it:

1. The system builds the same initial route as fast calculation (steps 1-4 above).
2. It then repeatedly examines pairs of segments in the route and checks whether reversing the section between them produces a shorter total distance.
3. When a shorter route is found, the system applies the change and continues checking.
4. The process repeats until no further improvements are found or the maximum number of improvement passes is reached.

This additional optimization step can eliminate crossing paths and produce noticeably shorter routes, especially for complex pick patterns. The trade-off is slightly longer calculation time.

**Best for:** Warehouses where minimizing total travel distance is critical, especially when pick locations are clustered in groups or scattered in patterns where the nearest-neighbor approach produces crossing paths.

### When to choose each algorithm

- **Fast calculation** is recommended for most scenarios. It produces near-optimal routes with minimal processing time and is suitable for high-volume wave processing.
- **Optimized route** is recommended when pick locations are scattered across the warehouse in patterns where the nearest-neighbor approach might create inefficient crossing paths. The optimization adds processing time but can reduce travel distance for complex pick patterns.

### Example: Sorting algorithm comparison

Consider a warehouse with a put location (bay door) at coordinates (1, 1, 1) and five pick locations arranged in a pattern that challenges the nearest-neighbor approach:

| Location | X  | Y  | Z |
|----------|----|----|---|
| PICK-A   | 1  | 50 | 1 |
| PICK-B   | 50 | 1  | 1 |
| PICK-C   | 50 | 50 | 1 |
| PICK-D   | 25 | 25 | 1 |
| PICK-E   | 25 | 50 | 1 |

**Fast calculation result:** The nearest-neighbor approach starts at the put (1, 1, 1) and repeatedly selects the closest unvisited location. It then reverses the result. This can produce a route where the worker's path crosses itself, such as: PICK-C → PICK-A → PICK-E → PICK-B → PICK-D → Put.

**Optimized route result:** The algorithm starts with the same route, then detects that reversing certain segments eliminates crossing paths. The result is a loop-free route with shorter total distance, such as: PICK-C → PICK-B → PICK-D → PICK-E → PICK-A → Put.

> [!TIP]
> For warehouses with aisle-based layouts where pick locations fall along predictable lines (such as locations within the same aisle), fast calculation typically produces routes that are close to optimal. The optimized route algorithm provides the greatest benefit in open or irregularly laid-out warehouses where locations are scattered across multiple aisles and levels.

## Distance calculation strategies

The **Distance calculation strategy** setting controls how the system measures the distance between two locations. The sorting algorithm uses these distances to determine which pick locations are closer or farther from the put location and from each other. The choice of strategy should match your warehouse layout so that the calculated distances reflect the actual paths that workers follow.

### Straight line

The straight-line strategy calculates the direct (Euclidean) distance between two points. It assumes that workers can move freely in any direction between locations:

$distance = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2 + (\lvert z_2 \rvert + \lvert z_1 \rvert)^2}$

The horizontal component uses the difference in X and Y coordinates. The vertical component uses the sum of the absolute heights of both locations (explained in the [Vertical distance calculation](#vertical-distance-calculation) section).

**Best for:** Open warehouse layouts where workers can move diagonally, such as open floor areas or wide-aisle warehouses.

### City block

The city-block strategy calculates the distance along a grid-like path (also known as Manhattan distance). It assumes that workers must follow aisles and cannot cut diagonally:

$distance = \lvert x_2 - x_1 \rvert + \lvert y_2 - y_1 \rvert + \lvert z_2 \rvert + \lvert z_1 \rvert$

The horizontal component sums the absolute differences in X and Y separately, which means the distance reflects the path a worker takes along aisles (first walking along one axis, then the other). The vertical component uses the sum of the absolute heights of both locations (explained in the [Vertical distance calculation](#vertical-distance-calculation) section).

**Best for:** Warehouses with aisle-based layouts where workers must walk along aisles and turn corners rather than cutting across open space.

### Vertical distance calculation

Both strategies handle vertical movement (the Z axis) the same way: the system adds the absolute height of the starting location to the absolute height of the destination location.

For example, to move from shelf level 1 to shelf level 4, the vertical distance is
|1| + |4| = 5, not |4 - 1| = 3.

This approach models the real cost of vertical movement in a warehouse. A worker cannot move directly from one shelf level to another. Instead, the worker must climb down from the current level to the ground (costing the full height of that level) and then climb up to the target level (costing the full height of that level). For example, using a ladder or lift to descend from level 1 and then ascend to level 4 requires more effort than a simple height difference of 3 suggests.

> [!NOTE]
> Two locations at the same shelf level (for example, both at Z = 2) still have a vertical distance of |2| + |2| = 4, not 0. This reflects the fact that even on the same level, a worker must reach up to that shelf height at both the source and destination. If your warehouse has all locations on the ground level, set Z = 0 for all locations to eliminate the vertical component from distance calculations.

### Example: Distance calculation comparison

The following examples show how the two strategies calculate distance differently for the same pair of locations.

**Example 1: Two locations on the same level**

- Location A: (2, 3, 1)
- Location B: (8, 7, 1)

| Strategy      | Calculation                                                                        | Result   |
|---------------|------------------------------------------------------------------------------------|----------|
| Straight line | $\sqrt{(8-2)^2 + (7-3)^2 + (1+1)^2} = \sqrt{36 + 16 + 4}$                          | **7.48** |
| City block    | $\lvert 8-2 \rvert + \lvert 7-3 \rvert + \lvert 1 \rvert + \lvert 1 \rvert = 6 + 4 + 1 + 1$ | **12**   |

The straight-line distance (7.48) is shorter because it assumes the worker walks diagonally. The city-block distance (12) is larger because the worker must follow the aisle grid: 6 units along one axis, then 4 units along the other, plus the vertical component at both locations.

**Example 2: Two locations on different levels**

- Location A: (2, 3, 1)
- Location B: (2, 3, 4)

| Strategy      | Calculation                                                                         | Result |
|---------------|-------------------------------------------------------------------------------------|--------|
| Straight line | $\sqrt{(2-2)^2 + (3-3)^2 + (4+1)^2} = \sqrt{0 + 0 + 25}$                           | **5**  |
| City block    | $\lvert 2-2 \rvert + \lvert 3-3 \rvert + \lvert 4 \rvert + \lvert 1 \rvert = 0 + 0 + 4 + 1$ | **5**  |

When the locations differ only in shelf level, both strategies produce the same result (5 units) because vertical distance is calculated the same way in both: the worker climbs down from level 1 (1 unit) and climbs up to level 4 (4 units).

**Example 3: Diagonal movement across a warehouse**

- Location A: (1, 1, 1)
- Location B: (10, 10, 3)

| Strategy      | Calculation                                                                              | Result    |
|---------------|------------------------------------------------------------------------------------------|-----------|
| Straight line | $\sqrt{(10-1)^2 + (10-1)^2 + (3+1)^2} = \sqrt{81 + 81 + 16}$                       | **13.34** |
| City block    | $\lvert 10-1 \rvert + \lvert 10-1 \rvert + \lvert 3 \rvert + \lvert 1 \rvert = 9 + 9 + 3 + 1$ | **22**    |

The difference between the strategies is most pronounced when the worker must cover large horizontal distances. The straight-line distance (13.34) assumes a direct diagonal path, while the city-block distance (22) reflects walking 9 units in one direction, 9 units in another direction, and then handling the vertical change at both levels.

## Prerequisites

To use this feature, the following prerequisites must be met:

- The **Warehouse and Transportation management** configuration key must be enabled.
- The **Warehouse spatial location** feature must be enabled in the **Feature management** workspace.

> [!IMPORTANT]
> This feature is currently in preview. Preview features aren't meant for production use and might have limited functionality. These features are available before an official release so that customers can get early access and provide feedback.

## Enable the feature

To enable the warehouse spatial location feature, follow these steps.

1. Go to **System administration \> Workspaces \> Feature management**.
2. On the **All** tab, search for *Warehouse spatial location*.
3. Select the feature, and then select **Enable now**.

> [!NOTE]
> After the feature is enabled, you can disable it again if needed. However, any coordinate values and configuration that you've already entered will remain in the database.

## Related information

- [Set up warehouse spatial locations](set-up-warehouse-spatial-locations.md)
- [Feature management overview](/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview)
- [Wave processing](wave-processing.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
