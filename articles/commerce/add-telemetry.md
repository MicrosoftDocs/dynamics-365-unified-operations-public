---
title: Add script code to site pages to support telemetry
description: This article describes how to add client-side script code to your site pages to support the collection of client-side telemetry.
author: bicyclingfool
ms.date: 07/26/2024
ms.topic: how-to
audience: Application user
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Add script code to site pages to support telemetry

[!include [banner](includes/banner.md)]

This article describes how to add client-side script code to your site pages to support the collection of client-side telemetry.

Web analytics are an essential tool when you want to understand how your customers interact with your site and make decisions that will help optimize the experience for maximum conversion. Many web analytics packages are available to help you achieve these goals, such as Google Analytics, Clicky, Moz Analytics, and KISSMetrics. Most web analytics packages require that you add client-side script code in the **\<head\>** element of the HTML for all pages of your site.

> [!NOTE]
> The instructions in this article also apply to other custom client-side functionality that Microsoft Dynamics 365 Commerce doesn't natively offer.

## Create a reusable fragment for your script code

A fragment allows you to reuse inline or external script code across all pages on your site, regardless of the template they use.

### Create a reusable fragment for your inline script code

To create a reusable fragment for your inline script code in site builder, follow these steps.

1. Go to **Fragments**, and then select **New**.
1. In the **New fragment** dialog box, select **Inline script**.
1. Under **Fragment name**, enter a name for the fragment, and then select **OK**.
1. Under the fragment that you created, select the **Default inline script** module.
1. In the property pane on the right, under **Inline script**, enter your client-side script. Then configure other options as you require.
1. Select **Save**, and then select **Finish editing**.
1. Select **Publish**.

### Create a reusable fragment for your external script code

To create a reusable fragment for your external script code in site builder, follow these steps.

1. Go to **Fragments**, and then select **New**.
1. In the **New fragment** dialog box, select **External script**.
1. Under **Fragment name**, enter a name for the fragment, and then select **OK**.
1. Under the fragment that you created, select the **Default external script** module.
1. In the property pane on the right, under **Script source**, add an external or relative URL for the external script source. Then configure other options as you require.
1. Select **Save**, and then select **Finish editing**.
1. Select **Publish**.

> [!NOTE]
> If content security policy (CSP) is enabled for your site, ensure that all external URLs are added to the **script-src** CSP directive in Commerce site builder. For more information, see [Manage Content Security Policy (CSP)](dev-itpro/manage-csp.md).

## Add a fragment that includes script code to a template

To add a fragment that includes script code to a template in site builder, follow these steps.

1. Go to **Templates**, and open the template for the pages that you want to add your script code to.
1. In the left pane, expand the template hierarchy to show the **HTML Head** slot.
1. In the **HTML Head** slot, select the ellipsis button (**...**), and then select **Add fragment**.
1. Select the fragment that you created for your script code.
1. Select **Save**, and then select **Finish editing**.
1. Select **Publish**.

## Add an external script or inline script directly to a template

If you want to insert an inline or external script directly into a set of pages that are controlled by a single template, you don't have to create a fragment first.

### Add an inline script directly to a template

To add an inline script directly to a template in site builder, follow these steps.

1. Go to **Templates**, and open the template for the pages that you want to add your script code to.
1. In the left pane, expand the template hierarchy to show the **HTML Head** slot.
1. In the **HTML Head** slot, select the ellipsis button (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select **Inline script**.
1. In the property pane on the right, under **Inline script**, enter your client-side script. Then configure other options as you require.
1. Select **Save**, and then select **Finish editing**.
1. Select **Publish**.

### Add an external script directly to a template

To add an external script directly to a template in site builder, follow these steps.

1. Go to **Templates**, and open the template for the pages that you want to add your script code to.
1. In the left pane, expand the template hierarchy to show the **HTML Head** slot.
1. In the **HTML Head** slot, select the ellipsis button (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select **External script**.
1. In the property pane on the right, under **Script source**, add an external or relative URL for the external script source. Then configure other options as you require.
1. Select **Save**, and then select **Finish editing**.
1. Select **Publish**.

## Additional resources

[Add a logo](add-logo.md)

[Select a site theme](select-site-theme.md)

[Work with CSS override files](css-override-files.md)

[Add a favicon](add-favicon.md)

[Add a copyright notice](add-copyright-notice.md)

[Add languages to your site](add-languages-to-site.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
