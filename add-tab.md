---
# required metadata

title: Tab module 
description: This topic covers Tab module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.
author:  anupamar-ms
manager: annbe
ms.date: 04/24/2020
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

This topic covers Tab module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.

## Overview
Tab module is used to organize information within tabs on a page. It can be used on any page that requires information to be presented in tabs.

Below is an example of tabs
![Example of a Accordion module](./media/ecommerce-accordion.PNG)

## Details
**Tab** is a container-like module that allows one or more **Tab item** modules to be added to it. Each Tab item represents a tab. Within each Tab item,  one or more modules can be added. There are no restrictions on the type of modules that can be added within a Tab item.


## Tab module properties

| Property name  | Values | Description |
|----------------|--------|-------------|
| Heading          | Heading| A heading can be provided to the Tab module|
| Active tab index  | Number | This defines the tab index that should be active by default on page load. If no index is provided, it defaults to first tab as the active tab |

## Tab item module properties

| Property name  | Values | Description |
|----------------|--------|-------------|
| Tite          | Text|  This defines the text for the tab item|


## Add a Tab module to a new page

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
