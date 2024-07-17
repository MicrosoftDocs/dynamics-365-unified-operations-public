---
title: Configure the Traceability app in Power Apps (preview)
description: This article describes how to configure the Traceability app in Power Apps
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 07/29/2024
ms.custom: 
  - bap-template
---

# Configure the Traceability app in Power Apps (preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

<!-- KFM: NOTE: UI uses the term "trace" while the doc uses the term "track". I used "trace" everywhere here. Should we do that everywhere? The FM feature name uses "tracked"; will that be changed?  -->

## <a name="api-endpoint"></a>API endpoint

The Traceability app provides an API endpoint that you can use to exchange messages with external systems. It lets you integrate Traceability with other systems, such as ERP systems, warehouse management systems, and quality management systems. To use the API, you need to know the URL of the endpoint. To find it, follow these steps:

1. [Open the Traceability app](traceability-app-run.md) in Power Apps.
1. On the left navigation pane, select **Settings** \> **System**.
1. On the **General** tab of the System page, you can find the API endpoint URL in the **Endpoint** field. You can use the copy button to copy the URL to the clipboard.

## Exclude products from Traceability

If you have products that don't need to be traced, you can choose to exclude them from the Traceability app. All products that aren't specifically included on the exclude list will be traced.

To exclude or re-include a product, follow these steps:

1. [Open the Traceability app](traceability-app-run.md) in Power Apps.
1. On the left navigation pane, select **Settings** \> **Exclude product**.
1. The **Exclude product** page opens, showing a list of currently excluded products (if any). Use the buttons in the toolbar to add, remove, or edit rows in the list. For each row, make the following settings:
    - **Company** – Specify the legal entity (company) of the product that shouldn't be traced.
    - **Item number** – Specify the item number of the product that shouldn't be traced.

> [!NOTE]
> Your setting here only affect transactions that occur after you make the change. Transactions that occurred for a product before you added it to the exclude list will continue to be shown in the Traceability app. <!--KFM: Should we say "activities" or "activity event" instead of "transaction"? -->

## Configure activities that are traced in Traceability

All activities throughout the logistics process are logged as *activity events*. Activity events include *goods receipt*, *consumption*, *registration*, and so on. <!--KFM: What is the difference between activities and activity events? -->

<!--KFM: I think some more background would help here. For example, I think these settings are important when integrating with external systems. -->

To maintain the credibility of Traceability, the activity event is immutable. <!--KFM: I'm not sure what this means. Can we clarify or remove this? -->

You can make the following configuration settings for each activity:

- Enable and disable transactions traced at the company level.
- Map original activities and activity types to specific activity codes.

> [!NOTE]
> Your configuration settings only affect transactions that occur after you make the change. Transactions that occurred for a product before you added it to the exclude list will continue to be shown in the Traceability app. <!--KFM: Should we say "activities" or "activity event" instead of "transaction"? -->

To configure activities that are traced in Traceability, follow these steps:

1. [Open the Traceability app](traceability-app-run.md) in Power Apps.
1. On the left navigation pane, select **Settings** \> **Activity**.
1. The **Activity** page opens, showing a list of activities currently configured for your environment. Use the buttons in the toolbar to add, remove, or edit rows in the list. For each row, make the following settings:

    - **Activity code** – Enter a name that identifies the activity to users. The Traceability app displays this name to identify the activity when users make a genealogy trace.
    - **Activity type** – Select the type of activity, as it should be shown to users (for example, *Sales*, *Purchase*, *Production*, *Quality*, *Warehouse*, *Maintenance*, or *Transportation*). The Traceability app displays this value to identify the activity when users make a genealogy trace.
    - **Source activity type** – Select the activity type reported by the source system (for example, *Sales*, *Purchase*, *Production*, *Quality*, *Warehouse*, *Maintenance*, or *Transportation*). See the table after this procedure for a list of source activity types and codes by Supply Chain Management.
    - **Source activity code** – Enter the activity code reported by the source system. See the table after this procedure for a list of source activity types and codes by Supply Chain Management.
    - **Company** – Specify the legal entity of the activity to be traced. If the value is "\*", the activity will be traced for all companies.
    - **Trace or Not** – Set to *True* for activities that should be traced. Set to *False*, for activities that shouldn't be traced.

1. On the toolbar, select **Save**.

The following table lists the source activity codes and types that supported out of the box by Supply Chain Management. <!--KFM: Please confirm this. I think these should be the "source" values. Are these present by default, or should we tell users to enter these if they are integrating with SCM? -->

| Source activity code | Source activity type | Integration Scenario |
|--|--|--|
| PurchaseGoodsReceipt | Purchase | Purchase order goods received. |
| ProductionReportFinished | Production | Components consumed during manufacturing assembly. |
| ProductionPickingList | Production | Finished goods produced during production.|

<!--KFM: My system also includes other default values. What are those for? -->
