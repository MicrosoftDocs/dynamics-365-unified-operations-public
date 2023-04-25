---
# required metadata

title: Location product dimension mixing
description: This article provides information about location product dimension mixing. This location profile functionality helps improve location management when product variants or products that have dimensions are used, such as in the fashion industry. It lets you decide whether configurations, colors, styles, and sizes can be mixed for a specific location profile, or whether just one of these dimensions or a combination of them can be put to the same location.
author: Mirzaab
ms.date: 07/01/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: WHSLocationProfile, WHSReservationHierarchy, WHSInventTableReservationHierarchy
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for articles migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2020-07-01
ms.dyn365.ops.version: 10.0.7
---

# Location product dimension mixing

[!include [banner](../includes/banner.md)]

Location product dimension mixing is location profile functionality that helps improve location management when product variants or products that have dimensions are used, such as in the fashion industry. It lets you decide whether configurations, colors, styles, and sizes can be mixed for a specific location profile, or whether just one of these dimensions or a combination of them can be put to the same location.

## Turn the Location product dimension mixing feature on or off

To use the functionality described in this article, the *Location product dimension mixing* feature must be turned on for your system. As of Supply Chain Management 10.0.25, this feature is mandatory and can't be turned off. If you're running a version older than 10.0.25, then admins can turn this functionality on or off by searching for the *Location product dimension mixing* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

## Setup

Every location in the warehouse needs to have a location profile associated with it that describes the properties of the location. Therefore, all locations that use the same location profile will be able to allow product dimension mixing after it has been set up.

### Configure location profiles to allow product dimension mixing

1. Go to **Warehouse management \> Setup \> Warehouse \> Location profiles**.
1. In the list of location profiles, select **BULK**.
1. On the Action Pane, select **Edit**.
1. On the **General** FastTab, set the **Enable location product dimension specific mixing** option to *Yes*.

    > [!NOTE]
    > You can set this option to *Yes* only if the **Allow mixed items** option is set to *No*.

1. On the **Allowed product dimension mixing** FastTab, set the **Size** option to *Yes*. In the scenario that is described in this article, mixing can be done only for products that have different **Size** dimensions. However, other options are also available.
1. Select **Save**.

### Create a new product master and product variants

1. Go to **Product information management \> Products \> Product masters**.
1. On the Action Pane, select **New** to create a product master.
1. In the **New product** dialog box, set the following values:

    - **Product type:** *Item*
    - **Product subtype:** *Product master*
    - **Product number:** *B0001*
    - **Product name:** *B0001 Size*
    - **Product dimension group:** *Size*
    - **Configuration technology:** *Predefined variant*

1. Select **OK**.
1. On the **Product details** page, on the **General** FastTab, set the following values:

    - **Generate variants automatically:** *Yes*
    - **Size group:** *CASUALDHIR*

1. To view the predefined variants, on the Action Pane, select **Product variants**.

    The **Product variants** page appears and shows a list of variants from the configuration of the size group.

### Release products to the USMF company

1. On the Action Pane, select **Release products**.
1. On the **Select products to release** page, confirm that product number *B0001* is in the list, and then select **Next**.
1. Select **Next** to confirm the product variants to release.
1. On the **Select companies to release to** page, select *USMF*, and then select **Next** to confirm the selection.
1. On the **Confirm selection** page, select **Finish** to complete the release.

    You receive an "Operation completed" message.

### Update a released product in the USMF company

1. Make sure that you're signed in to the **USMF** company.
1. Go to **Product information management \> Products \> Released products** to finish creating the released product.
1. Find and select item number *B0001* to open the **Released product details** page.
1. On the Action Pane, select **Edit**.
1. On the **General** FastTab, make sure that the **Item model group** field is set to *FIFO*.
1. On the Action Pane, on the **Product** tab, in the **Set up** group, select **Dimension groups**.
1. Set the following values:

    - **Storage dimension group:** *Ware*
    - **Tracking dimension group:** *None*

1. Select **OK**.
1. On the Action Pane, on the **Product** tab, in the **Set up** group, select **Reservation hierarchy**.
1. Set the **Reservation hierarchy** field to *Default*, and then select **OK**.
1. On the **General** FastTab, in the **Administration** section, notice that your selections have been updated.
1. On the **Purchase** FastTab, in the **Price** field, enter *10*.
1. On the **Manage costs** FastTab, in the **Item group** field, enter *Audio*.
1. On the **Purchase** FastTab, in the **Price** field, enter *10*.
1. On the **Warehouse** FastTab, in the **Unit sequence group ID** field, enter *ea*.
1. Select **Save**.

### Create a location directive

1. Go to **Warehouse management \> Setup \> Location directives**.
1. In the left pane, in the **Work order type** field, select *Purchase orders*.
1. In the list, select the location directive that is named *24 PO Direct*.
1. On the **Location Directive Actions** FastTab, select **New** to add a line to the grid.
1. On the new line, set the following values:

    - **Sequence number:** *1*

        The new line should be in front of the previously existing line. To make the change, use the **Move up** and **Move down** buttons on the toolbar, or change the existing line's **Sequence number** value to *2*.

    - **Name:** *Put to BULK Location profile*
    - **Fixed location usage:** *Fixed and non-fixed locations*
    - **Allow negative inventory:** *Clear this check box (=No)*
    - **Batch enabled:** *Clear this check box (=No)*
    - **Strategy:** *None*

1. While the new line is still selected, select **Edit query** above the grid.
1. In the query dialog box, on the **Range** tab, select **Add** to add a line to the grid.
1. On the new line, set the following values:

    - **Table:** *Locations*
    - **Derived table:** *Locations*
    - **Field:** *Location profile ID*
    - **Criteria:** *BULK*

1. Select **OK**.
1. On the **Location directives** page, on the Action Pane, select **Save**.

> [!NOTE]
> On the **Location Directive Actions** FastTab **Strategy** field, if you use the *Consolidate* location strategy, the setup of the **Allowed product dimension mixing** FastTab on the **Location profiles** will be overridden, and items will be put to the same location even if this behavior isn't allowed by the setup.

### Create a mobile device menu item

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. On the Action Pane, select **New** to create a menu item to use for sorting.
1. In the header, set the following values:

    - **Menu item name:** *PO line receiving*
    - **Title:** *PO line receiving*
    - **Mode:** *Work*
    - **Use existing work:** *No*

1. On the **General** FastTab, set the following values:

    - **Work creation process:** *Purchase order line receiving and putaway*
    - **Generate license plate:** *Yes*

1. Select **Save**.

### Configure the mobile device menu

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu**.
1. In the list of menus, select **Inbound**.
1. On the Action Pane, select **Edit**.
1. In the **Available Menus And Menu Items** list, find and select the **PO line receiving** menu item.
1. Select the right arrow button to move the **PO line receiving** menu item to the **Menu Structure** list. In this way, you add your new menu item to the selected menu.
1. Select **Save**.

## Scenario

This demo scenario shows how two different product variants can be put to the same location when the location profile doesn't allow for mixed items, but the *Location product dimension mixing* feature is enabled. In this case, you will use the **Size** variant as the criterion.

Before you begin, make sure that there are empty locations in warehouse *24* that use the *BULK* location profile.

### Create a purchase order

You will create a purchase order that has three lines: two lines for the same product number but different **Size** variants, and a third line for a different product that has no variants.

1. Go to **Accounts payable \> Purchase orders \> All purchase orders**.
1. On the Action Pane, select **New**.
1. In the **Create purchase order** dialog box, set the following values:

    - **Vendor account:** *1001*
    - **Warehouse:** *24*

1. Select **OK**.
1. The purchase order is created, and a new line is added on the **Purchase order lines** FastTab. Make a note of the purchase order number.
1. On the new line, set the following values:

    - **Item number:** *B0001*
    - **Size** *L*
    - **Quantity:** *2*

1. Select **Add line** above the grid to add a second purchase order line, and set the following values:

    - **Item number:** *B0001*
    - **Size** *XL*
    - **Quantity:** *2*

1. Select **Add line** to add a third purchase order line, and set the following values:

    - **Item number:** *A0001*
    - **Quantity:** *1*

1.Select **Save**.

### Receive purchase order lines in the Warehouse Management mobile app

1. Sign in to the Warehouse Management mobile app as a user who is enabled for warehouse *24*.
1. Select the **Inbound** menu.
1. Select **PO Line receiving**.
1. Select the **PONUM** field, and then enter the purchase order number.
1. Confirm your entry by selecting the confirm button ( ✔ ) at the bottom of the page.
1. Enter the line number from the purchase order that is being received. Select the **LINENUM** field, and then use the number pad to enter *1*.
1. Confirm your entry.
1. Enter the quantity to receive. Select the plus sign (**+**) button two times to increase the value in the **Qty** field to *2*.
1. Register your entry by selecting the button ( ✔ ) at the bottom of the page, and then confirm your entry by selecting the button ( ✔ ) again.
1. View the information on the **Purchase orders: Put** page. This page shows the work that has been created for the put-away (Work 1).

    The location where the received item will be put away, the license plate, the item, the size, and the quantity of the **PO Line receiving** task that you just completed are shown.

1. Confirm the put-away work.
1. Repeat the steps 4 through 11 for the purchase order line 2. However, in step 8, specify a quantity of *1*.

    New put-away work (Work 2) is created for the same location as Work 1.

1. Repeat the steps 4 through 11 again for purchase order line 2. In step 8, specify the remaining quantity of *1*.

    New put-away work (Work 3) is created for the same location as Work 1 and Work 2. This behavior occurs because the *Consolidate* location directive strategy is used, and the **Allowed product dimension mixing** FastTab on the *Bulk* **Location profiles** setup allows the **Size** variant to be mixed on a location.

1. Repeat the steps 4 through 11 for purchase order line 3. In step 8, specify a quantity of *1* for item number *A0001*.

    New put-away work (Work 4) is created for a different location than the location that is used for purchase order lines 1 and 2. This behavior occurs because the location profile doesn't allow for mixed products, but it does allow for mixed dimensions of the same product master.

1. Select the Menu button at the top of the page (sometimes referred to as the hamburger or the hamburger button), and then select **Cancel** to exit **PO Line receiving**.

> [!TIP]
> You can repeat this scenario, but this time, set **Size** - *No* under the **Allow product dimension mixing** FastTab on the *BULK* **Location profiles**, so that none of the product dimensions can be mixed. In this case, when you receive the purchase order, each product variant will be put to a new location.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]