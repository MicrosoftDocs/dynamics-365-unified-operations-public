---
# required metadata

title: Revenue recognition overview  (contains video)
description: This topic provides information about the Revenue recognition feature. This feature provides a flexible framework that lets you define company-specific rules for recognizing both the revenue price and the revenue schedule for multi-element orders.
author: kweekley
ms.date: 03/15/2022
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  Customer
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 

ms.search.region: Global 
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2018-08-30
ms.dyn365.ops.version: 8.0.4

---

# Revenue recognition overview

[!include [banner](../includes/banner.md)]

Companies in industries that sell multiple elements, such as products, services, subscriptions, and so on, must be able to break out multi-element orders so that revenue can be recognized based on a set of company-specific and industry-specific guidelines.

Revenue recognition, including bundle functionality, isn't supported for use in Commerce channels (e-commerce, POS, call center). Items configured with revenue recognition should not be added to orders or transactions created in Commerce channels.

In general, the revenue recognition process can be used to perform these tasks:

* Allocate revenue, to help ensure that the appropriate revenue price is recognized, based on the value of the components on multi-element orders.
* Defer revenue, based on a revenue schedule that represents the contractual time frame and percentages for recognizing revenue over time.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE44iER]

The [How to use revenue recognition in Dynamics 365 Finance](https://youtu.be/v3amIsiqvoo) video (shown above) is included in the [Finance and Operations playlist](https://www.youtube.com/playlist?list=PLcakwueIHoT_SYfIaPGoOhloFoCXiUSyW) available on YouTube.

The Revenue recognition feature provides a flexible framework that lets you define company-specific rules for recognizing both the revenue price and the revenue schedule.

Released products are used to support revenue recognition on sales order documents. The released products contain the setup that is required to determine the revenue price and the revenue schedule. The sales order can originate from a Time and materials project.

Companies can use the revenue schedule functionality without using the revenue price functionality. Therefore, the price on the sales order lines will be used as either revenue or deferred revenue. If a revenue schedule exists on the sales order line, the price on the sales order line will be deferred. If a revenue schedule doesn't exist on the sales order line, the price on the sales order line will be posted to a revenue account when it's invoiced.

The revenue price is calculated either when the sales order is confirmed or when the invoice is posted. To preview the revenue price before the invoice is posted, you must confirm the sales order.

When the sales order is confirmed, an expected revenue schedule is also created if any sales order line has a revenue schedule. When the sales order is invoiced, the expected revenue schedule is deleted, and the expected revenue schedule is replaced with the actual revenue recognition schedule.

The details of the revenue recognition schedule are maintained for each sales order line. Therefore, the revenue recognition manager can view the details and can release lines to revenue when the contractual obligation has been completed. At the end of each period, the revenue recognition manager can create a revenue journal to release any schedule lines that are due on or before a date they define. This revenue journal isn't posted immediately. Therefore, the revenue recognition manager can verify that the correct amounts are being released from deferred revenue to actual revenue.

If a contractual change causes a new sales order line to be added either to the existing sales order or a new sales order, a reallocation process can be run to correct the revenue price across all lines on the sales orders.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
