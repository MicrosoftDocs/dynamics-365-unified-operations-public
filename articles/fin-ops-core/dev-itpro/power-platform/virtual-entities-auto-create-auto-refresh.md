---
title: Create and refresh virtual entities automatically
description: Learn about automatic creation and refresh of virtual entities for finance and operations apps in Dataverse.
author: mkannapiran
ms.author: johnmichalak
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 01/21/2026
ms.reviewer: johnmichalak
---

# Create and refresh virtual entities automatically

[!include[banner](../includes/banner.md)]

This article provides information about automatic creation and refreshes of virtual entities for finance and operations apps in Dataverse.

> [!IMPORTANT]
> Supported release information:
>
> - **Auto Refresh:** Supported platform versions are PU62 (7.0.7120.170), PU63 (7.0.7198.123), PU64 (7.0.7279.31), or later.
> - **Auto Create:** Supported platform versions are PU63 (7.0.7198.123), PU64 (7.0.7279.31), or later.

When you make changes to data entities in finance and operations apps, you can make those changes visible to Dataverse through a manual refresh. The Auto Create and Refresh capability in finance and operations apps enables automatic metadata creation or modification in Dataverse to occur immediately, reliably, and efficiently. Automatic refresh of metadata ensures timely updates in Dataverse from finance and operations apps. By enabling the Automatic Create and Refresh capability, you don't need to manually refresh finance and operations entities in Dataverse. This capability paves way to automatic creation of virtual tables in Dataverse for finance and operations apps data entities.

:::image type="content" source="media/AutoCreate_Refresh_Overview.png" alt-text="Screenshot of the architecture of virtual entities for the Auto Create and Refresh capability.":::

**Auto Refresh**

- The Virtual Table Auto Refresh feature is activated when you deploy the supported version of the package. Supported platform versions are PU62 (7.0.7120.170), PU63 (7.0.7198.123), PU64 (7.0.7279.31), or later.
- When you deploy the package in finance and operation apps, it triggers an X++ batch job (CDSVirtualEntityRefreshBatch). This batch job is triggered 30 minutes after successful deployment of the feature package.

**Auto Create**

- The Auto Create capability is activated when you deploy the supported version of the feature. Supported platform versions are PU63 (7.0.7198.123), PU64 (7.0.7279.31), or later.
- In finance and operations apps, set the value of the **Dataverse.AutoCreate** metadata property to *Yes* to enable automatic creation of virtual tables in the linked Dataverse environment.
- A batch job (CDSVirtualEntityAutoCreateBatch) manages the automatic creation of virtual tables in Dataverse from finance and operations apps. This batch is triggered 90 minutes after successful deployment of the feature package.

After a **failure**, the Auto Create and Auto Refresh batch jobs automatically retry three times. You can't modify or configure the retry setting.

## Monitoring

- Use the existing **Batch Jobs** page to monitor the status of the Auto Create or Auto Refresh batch job.
- Use the new **Virtual entity metadata sync status** page in finance and operations apps to monitor the status of automatic metadata synchronizations. This page shows all automatically created and refreshed finance and operations entities.

  - If synchronization is successful, the **Last refresh time** field shows the time of the last successful synchronization.
  - If synchronization fails:

    - For enhanced visibility and troubleshooting, personalize the grid on this page by adding the **IsTransientFailure** field. This field indicates whether the failure is transient, and whether a retry is attempted.
    - The **Failure message** field provides details about the error. To learn about error codes that are included in the failure message, see [Web service error codes](/power-apps/developer/data-platform/reference/web-service-error-codes).
    - For entities that are marked as failed, if the **Refresh needed** checkbox is cleared, manual refresh from Dataverse is required after you fix the issue. You must take this action because the system doesn't automatically address these issues.

    :::image type="content" source="media/VEMetadataSyncStatus.png" alt-text="Screenshot of the Virtual entity metadata sync status form.":::

## Notes

- **Limitation of the Auto Refresh batch job history:** Each package deployment re-creates the Auto Refresh batch job. Therefore, the Auto Refresh job history is available only up to the last package deployment. This behavior persists in the current version. Microsoft is aware of this limitation and plans to address it in future releases.
- **Auto Delete feature:** Currently, no Auto Delete feature is implemented. If you delete a finance and operations apps data entity that you already enabled in the linked Dataverse environment, the system takes no automatic action. Administrators must manually delete the virtual table in Dataverse.
