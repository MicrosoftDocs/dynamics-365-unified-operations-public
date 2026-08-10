---
title: Park warehouse work on cancel (preview)
description: Learn how to let warehouse workers park an in-progress work at a scanned location so that the next worker is guided back to it.
author:
ms.author:
ms.reviewer: kamaybac
ms.search.form: InventLocation, WHSParameters, WHSWorkTable
ms.topic: how-to
ms.date: 08/10/2026
ms.custom:
  - bap-template
---

# Park warehouse work on cancel (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Warehouse workers often have to leave a work unfinished because of a break, a shift change, or a change in operational priorities. Without park work, cancelling an in-progress work unlocks it but doesn't record where the worker left the physical handling unit, so the next worker has no way to find it. Park work asks the worker to scan the location where they're leaving the work, stores that location on the work header, and then guides the next worker back to it.

Park work doesn't move on-hand inventory. The park location is an operational hand-off location only. The standard cancel cleanup continues to control the work line and inventory state.

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

<!-- TODO: PM input needed - confirm the minimum Supply Chain Management version that includes this feature -->

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.XX or later.
- The feature named *(Preview) Park warehouse work on cancel* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). This feature is turned off by default.
- To use guided park locations, the feature named *(Preview) Warehouse aisle* must also be turned on in feature management.

> [!IMPORTANT]
> Park work applies only to work-execution flows that run through the user-directed work-execution display. Every user-directed and system-directed mobile flow that's routed through that display supports park work. Cluster picking and other work-execution display types keep their existing **Cancel** behavior.

## Turn on park work for a warehouse

After the feature is turned on, you must also opt in each warehouse where workers should be prompted to park work. Warehouses that you don't opt in keep the standard **Cancel** behavior.

To turn on park work for a warehouse, follow these steps:

1. Go to **Warehouse management** \> **Setup** \> **Warehouse** \> **Warehouses** to open the **Warehouses** page.
1. In the list, select the warehouse that you want to set up.
1. Select **Edit**.
1. On the **Warehouse** FastTab, set the following field:
    - **(Preview) Park work policy** – Select *Mandatory* to prompt workers for a park location when they cancel an eligible in-progress work. Select *Disabled* to keep the standard cancel behavior for this warehouse.
1. Select **Save**.

## Set up guided park locations

By default, workers scan any valid location in the work's warehouse. You can instead guide workers to a dedicated type of park location in their own aisle. To do this, choose a location type that identifies your park locations, and then set it as the park location type.

To set up guided park locations, follow these steps:

1. Go to **Warehouse management** \> **Setup** \> **Warehouse management parameters** to open the **Warehouse management parameters** page.
1. Set the following field:
    - **(Preview) Park location type** – Select the location type that identifies the locations where work can be parked. Leave the field blank to let workers scan any valid location in the warehouse.
1. Select **Save**.

Make sure that the location profile of each park location uses the location type that you select here. Locations that use a different location type aren't suggested.

> [!NOTE]
> Guided park locations require the *(Preview) Warehouse aisle* feature. If either the park location type is blank or aisle support is turned off, workers scan the park location directly, and no current-location step is shown.

## Park a work from the Warehouse Management mobile app

Workers park a work from the existing **Cancel** action. No extra button is added to the mobile app.

A work can be parked only when it has at least one completed line and at least one open line. A work that's already parked isn't parked again.

To park a work, follow these steps:

1. In the Warehouse Management mobile app, start a work and complete at least one line.
1. Select **Cancel**.
1. If guided park locations are set up, scan the location where you are now. The app uses this location to find nearby park locations in the same aisle.
1. Review the suggested park location, and then choose one of the following options:
    - **Confirm** – Park the work at the suggested location. The suggested value is read-only.
    - **Skip** – Show the next park location in the aisle. The suggestions repeat from the beginning after the last candidate.
    - **Override** – Scan any valid location in the work's warehouse instead.
1. If guided park locations aren't set up, scan the location where you're leaving the work.

The work is then parked at the confirmed location, and the standard cancel cleanup unlocks the work so that another worker can take it.

Suggested locations are ordered by location ID. If the scanned aisle has no location that matches the park location type, the app shows your current location as a read-only fallback, and **Override** is still available.

> [!NOTE]
> Nothing is saved until you confirm the final park location. If you scan a current location, skip a suggestion, or select **Back**, no park location is written and the work isn't cancelled.

If the scanned location doesn't exist in the work's warehouse, or if the work was cancelled while you were on the park prompt, the app shows an error and the park prompt is shown again.

## Pick up a parked work

Because the park location is informational, the app requires physical confirmation before picking resumes. The next worker must scan the work's target license plate to prove that they've taken custody of the handling unit.

To pick up a parked work, follow these steps:

1. In the Warehouse Management mobile app, start the parked work by scanning or entering the work ID.
1. Go to the park location that the app shows.
1. Scan the target license plate that the app shows.

The park location is then cleared from the work, the otherwise redundant license plate verification on the first pick is skipped, and work execution resumes.

If you scan an incorrect license plate or leave the field empty, the work stays parked and the prompt is shown again with an error. If you cancel from the pick-up prompt, the work also stays parked.

> [!TIP]
> If you start the work by scanning its target license plate, that scan counts as the confirmation. The app clears the park location and continues without showing the pick-up prompt.

## Where the park location is stored

The park location is stored in the **Parked at location** field on the work header. The field is empty when the work isn't parked, and it's cleared when a worker picks up the work.

Park work doesn't add a work status value, a dedicated parked-work page, or a stored history of park events. Parked work stays eligible for normal work selection and system-directed prioritization, and it isn't assigned to a specific worker or worker group.

## Constraints

Keep the following limits in mind when you plan to use park work:

- On-hand inventory isn't moved to the park location. The standard cancel behavior leaves the on-hand inventory with the worker.
- No inventory is reserved at a suggested park location, and location capacity isn't considered.
- Suggested locations are limited to the aisle of the scanned current location.
- Cluster picking flows don't support park work.

<!-- TODO: PM input needed - screenshots of the Warehouses page park work policy field, the Warehouse management parameters park location type field, and the mobile app park and pick-up steps -->

## Related information

- [Warehouse management overview](warehouse-management-overview.md)
- [Install, configure, and connect the Warehouse Management mobile app](install-configure-warehouse-management-app.md)
- [Cancel warehouse work for exception handling](cancel-warehouse-work.md)
- [Warehouse work policies](warehouse-work-policies.md)
- [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
