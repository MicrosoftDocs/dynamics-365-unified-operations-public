---
# required metadata

title: Add or update a robots.txt file
description: This article describes how to create, edit, upload, and validate the robots.txt file for each domain hosted in Microsoft Dynamics 365 Commerce.
author: mssle
ms.date: 07/07/2022
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: sheaton
ms.search.validFrom: 2021-09-20
---

# Add or update a robots.txt file

[!include[banner](../includes/banner.md)]

This article describes how to create, edit, upload, and validate the robots.txt file for each domain hosted in Microsoft Dynamics 365 Commerce. 

Unexpected or undirected crawling of your site by search engines can result in a high volume of "404 Page Not Found" errors. These errors can lead to performance issues as the site responds to the many requests for pages that don't exist. To help fix this problem, your domain should always have an up-to-date and valid robots.txt file to instruct web crawlers to only look for relevant pages on your site. 

## Applies to

This article applies to the following configurations:

- **Version:** Commerce 10.0.16 or later
- **Component:** Business-to-consumer (B2C) or business-to-business (B2B)
- **Feature area:** Commerce website performance

## Prerequisites

-You're a [System Administrator](../manage-ecommerce-users-roles.md#system-administrator-role) in your Commerce instance.
-You've either created or downloaded a copy of robots.txt to your computer depending on your situation: 
- If you don't have a robots.txt file uploaded for your domain, create a new robots.txt file on your computer following the [robots exclusion standard](https://www.robotstxt.org/orig.html). Use the [robots.txt sample](#sample-robotstxt-file-contents) provided below as a starting point. 
- If you've previously uploaded a robots.txt file for your domain, [download](../manage-robots-txt-files.md#download-a-robotstxt-file) your existing file. 

## Steps to complete

To edit and upload a robots.txt file, follow these steps.

1. Open your local copy of robots.txt. 
1. Edit the file to ensure that it includes the **Disallow** entries shown in the [robots.txt sample](#sample-robotstxt-file-contents) provided below. 
1. Confirm the file is correctly formatted according to the [robots exclusion standard](https://www.robotstxt.org/orig.html).
1. Upload the file to your site by following the instructions in [Upload a robots.txt file](../manage-robots-txt-files.md#upload-a-robotstxt-file).

### Sample robots.txt file contents 

```Plaintext
User-agent: *
Disallow: /signin
Disallow: /cart
Disallow: /*refiners=
Disallow: /*sorting=
Disallow: /*search?
Disallow: /*search=
Disallow: /*.woff
Disallow: /*.woff2
Disallow: /*skip=
```

## Validate

Use the following methods to validate the file has been added.

- **Description or purpose:** Validate that your robots.txt file is available for your domain.
- **Steps to run:** Using a web browser, open the page at **\<your_domain\>/robots.txt**.
- **Passing result:** Your robots.txt file can be viewed successfully.

## Additional resources

[Manage robots.txt files](../manage-robots-txt-files.md)

[System Administrator role](../manage-ecommerce-users-roles.md#system-administrator-role)

