---
# required metadata

title: Footer module
description: 
author: AnupamaR
manager: annbe
ms.date: 08/30/2019
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Consumer
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: AnupamaR
ms.search.validFrom: 2019-08-30
ms.dyn365.ops.version: 
---

# Footer module

The **Footer** module is special container that is used for hosting the modules that will be displayed on the page footer. For instance, it includes links to various pages across the site such as Contact Us, Store Policies, Follow us.

## Properties of Footer

Footer supports Heading and Width property similar to most containers. Footer container has multiple Footer category slots. Each Footer category will render as a column in the footer module.

## Modules available in Footer

**Footer items:** Footer items can be a Heading, Image and/or a link. A Heading can be used standalone or in combination with image and link. Each web link on the footer can be configured as a Link E.g. Contact Us, Privacy etc. Image can also supported be for items in footer that require image and a link E.g. Social links.

**Back to top.** Back to top allows quick navigation to the top of the page. A destination must be provided, the default is # which takes to the top of the page. 


## Authoring a Footer Module

1. Create a page fragment with a Footer module

2. Populate the Footer module slots with the respective modules

3. In Footer category, add Footer items. Add a Heading

4. In Footer category, add multiple Footer items with Link

5. Repeat for each footer category

6. Save the page fragment

7. Check in and Publish

On every page template created for the site:

1. Add the Footer fragment to the Footer in the Main Slot of the Default Page

2. Save the template

3. Check in and Publish

This will ensure every page renders the footer
