---
title: Make finished goods physically available before posting to journals
description: When a worker reports a manufactured item as finished, the system registers the item as available for further physical processing (such as shipment or putaway). During this process, one or more journals are also posted. This topic describes how to defer journal postings by allowing them to be processed by a batch job in a message queue.
author: johanhoffmann
ms.date: 08/02/2022
ms.topic: article
ms.search.form: ProdParameters, JmgProdParameters, InventLocation, JmgMES3PMessageProcessorMessage
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: johanho
ms.search.validFrom: 2022-08-02
ms.dyn365.ops.version: 10.0.29
---

# Make finished goods physically available before posting to journals

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

When a worker reports a manufactured item as finished, the system registers the item as available for further physical processing (such as shipment or putaway). During this process, one or more journals are also posted (such as the report as the finished journal, picking list journal, and route card journal). If you'd like to make your items physically available before all postings have been processed, then you can set the system to defer the journal postings. Deferred postings are then managed by a batch job, which will process the postings as system resources allow.

The following illustration shows how processes for posting journals are invoked both with and without deferred posting.

![The report-as-finished process with and without deferred journal posting.](media/deferred-posting-flowchart.png "The report-as-finished process with and without deferred journal posting")

## Turn on deferred journal posting for your system

Before you can use deferred journal posting, it must be turned on in your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Production control*
- **Feature name**: *(Preview) Make finished goods physically available before posting to journals*

## Set up journal posting options for reporting as finished

You can report items as finished using any of the following clients:

- Web client
- Production floor execution interface
- Warehouse Management mobile app

Journal posting options for reporting as finished are configured separately for each client. Depending on your needs, you might choose to use deferred posting on some clients but not for others.

### Web client

When using the web client, workers can report as finished from the order list or details page. Use the following procedure to configure how the system will process journal postings when reporting as finished from the web client.

1. Go to **Production control \> Setup \> Production control parameters**.
1. Open the **Journals** tab.
1. In the **Report as finished journal** field group, set **Posting method** to one of the following values:

    - *Immediate* – On report as finished, the system will fully process all related journal postings before marking the finished item as physically available.
    - *Deferred* – On report as finished, the system will mark the finished item as physically available and add the journal postings to a message queue. The system won't wait until the postings are fully processed before marking the finished item as physically available.

### Production floor execution interface

Use the following procedure to configure how the system will process journal postings when reporting as finished from the production floor execution interface.

1. Go to **Production control \> Setup \> Manufacturing execution \> Production order defaults**.
1. Open the **Report as finished** tab.
1. In the **Report as finished journal** field group, set **Posting method** to one of the following values:

    - *Immediate* – On report as finished, the system will fully process all related journal postings before marking the finished item as physically available.
    - *Deferred* – On report as finished, the system will mark the finished item as physically available and add the journal postings to a message queue. The system won't wait until the postings are fully processed before marking the finished item as physically available.

### Warehouse Management mobile app

This section describes how to set up a mobile device menu item that will allow workers to report as finished using the Warehouse Management mobile app. It also describes how to configure the journal posting option that applies when workers use the app to report as finished at each warehouse.

### Set up a mobile device menu item for reporting as finished

The warehouse management app has two flows for reporting as finished production or batch orders (*Report as finished* or *Report as finished and put away*). You configure a flow for the app by creating a mobile device menu item. If you don't already have a menu item for reporting as finished, follow these steps to add one:

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**
1. Select **New** on the Action Pane to create a new menu item.
1. Make the following settings for the new item:

    - **Menu item name** – Enter a name for your menu item (for example, *Report as finished*).
    - **Title** – Enter a title for your menu item (for example, *Report as finished*).
    - **Mode** – Set to *Work*.
    - **Work creation process** – Select either *Report as finished* or *Report as finished and put away*.

1. Continue setting up the menu item as usual.

After you create a new menu item, you must associate it a mobile device menu. Follow these steps to associate the menu item to an existing menu:

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu**.
1. In the left pane, select the menu you want to add the new item to.
1. On the Action Pane, select **Edit**.
1. In the **Available menus and menu items** column, select the menu item you want to add to the selected menu. (For example, the menu item you created in previous procedure.)
1. Select the Add (right arrow) button to move the selected menu item to the **Menu structure** column.

### Configure journal posting options for the Warehouse Management mobile app

To configure journal posting options for the Warehouse Management mobile app, you must set the option for each warehouse as needed. Use the following procedure to set the option for each warehouse:

1. Go to **Warehouse management \> Setup \> Inventory breakdown \> Warehouses**
1. On the list pane, select the warehouse you want to set up.
1. On the Action Pane, select **Edit**.
1. Expand the **Warehouse** FastTab.
1. In the **Production orders** field group, set **Posting method** to one of the following values:

    - *Inherit* – The selected warehouse will inherit this setting from the **Production control parameters** page (described previously).
    - *Immediate* – On report as finished, the system will fully process all related journal postings before marking the finished item as physically available.
    - *Deferred* – On report as finished, the system will mark the finished item as physically available and add the journal postings to a message queue. The system won't wait until the postings are fully processed before marking the finished item as physically available.

## Schedule the message processor batch job to process deferred postings

The message processor batch job is responsible for processing the journal postings after they have been queued. To ensure that your journal postings are processed, you must configure this job to run at a regular interval. Use the following procedure to set up the required batch job.

1. Go to **System administration \> Message processor \> Message processor**.
1. On the **Parameters** FastTab, set  **Message queue** to *Production*.
1. On the **Run in the background** FastTab, set **Batch processing** to *Yes*. Then set up a recurrent schedule and make other settings as needed. The settings work just as they work for other types of [background jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.

## Track the progress of your deferred postings

Deferred journal postings are queued as *message processor messages*, which wait to be executed by the *message processor*, which should be set to run as a scheduled batch job. You can view the deferred posting messages that will be or have been processed by the message processor by going to **Production control \> Production orders \> Deferred production order posting**.

### Message grid columns and filters

You can use the fields at the top of the **Deferred production order posting** page to help find any particular messages you are looking for. Most of these filters match the column headings in the message grid. The following filters and column headings are available:

- **Message type** – Specifies the type of messages shown in the grid.
- **Message state** – Specifies the state of the messages shown in the grid. The following states exists:
  - *Queued* – The message is ready to be processed by the message processor.
  - *Processed* – The message was successfully processed by the message processor.
  - *Canceled* – The message was processed, but processing failed.
  - *Failed* – The message failed to be processed at the last attempt. The system will retry failed messages three times and after this will give up and leave the message in the *Failed* state. Note that you won't be able to manually cancel or edit the message until after the last of these three attempts.
- **Message content** – This filter does a full-text search of message content. (Message content is not shown in the grid.) The filter treats most special symbols (such as "-") as spaces, and treats all space characters as Boolean OR operators. For example, this means if you search for a specific `journalid` value equal "USMF-123456", the system will find all messages that contain "USMF" or "123456", which is likely to be a long list. Therefore, it would be better to enter just "123456" alone because that will return more specific results.

### View the message log, message content, and details

You can find detailed information about a message by selecting it in the grid and then opening the **Log** or **Raw content** tabs under the message grid, where each processing event is shown.

The toolbar on the **Log** tab includes the following buttons:

- **Log** – Displays the processing results. This is especially helpful for understanding the reasons for a processing failure for messages having a **Processing result** of *Failed*.
- **Bundle** – Multiple message processing operations can run as part of the same batch process. Select this button to view this detailed data. For example, you can see whether dependencies exist that require the system to process certain messages in a specific sequence.

### Manually process or cancel a message

If needed, you can manually process or cancel a message, depending on its current state. To do so, select the message in the grid and then select **Process** or **Cancel** on the Action Pane

### Set up business events to deliver alerts for failed processing results

You can set up [Business events](../../fin-ops-core/dev-itpro/business-events/home-page.md) to alert you to failed processing results. To do so, activate the business event named *Message processor message processed*  on the **Business events catalog** page (**System administration > Setup > Business events > Business events catalog**).

As part of the activation process, you will be guided to specify whether the event is specific to one or all legal entities and provide an **Endpoint name**, which must be defined first.

>[!NOTE]
> If **When a Business Event occurs** is set to *Microsoft Power Automate* (rather than *HTTPS*, for example), the **Endpoint name** will automatically be created in Supply Chain Management based on the *Microsoft Power Automate* setup.
