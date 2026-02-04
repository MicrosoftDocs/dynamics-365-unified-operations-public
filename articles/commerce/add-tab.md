---
title: Tab module
description: Learn about tab modules and how to add them to Microsoft Dynamics 365 Commerce site pages.
author: anupamar-ms
ms.date: 01/14/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Tab module

[!include [banner](includes/banner.md)]

This article describes tab modules and explains how to add them to Microsoft Dynamics 365 Commerce site pages.

Tab modules are container-like modules that organize the information on a site page into tabs. Use them on any page where you need to present information on tabs.

Add one or more tab item modules to each tab module. Each tab item module represents a single tab. Add one or more modules to each tab item module. There are no restrictions on the types of modules that you can add to a tab item module.

The following image shows an example of a tab module on a site page. In this example, the **Shipping** tab is selected.

:::image type="content" source="./media/ecommerce-tab.PNG" alt-text="Screenshot of a tab module.":::

## Tab module properties

| Property name | Values | Description |
|---------------|--------|-------------|
| Heading | Text | Enter an optional text heading for the tab module. |
| Active Tab Index | Number | Enter the tab that should be active by default when a page loads. If you don't provide a value, the first tab item is active by default. |

## Tab item module properties

| Property name | Values | Description |
|---------------|--------|-------------|
| Title | Text | Enter the title text for the tab item module. |

## Add a tab module to a page

To add a tab module to a page and set the properties, follow these steps:

1. Create a new page named **Store policies page** by using the Fabrikam marketing template or any template that has no restrictions.
1. In the **Main** slot of the **Default page**, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Container** module, and then select **OK**.
1. In the **Container** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Tab** module, and then select **OK**.
1. In the property pane of the tab module, select **Heading** next to the pencil symbol.
1. In the **Heading** dialog box, under **Heading Text**, enter heading text (for example, **Policies**). Then select **OK**.
1. In the **Tab** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Tab item** module, and then select **OK**.
1. In the property pane of the tab item module, under **Title**, enter title text (for example, **Delivery**).
1. In the **Tab item** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Text block** module, and then select **OK**.
1. In the property pane of the text block module, under **Rich text**, enter a paragraph of text.
1. In the **Tab** slot, add a few more tab item modules that have titles. In each tab item module, add a text block module that has content.
1. Select **Save**, and then select **Preview** to preview the page. The page shows a tab module that contains tab item modules with the content that you added.
1. Select **Finish editing** to check in the page, and then select **Publish** to publish it.

## Additional resources

[Module library overview](starter-kit-overview.md)

[Container module](add-container-module.md)

[Accordion module](add-accordion.md)

[Text block module](add-content-rich-block.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
