---
# required metadata

title: Revenue recognition overview 
description: Companies in industries that sell multiple elements, such as products, services, subscriptions, and so on, must be able to break out these multi-element orders to recognize revenue based on a set of company and industry-specific guidelines.
author: kweekley
manager: aolson
ms.date: 08/24/2018
ms.topic: index-page
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  Customer
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2018-08-30
ms.dyn365.ops.version: 8.0.4

---

# Revenue recognition overview

[!Note] The Revenue recognition feature is not enabled through Feature management yet. Currently you must use configuration keys to enable it. 

Companies in industries that sell multiple elements, such as products, services, subscriptions, and so on, must be able to break out these multi-element orders to recognize revenue based on a set of company and industry-specific guidelines.

In general, the revenue recognition process can be used to:

*	Allocate revenue to help ensure that the appropriate revenue price is recognized based on the value of the components within the multi-element orders
*	Defer revenue based on a revenue schedule that represents the contractual timeframe and percentages for recognizing revenue over time
The Revenue recognition feature provides a flexible framework for defining company specific rules for recognizing both the revenue price and the revenue schedule. 

The Revenue recognition feature provides a flexible framework for defining company specific rules for recognizing both the revenue price and the revenue schedule. 

Revenue recognition is supported on the sales order document with released products. The sales order can also originate from a time and material project. The released products contain the setup required to determine the revenue price and the revenue schedule. 

Companies can use the revenue schedule functionality without using the revenue price functionality, which means that the price on the sales order lines will be used, either as revenue or deferred revenue. If a revenue schedule exists on the sales order line, the price on the sales order line will be deferred. If a revenue schedule does not exist, the price on the sales order line will be posted to a revenue account when it is invoiced. 

The revenue price is calculated at either when the sales order is confirmed, or when the invoice is posted. To preview the revenue price before posting the invoice, the sales order must be confirmed.  

When the sales order is confirmed, an expected revenue schedule is also created if any sales order line contains a revenue schedule. The expected revenue schedule is deleted when the order is invoiced, and the expected revenue schedule is replaced with the actual revenue recognition schedule.  

The details of the revenue recognition schedule are maintained for each sales order line, allowing the revenue recognition manager to view the details, and release lines to revenue when the contractual obligation has been completed. The revenue recognition manager can create a revenue journal at the end of each period to release any schedule lines that are due on or before the date defined by the manager. The revenue journal is not posted immediately, allowing the manager to verify that the correct amounts are being released from deferred revenue to actual revenue. 

If there is a contractual change which results in a new sales order line, added to either the existing sales order or a new sales order, a reallocation process can be run to correct the revenue price across all lines of the sales order(s). 



