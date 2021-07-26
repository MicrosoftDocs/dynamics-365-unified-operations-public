---
# required metadata

title: Reason codes for inventory counting
description: This topic describes how to set up and apply reason codes for counting tasks.
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

Reason codes let you analyze the results of a counting process and any discrepancies that occur during that process. You can specify the reason for doing the count, such as a broken pallet or a stock adjustment that is based on inventory samples, and at the same time use the adjustment functionality to post the value of on-hand inventory adjustments to the appropriate offset account based on the reason for each inventory adjustment.

## Recommendation

Before you set up the system, we recommend that you define a strategy for working with reason codes. For example, try to answer the following questions:

- Should reason codes be mandatory on warehouses?
- Should reason codes be mandatory or optional on some items?
- How many reason codes do you require?
- Do you need to pre-select a limited list of reason codes for adjustments?
- How should users of barcode scanners use reason codes? Should the reason codes be preselected, mandatory, or not editable?
- Do warehouse workers require different reason code behavior on mobile scanners? If the answer is yes, you can create more menu items and assign them to different people.
- Should the reason codes drive financial offset account posting?

## Enable reason code features on your system

[!INCLUDE [preview-banner-section](../../includes/preview-banner-section.md)]

If you don't see all of the features described in this topic on your system, then you probably need to enable the *Post on-hand adjustments using configurable reason codes connected to offset accounts* feature. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on if it's required. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Warehouse management*
- **Feature name:** *Post on-hand adjustments using configurable reason codes connected to offset accounts*

## Set up reason codes

### Set up reason code policies

You can create multiple reason code policies, which will control when and how counting reason codes will be applied. Each reason code policy can have one of two counting reason code types (*Optional* or *Mandatory*). Counting reason code policies can be used at the warehouse level or the item level.

To create a reason code policy:

1. Go to **Inventory management** \> **Setup** \> **Inventory** \> **Counting reason code policies**.
1. Select **New** on the Action Pane to add a new policy to the grid.
1. Enter a **Name** for the new policy.
1. In the **Counting reason code type** field, select either *Mandatory* or *Optional* to specify whether selecting a reason code should be an optional or mandatory action in one of the following inventory adjustment processes:

    - Cycle Count (mobile device)
    - Spot Count (mobile device)
    - Threshold Count (mobile device)
    - Adjustment In (mobile device)
    - Adjustment Out (mobile device)
    - Counting Journal (rich client)
    - Quantity adjustment/Online counting (rich client)

You can set up reason code policies both for individual warehouses and for products. The reason code setup for a product can overrule the setup for its warehouse.

> [!Note]
> For warehouses and items where **Counting reason code policy** is set to a *Mandatory* policy, the counting journal can't be completed and closed until a reason code is provided. See also the next section.

### Assign counting reason code policies to warehouses

To assign a counting reason code policy to a warehouse:

1. Select **Inventory management** \> **Setup** \> **Inventory breakdown** \> **Warehouses**.
1. Select a warehouse in the list pane.
1. On the Action Pane, open the **Warehouse** tab and, from the **Set Up** group, select **Counting reason code policy**. The select one of the following types of values in the **Assign counting reason code policy** drop-down dialog box:

    - Enter no value (or delete the value) to use the policy set up for each item to determine whether counting journals are mandatory for it.
    - Select a reason policy that has **Counting reason code type** set to *Mandatory* to require a reason code on counting journals for the warehouse.
    - Select a reason policy that has **Counting reason code type** set to *Optional* to require a reason code on counting journals for the warehouse.

### Assign counting reason code policies to products

To assign a counting reason code policy to a product:

1. Select **Product information management** \> **Products** \> **Released products**.
1. Select a product in the grid.
1. On the Action Pane, open the **Product** tab and, from the **Set Up** group, select **Counting reason code policy**. The select one of the following types of values in the **Assign counting reason code policy** drop-down dialog box:

    - Enter no value (or delete the value) to use the policy set up for the warehouse to determine whether counting journals are mandatory for the product.
    - Select a reason policy that has **Counting reason code type** set to *Mandatory* to require a reason code on counting journals for the product. This setting overrides any reason code setting at the warehouse level.
    - Select a reason policy that has **Counting reason code type** set to *Optional* to require a reason code on counting journals for the product. This setting overrides any reason code setting at the warehouse level.

### Set up counting reason codes

To set up your counting reason codes:

1. Go to **Inventory Management** \> **Setup** \> **Inventory** \> **Counting reason codes**
1. On the Action Pane, select **New** to add a new row to the grid.
1. For the new row, assign a **Counting reason code** and **Description**.
1. To assign an *offset account*, key-in or select a value in the **Offset account** field

    > [!Note]
    > When you post a counting journal that has a counting reason code with an offset account defined, the value will be posted against the assigned **Offset account** rather than the default inventory posting profile account.

### Set up counting reason code groups

*Counting reason code groups* can be used as part of the Warehouse Management mobile app *Adjustment in* and *Adjustment out* menu items to limit the list of counting reason codes. (For more information about counting reason code groups, see [Set up mobile device menu items for adjustment in and adjustment out](#setup-adjustment-in-out) later in this topic.)

1. Go to **Inventory Management** \> **Setup** \> **Inventory** \> **Counting reason code groups**
1. Select **New** on the Action Pane to add a new group.
1. Enter a **Counting reason group** and **Group description** for the new group.
1. Select **Save** on the Action Pane.
1. In the **Details** section, select **New** from the toolbar to add a new row to the grid. Then select a **Counting reason code** for the new row. 
1. Repeat the previous step to assign more codes as needed. Select **Delete** from the toolbar to remove a selected code from the group if necessary.

### Set up reason codes for mobile device menu items

You can configure reason codes for the following on-hand adjustment types:

- Cycle Count
- Spot Count
- Threshold Count
- Adjustment In
- Adjustment Out

In most cases you can configure each relevant mobile device menu item with the following information:

- Whether the reason code is shown to the mobile device worker during counting.
- The default reason code that is shown on a mobile device menu item.
- Whether the user can edit the reason code.

#### Set up mobile device menu items for a counting process

To set up a mobile device menu item for a counting process:

1. Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu items**.
1. Select the relevant menu item from the list pane (or create a new one).
1. On the **Cycle count** tab, select **Cycle counting**. <!--KFM: I don't see this. Do you mean the Action Pane? Similar settings are *sometimes* available on the **General** tab. Not sure... -->
1. In the **Default counting reason code** field, set the default reason code that should be recorded when counting is done by using the mobile device menu item.
1. In the **Display counting reason code** field, select one of the following values:
    - *Line* – Shows the reason code after each variance is recorded.
    - *Hide*  – Doesn't show the reason code.
1. Set **Edit counting reason code** to *Yes* to allow the worker to edit the reason code when it's shown on the mobile device during counting. Set to *No* to prevent the worker from editing the code.

> [!NOTE]
> The **Cycle counting** button can be enabled on any mobile device menu item where counting can be done. Example include the menu items for spot counts, user-directed work, and system-directed work.

#### <a name="setup-adjustment-in-out"></a> Set up mobile device menu items for adjustment in and adjustment out

To set up a mobile device menu item for adjustment in or adjustment out:

1. Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu items**.
1. Select **Adjustment in** or **Adjustment out**. <!--KFM: Where can I select this? Am I actually creating a new menu item here? -->
1. Set the **Use existing work** option to *No*.
1. In the **Work creation process** field, select *Adjustment in* or *Adjustment out*. Either of these settings will add the following fields to the **General** FastTab: 
    - **Default counting reason code** – Set the default reason code that should be recorded when counting is done by using the mobile device menu item.
    - **Display counting reason code** – Select one of the following values:
        - *Line* – Shows the reason code after each variance is recorded.
        - *Hide* – Doesn't show the reason code.
    - **Edit counting reason code** – Set to *Yes* to allow the worker to edit the reason code when it's shown on the mobile device during counting. Set to *No* to prevent the worker from editing the code.
    - **Counting reason code group** <!--KFM: Describe this setting. -->

> [!Note]
> For *Adjustment in* and *Adjustment out* menu items that have **Use process guide** enabled, when you are assigning a **Counting reason code group**, you can get a limited list of the counting reason codes as part of the Warehouse Management mobile app processing. <!--KFM: This isn't clear. It might make more sense to describe this in the field list in the above procedure. -->
>
> The **Use process guide** option can also help prevent large adjustment quantities from occurring by mistake (which can happen, for example, if a worker accidentally scans a barcode of an item number rather than a quantity value). To set this up, enable the **Use process guide** option for each relevant menu item, and then define an **Adjustment quantity limit** for each relevant warehouse worker (at **Warehouse management \> Setup \> Worker**) to establish the maximum adjustment quantity each worker can register.

## Processing with the use of counting reason code

When workers are using the Warehouse Management mobile app, the reason codes are recorded and used right away as part of the following counting journal posting unless a counting approval process has been defined.  

### Cycle count approvals

Before a count is approved, the worker can change the reason code that is associated with the count. When the count is approved, the reason code is entered on the counting journal lines.

#### Modify cycle count approvals

To modify a cycle count approval:

1. Go to **Warehouse management** \> **Cycle counting** \> **Cycle count work pending review**.
1. Select a cycle count on the grid.
1. On the Action Pane, open the **Work** tab and select **Cycle counting**. Then, in the **Reason code** field, select a new reason code.

Reason codes are added to the journal lines in counting journals of the *Counting journal* type.

1. Go to **Inventory management** \> **Journal entries** \> **Item counting** \> **Counting**.
2. In the line details of the counting journal, in the **Counting reason code** field, select an option. <!--KFM: What are we doing here? What is this procedure for? What option might I choose? -->

### View the counting history as it's recorded by reason codes

To view the counting history as it's recorded by reason codes: <!--KFM: I don't understand what we are doing here. -->

1. Go to **Inventory management** \> **Inquiries and reports** \> **Counting history**.
1. Select an item count record in the list pane.
1. In the **Counting reason code** field, view the counting history that has been recorded through a reason code.

### Use reason codes for quantity adjustment or online counting

To use a reason code for a quantity adjustment or online counting:

1. Go to **Inventory management \> Inquiries and reports \> On-hand list**.
1. On the Action Pane, select **Quantity adjustment**.
1. Select **Quantity adjustment**, and then, in the **Counting reason code** field, select a reason code.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]