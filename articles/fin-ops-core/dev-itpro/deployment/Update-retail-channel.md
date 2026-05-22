---
title: Apply updates and extensions to Commerce Scale Unit (cloud)
description: Learn how to apply updates and extensions to cloud-hosted Commerce channel components, including prerequisites.
author: josaw
ms.author: josaw
ms.topic: how-to
ms.custom:
  - bap-template
ms.date: 04/02/2026
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2018-04-30
ms.dyn365.ops.version: 8
---

# Apply updates and extensions to Commerce Scale Unit (cloud)

[!include[banner](../includes/banner.md)]

If you're updating a Tier-2 sandbox or production environment on application version 8.1.2 or newer and have initialized Commerce Scale Unit (CSU), you'll also need to update channel components. This article shows how to apply updates and extensions to CSU.

Updates to CSU are cumulative. This means that any update that you apply will include all previously released changes. Applying a Dynamics 365 Commerce deployable package for extensions is also a cumulative process and will replace the previously deployed version of the extension.

## Prerequisites

Before you proceed, you must first apply updates and extensions (if applicable) to the environment. For more information, see [Apply updates to cloud environments](apply-deployable-package-system.md).

To update CSU, complete the following steps for each:

1. On the **Environment details** page, go to **Environment features > Retail and Commerce**.
1. On the **Commerce deployment setup** page, select **Update**.
1. In the selection panel, select the version to update to.
1. You can choose to update to the newest service update to access the latest features, or you can update to the latest quality update to apply quality improvements for the currently deployed service update. For more information, see [Download updates from Lifecycle Services](../migration-upgrade/download-hotfix-lcs.md).
1. You can choose to apply an extension at the same time.

To apply an extension to a CSU, complete the following steps:

1. On the **Commerce deployment setup** page, select **Apply Extension**.
1. In the selection panel, select the extension to apply.

> [!NOTE]
> You must first upload the Commerce deployable package to the project asset library in Microsoft Dynamics Lifecycle Services before you can select to deploy it on the **Commerce deployment setup page** in Lifecycle Services.

Both **Apply updates** and **Apply extension** operations involve a period of downtime that may last up to 1 hour, or in some cases up to 2 hours or more. For example, when updating non-US locations of CSU, large data volumes, or complex schema updates. For a realistic estimate of the downtime duration, note the downtime duration in Sandbox UAT for an equivalent update and dataset that you plan to use in your production environment. During this time, the following will occur:

- Cloud-hosted Commerce channels won't function (unless POS offline capability is enabled).
- POS devices that have the offline capability feature enabled will have reduced functionality.
- Any e-commerce clients that are dependent on CCSU will be disrupted.
- Channels hosted on CSUs remain unaffected.
- Head office functionality remains unaffected.

> [!NOTE]
> Applying an extension and an update at the same time requires a single downtime, and can be an effective way of averting multiple downtimes.

### Troubleshooting updates

#### Potential downgrade

When applying an update to a Commerce Scale Unit in your environment, you may be shown an error message about version downgrade detection.

**Error message**

"The operation was canceled because a potential downgrade was identified from version 'X.XX.XXXXX.X' to version 'X.XX.XXXXX.X'"

**Explanation**

This issue occurs when your Commerce Scale Unit has a Quality Update (hotfix) applied that may not be included in the Service Update that you're attempting to apply. This may be because the newest Service Update doesn't yet have the latest Quality Update issued (this is rare), or because you may be manually updating to a version of a Service Update that isn't the latest available version.

**Resolution**

1. Make sure you selected the most recent version of the Service Update during the update process.
1. If the latest Quality Update isn't yet available in the Service Update, wait up to three business days and try again. If the issue persists, you may want to file a support request.

## View history

To view the history of recent operations on a Scale Unit, select **History** on the **Action** tab to open the **Scale Unit History** page. On this page, you can view recent operations such as initialize, service update, quality update, version, extension details, and other relevant information.

## Restart Commerce Scale Unit

For troubleshooting, Commerce Scale Unit allows self-service restart of the service. Commerce Scale Unit restart can be useful for mitigation of service reliability or performance issues. To restart Commerce Scale Unit, select a Scale Unit and then select **Restart**. A dialog box displays. Select **Restart** to restart the service. Restarting Commerce Scale Unit closes all active connections before restarting. You can also choose an immediate restart by selecting the **Force restart** option. This will immediately close all active connections and initiate a restart.

## CSU autoupdate sequence

> [!NOTE]
> Auto-update for CSU is being gradually rolled out to all Commerce customers. If you're a Lifecycle Services project owner or environment administrator, you'll receive an email notification when CSU autoupdate is rolled out to your Lifecycle Services project.

When CSU is autoupdated by Microsoft, it takes place in the following sequence.

:::image type="content" source="./media/CSU-auto-update-timeline.png" alt-text="Screenshot of the CSU autoupdate sequence timeline.":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
