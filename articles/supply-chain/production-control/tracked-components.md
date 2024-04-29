---
title: Register batch/serial numbers for finished products and their components (preview)
description: Workers and managers can register batch/serial numbers for material and components used in manufacturing processes and associate these to batch/serial numbers for the products that are produced.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 04/29/2024
audience: Application User
ms.custom: 
  - bap-template
---


# Register batch/serial numbers for finished products and their components (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner-section](../includes/preview-banner-section.md)]
<!-- KFM: preview until further notice -->

Workers and managers can register batch/serial numbers for material and components used in manufacturing processes and associate these with batch/serial numbers for the products that are produced. This enables manufacturers to optimize their processes, enhance product quality, and respond quickly to any issues that arise. Managers can utilize the item tracing report to effectively track batch/serial numbers registered through the Tracked Components feature.

[!INCLUDE [preview-note](../includes/preview-note.md)]

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.40 or later.
- The feature that is named *Tracked components* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Register tracked components for finished items

To register tracked components for the finished items for any production order, follow these steps:

1. Start from any of the following pages:
    - **All production orders** list or details
    - **Picking list** journal line
    - **Route card** journal line
    - **Job card** journal line
    - **Report as finished** journal line
    - **Current operations**
    - Production order **Start** dialog
    - Production order **Report as finished** dialog

1. Select the production order you want to register batch or serial numbers for.
1. From the Action Pane, find the tab includes a button called **Track components** and select that button.
1. The **Tracked components** page opens. When you open the page, the **Batch or serial number** field is automatically in focus, and the **Scan mode** is set to *Product* (which means you are about to enter a finished product batch or serial number).
    - If you are using a scanner, scan the bar code of the first finished product you want to register.
    - If you are using a keyboard, enter the batch or serial number of the first product you want to register and then select **Submit**.
1. The **Scan mode** switches to *Component*. Now you are ready register a component batch or serial number.
    - If you are using [GS1 barcodes](../warehousing/gs1-barcodes.md), then your system may be able to detect which component you are scanning, so you can just scan the component bar code, which includes both he component item number and its serial or batch number.
    - If you are using simple barcodes, or are entering using a keyboard, first select a component on the **Component** FastTab grid and then enter or scan the batch or serial number for that component.
1. Repeat the previous step until you have registered all of the components for the current finished product.
1. Set **Scan mode** back to *Product* and repeat this procedure until you have registered all finished products and their components for the current production order. At any time, you can review and correct the registrations you have made so far by selecting **View associations** from the **Finished products** FastTab toolbar to open the **Tracked components associations** page. See the next section for details about how to work with this page.

As you work, the **Tracked components** page indicates the registration status of each finished product (on the **Finished product** FastTab) and of each component in the selected finished product (on the **Components** FastTab). The **Status** field on each FastTab can have the following values:

- *Not started*: No batch or serial number has been associated with the product or component.
- *In progress*: An association has been established, but only for part of the started quantity for the component or finished product. In the **Components** section, the **Started**, **Consumption**, and **Remaining quantity** columns let you track how much quantity has been allocated.
- *Completed*: There is no remaining quantity to be allocated or the component or finished product.

## Review and edit batch/serial numbers for finished products and their components

Use the **Tracked components associations** page to review and edit batch/serial numbers for finished products and their components. See the previous section for instructions on how to open this page for a selected production order.

### Finished products

The **Finished products** section lists batch/serial number registrations for the products being produced for the selected production order. The toolbar in this section provides the following buttons:

- **Create** – Add a new row to the grid so you can register the serial or batch number for a missing finished product.
- **Remove** – Remove one or more selected finished products.
- **Report as finished** – Report a selected row as finished. If necessary, you can first edit the **Good quantity** and/or **Error quantity** values for batch products as needed.

### Components

The **Components** section lists the components for the finished product selected in the **Finished products** grid. For each component, the page shows the registered batch or serial number and allows you to enter or correct these values. The toolbar in this section provides the following buttons:

- **Create** – Add a new row to the grid so you can register the serial or batch number for a missing component.
- **Remove** – Remove one or more selected component.
- **Pick** – Manually pick the quantity that is planned to be consumed, as specified in the Consumption field.
- **Adjust consumption** – Generate a production picking list journal to manually adjust the consumption. In this case, the quantity specified in the **Consumption** field will be defaulted to the picking list journal.

## Additional resources

- [How workers use the production floor execution interface](production-floor-execution-use.md)