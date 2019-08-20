---
# required metadata

title: Build custom response pages for 400/500 status code errors
description: This topic describes how to build custom response pages for 400 and 500 status code errors using the authoring tools in Dynamics 365 Retail.
author: brshoo
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
ms.reviewer: josaw
ms.search.scope: Operations, Retail, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: brshoo
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# Build custom response pages for 400/500 status code errors 

This topic describes how to build custom response pages for 400 and 500 status code errors using the authoring tools in Dynamics 365 Retail.

## Overview

A server will issue HTTP response status code errors when a client request is not successful. All 4xx categorical status codes are client error responses, and all 5xx categorical status codes are server error responses. In Dynamics 365 Retail, application users can build custom response pages to display to end users in the event of 4xx or 5xx status code error responses.

## Build a status code error response page
To begin building a status code error response page, do the following.

1. Log in to the Microsoft Dynamics 365 Retail Authoring Tools in your preferred browser. 
1. Select the site for which you will be building the 4xx/5xx status code error response page. 

#### Build the master template

To build the master template, do the following.

1. Select the **Master Template** section and create a new master template.
1. Name the master template.
1. Build the template according to how you want the error page to be structured.
1. Check in the master template.
1. Publish the master template.

##### Build the Error Page

  *  Navigate back to the Site Menu and select the **Pages** section.
  *  Click the **New Page** button and provide a Page Name for your error page. 
  * **<u>Do not</u>** fill in the **URL** field at this time. 

  **Note:** You may choose to use the same general error page, or create separate error pages per 4xx and 5xx errors.

- Build out the page in the Authoring Tool as you want presented to end users.

- Once completed, be sure to Check In and Publish your error page.

##### Set the Page for Error Redirection

- Navigate back to the Site Menu and go to the **URLs** section.
- Go to **New > New Alias** and Select the new error page just created
- For the **Alias**, enter "<u>default-4xx</u>" or "<u>default-5xx</u>" depending on which page you are setting up, 4xx or 5xx respectively.
- Select "OK" to commit the linking.
- **Note:** If using a single page instance for both error categories, repeat the process and link a new alias to the same page.

Your error pages are now ready for this Site.

