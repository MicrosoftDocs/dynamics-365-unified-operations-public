---
# required metadata

title: Tab module 
description: This topic covers tab modules and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.
author:  anupamar-ms
manager: annbe
ms.date: 05/25/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 
---

# Tab module

[!include [banner](includes/banner.md)]

This topic covers tab modules and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.

## Overview

Tab modules are container-like modules used to organize information within tabs on a site page, and can be used on any page that requires information to be presented in tabs.

A tab module can have one or more tab item modules added to it, with each tab item module representing a single tab. Within each tab item module, one or more modules can be added. There are no restrictions on the type of modules that can be added to tab item modules.

The following image shows an example of a tabs module on a site page with the **Shipping** tab selected.

![Example of a tab module](./media/ecommerce-tab.PNG)

## Tab module properties

| Property name  | Values | Description |
|----------------|--------|-------------|
| Heading          | Text | This property specifies an optional text heading for the tab module.|
| Active tab index  | Number | This property specifies the tab index that should be active by default on page load. If no tab index is provided, it defaults to the first tab item as the active tab. |

## Tab item module properties

| Property name  | Values | Description |
|----------------|--------|-------------|
| Title          | Text|  This property specifies the title text for the tab item module.|

## Add a tab module to a page

To add a Tab module to a page and set the properties, follow these steps
1. Create a new page *Store policies page* using Marketing template in Fabrikam or any template without restrictions
1. In the **Default page** add a Container
1. To the Container, add Tab module
1. In the Tab module property panel, set a heading "Policies"
1. To the Tab module, add an Tab item. Add Title as "Delivery".
1. To the Tab item, add a Text block module. Add a few paragraphs of text explaining how Delivery works
1. To the Tab module, add a few another Tab items called "Returns".
1. To the "Returns" tab item, add a text block and add a few paragraphs of text explaining how Returns work
1. Similarly, add few more tabs 
1. Select **Save**, and then select **Preview** to preview the page.
1. Select **Finish editing** to check in the template, and then select **Publish** to publish it. 
1. The Store policies page will show an tab with the content that was curated.

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Text block](add-content-rich-block.md)
