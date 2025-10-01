---
title: Configure Traceability (preview)
description: This article describes how to configure the Traceability Add-in.
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 09/29/2025
ms.custom: 
  - bap-template
---

# Configure Traceability (preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article describes how to configure the Traceability Add-in.

## <a name="api-endpoint"></a>API endpoint

The Traceability Add-in for Supply Chain Management provides an API endpoint that you can use to exchange messages with external systems. It lets you integrate Traceability with other systems, such as enterprise resource planning (ERP) systems, warehouse management systems, and quality management systems. To use the API, you need to know the URL of the endpoint. To find it, follow these steps:

1. [Open the Traceability app](../traceability-app-run.md) in Power Apps.
1. On the left navigation pane, select **Settings** \> **System**.
1. On the **General** tab of the **System** page, you can find the API endpoint URL in the **Endpoint** field. Use the **Copy** button to copy the URL to the clipboard.

## Exclude products from Traceability

If you have products that don't need to be traced, you can choose to exclude them from the Traceability Add-in. All products that aren't on the exclude list are traced.

To exclude or reinclude a product, follow these steps:

1. [Open the Traceability app](../traceability-app-run.md) in Power Apps.
1. On the left navigation pane, select **Settings** \> **Exclude product**.
1. The **Exclude product** page opens, showing a list of currently excluded products (if any). Use the buttons in the toolbar to add, remove, or edit rows in the list. For each row, make the following settings:
    - **Company** – Specify the legal entity (company) of the product that shouldn't be traced.
    - **Item number** – Specify the item number of the product that shouldn't be traced.

> [!NOTE]
> Your settings here only affect activity events that occur after you make the change. Activity events that occurred for a product before you added it to the exclude list continue to be included in Traceability. Activity events that occurred for a product while it was on the exclude list are never included in Traceability, even after you remove the product from the list.

## Configure activities that Traceability traces

All activities throughout the logistics process are logged as *activity events*. Activity events include *goods receipt*, *consumption*, *registration*, and so on.

You can make the following configuration settings for each activity:

- Enable and disable activity events traced at the company level.
- Map original activities and activity types to specific activity codes.

> [!NOTE]
> Your configuration settings only affect activity events that occur after you make the change. Events that occurred for an activity before you added it to the activities list never appear in Traceability. Events that occurred for an activity while it was on the activities list continue to be included in Traceability even after you remove the activity from the list.

To configure activities that Traceability traces, follow these steps:

1. [Open the Traceability app](../traceability-app-run.md) in Power Apps.
1. On the left navigation pane, select **Settings** \> **Activity**.
1. The **Activity** page opens, showing a list of activities currently configured for your environment. Use the buttons in the toolbar to add, remove, or edit rows in the list. For each row, make the following settings:

    - **Activity code** – Enter a name that identifies the activity to users. Traceability displays this name to identify the activity when users make a genealogy trace.
    - **Activity type** – Select the type of activity, as it should be shown to users (for example, *Sales*, *Purchase*, *Production*, *Quality*, *Warehouse*, *Maintenance*, or *Transportation*). Traceability displays this value to identify the activity when users make a genealogy trace.
    - **Source activity type** – Select the activity type reported by the source system (for example, *Sales*, *Purchase*, *Production*, *Quality*, *Warehouse*, *Maintenance*, or *Transportation*). See the table after this procedure for a list of source activity types and codes by Supply Chain Management.
    - **Source activity code** – Enter the activity code reported by the source system. See the table after this procedure for a list of source activity types and codes by Supply Chain Management.
    - **Company** – Specify the legal entity of the activity to be traced. Enter an asterisk (\*) to trace the activity for all companies.
    - **Trace or Not** – Set to *True* for activities that should be traced. Set to *False*, for activities that shouldn't be traced.

1. On the toolbar, select **Save**.

The following table lists the source activity codes and types supported by the tracked component feature.

| Source activity code | Source activity type | Integration scenario |
|--|--|--|
| PurchaseGoodsReceipt | Purchase | Goods receipt of purchase order. |
| ProductionReportFinished | Production | Component consumption during manufacturing assembly.|
| ProductionPickingList | Production | Finished goods produced during production.|
| ProductionPickingListPartialReverse | Production | Partial reverse picking list of component consumption.|
| ProductionReportFinishedPartialReverse | Production | Partial reverse report as finished.|
| ProductionPickingListFullReverse | Production | Full reverse picking list of component consumption.|
| ProductionReportFinishedFullReverse | Production | Full reverse report as finished.|

## Configure data collection fields that are traced in Traceability

*Data collection* captures various types of information at the activity code level, including document reference, order number, site, warehouse, and location. This data enhances track-and-trace capabilities and supports insights in reports like *Find items*. With this functionality, you can do the following actions:

- Create data collection fields.
- Assign data collection fields to specific companies and activity codes.
- Enable or disable data collection tracking.

> [!NOTE]
> Certain data collection fields, such as Document reference, Site, and Location, are preassigned to all companies for out-of-the-box integration with Supply Chain Management. To avoid disrupting this integration, don't modify the following predefined fields: Document reference, Journal number, Reference type, Order number, Vendor account, Vendor name, Site, Warehouse, Location, or Operator.

To configure data collection fields that are traced in Traceability, follow these steps:

1. [Open the Traceability app](../traceability-app-run.md) in Power Apps.
1. On the left navigation pane, select **Settings** \> **Data collections**.
1. Select the **Add** button on the menu bar to open the initial screen for creating a data collection field.
1. Make the following settings for the new data collection field:
    - **Name** – Enter the name of the data collection field. The integrated systems use this value to identify the specific field.
    - **Description** – Provide a brief description of the data collection field.
    - **Data collection ID** – Enter the internal ID of the data collection configuration record. This value uniquely represents the data collection field in storage. You can specify it manually or allow the system to generate it automatically.
    - **Data type** – Define the type of data the field can store. The following options are available:
      - *Text* – Accepts alphanumeric values.
      - *Number* – Accepts integer and decimal values, both positive and negative.
      - *Boolean* – Maps business values to system values *True* or *False*.
      - *Enum* – Lets you define a list of predefined values.
    - **UoM (unit of measure)** – Specify the unit of measure for the data collection field.
    - **Assignment** – Assign the data collection field to multiple entities. For each assignment, make the following settings:
      - **Activity** – Select a combination of activity type and activity code defined in the activity configuration for the assignment.
      - **Company code** – Specify the company code where the data collection field is assigned.
    - **Status (track or not)** – Set to *On* to track the data collection field. Set to *Off* to disable tracking.
