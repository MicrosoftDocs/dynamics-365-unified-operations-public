---
# required metadata

title: Reason codes for inventory counting
description: This topic describes how to set up and apply reason codes for counting tasks.
author: Mirzaab
manager: tfehr
ms.date: 03/15/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: InventCountingReasonCodePolicy
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 1705903
ms.assetid: 427e01b3-4968-4cff-9b85-1717530f72e4
ms.search.region: Global
# ms.search.industry: 
ms.author: mirzaab
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 8.0.0
---

# Reason codes for inventory counting

[!include [banner](../includes/banner.md)]

Reason codes let you analyze the results of a counting process and any discrepancies that occur during that process. You can specify the reason for doing the count, such as a broken pallet or a stock adjustment that is based on inventory samples.

## Recommendation

Before you set up the system, we recommend that you define a strategy for working with reason codes. For example, try to answer the following questions:

- Should reason codes be mandatory on warehouses?
- Should reason codes be mandatory or optional on some items?
- How many reason codes do you require?
- How should users of barcode scanners use reason codes? Should the reason codes be preselected, mandatory, or not editable?
- Do warehouse workers require different reason code behavior on mobile scanners? If the answer is yes, you can create more menu items and assign them to different people.

## Where reason codes apply

You can create multiple reason code policies, and each reason code policy can have two counting reason code policies. The counting reason code policies can be used at the warehouse level or the item level.

## Set up reason code policies

1. Select **Inventory management** \> **Setup** \> **Inventory** \> **Counting reason code policies**, and create a new reason code policy.
2. In the **Counting reason code type** field, select either **Mandatory** or **Optional** to specify whether selection of a reason code should be an optional or mandatory action in one of the following counting journals:

    - Cycle Count (mobile device)
    - Spot Count (mobile device)
    - Threshold Count (mobile device)
    - Adjustment In (mobile device)
    - Adjustment Out (mobile device)
    - Counting Journal (rich client)

You can also set up reason codes for individual warehouses and for products. The reason code setup for products can disregard the setup for warehouses.

## Mandatory reason codes

If the **Mandatory** parameter is set in the configuration of reason codes for warehouses or items, the counting journal can't be completed and closed until a reason code is provided.

### Set up reason codes for warehouses

1. Select **Inventory Management** \> **Setup** \> **Inventory breakdown** \> **Warehouses**.
2. On the **Warehouse** tab, in the **Counting reason code policy** field, select one of the following options:

    - **Blank** – The parameter that is set up for the item is used to determine whether counting journals are mandatory for the product.
    - **Mandatory** – A reason code is always required on counting journals for the warehouse.
    - **Optional** – A reason code isn't required on counting journals for the warehouse.

### Set up reason codes for products

1. Select **Product information management** \> **Products** \> **Released products**.
2. On the **Product** tab, select **Counting reason code policy**, and then select one of the following options:

    - **Blank** – The parameter that is set up for the warehouse is used to determine whether counting journals are mandatory for the product.
    - **Mandatory** – A reason code is always required on counting journals for the product. This setting overrides any reason code setting at the warehouse level.
    - **Optional** – A reason code isn't required on counting journals for the product. This setting overrides any reason code setting at the warehouse level.

### Use reason codes in counting journals

In a counting journal, you can add reason codes for counts of the following types:

- Cycle Count
- Spot Count
- Threshold Count
- Adjustment In
- Adjustment Out

Reason codes are added to the journal lines in counting journals of the **Counting journal** type.

1. Select **Inventory management** \> **Journal entries** \> **Item counting** \> **Counting**.
2. In the line details of the counting journal, in the **Counting reason code** field, select an option.

### View the counting history as it's recorded by reason codes

- Select **Inventory management** \> **Inquiries and reports** \> **Counting history**, and then, in the **Counting reason code** field, view the counting history that has been recorded through a reason code.

### Use a reason code for a quantity adjustment

1. On the **On-hand inventory** page, select **Adjust quantity**. You can open the **On-hand inventory** page in several ways. For example, select **Inventory management** \> **Inquiries and reports** \> **On-hand inventory**.
2. Select **Adjust quantity**, and then, in the **Counting reason code** field, select a reason code.

### Configure reason codes for mobile device menu items

You can configure reason codes for any type of count on a mobile device menu item. The configuration of the mobile device menu item includes the following information:

- Whether the reason code is shown to the mobile device worker during counting.
- The default reason code that is shown on a mobile device menu item.
- Whether the user can edit the reason code.

### Set up reason codes on a mobile device

1. Select **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu items**.
2. On the **Cycle count** tab, select **Cycle counting**.
3. In the **Default counting reason code** field, set the default reason code that should be recorded when counting is done by using the mobile device menu item.
4. In the **Display counting reason code** field, select **Line** to show the reason code after each variance is recorded. Alternatively, select **Hide** if the reason code shouldn't be shown.
5. Set the **Edit counting reason code** option to either **Yes** or **No**. If you set this option to **Yes**, the worker can edit the reason code when it's shown on the mobile device during counting.

> [!NOTE]
> The **Cycle counting** button can be enabled on any mobile device menu item where counting can be done. Example include the menu items for spot counts, user-directed work, and system-directed work.

## Cycle count approvals

Before a count is approved, the user can change the reason code that is associated with the count. When the count is approved, the reason code is entered on the counting journal lines.

### Modify cycle count approvals

1. Select **Warehouse management** \> **Cycle counting** \> **Cycle count work pending review**.
2. Select **Cycle counting**, and then, in the **Reason code** field, select a new reason code.

### Modify the mobile device menu item for Adjustment in and Adjustment out

1. Select **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu items**, and then select **Adjustment in and out**.
2. Set the **Use existing work** option to **No**.
3. In the **Work creation process** field, select **Adjustment in**.

The following fields will be added to the mobile device menu item when **Adjustment in** or **Adjustment out** is selected during the work creation process:

- Default counting reason code
- Display counting reason code
- Edit counting reason code
