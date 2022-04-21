---
# required metadata

title: Set up Microsoft Clarity in Dynamics 365 Commerce
description: This topic covers how to set up Microsoft Clarity in your Dynamics 365 Commerce environment. 
author: BrianShook
ms.date: 01/28/2022
ms.topic: article
ms.prod: 
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

This topic covers how to set up Microsoft Clarity in your Dynamics 365 Commerce environment. 

[Microsoft Clarity](https://clarity.microsoft.com/) is a user behavior analytics tool that can help site owners understand user interactions with their e-commerce sites. Clarity's analysis tools enable visibility using session recordings, heatmaps, and machine learning insights to review and study user interactions. 

Integrating Clarity into your Dynamics 365 Commerce site is easy, just follow the steps in this topic to enable Clarity to provide you with an in-depth look at your user interactions.

## Sign up for Clarity

To sign up for Clarity, go to the [Clarity](https://clarity.microsoft.com/) website and select **Get started**. During the setup process, use the live production domain URL associated with your Commerce site. For additional details about Clarity setup, see [Getting started](/clarity/getting-started).

## Integrate Clarity with your Commerce site

After you have signed up for Clarity, follow these steps in Commerce site builder to integrate Clarity with your e-commerce site.

### Configure Content Security Policy for Clarity

Content Security Policy (CSP) provides an extensive set of policy directives that help you control the resources that a site page is allowed to load. Each directive defines the restrictions for a specific type of resource. For Clarity to function on your site, some CSP directives must be configured to allow Clarity resources to be called. 

To configure CSP for Clarity in Commerce site builder, follow these steps.

1. Navigate to your Commerce site.
1. Select **Site Settings \> Extensions**.
1. Select the **Content security policy** tab.
1. In the **child-src** directive section, select **Add**.
1. Enter **``https://www.clarity.ms``**.
1. Repeat steps 4 and 5 for the **connect-src** and **script-src** directives.
1. Select **Save and Publish**.

### Embed Clarity tracking script code into site pages

You can embed Clarity tracking script code into any Commerce site page that you want to track with Clarity.

To get started, copy the tracking script code for your project from the Clarity portal. The Clarity tracking script code will then need to be added to a Commerce module library *inline script module*. Depending on your configuration, the inline script module may be added directly to a specific site page, or may be required to be added as an allowable option in a site page template. 

> [!NOTE]
> When copying the Clarity tracking script code to the inline script module, you can remove the surrounding **\<script\>** tags from the string. The inline script module will add the necessary **\<script\>** tags when the page or fragment is published and rendered.

The most efficient way to include Clarity tracking script code to a range of site pages is to embed the script code in a shared site page template. The following procedure describes how to insert Clarity script code into a fragment containing an inline script module that is then used by a site page template. 

To embed the Clarity tracking code into site pages in Commerce site builder, follow these steps.

1. Go to your site in Commerce site builder.
1. Select **Fragments**, and then select **New**
1. In the **New fragment** dialog box, select the **Inline script** module.
1. For **Fragment name**, enter a name, and then select **OK**.
1. Select the **Default inline script** module slot, and then in the module property pane, under **Inline script** paste in the Clarity script. Be sure to remove the surrounding **\<script\>** tags if you copied the script string.
1. Select **Save**, and then select **Publish**.
1. Select **Templates**, and then select the template to which you want to add the fragment with the Clarity script code.
1. Select **Edit**.
1. Select the **HTML Head** slot, select the ellipsis (...), and then select **Add fragment**.
1. In the **Select fragment** dialog box, select the new fragment with the Clarity script code, and then select **OK**. Verify that the fragment appears under the **HTML Head** slot.
1. Select **Save**, and then select **Publish**. All site pages that use the updated template will now have the embedded Clarity script code.
1. Repeat the previous steps as needed for any additional templates to which you want to add the Clarity script code.

For information about how to test if the Clarity script is embedded in site pages, see [Clarity Set-Up: Verification](/clarity/clarity-setup#verification).

### Embed Clarity tracking script code into a specific site page

> [!NOTE] 
> An inline script module must be present in the **HTML Head** section of a page's template to be able to add Clarity script code to the page instance.

To embed the Clarity tracking code into a specific site page in Commerce site builder, follow these steps.

1. Go to your site in Commerce site builder.
1. Select **Pages**, select the page to which you want to add Clarity script code, and then select **Edit**.
1. Select the root node slot in the module outline pane.
1. In the properties pane under **SEO Properties**, expand the **script tag** section. Under **Inline script**, paste the Clarity tracking code. Be sure to remove the surrounding **\<script\>** tags if you copied the script string.
1. Select **Save**, select **Finish editing**, and then select **Publish**.

After Clarity script has been added to your site pages, you should begin to see data and captures in your Clarity portal. Additional time may be needed to accumulate page views before you begin seeing results.

## Additional resources

[Add script code to site pages to support telemetry](add-telemetry.md)

