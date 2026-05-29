---
title: Clean up time series data
description: Learn how to review and permanently delete unused time series versions and entire time series to reclaim storage in Demand planning.
author: AndersEvenGirke
ms.author: aevengir
ms.topic: how-to
ms.date: 05/29/2026
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Clean up time series data

[!include [banner](../includes/banner.md)]

Almost every operation that changes a time series in Demand planning — such as running a transformation, calculation, or forecast — creates a new version. This version history is valuable, but over time, unused versions and entire time series that are no longer needed accumulate and consume storage.

The *data cleanup* feature lets you review everything that's stored and permanently delete the versions and time series you no longer need. The feature shows you exactly what you're removing, including its size and anything that still references it, so you can make informed decisions before deleting.

> [!IMPORTANT]
> Deletion is permanent and can't be undone. Always review the details shown in the confirmation dialog before proceeding.

## Prerequisites

Data cleanup is only available to users who have the *Demand planning manager* role. This restriction ensures that only authorized users can permanently remove data.

## Understand time series versions

Versions are organized in two levels:

- **Major versions** — Created by a job or action such as a transformation, calculation, forecast, revert, or copy. They're numbered sequentially (1, 2, 3, and so on).
- **Minor versions** — Individual data versions within a major version. They're numbered hierarchically (1.1, 1.2, and so on). Minor versions are user-named and typically represent saved edits to the major version.

Learn more about how versions are created and managed in [Time series, worksheets, and planning data](time-series.md#time-series-versions-version-control-and-change-log).

## Open the data cleanup page

To review and clean up time series data, in the Demand planning app navigation pane, go to the **Data management** group and select **Data cleanup**.

The page shows your time series and their versions. The newest versions appear first. You can expand or collapse major versions to show or hide their minor versions. The version currently in use is marked *(current)*.

## Understand version statuses

Each version has one of the following statuses.

| Status | Description |
|---|---|
| *Active* | The version exists normally and is available for use. |
| *Marked for deletion* | You confirmed the deletion of this version. A background cleanup process removes the data shortly afterward. This is a normal intermediate state, not an error. |
| *Failed deletion* | A cleanup attempt didn't finish, for example because of a temporary issue. The system retries these automatically, so a version may briefly show this status before the retry succeeds. |

## Understand references

When you use a time series or time series version as input for a calculation or forecast profile, the system creates a reference between the time series and the profile. Because of this dependency, you must remove all references to a time series or version before you can delete it. Versions that have references can't be selected for deletion.

## Delete time series versions

To delete one or more time series versions, follow these steps.

1. Open the **Data cleanup** page.
1. In the versions view, select the checkboxes of the versions you want to delete. Selecting a major version automatically selects all of its eligible minor versions, and clearing it clears them again. The *(current)* version and any version that has references can't be selected for deletion.
1. Select **Delete selected versions**.
1. A confirmation dialog titled *Permanently delete selected versions?* appears with the message: *This action will permanently remove all selected versions. This process is irreversible. Please confirm to proceed.*
1. Select **Confirm** to proceed, or **Cancel** to back out.

## Delete an entire time series

To delete one or more complete time series, including all of their versions and data, follow these steps.

1. Open the **Data cleanup** page.
1. In the time series list, select the time series you want to remove.
1. Select **Delete selected timeseries**.
1. A confirmation dialog titled *Permanently delete selected timeseries?* appears with the message: *This action will permanently remove all selected timeseries and their data. This process is irreversible. Please confirm to proceed.*
1. Select **Confirm** to proceed, or **Cancel** to back out.

> [!NOTE]
> Deleting versions of a time series or entire time series also affects worksheets that include them.

## Related information

- [Time series, worksheets, and planning data](time-series.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
