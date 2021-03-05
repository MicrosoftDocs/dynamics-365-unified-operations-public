---
# required metadata

title: Set up and use wave execution notifications 
description: This topic describes wave execution notifications and explains how to set it up.
author: lbc
manager: olkryva
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
ms.reviewer: lbc
# ms.tgt_pltfrm:
# ms.custom:
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: kamaybac
ms.search.validFrom: yyyy-mm-dd
ms.dyn365.ops.version: 10.0.0

---

# Set up and use wave execution notifications 

[!include [banner](../includes/banner.md)]

Business events provide a mechanism that lets external systems receive notifications from Finance and Operations applications. In this way, the systems can perform business actions in response to the business events.

Business events occur when a business process is run. During a business process, users who participate in it perform business actions to complete the tasks that make up the business process.

For more information about business events see here (../../fin-ops-core/dev-itpro/business-events/home-page.md) https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/business-events/home-page)

This feature uses business events and the action center to deliver notifications related to wave execution.


> [!NOTE]
> XXX

## Turn on the Wave execution notifications feature

Before you can use the *Wave execution notifications* feature, it must be turned on in your system. Admins can use the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace to check the status of the feature and turn it on if it's required. There, the feature is listed in the following way:

- **Module:** *Warehouse management*
- **Feature name:** *Wave execution notifications*

## Scenario : Send wave batch execution notification to action center.

This scenario shows the end-to-end flow on how to send notification to given role about wave batch execution errors in the message center. 

### Make demo data available

To follow this scenario, you must have demo data installed, and you must select the **USMF** legal entity.

### Make sure waves are executed in batch

1. Go to **Warehouse management \> Setup \> Warehouse management parameters**.
1. On the **Wave processing** FastTab, enable the *Process waves in batch*

> [!NOTE]
> If you want to disable the wave batch execution notifications, enabled the *Disable wave processing batch notifications*.

### Configure a wave notification policies

Wave notification policies defines when notification should be sent, if wave create should be notified and users to be notified.

1. Go to **Warehouse management \> Setup \> Waves \> Wave notification policies**.
1. Create a record that has the following settings:

    - **Wave notification policy:** *24BatchError*
    - **Description:** *Warehouse 24 wave batch error*
    - **Send notification on:** *Error only*
    - **To role:** *System administrator*
1. On the Action Pane, select **Save**.

> [!NOTE]
> For simplicity of the example, we use *System administrator* to ensure all users get the notification, but the idea is that you specific a specific role that should be notified about these wave errors e.g. *Warehouse manager*

### Configure a wave template

Wave templates let you link specific instances of wave methods to a corresponding wave label template.

1. Go to **Warehouse management \> Setup \> Waves \> Wave templates**.
1. Select a wave template type *Shipping* and select the *24 Shipping Default* wave template for warhouse *24*.
1. On the **General** FastTab, select the *24BatchError* for the **Wave notification policy**.

### Configure a work template

Work templates are used as part of the wave execution to generate work and for the purpose of this scenario we want the wave execution to trigger an error. 
Changing the work template query to a none existing warehouse will ensure the wave execution to fail and send notification.

1. Go to **Warehouse management \> Setup \> Work \> Work templates**.
1. Select a work template type *Sales orders* and select the *24 SO Stage* work template for warhouse *24*.
1. On the Action Pane, select **Edit query**.
1. In the query editor dialog box, on the **Range** tab, add a row that has the following settings:

    - **Table:** *Temporary work transactions*
    - **Derived table:** *Temporary work transactions*
    - **Field:** *Warehouse*
    - **Criteria:** *Error*

### Create a sales order and release it to the warehouse

1. Go to **Sales and marketing \> Sales order \> All sales orders**.
1. Create a sales order that has the following settings:

    - **Customer account:** *US-001*
    - **Warehouse:** *24*

1. Add a sales order line:

    - Sales order line:

        - **Item number:** *A0001*
        - **Quantity:** *10*

    > [!NOTE]
    > The items and quantities that are provided here are only examples. They must have stock in the specified warehouse.

1. Select sales order line 1. Then, in the **Sales order line** section, on the **Inventory** menu, select **Reservations**.
1. On the **Reservation** page, on the Action Pane, select **Reserve lot**, and then close the page.
1. On the Action Pane, on the **Warehouse** tab, select **Release to warehouse**.


The following events occur, after some time depending on the business events setup, the user will get a notification in the Action center, with a message like this and a link to open the failed wave.

**Error during wave execution**
An error occurred while executing wave USMF-000000001. Last messages: No Work was created for Wave USMF-000000001.**
Status : Active
Open wave details (Link)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]