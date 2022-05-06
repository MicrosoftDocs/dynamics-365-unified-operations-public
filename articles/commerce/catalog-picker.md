---
  
# required metadata

title: Add a catalog picker to your eCommerce website
description: This topic describes how to add a catalog picker for Microsoft Dynamics 365 Commerce business-to-business (B2B) sites.
author: ashishmsft
ms.date: 05/06/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2022-04-21
---

## Catalog picker module

This topic covers catalog picker module and describes how to add them to site pages in Microsoft Dynamics 365 Commerce. 

A catalog picker module is a special container that is used to list all the catalogs that are available to a business-to-business (B2B) user for shopping. The following example image shows an example of a catalog-picker module. 

## Add a catalog picker module to your site

To add a catalog picker module to your site, follow these steps.

1. Create a page for 'Catalog-picker' 
1. Provide details like page name, page URL etc.
1. Choose template as 'General content' 
1. Choose layout as 'Flexible layout' 
1. Review and finish page creation wizard experience. 
1. Next, go to page and click on 'Edit' 
1. From the page structure, under 'Main slot' add 'Container' fragment and to that add 'Catalog-picker' module. Here you can define 'Heading' and 'Text' to showcase on the loading of this page. Upon completing your edits, make sure to 'Publish' your changes for 'Catalog-picker' page. 
1. Now, we will hook the entry to this page from My accounts page 
1. Locate your 'My accounts' page and add a link to this 'Catalog-picker' page as shown below
1. Also, from the header fragment, add a link to 'My catalogs' and associate the 'view page' to 'catalog-picker' page. 

# Additional resources 

[Create Commerce catalogs for B2B sites](catalogs-b2b-sites.md)

[Extensibility impact of Commerce catalogs for B2B customizations](catalogs-b2b-sites-dev.md)

[Commerce catalogs for B2B FAQ](catalogs-b2b-sites-FAQ.md)
