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

## API endpoint

<!-- KFM: This section is a guess. Please review carefully. -->

The Traceability app provides an API endpoint that you can use to exchange messages with external systems. It lets you integrate Traceability with other systems, such as ERP systems, warehouse management systems, and quality management systems. To use the API, you need to know the URL of the endpoint. To find it, follow these steps:

1. Open the Traceability app in Power Apps.
1. On the left navigation pane, select **Settings** \> **System**.
1. On the **General** tab of the System page, you can find the API endpoint URL in the **Endpoint** field. You can use the copy button to copy the URL to the clipboard.

## Exclude products from Traceability

If you have products that don't need to be tracked, you can choose to exclude them from the Traceability app. All products that aren't specifically included on the exclude list will be tracked.

To exclude or re-include a product, follow these steps:

1. Open the Traceability app in Power Apps.
1. On the left navigation pane, select **Settings** \> **Exclude product**.
1. The **Exclude product** page opens, showing a list of currently excluded products (if any). Do one of the following steps:
    - To add a new product to the list, select **New** on the toolbar.
    - To remove a product from the list, select the product in the list and then select **Delete** on the toolbar.
    - To edit a product in the list, select the product and then select **Edit** on the toolbar.
1. Make the following settings for your new or selected product:
    - **Company** – Specify the legal entity (company) of the product that shouldn't be tracked.
    - **Item number** – Specify the item number of the product that shouldn't be tracked.

> [!NOTE]
> Your setting here only affect transactions that occur after you make the change. Transactions that occurred for a product before you added it to the exclude list will continue to be shown in the Traceability app.

## Configure activities that are tracked in Traceability

All activities throughout the whole logistics process will be logged as Activity Event. Activity events can be “Goods Receipt”, “Consumption”, “Registration” etc.

To keep the credibility of Supply Chain Traceability, the activity event is immutable.

In this configuration, you can do the following configuration:
•	Enable and disable the transaction for tracking at company level.
•	Map the Original activity/activity type to specific activity code.

Note: For those tracked/logged activities, you still can find them in Traceability. This configuration only affects the transaction after configuration change.
 
Field Explanation
•	Company – The legal entity of activity which needs to be tracked. If the value is “*”, the activity will be tracked for all company. 
•	Activity code – Manual input value. The activity code which will be displayed in Supply Chain Traceability front end.
•	Activity type – The activity type which will be displayed in Supply Chain Traceability front end. The values below are available: 
Purchase/Production/Sales.
(In later release Transportation/Warehouse Management/Quality Management/Asset Management will be included.)
•	Source activity type – The activity type of source system. The values below are available: Purchase/Production/Sales.
(In later release Transportation/Warehouse Management/Quality Management/Asset Management will be included.)
•	Source activity code – Manual input value. This field advises the source activity code which needs to be tracked. 
For the integration with Dynamics 365 Supply Chain Management, please use below activity code and activity type combinations.

Activity Code	Activity Type	Integration Scenario
PurchaseGoodsReceipt	Purchase	Integration of the goods receipt of purchase order.
ProductionReportFinished	Production	Integration of component consumption during manufacturing assembly.
ProductionPickingList	Production	Integration of finished goods receipt of production.


•	Track or Not – When the value is “True”, the activity will be tracked. When the value is “False”, the activity will not be tracked.



 
