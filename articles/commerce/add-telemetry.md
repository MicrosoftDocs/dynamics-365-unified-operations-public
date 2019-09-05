---
# required metadata

title: Add script code to site pages to support telemetry
description: This topic describes how to add client-side script code to your site pages to support the collection of client-side telemetry. 
author: bicyclingfool
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
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

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to add client-side script code to your site pages to support the collection of client-side telemetry. 

## Overview

Web analytics are an essential tool for understanding how your customers interact with your site and helping you make decisions that optimize the experience for maximum conversion. There are many web analytics packages available to help you in this regard, including (but not limited to) Google Analytics, Clicky, Moz Analytics, KISSMetrics, and others. Most web analytics packages require you to add client-side script within the <head> tag of the HTML on all pages of your site. 
 
[!NOTE]
These instructions are equally applicable for any other custom client-side functionality not offered natively by Dynamics 365 Commerce. 

### Create a reusable fragment to contain your script code

To create a fragment for your script code that can be reused across all pages on your site, do the following.

1. Go to **Fragments > New page fragment**.
3. Select **External Script**, enter a name for the fragment and click **OK**.
4. In the fragment hierarchy, click the **script injector** module child of the fragment you just created.
5. Add your client-side script and make other configuration options in the property panel on the right. See the help topic for the [External Script module](http://) for information about configuring this module.  

### Add the fragment to your template(s)

1. Go to **Templates** and open the template for the pages to which you want to add web analytics script.
3. Expand the template hierarchy in the left pane to expose the **HTML Head** slot.
4. Click on the ellipsis for the HTML Head slot and click **Add fragment**.
5. Select the fragment you created for your web analytics script.
6. Save the template and check it in.

[!NOTE]
When done, you will need to publish the fragment and the master template. 

For further information about adding script to master templates, see the [Add script to master templates](http://) help topic.
