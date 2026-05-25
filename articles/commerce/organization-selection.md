---
title: Organization selection module (preview)
description: Learn about the organization selection module and how to add it to Microsoft Dynamics 365 Commerce business-to-business (B2B) e-commerce sites.
author: Jcava-Evenica
ms.date: 05/25/2026
ms.topic: how-to
ms.reviewer: mirao
ms.search.region: Global
ms.author: v-jcavataio
ms.search.validFrom: 2022-04-21
ms.search.form: RetailOperations
ms.custom:
  - bap-template
---

# Organization selection module (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [banner](../includes/preview-banner.md)]

This article explains what the organization selection module is and how to add it to Microsoft Dynamics 365 Commerce business-to-business (B2B) e-commerce sites.

The organization selection module is a special container for listing all the organizations a signed-in user can access through the B2B multioutlet functionality. Multiple organization selection currently supports only B2B sites with the multioutlet feature enabled. The links to this module in the header of the B2B storefront only appear for users who have multiple organizations linked to their contact.

The following illustration shows an example of an organization selection module:

:::image type="content" source="media/organization-select-sample.png" alt-text="Screenshot of an organization selection module that lists three organizations." lightbox="media/organization-select-sample.png":::

## Add an organization selection module

To add an organization selection module to your site in the Commerce site builder, follow these steps:

### Step 1: Create an organization selection page

First, create the organization selection page:

1. Go to **Pages**, and select **New** to create a new page.
1. In **Create a new page**, under **Page name**, enter **Organization selection**.
1. Under **Page URL**, enter a URL for the page, and then select **Next**.
1. Under **Choose a template**, select **General content**, and then select **Next**.
1. Under **Choose a layout**, select **Flexible layout**, and then select **Next**.
1. Under **Review and finish**, review the page configuration. If you need to edit the page information, select **Back**. If the page information is correct, select **Create page**.
1. Under **Organization selection**, select **Main slot**, select the ellipsis (...), and then select **Add module**.

    :::image type="content" source="media/author-web-page-organization.png" alt-text="Screenshot of adding a module to the main slot under organization selection." lightbox="media/author-web-page-organization.png":::

1. In **Select modules**, select the **Container** module, and then select **OK**.
1. Select the **Container** slot, select the ellipsis (...), and then select **Add module**.
1. In **Select modules**, select the **Organization selection** module, and then select **OK**.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.

### Step 2: Link the organization selection page to the route in extensions

Next, connect the organization selection page to the appropriate route so you can access the multioutlet functionality.

1. Go to **Site Settings** in the lower left corner to expand the menu and see the navigation options.
1. Go to **Extensions** in this menu.
1. Go to the **Routes** tab at the top of the extensions page.
1. Find the route for **Organization selection** in the list and link it with the new page you created in previous steps.

1. Select **Save and Publish** at the top of the page.

    :::image type="content" source="media/extension-routes-organization.png" alt-text="Screenshot of configuring the organization selection route in the extensions page of Site builder." lightbox="media/extension-routes-organization.png":::

These settings enable the user interface changes tied to the B2B multioutlet feature in the header of the site to link to an organization selection page for multioutlet users.

## More resources

[B2B multioutlet overview](./b2b/b2b-multi-outlet.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
