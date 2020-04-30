---
# required metadata

title: Accordion module 
description: This topic covers Accordion module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.
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

# Accordion module


[!include [banner](includes/banner.md)]

This topic covers Accordion module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.

## Overview
Accordion module is used to organize information within a page. It provides a collapsible drawer like capability that makes it ideal for organizing information. It can be used on any page to organize information/modules.

Below is an example of Accordion module used on a Store FAQ page to organize information
![Example of a Accordion module](./media/ecommerce-accordion.PNG)

## Details
**Accordion** is a container-like module that allows one or more **Accordion item** modules to be added to it. Each Accordion item represents a collapsible drawer. Within each Accordion item,  one or more modules can be added. There are no restrictions on the type of modules that can be added within an Accordion item.


## Accordion module properties

| Property name  | Values | Description |
|----------------|--------|-------------|
| Heading          | Heading| A heading can be provided to the Accordion module|
| Expand All  | True/False | If true, an Expand/Collapse All functionality is provided to expand or collapse all items in the Accordion|
| Interaction Style| Independent, Expand one item only| This defines the type of interaction the accordion items provide. With **Independent**, each Accordion item can be expanded/collapsed independently. With **Expand one item only**, only one item can be expanded at any time, as items are expanded, previous items are collapsed|

## Accordion item module properties

| Property name  | Values | Description |
|----------------|--------|-------------|
| Tite          | Text|  This defines the text for the accordion. Selecting on the Title region, expands/collapses the section|
| Expand by default  | True/False | If true, this Accordion item will be expanded by defaul when the page is loaded|


## Add a Accordion module to a new page

To add a Accordion module to a page and set the properties, follow these steps
1. Create a new page *Store faq* using Marketing template in Fabrikam or any template without restrictions
1. In the **Default page** add a Container
1. To the Container, add Accordion module
1. In the Accordion module property panel, set a heading "Frequently asked questions"
1. In the Accordion module property panel, set Expand All to true and set Interaction style to Independent.
1. To the Accordion module, add an Accordion item. Add Title as "How do returns work".
1. To the Accordion item, add a Text block module. Add a  paragraph of text such as "Returns need to be processed via call center. Contact 1-800-FABRIKAM for returns. Products have a 30-day return policy. Return must be initiated within this time frame."
1. To the Accordion module, add a few more Accordion items and add more text block to each of them
1. Select **Save**, and then select **Preview** to preview the page.
1. Select **Finish editing** to check in the template, and then select **Publish** to publish it. 
1. The Store Faq page will show an Accordion with the content that was curated.

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Text block](add-content-rich-block.md)
