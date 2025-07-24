---
title: Register and track batch/serial numbers for finished products and their components
description: Learn how workers and managers can register batch/serial numbers for materials and components that are used in manufacturing processes.
author: johanhoffmann
ms.author: johanho
ms.topic: how-to
ms.date: 04/29/2024
ms.custom: 
  - bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Register and track batch/serial numbers for finished products and their components

[!INCLUDE [banner](../includes/banner.md)]

Workers and managers can register batch/serial numbers for materials and components that are used in manufacturing processes. They can also then associate those numbers with the batch/serial numbers of the products that are produced. In this way, manufacturers can optimize their processes, enhance product quality, and respond quickly to any issues that arise. Managers can use the item tracing report to effectively track batch/serial numbers that are registered through the *Tracked components* feature.

> [!TIP]
> You can also track batch/serial numbers for materials and components using the [Traceability Add-in for Dynamics 365 Supply Chain Management (preview)](../traceability/traceability-overview.md), which offers a graphical browser interface and an API for integration with external systems.

## Prerequisites

Before you can use the features that are described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.40 or later.
- The feature that's named *Tracked components* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). As of Supply Chain Management version 10.0.45, this feature is turned on by default.

## Enable registration of tracked component information

To enable registration of tracked component information in production processes, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **Inventory and warehouse management parameters**.
1. On the **Bills of materials** tab, set the **Enable tracked components** option to *Yes*.

## Enable registration of tracked components on products

Before you can use tracked components functionality for a product or its components, the following conditions must be met:

- The product must be defined as serial controlled or batch controlled.
- The product must be associated with a tracked components policy.

To create a tracked components policy, follow these steps.

1. Go to **Production** \> **Setup** \> **Production** \> **Tracked components policy**.
1. Use the buttons on the Action Pane to add a new policy or edit an existing one.
1. For the new or selected policy, set the following fields:

    - **Name** – Enter a name for the policy.
    - **Description** – Enter a description of the policy.
    - **Use tracked components** – Set this option to *Yes* to register tracked information for products that are associated with the policy.
    - **Check pre-allocation for product** – Set this option to *Yes* to validate serial or batch numbers for finished goods when tracked component information is registered.
    - **Check for pre-allocation for components** – Set this option to *Yes* to validate serial or batch numbers for components when tracked component information is registered.
    - **Serial number matching limit** – Set this option to *Yes* to ensure that the number of component serial numbers that are matched to a product serial number doesn't exceed the planned quantity on the production order bill of materials (BOM) line. If the number of matched components exceeds the planned quantity, the system blocks the match to prevent over-allocation.

## Register tracked components for finished items

To register tracked components for the finished items for any production order, follow these steps.

1. Start from any of the following places:

    - **All production orders** list or details
    - **Picking list** journal line
    - **Route card** journal line
    - **Job card** journal line
    - **Report as finished** journal line
    - **Current operations**
    - Production order **Start** dialog
    - Production order **Report as finished** dialog

1. Select the production order that you want to register batch or serial numbers for.
1. On the Action Pane, find the tab that includes the **Track components** button, and select that button.
1. On the **Tracked components** page, the **Type or scan serial or batch number** field is automatically in focus. In addition, the **Scan mode** field is automatically set to *Product* to indicate that you're about to enter the batch or serial number of a finished product. Follow one of the steps:

    - If you're using a scanner, scan the bar code of the first finished product that you want to register.
    - If you're using a keyboard, enter the batch or serial number of the first finished product that you want to register, and then select **Submit**.

    :::image type="content" source="media/tracked-components-register.png" alt-text="Screenshot of the Tracked components page." lightbox="media/tracked-components-register.png":::

1. The value of the **Scan mode** field is changed to *Component*. You can now register the batch or serial number of a component by following one of these steps:

    - If you're using [GS1 bar codes](../warehousing/gs1-barcodes.md), your system might be able to detect which component you're scanning. In this case, you can just scan the component bar code, which includes both the component item number and its serial or batch number.
    - If you're using simple bar codes, or if you're using a keyboard, first select a component in the grid on the **Component** FastTab. Then enter or scan the batch or serial number of that component.

1. Repeat the previous step until you finish registering all the components for the current finished product.
1. Change the value of the **Scan mode** field back to *Product*, and repeat this procedure until you finish registering all finished products and their components for the current production order.

    At any time, you can review and correct the registrations that you've made so far. On the **Finished products** FastTab, on the toolbar, select **View associations** to open the **Tracked components associations** page. For information about how to work with this page, see the next section.

As you work, the **Status** field on the **Finished product** FastTab of the **Tracked components** page indicates the registration status of each finished product. The **Status** field on the **Components** FastTab indicates the registration status of each component in the selected finished product. The **Status** field on each FastTab can have the following values:

- *Not started* – No batch or serial number has been associated with the product or component.
- *In progress* – An association has been established, but only for part of the started quantity for the finished product or the component. On the **Components** FastTab, the **Started**, **Consumption**, and **Remaining quantity** columns let you track the quantity that has been allocated.
- *Completed* – No remaining quantity remains to be allocated for the finished product or the component.

## Review and edit batch/serial numbers for finished products and their components

Use the **Tracked components associations** page to review and edit batch/serial numbers for finished products and their components. For information about how to open this page for a selected production order, see the previous section.

:::image type="content" source="media/tracked-components-view.png" alt-text="Screenshot of the Tracked components associations page." lightbox="media/tracked-components-view.png":::

### Finished products

The **Finished products** section lists batch/serial number registrations for the products that are being produced for the selected production order. The toolbar in this section provides the following buttons:

- **Create** – Add a new row to the grid so that you can register the serial or batch number for a missing finished product.
- **Remove** – Remove one or more selected finished products.
- **Report as finished** – Report a selected row as finished. You can first edit the **Good quantity** and/or **Error quantity** value for batch products as required.

### Components

The **Components** section lists the components of the finished product that's selected in the **Finished products** grid. For each component, this section shows the registered batch or serial number, and you can enter or correct these values as required. The toolbar in this section provides the following buttons:

- **Create** – Add a new row to the grid so that you can register the serial or batch number for a missing component.
- **Remove** – Remove one or more selected components.
- **Pick** – Manually pick the quantity that's planned for consumption, as specified in the **Consumption** field.
- **Adjust consumption** – Generate a production picking list journal to manually adjust the consumption. In this case, the quantity that's specified in the **Consumption** field is automatically entered in the picking list journal.

## Related information

- [How workers use the production floor execution interface](production-floor-execution-use.md#tracked-components)
- [Traceability overview (preview)](../traceability/traceability-overview.md)
