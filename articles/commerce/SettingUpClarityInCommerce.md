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

[Clarity](https://clarity.microsoft.com/) is a behavioral analysis tool which helps you as a site owner understand your public user's interactions with your site. Clarity's analysis tools enable visibility using Session Recordings, Heatmaps, and ML Insights to review and study user interactions. Integrating Clarity in your Dynamics 365 Commerce site is easy. Just follow the below steps to get Clarity running in your site and enabling an in-depth look at your user interactions!

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

### Set up the Correlation Header Excluded Domain in Site Settings

In the e-Commerce authoring tool, now set up the **Correlation header excluded domains** item for Clarity.

- Navigate to your site in the e-Commerce authoring tool if not already there from the previous setup steps.
- Select **Site Settings > Extensions**.
- Click on teh **Configruation** tab.
- In the **correlation header excluded domains** section, click **Add**.
- Enter "*.clarity.ms".
- Then click the **Save and Publish** button to commit the changes.

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

### Page-Specific Addition Option
If choosing to add the Clarity script to a specific page only, 
- Select a page you wish to track with Clarity from the **Pages** section of e-Commerce authoring tool and check-out for Editing
- Within the page editor, select the main or top-most node in the module tree view
- In the properties pane to the right-hand side, under **SEO Properties**, drop down the **INLINE SCRIPT** segment
    - **Note** that the Template for the page will require an **Inline script** module be added to the **HTML Head** section for **INLINE SCRIPT** to be available in a page instance.
- Expand the **script tag** dropdown and paste the Clarity tracking code into the **Inline script** section. Be sure to remove the surrounding '<script>' tags if included in your copied script string from the Clarity portal.
- **Save** your changes and **Check-in** your page edit. Then select **Publish** to publish the page.

Once the Clarity script is added to your site content, you should begin to see data and captures in your Clarity portal. Log in to Clarity and review results. Some time or traffic may be needed to begin seeing results.

