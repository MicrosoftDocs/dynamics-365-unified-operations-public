---
# required metadata

title: Creaet dynamc pages with URL parameters
description: This topic explains how to set up a Dynamics 365 Commerce e-commerce  page that can serve dynamic content based on a segment in the URL path. 
author: StuHarg
manager: AnnBe
ms.date: 01/08/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: josaw
#ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
# ms.search.industry: Retail
ms.author: stuharg
ms.search.validFrom: 2019-09-30
ms.dyn365.ops.version: 10.0.17

---
# Create dynamic pages with URL parameters

 

## Overview

An e-commerce page can be configured to serve dynamic content based on a segment in the URL path. For example, a page named blog_viewer can be created and associated with a URL such as https://fabrikam.com/blog. This page can then be used to display content based on the last segment in the path (e.g. https://fabrikam.com/blog/episode-1, https://fabrikam.com/blog/article-2, etc…) 

Separate pages can also be associated with URLs under the https://fabrikam.com/blog path that override the dynamic page to enable customization. Building on the example above, a page named blog_summary can be created and associated with the URL https://fabrikam.com/blog/about-this-blog. When that URL is requested, the blog_summary page is returned rather than the blog_viewer page with /about-this-blog as a parameter.

NOTE: The functionality for hosting, retrieving and displaying dynamic content in a page is implemented by customers through a custom module. Learn more about module development at ______. 



## Setting up a dynamic page

***Step 1: Create the page that will serve dynamic content***

Follow the steps outlined in Add a new Site page (https://docs.microsoft.com/en-us/dynamics365/commerce/add-new-page) to create a new page. This page will require the implementation of a module that uses the last segment on the URL path to retrieve the content from an external data source. Learn more about custom module development at _______. 

***Step 2: Create the base URL for the dynamic page***
1. Go to the URLs section in site builder and create a new URL.
2. In the Create new URL dialog, select **Internal page**, and enter the path that will serve as the root for  your dynamic page. In the example above, the URL path would be /blog.
3. Click **Next.**
4. Select the page you created  to serve as the dynamic page.
5. Click **Save**.

***Step 3: Configure the route to the dynamic page***

1. Go to **Extensions** under **site  settings**  in site builder. 
2. Scroll down to **Parameterized URL paths**.
3. Click **+Add**, and enter the URL path as  you entered it when you created the URL. In the example above, the  parameterized URL path would be /blog. 
4. Click **Save and  publish**. 

Once configured, all requests to parameterized URL path will return the page associated with that URL, and requests that contain an additional segment will return the page with any content that is retrieved using that segment as a parameter. In the example above,  https://fabrikam.com/blog/article-1 will return the blog_summary page with the content retrieved with the article-1 parameter. 


## Overriding a parameterized URL with a custom page
To override what is returned by a parameterized URL:
1. Create a URL of type Internal page and a URL path that includes the segment to be overridden. In the example above, specify the URL path /blog/about-this-blog
2. Associate that URL to the customized page.
3. Publish the URL and page.

Once published, the customized page will be served rather than the dynamic page with parameterized content. 

 
