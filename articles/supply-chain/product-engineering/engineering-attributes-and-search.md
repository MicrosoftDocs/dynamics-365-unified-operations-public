---
# required metadata

title: Engineering attributes and engineering attribute search
description: To ensure that the all product master data can be registered in the system, specify all non-standard characteristics using engineering attributes. With the engineering attribute search, you can easily find products based on these registered characteristics.
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

# Engineering attributes and engineering attribute search

To ensure that the all product master data can be registered in the system, specify all non-standard characteristics using engineering attributes. With the engineering attribute search, you can easily find products based on these registered characteristics.

## Engineering attributes

Engineering products have a lot of characteristics and properties which you want to capture. Some of these properties you can populate in available fields, but based on your requirements, additional properties need to be captured as well. With the engineering attributes, you can define your own engineering attributes and make them part of the product definition.

### Creating an engineering attribute

Before you can create engineering attribute, you will first need to create attribute types. Reason for this is, engineering attributes can be of different **data types** , as examples: free text, text with a table to choose from, integer and decimals. This data type is chosen at the attribute types, which makes this setup re-usable on multiple engineering attributes. The engineering attributes will have a name which is the name of the attribute and there is a **friendly name** which you can use to have a different name in the user interface of the system,

### Connecting the engineering attribute to the engineering product type

Some engineering attributes will be applicable for all products, but not all products will need the same engineering attributes. As an example, you will not need electrical related attributes on mechanical products. Therefore, you can assign per engineering product type, which engineering products are relevant and must be part of the product definition. You can also choose which engineering attributes are **mandatory** and if there is a **default value**.

### Populating the engineering attributes

The engineering attributes connected to the engineering product type, will appear in the engineering product creation dialog. Here you can populate them. Afterwards, the values can be changed in the engineering version form or as part of engineering change management in the engineering change order. For more information on engineering change management, see….

## Engineering attribute search

With the engineering attribute search, you can search on products that meet the engineering attributes values as you define them. This will enable you to find the existing engineering products easily based on their characteristics. You can search within products of an engineering product type, or you leave it empty to search across all engineering products. The search is enabled form product master data forms, as well from transactional places in the system, like sales orders. On a transactional form like the sales order, you can even use the engineering attribute form to search and create new lines with the **Add as new line** button.
