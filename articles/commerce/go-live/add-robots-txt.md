---
# required metadata

title: Add or update a robots.txt file
description: This topic describes how to create, edit, upload, and validate the robots.txt file for each domain hosted in Microsoft Dynamics 365 Commerce.
author: mssle
ms.date: 06/16/2022
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: sheaton
ms.search.validFrom: 2021-09-20
---

# Add or update a robots.txt file

[!include[banner](../includes/banner.md)]

This topic describes how to create (or edit), upload, and validate the robots.txt file for each domain hosted in Microsoft Dynamics 365 Commerce. 

Unexpected or undirected crawling of your site by search engines can result in a high volume of page not found errors, leading to performance issues as the site responds to the many requests for pages that do not exist. To help alleviate this problem, you should always upload a valid robots.txt file to guide conforming crawlers to crawl only relevant pages on your site. 

## Applies to

This topic applies to the following configurations:

- **Version:** Commerce 10.0.16 or later
- **Component:** Business to consumer (B2C) or business to business (B2B)
- **Feature area:** Commerce website performance

## Prerequisites

You are a [System Administrator](../manage-ecommerce-users-roles.md#system-administrator-role) in your Commerce instance.

You have either created or downloaded a copy of robots.txt to your computer depending on your situation: 
- If you do not have a robots.txt file uploaded for your domain, create a new robots.txt file on your computer according to the [robots exclusion standard](https://www.robotstxt.org/orig.html) by using the [provided sample](#sample-robotstxt-file-contents). 
- If you have previously uploaded a robots.txt file for your domain, [download](../manage-robots-txt-files.md#download-a-robotstxt-file) your existing robots.txt file. 

## Steps to complete

1. Open the local copy of robots.txt. 
1. Edit the file to ensure it includes the disallow entries shown in the [provided sample](#sample-robotstxt-file-contents). 
1. Confirm the file is correctly formatted according to the [robots exclusion standard](https://www.robotstxt.org/orig.html).
1. Upload the file to your site using these [upload instructions](../manage-robots-txt-files.md#upload-a-robotstxt-file).

### Sample robots.txt file contents 
```Plaintext
User-agent: *
Disallow: /signin
Disallow: /cart
Disallow: /*?refiners=
Disallow: /*?sorting=
Disallow: /*?search=
```

## Validate

Use the following method to validate the file has been added.

- **Description or purpose:** Validate your robots.txt file is available for your domain.
- **Steps to run:** Using a web browser, open the page at *&lt;domain&gt;*/robots.txt.
- **Passing result:** Your robots.txt file can be viewed successfully.

## Additional resources

[Manage robots.txt files](../manage-robots-txt-files.md)

[System Administrator role](../manage-ecommerce-users-roles.md#system-administrator-role)

