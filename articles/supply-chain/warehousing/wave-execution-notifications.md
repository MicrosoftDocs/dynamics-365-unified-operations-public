---
# required metadata

title: Wave execution notifications 
description: This article describes wave execution notifications and explains how to set them up.
author: Mirzaab
ms.date: 08/09/2022
ms.topic: article
ms.prod:
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
ms.search.validFrom: 2021-04-01
ms.dyn365.ops.version: 10.0.0

---

# Wave execution notifications

[!include [banner](../includes/banner.md)]

The *Wave execution notifications* feature uses business events and the Action center to deliver notifications that are related to wave execution. It lets you specify the types of events that generate notifications, the warehouses that generate them, and the users who receive them.

The **Show messages** button (bell symbol) on the right side of the navigation bar indicates when an Action center message is available for the current user. The user can select the **Show messages** button to open the Action center and review the messages.

Business events occur when business processes are run. Business processes are made up of tasks. During a business process, the users who participate in it perform business actions to complete those tasks. Business events provide a mechanism that lets external systems receive notifications from finance and operations applications. In this way, the systems can perform business actions in response to the business events. For more information, see [Business events overview](../../fin-ops-core/dev-itpro/business-events/home-page.md).

## Turn the Wave execution notifications feature on or off

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.25, the feature is turned on by default. As of Supply Chain Management version 10.0.29, the feature is mandatory and can't be turned off. If you're running a version older than 10.0.29, then admins can turn this functionality on or off by searching for the *Wave execution notifications* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

## Scenario: Send wave batch execution notifications to the Action center

This scenario shows the end-to-end flow for sending notifications about wave batch execution errors to a specific role via the Action center.

### Make demo data available

To follow this scenario, you must have demo data installed, and you must select the **USMF** legal entity.

### Make sure that waves are run in batch mode

1. Go to **Warehouse management \> Setup \> Warehouse management parameters**.
1. On the **Wave processing** FastTab, set the **Process waves in batch** option to *Yes*.

> [!NOTE]
> If you want to disable wave batch execution notifications, set the **Disable wave processing batch notifications** option to *Yes*.

### Configure a wave notification policy

Wave notification policies define the types of notifications that are sent and the users who are notified.

1. Go to **Warehouse management \> Setup \> Waves \> Wave notification policies**.
1. Create a record that has the following settings:

    - **Wave notification policy:** *24BatchError*
    - **Description:** *Warehouse 24 wave batch error*
    - **Send notification on:** *Error only*
    - **To role:** *System administrator*

        > [!NOTE]
        > Because this scenario uses demo data, the *System administrator* role is selected for the sake of simplicity. Therefore, because you're signed in as a system administrator user, you will receive the notifications. However, in practice, you should usually select a more specific role to notify about wave batch execution errors, such as *Warehouse manager*.

1. On the Action Pane, select **Save**.

### Configure a wave template

Wave templates let you link specific instances of wave methods to corresponding wave label templates.

1. Go to **Warehouse management \> Setup \> Waves \> Wave templates**.
1. In the list pane, set the **Wave template type** field to *Shipping*, and then select the *24 Shipping Default* wave template for warehouse 24.
1. On the **General** FastTab, set the **Wave notification policy** field to *24BatchError*.

### Configure a work template

Work templates are used during wave execution to generate work. For this scenario, wave execution should trigger an error. By setting the work template query to use a nonexistent warehouse, you will ensure that wave execution fails and therefore sends a notification.

1. Go to **Warehouse management \> Setup \> Work \> Work templates**.
1. In the list pane, set the **Work template type** field to *Sales orders* and then select the *24 SO Stage* work template for warehouse 24.
1. On the Action Pane, select **Edit query**.
1. In the query editor dialog box, on the **Range** tab, edit the following row (or add it if it doesn't exist):

    - **Table:** *Temporary work transactions*
    - **Derived table:** *Temporary work transactions*
    - **Field:** *Warehouse*
    - **Criteria:** Change the value from *24* to *Error*.

1. Select **OK**, and confirm the change.

### Create a sales order and release it to the warehouse

1. Go to **Sales and marketing \> Sales order \> All sales orders**.
1. Create a sales order that has the following settings:

    - **Customer account:** *US-001*
    - **Warehouse:** *24*

1. On the **Sales order lines** FastTab, add a sales order line that has the following settings:

    - **Item number:** *A0001*
    - **Quantity:** *10*

    > [!NOTE]
    > These items and quantities are only examples. The specified warehouse must contain enough stock.

1. While the new line is still selected on the **Sales order lines** FastTab, select **Inventory \> Reservation** on the toolbar.
1. On the **Reservation** page, on the Action Pane, select **Reserve lot**. Then close the page.
1. On the Action Pane, on the **Warehouse** tab, select **Release to warehouse**.

### Notifications from wave batch job execution

Depending on the setup of your business events, you will eventually receive a notification about wave execution failure. The Action center message will resemble the following example and will include a link to the wave that failed.

> **Error during wave execution**  
> An error occurred while executing wave USMF-000000001.  
> Last messages: No Work was created for Wave USMF-000000001.
>
> **STATUS**  
> Active
>
> Open wave details

[!INCLUDE[footer-include](../../includes/footer-banner.md)]

