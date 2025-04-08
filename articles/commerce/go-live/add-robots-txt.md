---
title: Add or update a robots.txt file
description: This article describes how to create, edit, upload, and validate the robots.txt file for each domain that is hosted in Microsoft Dynamics 365 Commerce.
author: mssle
ms.date: 07/30/2024
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2021-09-20
ms.custom: 
  - bap-template
---

# Add or update a robots.txt file

[!include[banner](../includes/banner.md)]

This article describes how to create, edit, upload, and validate the robots.txt file for each domain that is hosted in Microsoft Dynamics 365 Commerce.

Unexpected or undirected crawling of your site by search engines can cause a high volume of "404 Page Not Found" errors. These errors can affect performance as the site responds to all the requests for pages that don't exist. To help fix this issue, you should ensure that your domain always has an up-to-date and valid robots.txt file to instruct web crawlers to look for only relevant pages on your site.

## Applies to

This article applies to the following configurations:

- **Version:** Commerce 10.0.16 or later
- **Component:** Business-to-consumer (B2C) or business-to-business (B2B)
- **Feature area:** Commerce website performance

## Prerequisites

- You're a [system administrator](../manage-ecommerce-users-roles.md#system-administrator-role) in your Commerce instance.
- You've either created a robots.txt file on your computer or downloaded a copy, depending on your situation:

    - If you haven't previously uploaded a robots.txt file for your domain, create a new file on your computer by following the [robots exclusion standard](https://www.robotstxt.org/orig.html). Use the [sample robots.txt file](#sample-robotstxt-file-contents) later in this article as a starting point.
    - If you've previously uploaded a robots.txt file for your domain, [download](../manage-robots-txt-files.md#download-a-robotstxt-file) the existing file.

## Steps to complete

To edit and upload a robots.txt file, follow these steps.

1. Open your local copy of the robots.txt file.
1. Edit the file so that it includes all the **Disallow** entries in the [sample robots.txt file](#sample-robotstxt-file-contents) that follows.
1. Confirm that the file is correctly formatted according to the [robots exclusion standard](https://www.robotstxt.org/orig.html).
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

Use the following method to validate that the file has been added:

- **Description or purpose:** Validate that your robots.txt file is available for your domain.
- **Steps to run:** In a web browser, open the page at **\<your\_domain\>/robots.txt**.
- **Passing result:** You can successfully view your robots.txt file.

## Additional resources

[Manage robots.txt files](../manage-robots-txt-files.md)

[System Administrator role](../manage-ecommerce-users-roles.md#system-administrator-role)
