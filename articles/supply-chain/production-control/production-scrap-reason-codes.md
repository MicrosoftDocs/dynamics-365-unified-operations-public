---
title: Flexible production scrap reason codes (preview)
description: Learn how to define your own production scrap reason codes, scope them to production units, resource groups, and resources, and use them to report scrap.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: ProdScrapReasonCode, ProdParmReportFinished, ProdJournalTransRoute, ProdJournalTransJob
ms.topic: how-to
ms.date: 09/02/2026
ms.custom:
  - bap-template
ai-usage: ai-assisted
---

# Flexible production scrap reason codes (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

<!-- TODO: Verify ms.search.form value -->

Production scrap reason codes let you define your own set of reasons that explain why material was scrapped during manufacturing, and control where each reason is offered. Instead of choosing among the three fixed error causes (*Material*, *Machine*, and *Operator*), workers select a reason that reflects the actual cause of the scrap, such as tool wear, a setup error, or a surface defect. Because you can scope each reason code to a production unit, a resource group, or an individual resource, workers see only the reasons that apply to the equipment they're working on.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

More precise scrap data makes root-cause analysis and continuous improvement work possible. Each reason code also maps to one of the original error causes, so reports and analytics that are built on error causes keep working while you adopt the new reason codes.

## Prerequisites

To use production scrap reason codes, your system must meet the following requirements:

<!-- TODO: PM input needed - confirm the Supply Chain Management version that this feature first becomes available in. -->

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.XX or later.
- The feature named *(Preview) Flexible production scrap reason codes* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

While the feature is turned off, production scrap reason codes aren't available, and the **Error cause** field continues to appear on the pages where workers report scrap.

## How reason code scoping works

Each reason code is either available everywhere or restricted to specific parts of your production organization. The scope is defined by the assignment rows that you add to the reason code on the **Resources** tab:

- **A reason code with no assignment rows is global** – Every worker can use it, regardless of the resource they work on. Use this approach for reasons that apply across your whole operation, such as a general material defect.
- **A reason code with one or more assignment rows is restricted** –The reason code is available only where at least one of its assignment rows covers the resource that the worker is reporting against.

Each assignment row specifies a production unit and, optionally, a resource group and a resource within that group. The row covers a resource when every value that the row specifies matches that resource's current position in your production hierarchy. Values that you leave blank act as a wildcard. You can define scope at three levels of precision:

- **Production unit only** – The reason code is offered on every resource that belongs to a resource group under that production unit.
- **Production unit and resource group** – The reason code is offered on every resource that currently belongs to that resource group.
- **Production unit, resource group, and resource** – The reason code is offered only on that specific resource.

Because resource group membership is dated, a reason code follows a resource as it moves between groups. Only memberships that are valid on the current date are considered.

To offer one reason code in several unrelated places, add several assignment rows to it. For example, to make a *Seal defect* reason available on a whole packaging line plus one machine in another area, add one row for the packaging production unit and a second row that names the individual machine.

## Create a production scrap reason code

Create one reason code for each distinct cause of scrap that you want workers to be able to report. Keep the list short enough that workers can scan it quickly on the shop floor.

1. Go to **Production control** > **Setup** > **Production** > **Production scrap reason codes**.
1. On the Action Pane, select **New**.
1. Set the following fields:

    - **Reason code** – Enter a unique identifier for the reason. You can't change this value after you save the record, so establish a naming standard before you start. For example, *TOOLWEAR*.
    - **Description** – Enter text that explains the reason in terms that shop floor workers recognize. This text appears next to the identifier when workers choose a reason, so it does most of the work of guiding their selection. For example, *Tool wear beyond tolerance*.
    - **Error cause** – Select the original error cause that this reason maps to: *Material*, *Machine*, or *Operator*. Supply Chain Management stores this value on the journal line together with the reason code, so existing reports and analytics that group scrap by error cause continue to work. For example, a *Tool wear* reason typically maps to *Machine*.

1. On the Action Pane, select **Save**.

## Scope a reason code to your production resources

After you create a reason code, decide where workers should see it. Skip this procedure if the reason code applies everywhere.

1. Go to **Production control** > **Setup** > **Production** > **Production scrap reason codes**.
1. In the list, select the reason code that you want to scope.
1. On the **Resources** FastTab, select **New**, and then set the following fields:

    - **Production unit** – Select the production unit that the reason code applies to. This field is required on every assignment row.
    - **Resource group** – Optional. Select a resource group to narrow the scope from the whole production unit to a single group. The group must belong to the production unit that you selected.
    - **Resource** – Optional. Select an individual resource to narrow the scope further. You must select a resource group before you select a resource, and the resource must belong to that group.

1. Repeat the previous step for each additional place where the reason code should be offered.
1. On the Action Pane, select **Save**.

> [!NOTE]
> If you delete a reason code, you also delete all of its assignment rows.

## Report scrap in production journals

Workers and supervisors select reason codes on the pages where they already report error quantities. In each case, the **Reason code** lookup shows only the reasons that apply to the resource on the line, together with each reason's description and error cause.

When a worker selects a reason code, Supply Chain Management derives the **Error cause** value from the reason code and stores both values on the journal line. Workers therefore no longer choose an error cause themselves.

You can find reason codes in the following places:

- **Report as finished** – When you report a production order as finished and enter an error quantity, select a value in the **Reason code** field. Learn more in [Report production orders as finished](report-production-orders-as-finished.md).
- **Route card and job card journals** – On the journal lines, use the **Reason code** field to explain the error quantity that's registered against the operation or job.

## Report scrap in the production floor execution interface

Workers who use the production floor execution interface select a reason code as part of reporting scrap:

1. On the job that they're reporting against, the worker starts to report an error quantity.
1. The worker selects the reason code field to open the **Production scrap reason codes** page. This page opens as a full-screen list that shows the reason code, its description, and its error cause.
1. Because the list is already filtered to the resource that the job runs on, the worker sees only relevant reasons. The worker can also type in the search box to narrow a long list.
1. The worker selects a reason, and then selects **OK**.

If no reason codes apply to the resource that the worker is reporting against, the list is empty. If workers report an empty list, check that at least one reason code either is global or has an assignment row that covers their resource.

Learn more about the interface in [How workers use the production floor execution interface](production-floor-execution-use.md).

## Related information

- [Report production orders as finished](report-production-orders-as-finished.md)
- [How workers use the production floor execution interface](production-floor-execution-use.md)
- [Report as finished from the job card device](report-finished-job-device.md)
- [Operations resources](operations-resources.md)
- [Configure the production floor execution interface](production-floor-execution-configure.md)
