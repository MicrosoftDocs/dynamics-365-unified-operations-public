---
title: Advanced product search (preview)
description: Learn how to set up, synchronize, monitor, and turn off the Advanced product search pipeline in Dynamics 365 Commerce.
ms.topic: how-to
ms.date: 11/21/2026
author: miraoms
ms.author: amitrive
ms.reviewer: mirao
ms.search.form: RetailParameters, RetailCDXSchedule, RetailCDXDataGroup, RetailSearchPublishingSession
ms.search.region: Global
ms.custom:
  - bap-template
ai-usage: ai-assisted
---

# Advanced product search (preview)

[!INCLUDE [banner](includes/preview-banner.md)]

Advanced product search prepares and publishes product data for search in Microsoft Dynamics 365 Commerce. It combines product, variant, channel, and attribute relationships in headquarters to simplify search publishing. Administrators turn on the pipeline for selected legal entities and manage its synchronization and background processing.

## Prerequisites

Before you set up Advanced product search, ensure your environment meets these requirements:

- You're running Dynamics 365 Commerce headquarters or Dynamics 365 Supply Chain Management version 10.0.50 or later. Your Commerce Scale Unit (CSU) and Commerce Data Exchange (CDX) packages must be compatible with that headquarters version.
- The feature named **(Preview) Advanced product search** is turned on in feature management. For more information, see [Feature management overview](../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
- Price change tracking includes each legal entity where you plan to use the pipeline. Configure the legal entities on the **Prices and discounts** tab of **Commerce shared parameters**, on the **Price change tracking** FastTab. For more information, see [Price change tracking](price-change-tracking.md).
- Process automation is initialized so that it can schedule headquarters data population. For more information, see [Process automation](../fin-ops-core/fin-ops/sysadmin/process-automation.md).

## How the pipeline works

The pipeline moves product data from headquarters to your channels in four stages. Use the monitoring location for each stage to identify where a delay occurs.

| Stage | What happens | Where to monitor |
| ----- | ------------ | ---------------- |
| Headquarters data population | Background processing populates denormalized search tables and picks up incremental changes to products and assortments. | **System administration** > **Inquiries** > **Batch jobs**. Review **Advanced product search table data population** and its processing tasks. |
| Distribution to the channel database | CDX distribution schedule **1250** moves the prepared search data to channel database tables on the CSU. | **Retail and Commerce** > **Retail and Commerce IT** > **Distribution schedule**. Select schedule **1250** and, on the Action pane, select **History**. |
| Search index publishing | The Azure AI Search index publisher automatically picks up the distributed data and publishes it to the search index. | **Retail and Commerce** > **Channel setup** > **Search publishing sessions**. |
| Channel search | CSU search endpoints provide the results to point of sale (POS) and e-commerce channels. | Product search in your POS and e-commerce channels. |

By default, the headquarters background process checks for work every 15 minutes. End-to-end refresh time also depends on headquarters processing, the recurrence of schedule **1250**, and search index publishing. If you don't schedule **1250**, changes remain in headquarters until the next time you run it.

You turn on the pipeline per legal entity. Headquarters prepares channel data for channels whose inventory legal entity has the pipeline turned on. Other channels, including channels on the same CSU, continue to use the legacy publisher.

The pipeline doesn't change price calculation. Your existing CSU pricing, whether it uses legacy pricing or Unified pricing management, continues to work as before.

## Set up Advanced product search

Complete the following setup for each legal entity that should use the pipeline. Wait for the initial headquarters data population to finish before you start the first full synchronization.

### Turn on the pipeline for a legal entity

The company setting determines which channels use the new pipeline. Turn it on in the legal entity that supplies inventory for those channels.

1. In headquarters, switch to the legal entity that you want to configure.
1. Go to **Retail and Commerce** > **Headquarters setup** > **Parameters** > **Commerce parameters**.
1. Open the **(Preview) Advanced product search** tab.
1. Expand the **General** FastTab.
1. Set **Enable advanced product search** to **Yes**. This setting includes the legal entity in subsequent headquarters data population cycles.
1. On the Action pane, select **Save**.

### Initialize and check headquarters processing

Process automation schedules the work that prepares product data for distribution. Check that the new background process is available and that its initial processing completes.

1. Go to **System administration** > **Setup** > **Process automation**.
1. If process automation isn't initialized, or the new background process isn't available, on the Action pane, select **Initialize process automation**.
1. On the **Background processes** tab, check that **Advanced product search table data population** is available.
1. Go to **System administration** > **Inquiries** > **Batch jobs**. Review **Advanced product search table data population** and its processing tasks, and wait for the initial work to finish.

Processing includes shared product data and parallel workers for channel and catalog data. Don't expect exactly one task per table. The process doesn't queue another population cycle while earlier denormalization work remains unfinished.

### Synchronize channel configuration and search data

First, distribute the company setting, and then send the prepared product data to the channel databases. Associate the target channel database groups with schedule **1250** before you request a full synchronization.

1. Go to **Retail and Commerce** > **Retail and Commerce IT** > **Distribution schedule**.
1. Select **1110 (Global configuration)**. On the Action pane, select **Run now**, and confirm the dialog to run the schedule. This schedule distributes the updated Commerce parameters, including the pipeline setting.
1. After schedule **1110** completes, select schedule **1250**, **(Preview) Advanced product search**.
1. Expand the **Channel database groups** FastTab. Add the channel database groups that contain your target channel databases, and save your changes.
1. Go to **Retail and Commerce** > **Headquarters setup** > **Commerce scheduler** > **Channel database group**.
1. Select a channel database group that you associated with schedule **1250**.
1. Expand the **Channel database** FastTab, and select the databases that should receive the data. Above the grid, select **Full data sync**.
1. In the dialog, select schedule **1250**, and then select **OK**. Confirm the full synchronization settings to start the job.
1. Repeat the full synchronization for the target databases in each additional channel database group.
1. If you want to send subsequent changes automatically, configure a recurring batch job for distribution schedule **1250**. Select its recurrence based on your product update frequency and freshness requirements.

Use a one-time full synchronization for the initial data load and ordinary incremental runs of schedule **1250** for subsequent updates. Don't configure the full synchronization itself as a recurring job.

If schedule **1250** isn't available, check whether your Commerce scheduler configuration is current. For more information, see [Commerce Data Exchange best practices](dev-itpro/CDX-Best-Practices.md#update-configurations).

After setup, the search index publisher picks up the data automatically and performs the initial publish. You don't need to reconfigure POS or e-commerce clients to use the pipeline.

## Monitor data population and publishing

If product changes don't reach search results, check the stages in order. A completed headquarters task doesn't mean that CDX distribution and search index publishing also finished.

1. Go to **System administration** > **Inquiries** > **Batch jobs**. Review the data population jobs and their tasks for unfinished work or errors.
1. Go to **Retail and Commerce** > **Retail and Commerce IT** > **Distribution schedule**. Select schedule **1250** and, on the Action pane, select **History** to review its distribution sessions.
1. Go to **Retail and Commerce** > **Channel setup** > **Search publishing sessions**. Review publishing status for the affected channel or operating unit.

If **Search publishing sessions** isn't available, check whether the **Search publishing sessions monitoring** feature is turned on in feature management. For more information, see [View product search publishing status in headquarters](publish-status-headquarters.md).

## Turn off the pipeline and return to legacy publishing

Use the company setting to turn off the pipeline and schedule cleanup of the legal entity's search data. Keep the feature turned on in feature management if other legal entities still use it.

1. In headquarters, switch to the legal entity that you want to return to legacy publishing.
1. Go to **Retail and Commerce** > **Headquarters setup** > **Parameters** > **Commerce parameters**.
1. Open the **(Preview) Advanced product search** tab.
1. Expand the **General** FastTab.
1. Set **Enable advanced product search** to **No**.
1. Select **Yes** in the confirmation dialog to confirm deletion of the legal entity's denormalized search data. If you select **No**, the pipeline stays turned on.
1. On the Action pane, select **Save**. Saving schedules the cleanup batch job.
1. Go to **System administration** > **Inquiries** > **Batch jobs**. Wait for **Advanced product search cleanup of data per legal entity** to complete.
1. Go to **Retail and Commerce** > **Retail and Commerce IT** > **Distribution schedule**. Run **1110 (Global configuration)** to distribute the changed setting, and then run schedule **1250** incrementally to distribute the cleanup.

Cleanup removes denormalized channel and catalog product data for channels associated with the legal entity. It doesn't delete your original products or all shared search data in headquarters.

The legacy CDX schedules **1040 (Products)**, **1070 (Channel configuration)**, and **1150 (Catalog)** resume supplying data for search publishing. Ensure that these schedules continue to run. Publishing the changes made while the new pipeline was active can take time, depending on your data volume.

Repeat the procedure for each legal entity that you want to return to legacy publishing. If you want to turn off the feature everywhere, finish cleanup and synchronization for all affected legal entities before turning it off in feature management.

## Preview limitations

The following limitations apply to this preview:

- The pipeline supports POS and e-commerce channels only. It doesn't support product search in call center or Supply Chain Management sales orders.
- Queued and completed publishing times aren't available for the advanced pipeline on the **Search publishing sessions** page.

## Provide feedback

Send feedback about Advanced product search to [D365advancedproductsearch@microsoft.com](mailto:D365advancedproductsearch@microsoft.com). You can also discuss the preview in the Dynamics 365 Commerce community.

## Related information

- [Cloud-powered search overview](cloud-powered-search-overview.md)
- [View product search publishing status in headquarters](publish-status-headquarters.md)
- [Commerce Data Exchange and commerce channel communications](dev-itpro/define-retail-channel-communications-cdx.md)
- [Price change tracking](price-change-tracking.md)
- [Process automation](../fin-ops-core/fin-ops/sysadmin/process-automation.md)
