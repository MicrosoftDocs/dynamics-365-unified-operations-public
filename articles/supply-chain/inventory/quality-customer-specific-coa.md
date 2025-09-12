---
title: Customer-specific certificate of analysis (COA)
description: Learn how to customize the content of a certificate of analysis (COA) to meet specific customer requirements and automatically print the COA when a sales order packing slip is generated.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: QMSInventTestCertOfAnalysisCustGroup, InventTestGroup, InventQualityOrderTable
ms.topic: how-to
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# Customer-specific certificate of analysis (COA)

[!include [banner](../../includes/banner.md)]

Microsoft Dynamics 365 Supply Chain Management lets you create a basic certificate of analysis (COA) either from the quality order or from the menu directly after you select a quality order. Learn more about how to use the basic COA in [Quality orders](quality-orders.md). This article explains how to customize the content of a COA to meet specific customer requirements and automatically print the COA when a sales order packing slip is generated.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

Before you can use the features that are described in this article, your system must meet the following requirements:

- You must be running Supply Chain Management version 10.0.44 or later.
- The feature that is named *Advanced quality management* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Set up a COA customer group

To manage COAs for different customers, you can group customers into COA customer groups. To create a COA customer group and add customers to it, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **Certificate of analysis** \> **Certificate of analysis customer groups**.
1. Use the buttons on the Action Pane to add a new COA customer group or edit an existing one. (You can also delete existing groups.)
1. For the new or selected COA customer group, set the following fields:

    - **COA customer group** – Enter the identifier of the COA customer group.
    - **Description** – Enter a description for the COA customer group.

## Set up and maintain customer-specific COA requirements on test groups

To set up customer-specific COA requirements on test groups, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Test groups**.
1. In the lower section of the page, select a test.
1. On the toolbar, select **Customer COA requirements** to open the **Customer COA requirements** page.
1. Use the buttons on the Action Pane to add a new customer COA requirement or edit an existing one. (You can also delete existing requirements.)

    If you add a new customer COA requirement, the **Test** and **Test group** fields are automatically set. If the test is associated with a batch attribute, the **Attribute** field is also set.

1. For the new or selected customer COA requirement, set the following fields in the grid:

    - **Customer code** – Select *All* to make the requirement applicable to all customers, *Group* to make it applicable to a group of customers, or *Table* to make it applicable to a specific customer.
    - **Customer relation** – If you selected *Group* in the **Customer code** field, select a COA customer group. If you selected *Table*, select a specific customer account. (If you selected *All*, this field is unavailable.)
    - **Exclude** – Select whether the test should appear on the customer-specific COA. The assumption is that the customer-specific COA includes all tests except tests are explicitly marked as excluded.
    - **Use customer specific ranges** – Specify whether the customer-specific batch attribute range should be used for the customer-specific COA. If no customer -specific batch attribute range if found, the standard range is printed.
    - **Suppress Min/Max values** – Specify whether the minimum and maximum values of the test should be suppressed on the customer-specific COA. For example, the minimum value for a test is *1*, the maximum value is *10*, and the result is *1*. In this case, you might not want the range to be shown at all for some customers, to avoid drawing attention to the fact that the result barely passed the quality test.
    - **Replace pass results** – Enter text that should replace the test results on the customer-specific COA if the test is passed. In this situation, some businesses prefer to show standard text, such as "Within specification," instead of the actual test results.
    - **Replace fail results** – Enter text that should replace the test results on the customer-specific COA if the test is failed. In this situation, some businesses prefer to show standard text, such as "Outside acceptable range," instead of the actual test results.

## Set up and maintain customer-specific COA requirements from a quality order

To set up and maintain customer-specific COA requirements from a quality order, follow these steps.

1. Go to **Inventory management** \> **Periodic** \> **Quality management** \> **Quality orders**.
1. Select a quality order.
1. Select a line on the selected quality order.
1. On the Action Pane, select **Customer COA requirements**.
1. Follow steps 4 and 5 of the previous procedure to add, edit, or delete customer-specific COA requirements.

## Include product-specific and customer-specific batch attributes on a COA

You can mark product-specific and customer-specific batch attributes for inclusion on a COA, even if they aren't included in testing through a quality order.

1. Go to **Product information management** \> **Products** \> **Released products**.
1. On the **All released products** list page, find and select or open the batch-enabled product that you want to set up.
1. On the Action Pane, on the **Manage inventory** tab, in the **Batch attributes** group, select either **Product specific** or **Customer specific**.
1. Select an existing attribute in the list pane, or create a new one.
1. To include the new or selected attribute on a COA, set the **Include in COA independent of quality order** option to *Yes*.
1. Repeat the previous steps for every other attribute that you want to include on the COA.

After the customer-specific COA requirements are set for a test group, they automatically apply to all quality orders that use that test group. However, they can be adjusted on individual quality orders as required.

## Access customer-specific COAs

The following table describes the different ways to access customer-specific COAs.

| Access method | Navigation path | Details |
|---|---|---|
| Directly from the menu | Go to **Inventory management** \> **Inquiries** \> **Quality management** \> **Certificate of analysis**. | You can print either the standard COA or a customer-specific COA. (You trigger printing of a customer-specific COA by selecting a specific customer account.) In both cases, you must select a quality order. |
| From a quality order | Go to **Inventory management** \> **Periodic** \> **Quality management** \> **Quality order**, and then, on the Action Pane, select **Inquiries** \> **Certificate of analysis**. | You can print either the standard COA or a customer-specific COA. (You trigger printing of a customer-specific COA by selecting a specific customer account.) Because access is from a quality order, that quality order is assumed in both cases. |
| From an inventory batch | Go to **Inventory management** \> **Inquiries** \> **Dimensions** \> **Batches**, and then, on the Action Pane, select **Inquiries** \> **Certificate of analysis**. | You can print either the standard COA or a customer-specific COA. (You trigger printing of a customer-specific COA by selecting a specific customer account.) Because access is from an inventory batch, the COA quality order that is specified on the **General** tab of the inventory batch is used to generate the COA in both cases. If the COA quality order must be updated, you can use the **Reset COA Quality order** button on the Action Pane to change the quality order that drives the details of the COA. |
| As part of processing the sales order packing slip | Go to **Sales and marketing** \> **Common** \> **Sales orders** \> **All sales orders**, and then, on the Action Pane, on the **Pick and pack** tab, select **Generate** \> **Packing slip**. Alternatively, go to **Sales and marketing** \> **Periodic** \> **Sales update** \> **Packing slip**. | Only customer-specific COAs are printed from this process. Depending on the customer who placed the order, a customer-specific COA is printed for every item/batch combination on the order that has a COA quality order specified for it in the batch. A COA is printed only for items that are batch controlled and items where the batch specifies a quality order. |

> [!NOTE]
> The setting of the option to print customer-specific COAs initially comes from the **Updates** tab of the **Accounts receivable parameters** page. By default, this setting is used for new customers. If you process the packing slip for a single order, the setting of the checkbox on the packing slip processing page comes from the customer. If you process packing slips for multiple orders, you must select the checkbox to print customer-specific COAs.
