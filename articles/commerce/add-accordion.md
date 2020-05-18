---
# required metadata

title: Accordion module 
description: This topic covers accordion modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
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

# Accordion module

[!include [banner](includes/banner.md)]

This topic covers accordion modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

## Overview

Accordion modules are container-like modules used to organize information within a page by providing a collapsible drawer-like capability. An accordion module can be used on any page to organize information or modules.

The accordion module allows one or more accordion item modules to be added to it. Each accordion item represents a collapsible drawer. Within each accordion item, one or more modules can be added. There are no restrictions on the type of modules that can be added within an accordion item.

The following image shows an example of an accordion module used to organize information on a store FAQ page.

![Example of a Accordion module](./media/ecommerce-accordion.PNG)

## Accordion module properties

| Property name  | Values | Description |
|----------------|--------|-------------|
| Heading          | Heading| Optional heading for the accordion module|
| Expand All  | True/False | If true, an Expand/Collapse All functionality is enabled to expand or collapse all items in the accordion module|
| Interaction Style| Independent, Expand one item only| Defines the type of interaction the accordion items provide. With **Independent**, each accordion item can be expanded or collapsed independently. With **Expand one item only**, only one item can be expanded at any time, and as items are expanded, previous items are collapsed|

## Accordion item module properties

| Property name  | Values | Description |
|----------------|--------|-------------|
| Title          | Text|  This defines the text for the accordion. Selecting on the title region expands or collapses the section|
| Expand by default  | True/False | If True, this accordion item will be expanded by default when the page is loaded|


## Add an accordion module to a test page

To add a accordion module to a test page and set its properties in site builder, follow these steps.

1. Create a new page named "Store FAQ" using the Fabrikam marketing template (or any template without restrictions).
1. In the **Main** slot of the **Default page**, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Container** module, and then select **OK**.
1. In the **Container** slot, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Accordion** module, and then select **OK**.
1. In the accordion module property pane on the right, next to the pencil symbol select **Heading**.
1. In the **Heading** dialog box, enter "Frequently asked questions" under **Heading Text**, and then select **OK**.
1. In the accordion module property pane, select the **Show expand all** check box, and then select **Independent** from the **Interaction style** drop down menu.
1. In the **Accordion** slot, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Accordion item** module, and then select **OK**.
1. In the accordion module property pane, enter "How do returns work" under **Title**.
1. In the **Accordion item** slot, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Text block** module, and then select **OK**.
1. In the text block module property pane, enter a paragraph of text such as "Returns need to be processed via call center. Contact 1-800-FABRIKAM for returns. Products have a 30-day return policy. Return must be initiated within this time frame.".
1. In the **Accordion** slot, add a few more accordion item modules, each containing a text block with content added. 
1. Select **Save**, and then select **Preview** to preview the page. The page will show an accordion module with the content that was added above.
1. Select **Finish editing** to check in the page, and then select **Publish** to publish it. 

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Text block](add-content-rich-block.md)
