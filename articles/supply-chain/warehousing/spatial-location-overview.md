---
title: Warehouse spatial location overview (preview)
description: Learn how to assign coordinates to warehouse locations to optimize picking routes and reduce travel time.
author: ismailjad
ms.author: ismailjad
ms.reviewer: kamaybac
ms.search.form: InventLocation, WMSLocation
ms.topic: conceptual
ms.date: 04/24/2026
ms.custom:
  - bap-template
---

# Warehouse spatial location overview (preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: preview until further notice -->

The *warehouse spatial location* feature lets you assign X, Y, and Z coordinates to warehouse locations. The system uses these coordinates to calculate optimized picking routes that minimize the travel distance required for warehouse workers to move between locations during pick work. When you use this feature, the *Sort picking work lines* wave processing step reorders the pick work lines within a work record so that workers follow an efficient route through the warehouse. The step uses the assigned coordinates, your selected distance calculation strategy, and your selected sorting algorithm to determine the optimal order.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Key concepts

The *warehouse spatial location* feature employs the following key concepts:

- **Spatial coordinates** – The X, Y, and Z values that represent a location's physical position in the warehouse. The X and Y axes represent the horizontal position, and the Z axis represents the vertical position (for example, a rack level).
- **Pick work line** – A line in a work that instructs a worker to pick items from a specific warehouse location. A work record typically contains multiple pick work lines followed by a put work line.
- **Put work line** – A line in a work record that instructs a worker to place (put) the picked items at a destination location, such as a bay door or staging area.
- **Location sorting algorithm** – The algorithm that determines the order in which pick work lines are sorted. You can choose between a fast calculation or an optimized route. Both algorithms produce a route that starts at the farthest pick location and ends at the pick location nearest to the put location.
- **Distance calculation strategy** – The method that the system uses to calculate the distance between two locations. You can choose between a straight-line calculation or a city-block calculation. The choice affects the relative distances between locations, which in turn affects the sort order.
- **Coordinate retrieval strategy** – The method that the system uses to retrieve coordinate values for a location. Currently, the only available method retrieves the X, Y, and Z values directly from the location record.
- **Sort picking work lines** – A wave processing step that reorders pick work lines based on the spatial coordinates of the locations involved. This step only sorts pick lines that appear before the first put line in a work.

## How sorting works

When the *Sort picking work lines* step runs during wave processing, the system performs the following steps for each work record:

1. *Identify the first put line in the work.* This line is the destination where the worker delivers the picked items.
1. *Collect all pick lines before the first put line.* The system sorts only these lines. Any lines after the first put line (such as additional pick and put cycles in the same work) remain in their original positions.
1. *Validate the work.* The system checks that there are at least two pick lines to sort, that the put location has valid coordinates, and that at least one pick location has valid coordinates. If validation fails, the system skips the work and keeps the pick lines in their original order.
1. *Calculate distances between locations* by using the warehouse's configured distance calculation strategy.
1. *Sort the pick lines* by using the warehouse's configured sorting algorithm so that the farthest pick location is first and the nearest pick location (closest to the put location) is last.
1. *Renumber the sorted pick lines* in the database so that the new order is preserved when the work is done.

## Sorting algorithms

The *location sorting algorithm* controls how the system determines the order of pick work lines. Both algorithms produce a route where the worker starts at the farthest pick location from the put location and finishes at the nearest pick location, so the last pick is close to the put destination.

### Fast calculation algorithm

The *fast calculation algorithm* works best for warehouses that need quick route calculation with good (but not always optimal) results. It works well when pick locations are spread evenly or arranged in lines. It uses a nearest-neighbor approach:

1. Starting at the put location, the system finds the closest unvisited pick location.
1. From that location, it finds the next closest unvisited pick location.
1. This process continues until all pick locations are visited.
1. The resulting route visits locations from nearest-to-farthest (relative to the put). The system then reverses the route so that the worker starts at the farthest location and ends at the nearest.

This algorithm is fast because it makes a single pass through the pick locations. However, because it always chooses the next closest location, it can produce routes with crossing paths when locations are spread across the warehouse in complex patterns.

### Optimized route algorithm

The *optimized route algorithm* works best in warehouses where minimizing total travel distance is critical. This algorithm is especially useful when pick locations are clustered in groups or scattered in patterns where the nearest-neighbor approach produces crossing paths. It starts with the same nearest-neighbor route as fast calculation, and then improves it:

1. The system builds the same initial route as fast calculation (as described in the previous section).
1. It repeatedly examines pairs of segments in the route and checks whether reversing the section between them produces a shorter total distance.
1. When it finds a shorter route, the system applies the change and continues checking.
1. The process repeats until no further improvements are found or the maximum number of improvement passes is reached.

The additional optimization step can eliminate crossing paths and produce noticeably shorter routes, especially for complex pick patterns. The trade-off is slightly longer calculation time.

### When to choose each algorithm

Use the following guidelines to choose the best algorithm for your warehouse:

- *Fast calculation* is best for most scenarios. It produces near-optimal routes with minimal processing time and is suitable for high-volume wave processing.
- *Optimized route* is best when pick locations are scattered across the warehouse in patterns where the nearest-neighbor approach might create inefficient crossing paths. The optimization adds processing time but can reduce travel distance for complex pick patterns.

### Example: Sorting algorithm comparison

Consider a warehouse with a put location (bay door) at coordinates (1, 1, 1) and five pick locations arranged in a pattern that challenges the nearest-neighbor approach:

| Location | X | Y | Z |
|--|--|--|--|
| PICK-A | 1 | 50 | 1 |
| PICK-B | 50 | 1 | 1 |
| PICK-C | 50 | 50 | 1 |
| PICK-D | 25 | 25 | 1 |
| PICK-E | 25 | 50 | 1 |

- **Fast calculation result** – The nearest-neighbor approach starts at the put (1, 1, 1) and repeatedly selects the closest unvisited location. It then reverses the result. This approach can produce a route where the worker's path crosses itself, such as: *PICK-C \> PICK-A \> PICK-E \> PICK-B \> PICK-D \> Put*.
- **Optimized route result** – The algorithm starts with the same route, then detects that reversing certain segments eliminates crossing paths. The result is a loop-free route with shorter total distance, such as: *PICK-C \> PICK-B \> PICK-D \> PICK-E \> PICK-A \> Put*.

> [!TIP]
> For warehouses with aisle-based layouts where pick locations fall along predictable lines (such as locations within the same aisle), *fast calculation* typically produces routes that are close to optimal. The *optimized route* algorithm provides the greatest benefit in open or irregularly laid-out warehouses where locations are scattered across multiple aisles and levels.

## Distance calculation strategies

The *distance calculation strategy* controls how the system measures the distance between two locations. The sorting algorithm uses these distances to determine which pick locations are closer or farther from the put location and from each other. Choose a strategy that matches your warehouse layout so that the calculated distances reflect the actual paths that workers follow.

### Straight line calculation strategy

The *straight-line calculation strategy* works best for open warehouse layouts where workers can move diagonally, such as open floor areas or wide-aisle warehouses. It calculates the direct (Euclidean) distance between two points. It assumes that workers can move freely in any direction between locations. It's calculated using the formula:

$distance = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2 + (\lvert z_2 \rvert + \lvert z_1 \rvert)^2}$

The horizontal component uses the difference in X and Y coordinates. The vertical component uses the sum of the absolute heights of both locations (as explained in the [Vertical distance calculation](#vertical-distance-calculation) section).

### City block calculation strategy

The *city-block calculation strategy* works best for warehouses with aisle-based layouts where workers walk along aisles and turn corners rather than cutting across open space. It calculates the distance along a grid-like path (also known as Manhattan distance). It assumes that workers must follow aisles and can't cut diagonally. It's calculated using the formula:

$distance = \lvert x_2 - x_1 \rvert + \lvert y_2 - y_1 \rvert + \lvert z_2 \rvert + \lvert z_1 \rvert$

The horizontal component sums the absolute differences in X and Y separately, which means the distance reflects the path a worker takes along aisles (first walking along one axis, then the other). The vertical component uses the sum of the absolute heights of both locations (as explained in the [Vertical distance calculation](#vertical-distance-calculation) section).

### Vertical distance calculation

Both calculation strategies handle vertical movement (the Z axis) the same way: the system adds the absolute height of the starting location to the absolute height of the destination location.

For example, to move from shelf level 1 to shelf level 4, the vertical distance is *|1| + |4| = 5*, not *|4 - 1| = 3*.

This approach models the real cost of vertical movement in a warehouse. A worker can't move directly from one shelf level to another. Instead, the worker must climb down from the current level to the ground (costing the full height of that level) and then climb up to the target level (costing the full height of that level). For example, using a ladder or lift to descend from level 1 and then ascend to level 4 requires more effort than a simple height difference of 3 suggests.

> [!IMPORTANT]
> Two locations at the same shelf level (for example, both at Z = 2) still have a vertical distance of |2| + |2| = 4, not 0. This result reflects the reality that even on the same level, a worker must reach up to that shelf height at both the source and destination. If your warehouse has all locations on the ground level, set Z = 0 for all locations to eliminate the vertical component from distance calculations.

### Distance calculation examples

The following examples show how the two strategies calculate distance differently for the same pair of locations.

#### Example 1: Two locations on the same level

You have two locations on the same shelf level (Z = 1) but different X and Y coordinates:

- Location A: (2, 3, 1)
- Location B: (8, 7, 1)

The following table shows the distance calculations for both strategies:

| Strategy | Calculation | Result |
|--|--|--|
| Straight line | $\sqrt{(8-2)^2 + (7-3)^2 + (1+1)^2} = \sqrt{36 + 16 + 4}$ | **7.48** |
| City block | $\lvert 8-2 \rvert + \lvert 7-3 \rvert + \lvert 1 \rvert + \lvert 1 \rvert = 6 + 4 + 1 + 1$ | **12** |

The straight-line distance (7.48) is shorter because it assumes the worker walks diagonally. The city-block distance (12) is larger because the worker must follow the aisle grid: 6 units along one axis, then 4 units along the other, plus the vertical component at both locations.

#### Example 2: Two locations on different levels

You have two locations with the same X and Y coordinates but different shelf levels:

- Location A: (2, 3, 1)
- Location B: (2, 3, 4)

The following table shows the distance calculations for both strategies:

| Strategy | Calculation | Result |
|--|--|--|
| Straight line | $\sqrt{(2-2)^2 + (3-3)^2 + (4+1)^2} = \sqrt{0 + 0 + 25}$ | **5** |
| City block | $\lvert 2-2 \rvert + \lvert 3-3 \rvert + \lvert 4 \rvert + \lvert 1 \rvert = 0 + 0 + 4 + 1$ | **5** |

When the locations differ only in shelf level, both strategies produce the same result (5 units) because vertical distance is calculated the same way in both: the worker climbs down from level 1 (1 unit) and climbs up to level 4 (4 units).

#### Example 3: Diagonal movement across a warehouse

You have two locations that differ significantly in X, Y, and Z coordinates:

- Location A: (1, 1, 1)
- Location B: (10, 10, 3)

The following table shows the distance calculations for both strategies:

| Strategy | Calculation | Result |
|--|--|--|
| Straight line | $\sqrt{(10-1)^2 + (10-1)^2 + (3+1)^2} = \sqrt{81 + 81 + 16}$ | **13.34** |
| City block | $\lvert 10-1 \rvert + \lvert 10-1 \rvert + \lvert 3 \rvert + \lvert 1 \rvert = 9 + 9 + 3 + 1$ | **22** |

The difference between the strategies is most pronounced when the worker must cover large horizontal distances. The straight-line distance (13.34) assumes a direct diagonal path, while the city-block distance (22) reflects walking 9 units in one direction, 9 units in another direction, and then handling the vertical change at both levels.

## Related information

- [Set up warehouse spatial locations](spatial-locations-setup.md)
- [Wave processing](wave-processing.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
