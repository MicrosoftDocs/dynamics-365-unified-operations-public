---
# required metadata

title:Setting up Clarity in Commerce
description: This topic reviews setting up the Clarity service in your Dynamics 365 Commerce environment.
author: BrianShook
manager: BrendanSullivanMSFT
ms.date: 01/25/2021
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: josaw
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

# Setting up Clarity in Dynamics 365 Commerce

This topic covers the set up of Clarity service in your Dynamics 365 Commerce environment. 

## Overview

[Clarity](https://clarity.microsoft.com/) is a behavioral analysis tool which helps you as a site owner understand your end user's interactions with your site. Clarity's analysis tools enable visibility using Session Recordings, Heatmaps, and ML Insights to review and study user interactions. Integrating Clarity in your Dynamics 365 Commerce site is easy. Just follow the below steps to get Clarity running in your site and enabling an in-depth look at your user interactions!

## Sign Up for Clarity

Navigate to the [Clarity](https://clarity.microsoft.com/) website and use the "Get started" option to sign-up for Clarity. 

During the setup process, use the production website url that will be associated to your Commerce site (the live production domain).

See Clarity's [Getting Started](https://docs.microsoft.com/en-us/clarity/getting-started) guide for additional details for initial Clarity setup.

## Integrate Clarity with your Commerce Site

Once you have completed the Clarity setup, follow these steps in Commerce to connect Clarity to your Commerce site:



### Set the Content security policy for Clarity

Open the e-Commerce authoring tool instance for your commerce environment associated to your site. Then follow these steps:

- Navigate to your site in the e-Commerce authoring tool
- Select **Site Settings > Extensions**
- Click on the **Content security policy** tab
- In the **child-src** section, click **Add**
- Enter "https://www.clarity.ms"
- Repeat these steps for the **connect-src** and **script-src** sections also, adding the "https://www.clarity.ms" lines per section
- Then click the **Save and Publish** button to commit the changes



### Embed the Clarity tracking code into your site pages

Now you can embed the Clarity provided tracking code into any Commerce site page you wish to track with Clarity.

- In the Clarity portal, copy the provided **Clarity tracking code** from your Clarity project.

- Navigate to your e-Commerce authoring tool instance for your Commerce environment associated to your site.
- Select a page you wish to track with Clarity from the **Pages** section of e-Commerce authoring tool and check-out for Editing
- Within the page editor, select the main or top-most node in the module tree view
- In the properties pane to the right-hand side, under **SEO Properties**, drop down the **INLINE SCRIPT** segment
    - Note that the Template for the page will require the **Inline script** module be added to the **HTML Head** section for **INLINE SCRIPT** to be available in a page instance.
- Expand the **script tag** dropdown and paste the Clarity tracking code into the **Inline script** section.
- **Save** your changes and **Check-in** your page edit. Then select **Publish** to publish the page

Your page now contains the tracking script and is ready to track activity by Clarity. Some time may be required for data collection and aggregation before results begin to show in the Clarity portal.



