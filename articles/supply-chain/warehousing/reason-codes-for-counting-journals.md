Reason codes for inventory counting 
====================================

Reason codes enable you to analyze the results of and discrepancies within a
counting process. You can identify the reason for a counting such as a broken
pallet or a stock adjustment based on inventory samples.

## Recommendation

We recommend that you set a strategy for working with reason codes before you
set up the system.

For example, try to determine the following:

-   Should reason codes be mandatory on the warehouses?

-   Should reason codes be mandatory or optional on some of the items?

-   How many different reason codes will you need?

-   How should users of barcode scanners use reason codes? Should the reason codes
    be pre-selected, mandatory or not editable?

-   Do warehouse workers need different reason code behavior on mobile scanners?
    In that case, more menu items can be created and assigned to different
    people.

## Where reason codes apply

You can create multiple reason code policies with two different counting reason
policies for each. The counting reason code policies can be used on the
warehouse or the item level.

## Set up reason code policies

1.  Select **Inventory management** \> **Setup** \> **Inventory** \> **Counting
    reason code policies** to create a new reason code policy.

2.  In the **Counting reason code type** list, select **Mandatory** or
    **Optional** to define if the selection of a reason code should be an
    optional or a mandatory action in one of the following counting journals:

-    Cycle Count (mobile device)

-   Spot Count (mobile device)

-   Threshold Count (mobile device)

-   Adjustment In (mobile device)

-   Adjustment Out (mobile device)

-   Counting Journal (rich client)

Reason codes can also be set up for individual warehouses and for products. The
reason code setup for warehouses may be disregarded by settings on the product
level.

## Mandatory reason codes 
If the **Mandatory** reason code parameter is set in the configuration of reason
codes for warehouses or items, the counting journal cannot be completed and
closed until a reason code is provided.

### Set up reason codes for warehouses

1.  Select **Inventory Management** \> **Setup** \> **Inventory breakdown** \>
    **Warehouses.**

2.  In the **Counting reason code policy** field on the **Warehouse** tab,
    select one of the following options:

-   **Blank –** Select this option to use the parameter that is set up for the
    item to determine if counting journals are mandatory for the product.

-   **Mandatory –** Select this option to require a reason code on counting
    journals for the warehouse.

-   **Optional** –Select this option if a reason code should not be a
    requirement on counting journals for the warehouse.

### Set up reason codes for products

1.  Select **Product information management** \> **Products** \> **Released
    products**.

2.  On the **Product** tab, click **Counting reason code policy**, and select
    one of the following options:

-   **Blank** – Select this option to use the warehouse parameter to determine
    if counting journals are mandatory for the product.

-   **Mandatory** – Select this option to always require a reason code on
    counting journals for the product. This setting will override any reason
    code setting on the warehouse level.

-   **Optional** – Select this option if a reason code should not be a
    requirement on counting journals for this product. This setting will
    override any reason code setting on the warehouse level.

### Use reason codes in counting journals

In a counting journal, you can add reason codes for counts of the following
types:

-   Cycle Count

-   Spot Count

-   Threshold Count

-   Adjustment In

-   Adjustment Out

Reason codes are added to the journal lines on counting journals of the type
**Counting journal**.

1.  Select **Inventory management\>Journal entries \> Item counting \>
    Counting**.

2.  On the line details of the counting journal, select an option in the
    **Counting reason code** field.

### View counting history as recorded by reason codes

-   Select **Inventory management** -\> **Inquiries -**\> **Counting history**
    and in the **Counting reason code** field, see the counting history that has
    been recorded with a reason code.

### Use a reason code for a quantity adjustment

1.  From the On-hand inventory page, click **Adjust quantity**. The **On-hand
    inventory** page can be opened from several locations such as **Inventory
    management** \> **Inquiries and reports** \> **On-hand inventory**.

2.  Click the **Adjust quantity** button, and select a reason code in the
    **Counting reason code** field.

### Configure reason codes for mobile device menu items

You can configure reason codes for any type of counting on a mobile device menu
item. Configuration of the mobile device menu item includes:

-   Whether the reason code is displayed to the mobile device worker during
    counting.

-   The default reason code displayed on a mobile device menu item.

-   Whether the user can edit the reason code.

### Set up reason codes on a mobile device

1.  Select **Warehouse management \> Setup \> Mobile device \> Mobile device
    menu items**.

2.  Select the **Cycle count** tab, and click **Cycle counting**.

3.  In the **Default counting reason code** field, set the default reason code
    to be recorded when counting using the mobile device menu item.

4.  In the **Display counting reason code** field, select **Line** to display
    the reason code after each variance is recorded, or select **Hide** to not
    display the reason code.

5.  Set the **Edit counting reason code** to either **Yes** or **No**. If set to
    yes, the worker will be allowed to edit the reason code when it is shown on
    the mobile device during counting.

[!NOTE]
The **Cycle counting** button can be enabled on any mobile device menu
item where counting is possible such as for spot counts, user directed work, and
system directed work.

## Cycle count approvals

Before approving a count, the user can change the reason code that has been
associated with the count. When the count is approved, the reason code is
populated on the counting journal lines.

### Modify cycle count approvals

1.  Select **Warehouse management** -\> **Cycle counting** \> **Cycle count work
    pending review**

2.  Click the **\> Cycle counting** button and, in the **Reason code** field,
    select a new reason code.

### Modiy the mobile device menu item for Adjustment in and Adjustment out

1.  Select **Warehouse management** \> **Setup** \> **Mobile device** \>
    **Mobile device menu items** for Adjustment in and out.

2.  Set the **Use existing work** slider to **No**.

3.  In the **Work creation process** field, select **Adjustment in**.

The following fields will be added to the mobile device menu item when
**Adjustment in** or **Adjustment out** is selected during the work creation
process:

-   Default counting reason code

-   Display counting reason code

-   Edit counting reason code
