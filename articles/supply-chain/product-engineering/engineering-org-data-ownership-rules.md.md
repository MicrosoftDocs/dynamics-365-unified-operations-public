---
# required metadata

title: Engineering organization and data ownership rules
description: To ensure that the master data for products is created and maintained centrally, you can use one or more engineering organizations. The engineering organization represents the organization that owns the engineering products and its engineering relevant data.
author: XXXX
manager: tfehr
ms.date: 07/31/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: benebotg
ms.search.validFrom: 2020-07-31
ms.dyn365.ops.version: Release 10.0.13
---

# Engineering organization and data ownership rules

## Engineering organization

To ensure that the master data for products is created and maintained centrally, you can use one or more **engineering organizations**. The engineering organization represents the organization that owns the engineering products and its engineering relevant data. The engineering organization is always connected to a **legal entity** , which is also an organization. With this connection, the system makes sure that there is **central entry point for all engineering relevant data** within the company for engineering products. Here the engineering products will be created, and the engineering relevant data will be maintained. From this central point, the engineering products and engineering relevant data will be released to **operational companies** , which are the other legal entities (For more information about the release management, see…). These operational companies will use the engineering data as it is designed by the engineering organization. Any logistical data will be maintained locally by each company itself.

## Engineering product category and engineering organizations

To ensure that engineering products can be created as per the company&#39;s business rules, you need to setup engineering product categories. Engineering product categories will help the users by ensuring the behavior of the products will be as needed. For more information on engineering product categories, see …

On the engineering product category, it is defined which organization owns the products of this engineering product category. This will help the users by making sure the engineering product category can only be used to create product in the correct engineering organization. With this, also automatically the maintenance of the engineering products of this engineering product category, belongs to this engineering organization.

## Data owned by the engineering organization

With the ownership of the engineering relevant data, the engineering organization will control the following (engineering) data:

- (creation of) **engineering products** : the engineering product types, can only be used to create new products in the connected engineering organization. In the operational companies, the local data will be maintained.
- (creation of) **engineering versions** : with creating engineering products in the engineering organization, also automatically engineering version are created. Creating new versions is only possible in the engineering organization as well.
- (creation and maintenance of) **engineering attributes** : with creating engineering products in the engineering organization, also automatically the engineering attributes are added. The values can only be maintained in the engineering organization. For more information about engineering attributes, see…
- (creation and maintenance of) **bill of materials connected to the engineering versions** : bill of materials can be directly connected to the engineering versions in the engineering organization. When these bills of materials are released to other legal entities, the engineering data on the bills of materials are protected from being changed:
  - The released bill of material lines cannot be removed in the operational organization
  - The engineering fields on the bill of material lines are protected to be edited. All other fields are logistical implementation fields and they can be edited in the operational organization.

It will be possible in the operational organization to add additional bill of material lines to the same bill of material which enables adding local additions like packaging materials or lubrication fluids.

It is also possible to add completely new local bill of materials in the operational organization. This can be needed as an example in case it is chosen to not receive the bill of material during the release (For more information about the release management, see…). The ownership and maintenance of these local bill of materials is with the operational organization as well.

All changes made locally are preserved when updates from the engineering organization to the bill of material are released again.

- (creation and maintenance of) **routes connected to the engineering versions** : routes can be directly connected to the engineering versions in the engineering organization. When these routes are released to other legal entities, the engineering data on the routes are protected from being removed. It will be possible to add additional operations to the same route which enables adding local specific route steps.

It is also possible to add completely new routes in the operational organization. This can be needed as an example in case it is chosen to not receive the routes during the release (For more information about the release management, see…). The ownership and maintenance of these local routes is with the operational organization as well.

All changes made locally are preserved when updates from the engineering organization to the routes are released again.

- (creation and maintenance of) **engineering documents** : engineering documents which are attached to the engineering version in the engineering organization. When these documents are released to other legal entities, the documents are protected from being removed in the operational organization

It is possible to add completely new documents in the operational organization. The ownership and maintenance of these documents is with the operational organization as well.