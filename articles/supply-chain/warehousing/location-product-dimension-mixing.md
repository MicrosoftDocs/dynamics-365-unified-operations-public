# Location product dimension mixing

## About

This Location profile functionality enables better location management when using product variants or products with dimensions, such as with the fashion industry. It allows you to decide whether configurations, colors, style, and sizes can be mixed on a specific **Location profile**, or if only one, or a combination of some of those dimensions, can be put to the same location.

## Enable the Location product dimension mixing feature

Before you can use this feature, it must be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - *Warehouse management*
- **Feature name** - *Location product dimension mixing*

## Setup

Every location in the warehouse needs to have a location profile associated with it that describes the properties of the location. Therefore, all locations with the same location profile will be enabled to allow product dimension mixing when it has been setup.

### Location Profiles - Allow product dimension mixing

1. Go to **Warehouse management > Setup > Warehouse > Location profiles**.
1. Select **BULK** from the Location profiles list.
1. Select **Edit** in the Toolbar.
1. In the **General** FastTab make the following edit:
    - **Enable location product dimension specific mixing** - *Yes*
    - Note: this can only be enabled when **Allow mixed items** is set to *No*.

1. Expand the **Allowed product dimension mixing** FastTab and select the following:
    - **Size** - *Yes*
    - In this scenario we are only enabling mixing of products with different **Size** dimensions. The other available options are:
        - **Configuration**
        - **Color**
        - **Style**

1. Select **Save**.

### Create new product master and product variants

1. Go to **Product information management > Products > Product masters**.
1. Select **New** in the Action Pane to create a new product master.
1. In the **New product** FlyOut enter the following:
    - **Product type** - *Item*
    - **Product subtype** - *Product master*
    - **Product number** - *B0001*
    - **Product name** - *B0001 Size*
    - **Product dimension group** – *Size*
    - **Configuration technology** - *Predefined variant*

1. Select **OK**.
1. On the **Product details** form, **General** FastTab select the following:
    - **Generate variants automatically** - *Yes*
    - **Size group** - *CASUALDHIR*

1. To view the predefined variants, in the Action Pane select **Product variants**.
1. The **Product variants** form opens with list of variants from the **Size group** configuration.

### Release to Company USMF

1. In the Action Pane select **Release products**.
1. On the **Select products to release** form confirm that **Product number** - *B0001* is in the list and select **Next**.
1. Select **Next** to confirm the product variants to release.
1. On the **Select companies to release to** form, select *USMF*.
1. Select **Next** to confirm the selection.
1. On the **Confirm selection** form select **Finish** to complete the release.
1. A message saying **Operation completed** is generated.

### Update Released Product in Company USMF

1. Ensure your are logged in to Company **USMF**.
1. Go to **Product information management > Products > Released products** to complete the released product creation.
1. On the **Released product details** list page, find and select **Item number** - *B0001* to open **Released product details**.
1. Select **Edit** in the Action Pane.
1. In the **General** FastTab confirm or enter the following:
    - **Item model group** – *FIFO*

1. Select the **Product** tab in the Action Pane.
1. In the **Set up** group select **Dimension groups** and enter the following:
    - **Storage dimension group** - *Ware*
    - **Tracking dimension group** - *None*
    - Select **OK**

1. Next select **Reservation hierarchy** in the **Set up** group and enter the following:
    - **Reservation hierarchy** - *Default*
    - Select **OK**

1. Note that in the **General** FastTab **Administration** group, your selections have been updated.
1. In the **Purchase** FastTab enter the following:
    - **Price** - *10*

1. In the **Manage costs** FastTab enter the following:
    - **Item group** – *Audio*

1. In the **Purchase** FastTab enter the following:
    - **Price** - *10*

1. In the **Warehouse** FastTab enter the following:
    - **Unit sequence group ID** – *ea*

1. Select **Save**.

### Location directives

1. Go to **Warehouse management > Setup > Location directives**. 1. In the left column heading, change **Work order type** to *Purchase orders*.
1. Then select the Location Directive **Name** - *24 PO Direct*.
1. On the **Location Directive Actions** FastTab Toolbar, select **New** to add a new line. Enter the following:
    - **Sequence number** – *1*
        - It should be in front of the already existing line, use the **Move up** - **Move down** buttons in the Toolbar, or edit the existing line's **Sequence number** to *2* to make the change.
    - **Name** – *Put to BULK Location profile*
    - **Fixed location usage** – *Fixed and non-fixed locations*
    - **Allow negative inventory** – *No* (blank)
    - **Batch enabled** – *No* (blank)
    - **Strategy** – *None*

1. On the line you created, select **Edit query** in the Toolbar.
1. On the query form, **Range** tab, select **Add** to add a new line on Range. enter the following:
    - **Table** – *Locations*
    - **Derived table** – *Locations*
    - **Field** – *Location profile ID*
    - **Criteria** - *BULK*

1. Select **OK**.
1. Select **Save** in the **Location directives** Action Pane.

> [!NOTE]
> If using Location Directive Strategy *Consolidate*, the *Allow product dimension mixing* setup will be overridden and items will be put to the same location even if not allowed by the setup.

### Mobile Device Menu Items

1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu items**.
1. Select **New** in the Action Pane, and create a new menu item to be used for sorting.
1. In the Header, enter the following:
    - **Menu item name** – *PO line receiving*
    - **Title** – *PO line receiving*
    - **Mode** – *Work*
    - **Use existing work** – *No*

1. In **General** FastTab, select the following:
    - **Work creation process** – *Purchase order line receiving and putaway*
    - **Generate license plate** – *Yes*

1. Select **Save**.

### Mobile device menu

1. Go to **Warehouse management >  Setup > Mobile device > Mobile device menu**.
1. Select **Inbound** from the list of menus.
1. Select **Edit** in the Toolbar.
1. In the **Available Menus And Menu Items** scroll until you find the menu item **PO line receiving**.
1. Select **PO line receiving** in the list then select the arrow button **(->)** to move the menu item into the **Menu Structure** list. and add the newly created menu item to the desired menu.
1. Select **Save**.

## Scenario

This demo will demonstrate how two different product variants can still be put to the same location when the Location profile does not allow mixed items but *Allow product dimension mixing* is enabled. In this case, we will use the variant *Size* as the criteria.

Before starting, ensure there are empty locations in Warehouse 24 with **Location profile** *BULK*.

### Create Purchase order

Create a purchase order with three lines: two lines with the same product number, but different **Size** variants, and a third line with a different product that has no variants.

1. Go to **Accounts payable > Purchase orders > All purchase orders**.
1. Select **New** in the Action Pane.
1. In the **Create purchase order** FlyOut enter the following:
    - **Vendor account** - *1001*
    - **Warehouse** - *24*

1. Select **OK**.
1. The purchase order is created with a new line in the **Purchase order lines** FastTab. Make note of the purchase order number. Enter the following:
    - **Item number** - *B0001*
    - **Size** *L*
    - **Quantity** - *2*

1. Select **Add line** in the Toolbar to add another line with the following:
    - **Item number** - *B0001*
    - **Size** *XL*
    - **Quantity** - *2*

1. Select **Add line** in the Toolbar to add another line with the following:
    - **Item number** - *A0001*
    - **Quantity** - *1*

1.Select **Save**.

### Mobile App PO Line Receiving

1. Log in to the Mobile app with a user enabled for **Warehouse** - *24*.
1. Select the **Inbound** menu.
1. Select **PO Line receiving**.
1. Select **PONUM** to enter the purchase order number.
1. Enter the *Purchase order number* and confirm your entry by selecting the button at the bottom of the screen.
1. Next you will enter the line number from the purchase order to be received.
1. Select **LINENUM** and then select **1** from the number pad and confirm.
1. Next enter the quantity to be received. Select the **+** button two times to increase **Qty** the received quantity to be *2*.
    - Register your entry by selecting the button at the bottom of the screen.
    - Next confirm your entry by selecting the button again.

1. View the information on the **Purchase orders: Put** screen. This is the **Work** created for the put away (Work 1).
    - The Location where the received item will be Put Away, License plate, Item, Size and Quantity of the PO Line Receiving task just completed will be displayed.
    - Confirm the put away work.

1. Repeat this for PO line 2.
    - This time specify a **Quantity** of *1* and confirm.
    - New Putaway Work (Work 2) is created to the same location as Work 1.
    - Confirm the put away.

1. Repeat once again for PO line 2.
    - Specify the remaining **Quantity** *1* and confirm.
    - New Putaway Work (Work 3) is created to the same location as Work 1 and Work 2.
    - This is due to the Consolidation Location Directive strategy and the *Allow product dimension mixing* allowing the *Size* to be mixed on a location.

1. Receive the last PO line (line 3).
    - Specify **Quantity** *1* for **Item** *A0001* and confirm.
    - New Putaway Work (Work 4) is created to a different location than Line 1 and Line 2.
    - This is because the location profile does not allow mixed products, but does allow mixed dimensions of the same product master.

1. Select the menu button in the header (some call it the hamburger) then select **Cancel** to exit **PO Line Receiving**.

> [!TIP]
> This Scenario can be repeated with not allowing any of the Product dimension to be mixed (in this case, disable *Size* under *Allow product dimension mixing*). When receiving the PO in that case, each Product variant will be put to a new location.
