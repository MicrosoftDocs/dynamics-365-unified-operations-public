---
# required metadata

title: Add script code to site pages to support telemetry
description: This topic describes how to add client-side script code to your site pages to support the collection of client-side telemetry. 
author: bicyclingfool
manager: annbe
ms.date: 12/12/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Operations, Retail, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: StuHarg
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5
---

# Add script code to site pages to support telemetry


[!include [banner](includes/banner.md)]

This topic describes how to add client-side script code to your site pages to support the collection of client-side telemetry.

## Overview

Web analytics are an essential tool when you want to understand how your customers interact with your site and make decisions that will help optimize the experience for maximum conversion. Many web analytics packages are available to help you achieve these goals, such as Google Analytics, Clicky, Moz Analytics, and KISSMetrics. Most web analytics packages require that you add client-side script code in the **\<head\>** element of the HTML for all pages of your site.

> [!NOTE]
> The instructions in this topic also apply to other custom client-side functionality that Microsoft Dynamics 365 Commerce doesn't natively offer.

## Create a reusable fragment for your script code

After you create a fragment for your script code, it can be reused across all pages on your site.

1. Go to **Fragments \> New page fragment**.
2. Select **External Script**, enter a name for the fragment, and then select **OK**.
3. In the fragment hierarchy, select the **script injector** module child of the fragment that you just created.
4. In the property pane on the right, add your client-side script, and set other configuration options as you require.

## Add the fragment to templates

1. Go to **Templates**, and open the template for the pages that you want to add your script code to.
2. In the left pane, expand the template hierarchy to show the **HTML Head** slot.
3. Select the ellipsis button (**...**) for the **HTML Head** slot, and then select **Add fragment**.
4. Select the fragment that you created for your script code.
5. Save the template, and check it in.

> [!NOTE]
> After you've finished, you must publish the fragment and the master template. 

## Additional resources

[Add a logo](add-logo.md)

[Select a site theme](select-site-theme.md)

[Work with CSS override files](css-override-files.md)

[Add a favicon](add-favicon.md)

[Add a welcome message](add-welcome-message.md)

[Add a copyright notice](add-copyright-notice.md)

[Add languages to your site](add-languages-to-site.md)

