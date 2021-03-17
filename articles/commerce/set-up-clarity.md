---
# required metadata

title: Set up Microsoft Clarity in Dynamics 36 Commerce
description: This topic covers how to set up Microsoft Clarity in your Dynamics 365 Commerce environment. 
author: BrianShook
manager: annbe
ms.date: 03/17/2021
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

### Embed Clarity tracking script code into site pages

You can embed Clarity tracking script code into any Commerce site page you want to track with Clarity.

In the Clarity portal, copy the Clarity tracking code for your project. Note that for use in the Commerce inline script module, you can remove the surrounding **\<script\>** tags from the string copied directly from the Clarity portal (The inline script module will add the necessary '<script>' tags when the page or fragment is published and rendered).

The Clarity script code will be need to be added to an *Inline script* module. Depending on your configuration, the inline script module can be added directly to a specific page  or may be required to be added as an allowable option in the site page's template. 

The most efficient way to include Clarity tracking script code to a range of site pages is to embed the script code in a shared template. The following procedure describes how to insert Clarity script code into a fragment containing an inline script module that is then used by a template. 

To embed the Clarity tracking code into site pages in Commerce site builder, follow these steps.

1. Go to your site in Commerce site builder.
1. Select **Fragments**, and then select **New**
1. In the **New fragment** dialog box, select the **Inline script** module.
1. For **Fragment name**, enter a name, and then select **OK**.
1. Select the **Default inline script** module slot, and then in the module property pane, under **Inline script** paste in the Clarity script. Be sure to remove the surrounding **\<script\>** tags if present in your copied script string.
1. Select **Save**, and then select **Publish**.
1. Select **Templates**, and then select the template to which you want to add the fragment with the Clarity script code.
1. Select **Edit**.
1. Select the **HTML Head** slot, select the ellipsis ("*...*"), and then select **Add fragment**.
1. In the **Select fragment** dialog box, select the new fragment with the Clarity script code, and then select **OK**. Verify you see the fragment under the **HTML Head** slot.
1. Select **Save**, and then select **Publish**. All site pages that use the updated template will now have the embedded Clarity script code.
1. Repeat the previous steps as needed for any additional templates to which you want to add the Clarity script code.

For information on how to test that the Clarity script is embedded in site pages, follow the steps in [Clarity Set-Up: Verification](https://docs.microsoft.com/clarity/clarity-setup#verification).

### Embed Clarity tracking script code into a specific site page

> [!NOTE] 
> The template for the page will require an inline script module be added to the **HTML Head** section for the Clarity script code to be available in a page instance.

To embed the Clarity tracking code into a specific site page in site builder, follow these steps.

1. Select **Pages**, select the page to which you want to add Clarity script code, and then select **Edit**.
1. Select the main or top-most slot.
1. In the properties pane under **SEO Properties**, expand the **script tag** section. Under **Inline script**, paste the Clarity tracking code. Be sure to remove the surrounding **\<script\>** tags if present in your copied script string.
1. Select **Save**, select **Finish editing**, and then select **Publish**.

Once Clarity script is added to your site pages, you should begin to see data and captures in your Clarity portal. Some time or page views may be needed before you begin seeing results.

