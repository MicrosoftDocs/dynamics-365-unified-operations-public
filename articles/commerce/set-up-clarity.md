---
# required metadata

title: Set up Microsoft Clarity in Dynamics 36 Commerce
description: This topic covers how to set up Microsoft Clarity in your Dynamics 365 Commerce environment. 
author: BrianShook
manager: annbe
ms.date: 03/16/2021
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: brshoo
ms.search.validFrom: 2021-01-25
ms.dyn365.ops.version: 

---

# Set up Microsoft Clarity in Dynamics 365 Commerce

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic covers how to set up Microsoft Clarity in your Dynamics 365 Commerce environment. 

[Microsoft Clarity](https://clarity.microsoft.com/) is a user behavior analytics tool which can help site owners understand user interactions with their e-commerce site. Clarity's analysis tools enable visibility using session recordings, heatmaps, and machine learning insights to review and study user interactions. Integrating Clarity into your Dynamics 365 Commerce site is easy. Just follow the below steps to get Clarity running in your site and enabling an in-depth look at your user interactions.

## Sign up for Clarity

To sign up for Clarity, go to the [Clarity](https://clarity.microsoft.com/) website and select **Get started**. During the setup process, use the live production domain URL associated with your Commerce site. For additional details on initial Clarity setup, see [Getting started](https://docs.microsoft.com/en-us/clarity/getting-started).

## Integrate Clarity with your Commerce site

Once you have set up Clarity, follow these steps in Commerce to integrate Clarity with your Commerce site.

### Set the Content Security Policy in Commerce site builder

To set the Content Security Policy in Commerce site builder, follow these steps.

1. Navigate to your Commerce site.
1. Select **Site Settings \> Extensions**.
1. Select the **Content security policy** tab.
1. In the **child-src** directive section, select **Add**.
1. Enter **``https://www.clarity.ms``**.
1. Repeat steps 4 and 5 for the **connect-src** and **script-src** directives.
1. Select **Save and Publish**.

### Set up the correlation header excluded domain in site builder

In the e-Commerce authoring tool, now set up the **Correlation header excluded domains** item for Clarity.

1. Navigate to your Commerce site.
1. Select **Site Settings > Extensions**.
1. Select the **Configuration** tab.
1. In the **Correlation header excluded domains** section, select **Add**.
1. Enter **\*.clarity.ms**.
1. Select **Save and Publish**.

### Embed the Clarity tracking code into your site pages

Now you can embed the Clarity provided tracking code into any Commerce site page you wish to track with Clarity.

- In the Clarity portal, copy the provided **Clarity tracking code** from your Clarity project. Note that for use in the Commerce inline script module, you can remove the surrounding '<script>' tags from the string copied directly from the Clarity portal (The inline script module will add the necessary '<script>' tags when the page or fragment is published and rendered).

The **Inline script** module will be needed to include the Clarity script. This module can be added to a specific page directly or may be required to be added as an allowable option in your page's template- depending on your set up. The following instructions will provide an efficient means to include the Clarity script in Commerce by using the **Inline script** module in its own fragment and including the fragment into your template. This is the most efficient example to include the Clarity script across a range of pages (using the template).

- Navigate to your e-Commerce authoring tool instance for your Commerce environment associated to your site.
- Select the **Fragments** menu and click **New** to add a new fragment.
- In the **New fragment** dialogue, under the "Select a module" section, search for "Inline" and select the **Inline script** module name presented.
- In the **Fragment name** input, provide a name for your fragment. Click **OK** to create the fragment.
- With the new fragment page, select the "Default inline script" module selected, in the property panel under the "script tag", paste the Clarity script into the **Inline script** section. Be sure to remove the surrounding '<script>' tags if included in your copied script string from the Clarity portal.
- Click **Save** and then **Publish**.
- Navigate to the **Templates** menu in site builder and choose the template you wish to include with the fragment with Clarity inline script code.
- Click **Edit** on the chosen template.
- Select the "HTML Head" section of the template tree, click the '...' and choose **Add fragment**.
- In the "Select fragment" dialogue, choose your newly created fragment with the Clarity code by name.
- Click **Ok** Verify you see the fragment under the "HTML Head" section of the template tree.
- Click **Save** and then **Publish**.
- Repeat these last 6 steps for any additional templates you wish to add the Clarity code.

Now all pages utilizing the Templates updated with the Clarity fragment will have the Clarity code included. You can test that the script is present using the steps outlined in the (Clarity Set-Up: Verification)[https://docs.microsoft.com/en-us/clarity/clarity-setup#verification] section of the Clarity Setup page.

### Page-specific addition option

If choosing to add the Clarity script to a specific page only, 
- Select a page you wish to track with Clarity from the **Pages** section of e-Commerce authoring tool and check-out for Editing
- Within the page editor, select the main or top-most node in the module tree view
- In the properties pane to the right-hand side, under **SEO Properties**, drop down the **INLINE SCRIPT** segment
    - **Note** that the Template for the page will require an **Inline script** module be added to the **HTML Head** section for **INLINE SCRIPT** to be available in a page instance.
- Expand the **script tag** dropdown and paste the Clarity tracking code into the **Inline script** section. Be sure to remove the surrounding '<script>' tags if included in your copied script string from the Clarity portal.
- **Save** your changes and **Check-in** your page edit. Then select **Publish** to publish the page.

Once the Clarity script is added to your site content, you should begin to see data and captures in your Clarity portal. Log in to Clarity and review results. Some time or traffic may be needed to begin seeing results.

