---
title: Organization Selection module
description: Learn about the Organization selection module and how to add it to Microsoft Dynamics 365 Commerce business-to-business (B2B) e-commerce sites.
author: Jcava-Evenica
ms.date: 03/24/2026
ms.topic: how-to
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: v-jcavataio
ms.search.validFrom: 2022-04-21
ms.search.form: RetailOperations
ms.custom:
  - bap-template
---

# Organization selection module

[!include [banner](../includes/banner.md)]

This article covers the organization selection module and how to add it to Microsoft Dynamics 365 Commerce business-to-business (B2B) e-commerce sites.

The organization selection module is a special container for listing all the organizations a signed-in user is able to access through the B2B multioutlet functionality. Multiple organization selection is currently supported only for B2B sites with the multioutlet feature enabled. The links to this module in the header of the B2B storefront will only appear for users who have multiple organizations linked to their contact.

The following illustration shows an example of an organization selection module.

:::image type="content" source="media/organization-select-sample.png" alt-text="Screenshot of an organization selection module that lists three organizations." lightbox="media/organization-select-sample.png":::

## Add an Organization selection module to your site

To add an organization selection module to your site in Commerce site builder, follow these steps:

### Create an organization selection page

First, create the organization selection page.

1. Go to **Pages**, and select **New** to create a new page.
1. In the **Create a new page** dialog box, under **Page name**, enter **Organization selection**.
1. Under **Page URL**, enter a URL for the page, and then select **Next**.


1. Under **Choose a template**, select **General content**, and then select **Next**.
1. Under **Choose a layout**, select **Flexible layout**, and then select **Next**.
1. Under **Review and finish**, review the page configuration. If you need to edit the page information, select **Back**. If the page information is correct, select **Create page**.
1. Under **Organization selection**, select **Main slot**, select the ellipsis (**...**), and then select **Add module**.

    :::image type="content" source="media/author-web-page-organization.png" alt-text="Screenshot of adding a module to the main slot under organization selection." lightbox="media/author-web-page-organization.png":::


2. In the **Select modules** dialog box, select the **Container** module, and then select **OK**.
3. Select the **Container** slot, select the ellipsis (**...**), and then select **Add module**.
4. In the **Select modules** dialog box, select the **Organization selection** module, and then select **OK**.
5. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.

### Link the organization selection page to the route in extensions

Next, connect the organization selection page to the appropriate route in order to access the multioutlet functionality.

1. Go to **Site Settings** in the bottom left corner to expand the menu and see the navigation options.
1. Go to **Extensions** in this menu.
1. Go to the **Routes** tab at the top of the Extensions page.
1. Find the route for **Organization selection** in the list and link it with the new page created in the steps above.

1. Select **Save and Publish** at the top of the page.

    :::image type="content" source="media/extension-routes-organization.png" alt-text="Screenshot of configuring the organization selection route in the extensions page of Site builder." lightbox="media/extension-routes-organization.png":::

These settings will enable the user interface changes tied to the B2B multioutlet feature in the header of the site to link to an organization selection page for multioutlet users.

## Additional resources

[B2B multioutlet overview](./b2b/b2b-multi-outlet.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
