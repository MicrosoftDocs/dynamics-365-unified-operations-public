---
# required metadata

title: Service objects overview
description: Service objects are a customer’s assets and products for which you can perform a service.
author: ShylaThompson
manager: tfehr
ms.date: 07/25/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: SMAServiceObjectTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: ShylaThompson
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Service objects overview

[!include [banner](../includes/banner.md)]

Service objects are a customer’s assets and products for which you can perform a
service. Depending on the type of service you provide, objects can be tangible
or intangible:

-  Tangible objects are things, such as a machine or a building, on which you
can perform a physical service task.

    A tangible service object can also be an inventory item that you create in
the Released product details form. Depending on the inventory dimension
group that you attach to the item, you can create a service object to a
level of detail that includes the item serial number. This is useful when
you must keep track of the exact item that the service object represents.

    A tangible service object can also be an item that is not directly related
to a company's direct production or supply chain. For example, a tool kit
that is used for repairs in a service order can be a service object that is
not included in inventory. In this case, you don’t register it as an
inventory item.

-  Intangible objects are nonphysical things, such as a set of accounts or a
legal document, on which you can perform a service task.

## Example of an intangible service object

Company A maintains the financial records for several small companies. One
of Company A's clients is the local football team, for which Company A does
the weekly bookkeeping and annual audit of the club's accounts. The club's
accounts are set up in the Service objects form and specified as the object
in the service agreement. There are two service agreement lines for the
object. Line 1 is weekly bookkeeping with a weekly interval assigned to the
line, and line 2 is the annual audit with a yearly interval assigned to it.

## Related topics

[Create service objects](create-service-objects.md)

