---
# required metadata

title: Reason codes for inventory counting
description: This article describes how to set up and apply reason codes for counting tasks.
author: perlynne
ms.date: 08/02/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: InventCountingReasonCodePolicy, InventCountingReasonCode
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 1705903
ms.assetid: 427e01b3-4968-4cff-9b85-1717530f72e4
ms.search.region: Global
# ms.search.industry: 
ms.author: perlynne
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: 10.0.21
---

# Reason codes for inventory counting

[!include [banner](../includes/banner.md)]

Reason codes let you analyze the results of a counting process and any discrepancies that occur during that process. You can specify the reason for doing the count, such as a broken pallet or a stock adjustment that is based on inventory samples. At the same time, you can use the adjustment functionality to post the value of on-hand inventory adjustments to the appropriate offset account, based on the reason for each inventory adjustment.

## Recommendation

Before you set up the system, we recommend that you define a strategy for working with reason codes. For example, try to answer the following questions:

- Should reason codes be mandatory on warehouses?
- Should reason codes be mandatory or optional on some items?
- How many reason codes do you require?
- Do you have to pre-select a limited list of reason codes for adjustments?
- How should users of bar code scanners use reason codes? Should the reason codes be preselected, mandatory, or not editable?
- Do warehouse workers require different reason code behavior on mobile scanners? If the answer is yes, you can create more menu items and assign them to different people.
- Should the reason codes drive financial offset account posting?

## Turn the reason code features on or off

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.32, it's turned on by default. As of Supply Chain Management version 10.0.36, the feature is mandatory and can't be turned off. If you're running a version older than 10.0.36, then admins can turn this functionality on or off by searching for the *Post on-hand adjustments using configurable reason codes connected to offset accounts* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

## Set up reason codes

### Set up reason code policies

You can create multiple reason code policies to control when and how counting reason codes are applied. Each reason code policy can have one of two counting reason code types (*Optional* or *Mandatory*). Counting reason code policies can be used at the warehouse level or the item level.

To create a reason code policy, following these steps.

1. Go to **Inventory management** \> **Setup** \> **Inventory** \> **Counting reason code policies**.
1. On the Action Pane, select **New** to add a policy to the grid.
1. Set the **Name** field for the new policy.
1. In the **Counting reason code type** field, select either *Mandatory* or *Optional* to specify whether selection of a reason code should be optional or mandatory in one of the following inventory adjustment processes:

    - Cycle Count (mobile device)
    - Spot Count (mobile device)
    - Threshold Count (mobile device)
    - Adjustment In (mobile device)
    - Adjustment Out (mobile device)
    - Counting Journal (rich client)
    - Quantity adjustment/Online counting (rich client)

You can set up reason code policies both for individual warehouses and for products. The reason code setup for a product can overrule the setup for the product's warehouse.

> [!NOTE]
> For warehouses and items where the **Counting reason code policy** field is set to *Mandatory*, the counting journal can't be completed and closed until a reason code is provided. For more information, see the next section.

### Assign counting reason code policies to warehouses

To assign a counting reason code policy to a warehouse, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **Inventory breakdown** \> **Warehouses**.
1. Select a warehouse in the list pane.
1. On the Action Pane, on the **Warehouse** tab, in the **Set Up** group, select **Counting reason code policy**. Then, in the **Assign counting reason code policy** drop-down dialog box, follow one of these steps:

    - To use the policy setup for each item to determine whether counting journals are mandatory for it, enter no value (or delete the existing value).
    - To require a reason code on counting journals for the warehouse, select a reason policy where the **Counting reason code type** field is set to *Mandatory*.
    - If a reason code is optional on counting journals for the warehouse, select a reason policy where the **Counting reason code type** field is set to *Optional*.

### Assign counting reason code policies to products

To assign a counting reason code policy to a product, follow these steps.

1. Go to **Product information management** \> **Products** \> **Released products**.
1. Select a product in the grid.
1. On the Action Pane, on the **Product** tab, in the **Set Up** group, select **Counting reason code policy**. Then, in the **Assign counting reason code policy** drop-down dialog box, follow one of these steps:

    - To use the policy setup for the warehouse to determine whether counting journals are mandatory for the product, enter no value (or delete the existing value).
    - To require a reason code on counting journals for the product select a reason policy where the **Counting reason code type** field is set to *Mandatory*. This setting overrides any reason code setting at the warehouse level.
    - If a reason code is optional on counting journals for the product, select a reason policy where the **Counting reason code type** field is set to *Optional*. This setting overrides any reason code setting at the warehouse level.

### Set up counting reason codes

To set up your counting reason codes, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **Inventory** \> **Counting reason codes**.
1. On the Action Pane, select **New** to add a row to the grid.
1. Set the **Counting reason code** and **Description** fields for the new row.
1. To assign an offset account, enter or select a value in the **Offset account** field.

    > [!NOTE]
    > If an offset account is assigned to a counting reason code, when you post a counting journal uses has that counting reason code, the value is posted against the assigned offset account instead of the default inventory posting profile account.

### <a name="reason-groups"></a>Set up counting reason code groups

*Counting reason code groups* can be used as part of the *Adjustment in* and *Adjustment out* menu items in the Warehouse Management mobile app to limit the list of counting reason codes. (For more information about counting reason code groups, see the [Set up mobile device menu items for adjustment in and adjustment out](#setup-adjustment-in-out) section later in this article.)

1. Go to **Inventory management** \> **Setup** \> **Inventory** \> **Counting reason code groups**.
1. On the Action Pane, select **New** to add a group.
1. Set the **Counting reason group** and **Group description** fields for the new group.
1. On the Action Pane, select **Save**.
1. In the **Details** section, select **New** on the toolbar to add a row to the grid. Then set the **Counting reason code** field for the new row. 
1. Repeat the previous step to assign more codes as required. If you must remove a code from the group, select it, and then select **Delete** on the toolbar.

### Set up reason codes for mobile device menu items

You can configure reason codes for the following on-hand adjustment types:

- Cycle Count
- Spot Count
- Threshold Count
- Adjustment In
- Adjustment Out

In most cases, you can define the following information for each relevant mobile device menu item:

- Whether the reason code is shown to the mobile device worker during counting.
- The default reason code that is shown on a mobile device menu item.
- Whether the user can edit the reason code.

#### Set up mobile device menu items for a counting process

To set up a mobile device menu item for a counting process, follow these steps.

1. Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu items**.
1. Select the relevant menu item in the list pane, or create a new menu item.
1. On the Action Pane, select **Cycle counting**.
1. In the **Default counting reason code** field, set the default reason code that should be recorded when the mobile device menu item is used to do counting.
1. In the **Display counting reason code** field, select one of the following values:

    - *Line* – Show the reason code after each variance is recorded.
    - *Hide* – Don't show the reason code.

1. Set the **Edit counting reason code** to *Yes* to allow the worker to edit the reason code when it's shown on the mobile device during counting. Set it to *No* to prevent the worker from editing the code.

> [!NOTE]
> The **Cycle counting** button can be enabled on any mobile device menu item where counting can be done. Examples include the menu items for spot counts, user-directed work, and system-directed work.

#### <a name="setup-adjustment-in-out"></a>Set up mobile device menu items for adjustment in and adjustment out

To set up a mobile device menu item for adjustment in or adjustment out, follow these steps.

1. Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu items**.
1. On the Action Pane, select **New** to create a menu item.
1. Set the **Mobile item name** and **Title** fields for the new menu item.
1. Set the **Mode** field to *Work*.
1. Set the **Use existing work** option to *No*.
1. In the **Work creation process** field, select *Adjustment in* or *Adjustment out*.
1. On the **General** FastTab, set the following fields. (All these fields are added when you select *Adjustment in* or *Adjustment out* in the **Work creation process** field.)

    - **Use process guide** – If you're creating an *Adjustment out* process, be sure to set this option to *Yes*. If you're creating an *Adjustment out* process, this option is always set to *Yes*.
    - **Default counting reason code** – Set the default reason code that should be recorded when the mobile device menu item is used to do counting.
    - **Display counting reason code** – Select one of the following values:

        - *Line* – Show the reason code after each variance is recorded.
        - *Hide* – Don't show the reason code.

    - **Edit counting reason code** – Set this option to *Yes* to allow the worker to edit the reason code when it's shown on the mobile device during counting. Set it to *No* to prevent the worker from editing the code.
    - **Counting reason code group** – Select a reason code group if you want to limit the list of options that is presented to workers. For information about how to set up reason code groups, see the [Set up counting reason code groups](#reason-groups) section earlier in this article. 

> [!NOTE]
> When you assign a counting reason code group to *Adjustment in* and *Adjustment out* menu items where the **Use process guide** option is set to *Yes*, you can get a limited list of the counting reason codes as part of the processing in the Warehouse Management mobile app.
>
> The **Use process guide** option can also help prevent large adjustment quantities from occurring by mistake. (For example, a worker might accidentally scan a bar code of an item number instead of a quantity value.) To set this up functionality, set the **Use process guide** option to *Yes* for each relevant menu item. Then go to **Warehouse management \> Setup \> Worker**, and set the **Adjustment quantity limit** field for each relevant warehouse worker to specify the maximum adjustment quantity that the worker can register.

## Processing that uses counting reason codes

When workers use the Warehouse Management mobile app, the reason codes are recorded. Unless a counting approval process has been defined, the recorded reason codes are immediately used as part of the counting journal posting that follows.

### Cycle count approvals

Before a count is approved, the worker can change the reason code that is associated with the count. When the count is approved, the reason code is entered on the counting journal lines.

#### Modify reason codes for cycle count approvals

To modify a cycle count approval, follow these steps.

1. Go to **Warehouse management** \> **Cycle counting** \> **Cycle count work pending review**.
1. Select a cycle count in the grid.
1. On the Action Pane, on the **Work** tab, select **Cycle counting**. Then, in the **Reason code** field, select a new reason code.

Reason codes are added to the journal lines in counting journals of the *Counting journal* type.

1. Go to **Inventory management** \> **Journal entries** \> **Item counting** \> **Counting**.
2. In the line details of the counting journal, in the **Counting reason code** field, select the reason code that matches your current situation.

### View the reason codes recorded in the counting history

To view the reason codes that have been recorded in the counting history, follow these steps.

1. Go to **Inventory management** \> **Inquiries and reports** \> **Counting history**.
1. Select an item count record in the list pane.
1. In the **Counting reason code** field, view the counting history that has been recorded through a reason code.

### Use reason codes for quantity adjustment or online counting

To use a reason code for a quantity adjustment or online counting, follow these steps.

1. Go to **Inventory management \> Inquiries and reports \> On-hand list**.
1. On the Action Pane, select **Quantity adjustment**.
1. Select **Quantity adjustment**, and then, in the **Counting reason code** field, select a reason code.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
