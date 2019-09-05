---
# required metadata

title: Content placement module
description: This topic describes content placement module and how it can be used on ecommerce pages.
author: Anupama Raju
manager: Brendan Sullivan
ms.date: 07/19/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: 
ms.search.industry: 
ms.author: Anupama Raju
ms.search.validFrom: 07/19/2019
ms.dyn365.ops.version: 

---
# Content Placement 

Content placement is a special container that allows modules to be placed within it in a specific layout. Content placement module supports Content placement item, Account welcome item, Account order item, Account Wishlist item and Account profile item. Its usage varies based on which modules are added to it. 

Content placement is a container of other modules and derives data from the children modules that it supports. 

## Usage examples in ecommerce:

* When content placement items are added to a content placement module, its used for showcasing product features, promotions and other informational messages using both image and text. See content placement items for more details.  

* When account welcome item or account order item are added to a content placement it’s used in Account management page. See Account management for more details. 

## Content Placement module properties

| Property name | Values                                                    | Property Description                                         |
| :-----------: | :-------------------------------------------------------- | ------------------------------------------------------------ |
|     Width     | Fit container<br />Fill screen                            | Fill container restricts the items inside   the content placement to fit within the content placement width. Fill screen   allows the items to go full-bleed and does not restrict within carousel width. <br/>The values can be changed to achieve the layout that we  want. |

 

## Creating a page with a Content Placement module

Refer to Content Placement Items and Account Management for details on how to author a page with content placement module.
