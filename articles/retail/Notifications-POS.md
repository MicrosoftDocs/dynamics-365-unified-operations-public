---
# required metadata

title: Display order notifications in Point of Sale
description: This topic describes enabling order notifications in the point of sale and the notifications framework which can be extended to other operations. 
author: ShalabhjainMSFT
manager: AnnBe
ms.date: 10/30/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
# ms.reviewer: josaw
ms.search.scope: 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: Retail
ms.author: ShalabhjainMSFT
ms.search.validFrom: 2017-10-30
ms.dyn365.ops.version: 

---


# Display notifications in Point of Sale


In today's modern retail environment, the store associates are assigned various tasks such as helping customers, ringing transactions, performing stock counts, receiving orders in store etc. Our Point of Sale (POS) clients empower the associates to do these and much more, all in a single application. With various tasks to be performed during a day, there was a need to notify the associates, whenever something requires their attention. The notification framework in the POS solves this problem by allowing the retailers to configure role based notifications. With the App update 5, monthly release of Dynamics 365 for Retail, the notifications can be configured for the POS operations only.

Currently, the system provides the capability to display notifications for Order fulfillment operation, however, the framework is designed to be extensible, so that, in near future, the developers will be able to write notification handler for any operation and display the notifications on POS.  

## Enable the notifications for order fulfillment operation

To enable the notification for the order fulfillment operation, follow the below steps:

* Navigate to Operations form - Retail > Channel setup > POS setup > POS > Operations
* Search for the Order fulfillment operation and select the "Enable notifications" checkbox for this operation. This indicates to the notification framework to listen to the handler for the Order fulfillment operation. If the handler is implemented, then the notifications will be displayed on POS, else, the notifications will not be displayed for this operation.
* Navigate to the "POS permissions" associated with the workers and under the "Notifications" fast tab, add the Order fulfillment operation with the "Display order" as 1. When there is more than one notification configured, the display order is used to arrange the notification from top to bottom with 1 being on top. Only those operations can be added for which the "Enable notifications" checkbox has been checked. Also, the notifications will be displayed only for the operations that have been added here and only to those workers for whom the operations have been added to the corresponding POS permissions. 

Note:
Notifications can be overridden at the user level by navigating to the worker's record and selecting "POS Permissions" then editing that user's notification subscription.

* Navigate to the functionality profile form - Retail > Channel setup > POS setup> POS profiles > Functionality profiles and update the "Notification interval" property, to set the interval in minutes, at which the notifications should be pulled. We recommend to set this value to 10 minutes to avoid unnecessary communication to the headquarters. Setting the notification interval to "0" will turn off notifications.  

* Navigate to **Retail**>**Retail IT**>**Distribution schedule**. Select schedule "1060-Staff" to synch notification subscription settings and then click **Run now**. Next, synch the permission interval by selecting "1070-Channel configuration" and then click **Run now**. 

## Viewing notifications in POS

Once the above steps are complete, the workers, for whom the notifications are set up, can view the notifications in POS. To view the notifications, click on the notification icon in the title bar of the POS; this opens up a notification center with the notifications
for Order fulfillment operation. The notification center should display three groups within the order fulfillment operation namely "Pending orders", "Store pickup" and "Ship from store". 

* Pending orders - This group displays the count of orders which are in the pending state i.e. orders which need to be accepted by a POS worker, having the required permissions, for store fulfillment. Clicking the number on the group will open the order fulfillment form, filtered to display only the pending orders assigned to the store for fulfillment. If the orders are auto accepted for the store, then the count for this group will be zero.

* Store pickup - This group displays the count of orders which have the delivery mode of 'Pickup' and the pickup is scheduled from the current store. Clicking the number on the group will open the order fulfillment form, filtered to display the active orders which are set up to be picked from the current store.

* Ship from store - This group displays the count of orders which have the delivery mode of 'Shipping' and the shipping is scheduled from the current store. Clicking the number on the group will open the order fulfillment form, filtered to display the active orders which are set up to be shipped from the current store.

Whenever there are new orders assigned to the store for fulfillment, the notification icon will change to indicate new notifications and the count of the corresponding groups will be updated. The user can also click on the refresh icon, next to the operation name, to immediately update the count of the groups, else, the count will be updated at the predefined interval. Any group which has a new item, which is not seen by the current worker, will display a burst icon indicating this group has a new item. Clicking on the tiles within notifications will open the specific operation for which that notification is configured. In the above cases, clicking on the notifications will open the order fulfillment page and pass the appropriate parameters (Pending, store pickup and ship from store). 

Note: Pending orders notifications will be enabled in a hotfix after AppUpdate 5 ships. 

