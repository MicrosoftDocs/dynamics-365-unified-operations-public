---
title: Query data using Warehouse Management mobile app detours
description: This article describes how to configure data inquiry mobile device menu items and how to use them as part of detours.
author: perlynne
ms.date: 08/01/2022
ms.topic: article
ms.search.form: WHSMobileAppFlowStepListPage, WHSMobileAppFlowStepAddDetour,WHSMobileAppFlowStepDetourSelectFields
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: perlynne
ms.search.validFrom: 2022-08-01
ms.dyn365.ops.version: 10.0.29
---

# Query data using Warehouse Management mobile app detours

[!include [banner](../includes/banner.md)]

## Feature introduction

By providing bar code scanning capability, the Warehouse Management mobile app offers an easy and accurate way to capture data as part of your warehouse processes. But sometimes, bar codes get damaged and unreadable, or the needed data information might not exist as a bar code in your business process flows. In these cases, it can take a long time to manually key in the data and can even result in capturing incorrect data, resulting in reduced effectivity and a lower service level.

By using a flexible data inquiry process, workers can easily look up the required information as part of the embedded Warehouse Management mobile app flows, applying filtering options that only list the relevant data, thereby making manual selection faster and more accurate.

One example is the purchase order receiving flow, where a purchase order number is required to match arriving inventory. As part of this process, you can easily configure menu items to provide a card list view of the relevant purchase order numbers, making it possible to continue the receiving flow using a quick point-to-select approach. This article provides an example scenario, but this functionality can also be used within any or all your Warehouse Management mobile app flows.

## Turn on the data inquiry flow feature and its prerequisites

Before you can use the functionality described in this article, you must complete the following procedure to turn on the required features.

1. Go to **System administration \> Workspaces \> Feature management**. (For more information about how to use this workspace, see the [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).)
1. Turn on the feature that is listed in the following way:

    - **Module:** *Warehouse management*
    - **Feature name:** *Warehouse app step instructions*

    This feature is a prerequisite for the *Warehouse management app data inquiry flow* feature. For more information about the *Warehouse app step instructions* feature, see [Customize step titles and instructions for the Warehouse Management mobile app](mobile-app-titles-instructions.md). 

1. Turn on the feature that is listed in the following way:

    - **Module:** *Warehouse management*
    - **Feature name:** *Warehouse management app detours*

    This feature is a prerequisite for the *Warehouse management app data inquiry flow* feature. For more information about the *Warehouse management app detours* feature, see [Configure detours for steps in mobile device menu items](warehouse-app-detours.md).

1. If the *Warehouse management app detours* feature wasn't already turned on, then update the field names in the Warehouse Management mobile app by going to **Warehouse management \> Setup \> Mobile device \> Warehouse app field names** and selecting **Create default setup**. Repeat this step for each legal entity (company) where you use the Warehouse Management mobile app. For more information, see [Configure fields for the Warehouse Management mobile app](configure-app-field-names-priorities-warehouse.md).

1. Turn on the feature that is listed in the following way:

    - **Module:** *Warehouse management*
    - **Feature name:** *Warehouse management app data inquiry flow*

    This is the feature described in this article.

## Example scenarios

This article uses example scenarios to show how you can use the *Warehouse management app data inquiry flow* feature to improve the purchase receipt flow. The scenarios use the standard sample data, which includes a flow called **Purchase receive**. This flow starts by prompting workers to identify a purchase order number to receive against. To make it easier to identify the purchase order, you'll enhance the first page of this flow by adding following new query options as [detours](warehouse-app-detours.md):

- **Look up POs by vendor** – Opens a page that prompts the worker to enter a vendor name or part of a vendor name (which they can enter using wildcards). For example, if the worker is expecting an inbound delivery today from a vendor that includes *Tailspin* in its name, the worker can enter "Tail\*" to view a set of cards for open purchase orders that include this text. Each card has several fields that convey information about each purchase order. In addition to the vendor's name, you can design the cards to show the vendor account number, delivery date, and document status.

- **Look up POs for today** – Opens a page that doesn't ask workers to enter data, but instead shows preconfigured filters (such as today's date). The page then shows a set of cards that match the filter. Workers proceed by selecting a card for the purchase order they want to register inventory items against.

- **Look up POs by item** – Opens a page that asks the worker to scan the bar code of any item in the arrived inventory. The flow then lists all open purchase orders that contain lines for the scanned item number. To cover situations where a bar code can't be read, you could also add another detour lookup to this page that lets workers to search for item numbers within a specific purchase order.

In each case, the worker identifies a purchase order by selecting a card and then returns to the first page, which shows the selected purchase order number, making it possible for the worker to continue the inbound inventory item registration flow.

## Enable sample data

To work through the example scenarios described in this article, you must be on a system where the standard [demo data](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) is installed. Additionally, you must select the *USMF* legal entity (company) before you begin.

## Configure the mobile device menu items

To create each of the new query options you need to add to the first page of the flow, you must set them up as mobile device menu items, which you'll later make available as detours to the **Purchase receive** flow.

### Create the "Look up POs by vendor" menu item

Create the **Look up POs by vendor** menu item by following these steps:

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. Select **New** on the Action Pane to add a new mobile device menu item.
1. Make the following settings for the new item:
   - **Menu item name:** *Look up POs by vendor*
   - **Title:** *Look up POs by vendor*
   - **Mode:** *Indirect*

1. On the **General** FastTab, make the following settings:
   - **Activity code:** *Data inquiry*
   - **Use process guide:** *Yes* (Automatically selected.)
   - **Table name:** *PurchTable* (We would like to look up purchase order numbers from this table.)

1. On the Action Pane, select **Edit query**. (This action will allow you to define a query based on the selected base table, which in this case is the purchase orders.)
1. The query editor opens. On the **Range** tab, add the following lines to the grid:

    | Table | Derived table | Field | Criteria |
    |---|---|---|---|
    | Purchase orders | Purchase orders | Purchase order status | Open order |
    | Purchase orders | Purchase orders | Delivery date | (dayRange(-10,10)) |
    | Purchase orders | Purchase orders | Vendor name |  |

1. Select **OK**.

    In this example, the new menu item is configured to find open purchase orders that are expected to arrive anytime between 10 days in the past and 10 days in the future.

    In the query, the **Criteria** column for *Vendor name* has been left blank, which will let workers specify this value while using the Warehouse Management mobile app.

    If you would like to choose how the list will be sorted, you can set this up on the **Sorting** tab.

1. In addition to the query, you must also choose which fields will be displayed on the cards in the inquiry list screen, so select **Field list** on the Action Pane.
1. The **Field list** page opens. Make the following settings:
    - **Display field 1:** *PurchId* (This field will be shown as the header for each card.)
    - **Display field 2:** *PurchStatus*
    - **Display field 3:** *PurchName*
    - **Display field 4:** *OrderAccount*
    - **Display field 5:** *DeliveryDate*
    - **Display field 6:** *displayDocumentStatus()* (This is a display method, as indicated by the "()" at the end.)

1. Select **Save** on the Action Pane and close the page.

### Create the "Look up POs for today" menu item

Create the **Look up POs for today** menu item by following these steps:

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. Select **New** on the Action Pane to add a new mobile device menu item.
1. Make the following settings for the new item:
   - **Menu item name:** *Look up POs for today*
   - **Title:** *Look up POs for today*
   - **Mode:** *Indirect*

1. On the **General** FastTab, make the following settings:
   - **Activity code:** *Data inquiry*
   - **Use process guide:** *Yes* (Automatically selected.)
   - **Table name:** *PurchTable* (We would like to look up purchase order numbers from this table.)

1. On the Action Pane, select **Edit query**. (This action will allow you to define a query based on the selected base table, which in this case is the purchase orders.)
1. The query editor opens. On the **Range** tab, add the following lines to the grid:

    | Table | Derived table | Field | Criteria |
    |---|---|---|---|
    | Purchase order | Purchase order | Purchase order status | Open order |
    | Purchase order | Purchase order | Delivery date | (Day(0)) |

1. Select **OK**

    In this example, the new menu item is configured to find open purchase orders that are expected to arrive today.

    If you would like to choose how the list will be sorted, you can set this up on the **Sorting** tab.

1. In addition to the query, you must also choose which fields will be displayed on the cards in the inquiry list screen, so select **Field list** on the Action Pane.
1. The **Field list** page opens. Make the following settings:
    - **Display field 1:** *PurchName* (This field will be shown as the header for each card.)
    - **Display field 2:** *PurchId*
    - **Display field 3:** *PurchStatus*
    - **Display field 4:** *DlvMode*
    - **Display field 5:** *DlvTerm*
    - **Display field 6:** *OrderAccount*
    - **Display field 7:** *VendorName()* (This is a display method, as indicated by the "()" at the end.)

1. Select **Save** on the Action Pane and close the page.

### Create the "Look up POs by item" menu item

Create the **Look up POs by item** menu item by following these steps:

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. Select **New** on the Action Pane to add a new mobile device menu item.
1. Make the following settings for the new item:
   - **Menu item name:** *Look up POs by item*
   - **Title:** *Look up POs by item*
   - **Mode:** *Indirect*

1. On the **General** FastTab, make the following settings:
   - **Activity code:** *Data inquiry*
   - **Use process guide:** *Yes* (Automatically selected.)
   - **Table name:** *PurchLine* (We would like to look up purchase order numbers based on item number via the line data.)

1. On the Action Pane, select **Edit query**. (This action will allow you to define a query based on the selected base table, which in this case is the purchase order lines, but you could choose to use any of the values related to the header by joining to the *PurchTable*.)
1. The query editor opens. On the **Range** tab, add the following lines to the grid:

    | Table | Derived table | Field | Criteria |
    |---|---|---|---|
    | Purchase order lines | Purchase order lines | Line status | Open order |
    | Purchase order lines | Purchase order lines | Delivery date | (dayRange(-10,10)) |
    | Purchase order lines | Purchase order lines | Item number |  |

1. Select **OK**.

    In this example, the new menu item is configured to find open purchase order lines that are expected to arrive anytime between 10 days in the past and 10 days in the future.

    In the query, the **Criteria** column for *Item number* has been left blank, which will let workers specify this value while using the Warehouse Management mobile app.

    If you would like to choose how the list will be sorted, you can set this up on the **Sorting** tab.

1. In addition to the query, you must also choose which fields will be displayed on the cards in the inquiry list screen, so select **Field list** on the Action Pane.
1. The **Field list** page opens. Make the following settings:
    - **Display field 1:** *PurchId* (This field value will be used as the header for each card.)
    - **Display field 2:** *VendAccount*
    - **Display field 3:** *PurchQty*
    - **Display field 4:** *PurchUnit*
    - **Display field 5:** *PurchStatus*

1. Select **Save** on the Action Pane and close the page.

## Add the new mobile device menu items to a menu

Your three new mobile device menu items are now ready to be added to the mobile device menu, which is required in order to use them as part of a detour process. In this example, you'll create a new submenu and add the new menu items into it.

1. Open **Warehouse management > Setup > Mobile device > Mobile device menu**.
1. On the Action Pane, select **New**.
1. Make the following settings in the header of the new record:
    - **Name:** *Inquire*
    - **Description:** *Inquire*
1. In the **Available menus and menu items** list, select the first of the mobile device menu items you just created. Then select the right-arrow button to move that item into the **Menu structure** list.
1. Repeat the previous step for the other two new menu items.
1. From the list pane on the left, select the *Main* menu.
1. In the **Available menus and menu items** list, scroll down to the **Menus** section and select your new *Inquire* menu. Then select the right-arrow button to move that item into the **Menu structure** list.

## Configure detours in your mobile device steps

To finish the setup, you must now use the detour configuration on the **Mobile device steps** page to add the three new mobile device menu items to the existing purchase order identification step in the **Purchase receive** flow.

1. Go to **Warehouse management > Setup > Mobile device > Mobile device steps**.
1. In the **Filter** field, type *PONum* and then select *Step ID: "PONum"* from the drop-down list.
1. With the found record selected in the grid, select **Add step configuration** on the Action Pane to open a drop-down dialog and then set **Menu item** to *Purchase Receive* and select **OK** to close the dialog.
1. The details page for your new step configuration (**Purchase Receive : PONum**) opens. On the **Available detours (menu items)** FastTab, select **Add** from the toolbar.
1. The **Add detour** dialog opens. Find and select the *Look up POs by vendor* menu item that you created previously.
1. Select **OK** to close the dialog and add the selected menu item to the detours list.
1. Select the new detour and then select **Select fields to send** from the FastTab toolbar.
1. The **Select fields to send** dialog opens. Don't add anything to the **Send from purchase receive** section because you don't want to pass any values to the detour menu item. But in the **Bring back from look up POs by vendor** section, make the following settings for the empty row already added there:
   - **Copy from Look up POs by vendor:** *Purchase order*
   - **Paste in Purchase Receive:** *Purchase order*
1. Select **OK** to close the dialog.
1. Repeat from step 4 for the other two new menu items (*Look up POs for today* and *Look up POs by item*). Like the *Look up POs by vendor* menu item, you don't want to send any data to these detours, but you do want to return a purchase order number.
1. Close the page.

## Try out a purchase receiving flow with data inquiry as part of a detour

Follow these steps to test your new mobile app setup:

1. Create several purchase orders with lines for warehouse 51.
1. Go to a mobile device or emulator that is running the Warehouse Management mobile app, and sign in to warehouse 51 by using *51* as the user ID and *1* as the password.
1. From the mobile app menu, select **Inbound** and then **Purchase receive**.

1. You should now see the following page, which includes the three new menu items:

    ![Purchase receiving using PO number.](media/wma-purchase-receive-po-num-with-detours.png "Purchase receiving using PO number")

1. Now try out the different capabilities and note that you'll be able to send back a purchase order number by selecting one of the cards from the list.

    ![Purchase receiving using PO look up by vendor, example 1.](media/wma-purchase-receive-lookup-po-vendor-keyin-detours.png "Purchase receiving using PO look up by vendor, example 1")

    ![Purchase receiving using PO look up by vendor, example 2.](media/wma-purchase-receive-lookup-po-vendor-detours.png "Purchase receiving using PO look up by vendor, example 2")

> [!TIP]
>
> As an alternative way of running the receiving flow, instead of doing a look up from the **Purchase receive** menu item, you could start from an inquiry flow (**Main > Inquire > Look up POs by vendor**), and invoke a detour to do the desired flow by selecting one of the cards in the list. You can do this by defining a detour on the **Mobile device steps** page for the step with a **Step ID** of *GenericDataInquiryList*. Because this is a detour flow, you can't to invoke more detours from here. So when you, for example, get to the item number entry screen, it won't have the lookup available because the system currently supports just one level of detours.

!INCLUDE[footer-include](../../includes/footer-banner.md)]
