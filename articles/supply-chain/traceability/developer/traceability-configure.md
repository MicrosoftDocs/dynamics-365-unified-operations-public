---
title: Configure Traceability (preview)
description: This article describes how to configure the Traceability Add-in.
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 07/29/2024
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
1. On the **General** tab of the System page, you can find the API endpoint URL in the **Endpoint** field. You can use the copy button to copy the URL to the clipboard.

## Exclude products from Traceability

If you have products that don't need to be traced, you can choose to exclude them from the Traceability Add-in. All products that aren't on the exclude list are traced.

To exclude or reinclude a product, follow these steps:

1. [Open the Traceability app](../traceability-app-run.md) in Power Apps.
1. On the left navigation pane, select **Settings** \> **Exclude product**.
1. The **Exclude product** page opens, showing a list of currently excluded products (if any). Use the buttons in the toolbar to add, remove, or edit rows in the list. For each row, make the following settings:
    - **Company** – Specify the legal entity (company) of the product that shouldn't be traced.
    - **Item number** – Specify the item number of the product that shouldn't be traced.

> [!NOTE]
> Your settings here only affect activity events that occur after you make the change. Activity events that occurred for a product before you added it to the exclude list will continue to be included in Traceability. Activity events that occurred for a product while it was on the exclude list will never be included in Traceability, even after you remove the product from the list.

## Configure activities that are traced in Traceability

All activities throughout the logistics process are logged as *activity events*. Activity events include *goods receipt*, *consumption*, *registration*, and so on.

You can make the following configuration settings for each activity:

- Enable and disable activity events traced at the company level.
- Map original activities and activity types to specific activity codes.

> [!NOTE]
> Your configuration settings only affect activity events that occur after you make the change. Events that occurred for an activity before you added it to the activities list will never be included in Traceability. Events that occurred for an activity while it was on the activities list will continue to be included in Traceability even after you remove the activity from the list.

To configure activities that are traced in Traceability, follow these steps:

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

The following table lists the source activity codes and types that supported out of the box by the tracked component feature of Supply Chain Management.

| Source activity code | Source activity type | Integration scenario |
|--|--|--|
| PurchaseGoodsReceipt | Purchase | Goods receipt of purchase order. |
| ProductionReportFinished | Production | Component consumption during manufacturing assembly.|
| ProductionPickingList | Production | Finished goods produced during production.|
| ProductionPickingListPartialReverse | Production | Partial reverse pickinglist of component consumption.|
| ProductionReportFinishedPartialReverse | Production | Partial reverse Report as finished.|
| ProductionPickingListFullReverse | Production | Full reverse pickinglist of component consumption.|
| ProductionReportFinishedFullReverse | Production | Full reverse Report as finished.|

## Configure data collection fields that are traced in Traceability

**Data Collection** is designed to capture various types of information at the activity code level, such as Document Reference, Order Number, Site, Warehouse, and Location. This data enhances track-and-trace capabilities and supports insights in reports like **Find Items**.

Within this menu, you can:

- Create Data Collection fields.
- Assign them to specific companies and activity codes.
- Enable or disable Data Collection tracking as needed.

> [!NOTE]
> Certain Data Collection fields, such as Document Reference, Site, and Location, are preassigned to All Companies for out-of-the-box (OOB) integration with D365 SCM. To avoid disrupting this integration, please do not modify these predefined fields:
> Document reference/Journal number/Reference type/Order number/Vendor account/Vendor name/Site/Warehouse/Location/Operator

To configure data collection fields that are traced in Traceability, follow these steps:

1. [Open the Traceability app](../traceability-app-run.md) in Power Apps.
1. On the left navigation pane, select **Settings** \> **Data collections**.
1. Click the Add button in the menu bar to open the initial screen for creating a data collection field.
1. Make the following settings:
    - **Name** – Enter the name of the data collection field. This value is used in integrations to identify the specific field.
    - **Description** – Provide a brief description of the data collection field.
    - **Data Collection ID** – The internal ID of the Data Collection Configuration record. This value uniquely represents the data collection field in storage. You can specify it manually, or the system will generate it automatically.
    - **Data Type** – Defines the type of data the field can store. The following options are available:
      - **Text** – Accepts alphanumeric values.
      - **Number** – Accepts integer and decimal values, both positive and negative.
      - **Boolean** – Maps business values to system values True or False.
      - **Enum** – Allows you to define a list of predefined values.
    - **UoM (Unit of Measure)** – Specifies the unit of measure for the data collection field.
    - **Assignment** – Allows assigning the data collection field to multiple entities:
      - **Activity** – Select a combination of activity type and activity code defined in Activity Configuration for the assignment.
      - **Company Code** – Specify the company code where the data collection field is assigned.
    - **Status (Track or Not)** – When set to On, the data collection field will be tracked. When set to Off, tracking will be disabled.


   
