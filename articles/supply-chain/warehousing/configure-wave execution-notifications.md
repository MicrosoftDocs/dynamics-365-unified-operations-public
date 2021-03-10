---
# required metadata

title: Set up and use wave execution notifications 
description: This topic describes wave execution notifications and explains how to set them up
author: mirzaab
manager: tfehr
ms.date: 04/03/2021
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

ms.search.form: WhsWaveNotificationPolicy, WHSParameters, WHSWaveTemplateTable, BusinessEventsWorkspace
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
# ms.tgt_pltfrm:
# ms.custom:
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2022-04-01
ms.dyn365.ops.version: 10.0.0

---

# Set up and use wave execution notifications

[!include [banner](../includes/banner.md)]

The *Wave execution notifications* feature feature uses business events and the **Action center** to deliver notifications related to wave execution. The feature lets you configure which types of events will generate messages, which warehouses will generate the messages, and which users will receive them.

The bell icon on the right side of the navigation bar indicates when an **Action center** message is available for the current user. The user can select the bell icon to open the **Action center** and review the messages.

Business events occur when a business process is run. During a business process, users who participate in it perform business actions to complete the tasks that make up the business process. Business events provide a mechanism that lets external systems receive notifications from Finance and Operations applications. In this way, the systems can perform business actions in response to the business events.

For more information about business events see [Business events overview](../../fin-ops-core/dev-itpro/business-events/home-page.md).

## Turn on the Wave execution notifications feature

Before you can use the *Wave execution notifications* feature, it must be turned on in your system. Admins can use the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace to check the status of the feature and turn it on if it's required. There, the feature is listed in the following way:

- **Module** - *Warehouse management*
- **Feature name** - *Wave execution notifications*

## Scenario: Send wave batch execution notification to the action center

This scenario shows the end-to-end flow for how to send message center notification about wave batch execution errors to a given role.

### Make demo data available

To follow this scenario, you must have demo data installed, and you must select the **USMF** legal entity.

### Make sure waves are executed in batch

1. Go to **Warehouse management \> Setup \> Warehouse management parameters**.
1. On the **Wave processing** FastTab, set **Process waves in batch** to *Yes*.

> [!NOTE]
> If you want to disable the wave batch execution notifications, set **Disable wave processing batch notifications** to *Yes*.

### Configure a wave notification policy

Wave notification policies define which types of notification should be sent and who should be notified.

1. Go to **Warehouse management \> Setup \> Waves \> Wave notification policies**.
1. Create a record with the following settings:

    - **Wave notification policy** - *24BatchError*
    - **Description** - *Warehouse 24 wave batch error*
    - **Send notification on** - *Error only*
    - **To role** - *System administrator*

1. On the Action Pane, select **Save**.

> [!NOTE]
> To keep this example simple, we use *System administrator* because we are working with demo data in this example, which means that you are signed in as a system administrator user, so you will see the notification. However, in practice you should usually select a more specific role to notify about these wave errors, such as *Warehouse manager*.

### Configure a wave template

Wave templates let you link specific instances of wave methods to corresponding wave label templates.

1. Go to **Warehouse management \> Setup \> Waves \> Wave templates**.
1. In the list column, set **Wave template type** to *Shipping* and select the *24 Shipping Default* wave template for warehouse 24.
1. On the **General** FastTab, set **Wave notification policy** to *24BatchError*.

### Configure a work template

Work templates are used during wave execution to generate work and, for the purpose of this scenario, we want the wave execution to trigger an error. By setting the work template query to use a non-existing warehouse, we will ensure that wave execution will fail and therefore send a notification.

1. Go to **Warehouse management \> Setup \> Work \> Work templates**.
1. Set **Work template type** to *Sales orders* and select the *24 SO Stage* work template for warehouse 24.
1. On the Action Pane, select **Edit query**.
1. In the query editor dialog box, on the **Range** tab, edit the following row (or add it if it doesn't exist):

    - **Table** - *Temporary work transactions*
    - **Derived table** - *Temporary work transactions*
    - **Field** - *Warehouse*
    - **Criteria** - Change from *24* to *Error*

1. Select **OK** and confirm the change.

### Create a sales order and release it to the warehouse

1. Go to **Sales and marketing \> Sales order \> All sales orders**.
1. Create a sales order with the following settings:

    - **Customer account** - *US-001*
    - **Warehouse** - *24*

1. On the **Sales order lines** FastTab, add a sales order line with the following settings:

    - **Item number** - *A0001*
    - **Quantity** - *10*

    > [!NOTE]
    > These items and quantities are only examples. Sufficient stock must exist in the specified warehouse.

1. With your new line still selected, select **Inventory \> Reservation** from the **Sales order lines** toolbar.
1. The **Reservation** page opens. On the Action Pane, select **Reserve lot**, and then close the page.
1. On the Action Pane, open the **Warehouse** tab and select **Release to warehouse**.

### Notifications from wave batch job execution

After some time, depending on your business events setup, the **Action center** will show a message similar to the following, which includes a link to open the failed wave.

> **Error during wave execution**<br>
> An error occurred while executing wave USMF-000000001.<br>
> Last messages: No Work was created for Wave USMF-000000001.
>
> **STATUS**<br>
> Active
>
> Open wave details

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
