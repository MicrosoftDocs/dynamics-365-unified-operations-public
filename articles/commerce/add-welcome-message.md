---
# required metadata

title: Add a welcome message
description: This topic describes how to add a welcome message to your Microsoft Dynamics 365 Commerce website.
author: psimolin
manager: annbe
ms.date: 04/13/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: psimolin
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Add a welcome message


[!include [banner](includes/banner.md)]

This topic describes how to add a welcome message to your Microsoft Dynamics 365 Commerce website.

## Overview

A welcome message on your e-Commerce website can inform visitors about ongoing sales, site updates, or availability of seasonal collections. The welcome message is set by using the alert module.

The alert module should be added to the **Error/Information messages** slot of the header fragment. The alert module lets you specify the text that is shown, the text color, and the alignment. It also lets you specify whether visitors to the site can dismiss the message.

When a welcome message is added to a shared header fragment, it will be shown on every page that uses the template where that shared header fragment is used.

To add a welcome message to your site, follow these steps.

1. In Commerce site builder, go to your site.
1. Select **Fragments**.
1. Select the header fragment to add the message to.
1. In the outline tree, expand **Error/Information messages**.
1. Select the alert module, and then select **OK**. If an alert module doesn't yet exist, first select the ellipsis button (**...**) next to **Error/Information messages**, and then select **Add module**.
1. In the property pane on the right, on the **Data** tab, select **Add Data Source**, and then select **Content**.
1. In the **Input Text** field, enter the text of the welcome message.
1. Select **Save**, select **Finish editing** to check in the header fragment, and then select **Publish** to publish it. 

The welcome message will now appear at the top of every site page that uses the selected header fragment.

## Additional resources

[Add a logo](add-logo.md)

[Select a site theme](select-site-theme.md)

[Work with CSS override files](css-override-files.md)

[Add a favicon](add-favicon.md)

[Add a copyright notice](add-copyright-notice.md)

[Add languages to your site](add-languages-to-site.md)

[Add script code to site pages to support telemetry](add-telemetry.md)

