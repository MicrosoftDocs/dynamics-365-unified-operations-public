---
title: Query data using Warehouse Management mobile app detours
description: This article describes how to configure data inquiry mobile device menu items and how to use them as part of detours.
author: perlynne
ms.date: 08/01/2022
ms.topic: article
ms.search.form:
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

This article uses a example scenarios to show how you can use the *Warehouse management app data inquiry flow* feature to improve the purchase receipt flow. The scenarios use the standard sample data, which includes a flow called *Purchase receive*. This flow starts by prompting workers to identify a purchase order number to receive against. To make it easier to identify the purchase order, you will enhance the first page of this flow by adding following new query options:

- **Look up POs by vendor** – Opens a page that prompts the worker to enter a vendor name or part of a vendor name (which they can enter using wildcards). For example, if the worker is expecting an inbound delivery today from a vendor called *Tailspin* something, the worker can enter "Tail\*" to view a set of cards for open purchase orders that include this text. Each card has several fields that convey information about each purchase order. In addition to the vendor's name, you can design the cards to show the vendor account number, delivery date, and document status.

- **Look up POs for today** – Opens a page that prompts doesn't ask workers to enter data, but instead shows preconfigured filters (such as today's date). The page then shows a set of cards that match the filter. Workers proceed by selecting a card for the purchase order they want to register inventory items against.

- **Look up POs by item** – Opens a page that asks the worker to scan the bar code of any item in the arrived inventory. The flow then lists all open purchase orders that contain lines for the scanned item number. To cover situations where a bar code can't be read, you could add an additional detour lookup to this page that lets workers to search for item numbers within a specific purchase order.

In each case, the worker identifies a purchase order by selecting a card and then returns to the first page, which receives and shows the selected purchase order number, making it possible for the worker to continue the inbound inventory item registration flow.

## Enable sample data

To work through the scenarios described in this topic, you must be on a system where the standard [demo data](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) is installed. Additionally, you must select the *USMF* legal entity (company) before you begin.

## Configure the mobile device menu items

To create each of the new query options you need to add to the first page of the flow, you must set them up as mobile device menu items, which you will later make available as detours to the *Purchase receive* flow.

### Create the look up POs by vendor menu item

Create the **Look up POs by vendor** menu item by following these steps:

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. Select **New** on the Action Pane to add a new mobile device menu item.
1. Make the following settings for the new item:
   - **Menu item name:** *Look up POs by vendor*
   - **Title:** *Look up POs by vendor*
   - **Mode:** *Indirect*

1. On the **General** FastTab, select the following:
   - **Activity code:** *Data inquiry*
   - **Use process guide:** *Automatically selected*
   - **Table name:** *PurchTable (we would like to lookup purchase order numbers from this table)*

    Once a table name is selected the buttons *Edit query* and *Field list* gets available.
    **Edit query** will allow you to define a query based on the selected base table, in this case it's the Purchase orders.

1. Select **Edit query**.
1. In the **Range** section grid add the following three lines:

    | Table | Derived table | Field | Criteria |
    |---|---|---|---|
    | Purchase order | Purchase order | Purchase order status | Open order |
    | Purchase order | Purchase order | Delivery date | (dayRange(-10,10)) |
    | Purchase order | Purchase order | Vendor name |  |
1. Select **OK**.

    In this example it gets configured to query out open purchase orders that are expected to arrive anywhere within a day range of ten days in the past and ten days in the future.

    In the query the *Vendor name* criteria has been left blank, making it possible during the Warehouse app processing to provide the information.

    In case you would like a specific sorting of the list this can as well get defined as part of the **Sorting** tab.

    Apart from the query, you also need to configure the fields that will be displayed on the cards in the inquiry list screen.

1. Select **Field list**.
1. Add the following information:
    - **Display field 1:** *PurchId* (This field value will used as the header for each card)
    - **Display field 2:** *PurchStatus*
    - **Display field 3:** *PurchName*
    - **Display field 4:** *OrderAccount*
    - **Display field 5:** *DeliveryDate*
    - **Display field 6:** *displayDocumentStatus()* (Note this is a display method, indicated by the "()" at the end.)

1. Select **Save** and close the page by selecting **X** (Close) or back in the browser.

### Lookup POs for today

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. Select **New** on the Action Pane to add a new mobile device menu item.
1. Make the following settings:
   - **Menu item name:** *Lookup POs for today*
   - **Title:** *Lookup POs for today*
   - **Mode:** *Indirect*

1. Under **General** select the following:
   - **Activity code:** *Data inquiry*
   - **Use process guide:** *Automatically selected*
   - **Table name:** *PurchTable* (We would like to lookup purchase order numbers from this table.)

    Once a table name is selected the buttons **Edit query** and **Field list** gets available. **Edit query** will allow you to define a query based on the selected base table, in this case it's the Purchase orders.

1. Select **Edit query**.
1. In the **Range** section grid add the following two lines:

    | Table | Derived table | Field | Criteria |
    |---|---|---|---|
    | Purchase order | Purchase order | Purchase order status | Open order |
    | Purchase order | Purchase order | Delivery date | (Day(0)) |

1. Select **OK**

    In this example it gets configured to query out open purchase orders that are expected to arrive today.

    In case you would like a specific sorting of the list this can as well get defined as part of the **Sorting** tab.

    Apart from the query, you also need to configure the fields that will be displayed on the cards in the inquiry list screen.

1. Select **Field list**.
1. Add the following information:
    - **Display field 1:** *PurchName (This field value will used as the header for each card)*
    - **Display field 2:** *PurchID*
    - **Display field 3:** *PurchStatus*
    - **Display field 4:** *DlvMode*
    - **Display field 5:** *DlvTerm*
    - **Display field 6:** *OrderAccount*
    - **Display field 7:** *VendorName()* (Note this is a display method, indicated by the "()" at the end.)

1. Select **Save** and close the page by selecting **X** (Close) or back in the browser.

### Lookup POs by item

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. Select **New** on the Action Pane to add a new mobile device menu item.
1. Make the following settings:
   - **Menu item name:** *Lookup POs by item*
   - **Title:** *Lookup POs by item*
   - **Mode:** *Indirect*

1. Under **General** select the following:
   - **Activity code:** *Data inquiry*
   - **Use process guide:** *Automatically selected*
   - **Table name:** *PurchLine* (We would like to lookup purchase order numbers based on item number via the line data.)

    Once a table name is selected the buttons *Edit query* and *Field list* gets available.
    **Edit query** will allow you to define a query based on the selected base table, in this case it's the Purchase order lines, but you can as well choose to leverage any of the values related to the header by simply joining to the *PurchTable*.

1. Select **Edit query**.
1. In the **Range** section grid add the following three lines.

    | Table | Derived table | Field | Criteria |
    |---|---|---|---|
    | Purchase order lines | Purchase order lines | Line status | Open order |
    | Purchase order lines | Purchase order lines | Delivery date | (dayRange(-10,10)) |
    | Purchase order lines | Purchase order lines | Item number | |
1. Select **OK**.

    In this example it gets configured to query out open purchase order lines that are expected to arrive anywhere within a day range of ten days in the past and ten days in the future.

    In the query the *Item number* criteria has been left blank, making it possible during the Warehouse app processing to provide the information.

    In case you would like a specific sorting of the list this can as well get defined as part of the *Sorting* tab.

    Apart from the query, you also need to configure the fields that will be displayed on the cards in the inquiry list screen.

1. Select **Field list**
1. Add the following information
    - **Display field 1:** *PurchId* (This field value will used as the header for each card.)
    - **Display field 2:** *VendAccount*
    - **Display field 3:** *PurchQty*
    - **Display field 4:** *PurchUnit*
    - **Display field 5:** *PurchStatus*

1. Select **Save** and close the page by selecting **X** (Close) or back in the browser.

## Add the new mobile device menu items to a menu

With now having the three new *lookup* mobile device menu items, we are ready to get them added to the **Mobile device menu**. This is required to use them as part of a detour process.
In this example we will create a new sub menu and add the just created mobile device menu items into it.

1. Open **Warehouse management > Setup > Mobile device > Mobile device menu**.
1. Select **New**.
1. Add the following information:
    - **Name:** *Inquire*
    - **Description:** *Inquire*
1. Now with the focus on the newly created menu find and select the first of the three mobile device menu items in the **Available menus and menu items** list.
1. Select the arrow-bottom to move this menu item into the **Menu structure** list.
1. Do the same for the two remaining menu items.
1. Now select the **Main** menu for the demo data.
1. Find the just created menu under the *Menus* grouping in the **Available menus and menu items** list and select it.
1. Select the arrow-bottom to move this menu into the **Menu structure** list.

## Configure detours in your mobile device steps

To get the three additional mobile device menu items added to the existing purchase order identification step in the  **Purchase Receive** flow, we will use the detour configuration in the **Mobile device steps**.

1. Go to **Warehouse management > Setup > Mobile device > Mobile device steps**.
1. Filter in the grid **Step ID** column for *PONum*.
1. With the record selected, select **Add step configuration** and select the **Menu item** *Purchase Receive* and select **OK**.
1. Within the *Mobile device step* for the "Purchase Receive : PONum" Select **Add** in the *Available detours (menu item)*.
1. In the list select the previously created **Lookup POs by vendor** menu item.
1. Select **Select fields to send**.
1. In the **Send from purchase receive** we will not enter data because we do not want to pass any values to the detour menu item. But in the **Bring back from lookup POs by vendor** section, select the following:
   - **Copy from Lookup POs by vendor:** *Purchase order
   - **Paste in Purchase Receive:** *Purchase order
1. Select **OK**.
1. Do the same for the two remaining **Lookup POs for today** and **Lookup POs by item** menu items.

   For each of the detours we don't want to send any data, only to bring back a purchase order number.
1. Close the page.

## Try out a purchase receiving flow with data inquiry as part of a detour

1. Create several purchase orders with lines to try out your setup and then run the Warehouse Management mobile app process for the **Purchase Receive**.

1. You should now see the following page with the three additional menu items:

    ![Purchase receiving using PO number.](media/wma-purchase-receive-po-num-with-detours.png "Purchase receiving using PO number")

1. Now try out the different capabilities and note that you will be able to send back a purchase order number by doing a press and hold on one of the cards from the list.

    ![Purchase receiving using PO lookup by vendor, example 1.](media/wma-purchase-receive-lookup-po-vendor-keyin-detours.png "Purchase receiving using PO lookup by vendor, example 1")

    ![Purchase receiving using PO lookup by vendor, example 2.](media/wma-purchase-receive-lookup-po-vendor-detours.png "Purchase receiving using PO lookup by vendor, example 2")

> [!TIP]
>
> As an alternative way of running the receiving flow, instead of doing a look up from the **Purchase Receive** menu item, you could start from an inquiry flow (**Main > Inquire > Lookup POs by vendor**), and invoke a detour to do the desired flow by long pressing one of the cards in the list. This will be possible by defining a detour in the **Mobile device steps** for the *GenericDataInquiryList*. Because this is a detour flow it is not possible to invoke more detours from here. So when you e.g. get to the item number entry screen it will not have the look up for the items available, as it is only currently supported with one level of detours.
>
> ![Purchase receiving using PO lookup by vendor, alternative flow.](media/wma-data-inquire-detour.png "Purchase receiving using PO lookup by vendor, alternative flow")

<!--Add new picture-->

!INCLUDE[footer-include](../../includes/footer-banner.md)]
