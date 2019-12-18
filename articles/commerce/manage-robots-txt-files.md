---
# required metadata

title: Manage robots.txt files
description: This topic describes how to manage robots.txt files in Microsoft Dynamics 365 Commerce.
author: BrianShook
manager: annbe
ms.date: 12/16/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: retail
ms.author: brishoo
ms.search.validFrom: 2019-12-16
ms.dyn365.ops.version: 

---

# Manage robots.txt files

[!include [banner](includes/preview-banner.md)]
[!include [banner](includes/banner.md)]

This topic describes how to manage robots.txt files in Microsoft Dynamics 365 Commerce.

## Overview

The robots exclusion standard, or robots.txt, is a standard used by websites to communicate with web robots. The standard specifies how to instruct web robots on which areas of a website should not be visited. Robots are often used by search engines to index websites.

The method used to exclude robots from a server is to create a file on the server which specifies an access policy for robots. This file must be accessible via HTTP on the local URL as "/robots.txt." The robots.txt file assists search engines in the indexing of the content on your site.

Dynamics 365 Commerce supports users uploading their robots.txt file for their domain. One robots.txt file can be uploaded and associated with each domain in your Commerce environment.

For more information on the robots.txt file, visit https://www.robotstxt.org/.

## Upload a robots.txt file

Once you have created and edited your robots.txt file per the [robots exclusion standard](https://www.robotstxt.org/orig.html), have the file accessible on the machine on which you will be using the Dynamics 365 Commerce authoring tools. The file must be named 'robots.txt' and meet the format as noted in the standards for best results. The contents of the robots.txt file must be validated and maintained by each Commerce customer. You must be logged into Commerce as a system administrator to upload the robots.txt file. 

To upload a robots.txt file in Commerce, follow these steps.

- Sign in to Commerce as a system administrator.
- In the left navigation pane, select **Tenant Settings** (next to the gear icon) to expand it.
- Below **Tenant Settings**, select **Robots.txt**. A list of all the domains associated with the environment will appear in the main window.
- Click **Manage** to upload a robots.txt file for a domain on your environment.
- In the menu on the right, select the upload icon (upward-facing arrow) next to the domain associated with the robots.txt file. An **Open** file browser window appears.
- In the **Open** file browser window, browse to and select the the robots.txt file you want to upload for the given domain, and then select **Open** to complete the upload. 

>[!NOTE] 
>When uploading the file, Commerce will do a basic check that it is a text file, but will not validate the contents of the file.

## Download a robots.txt file

To download a robots.txt file in Commerce, follow these steps.

- Sign in to Commerce as a system administrator.
- In the left navigation pane, select **Tenant Settings** (next to the gear icon) to expand it.
- Below **Tenant Settings**, select **Robots.txt**. A list of all the domains associated with the environment will appear in the main window.
- Click **Manage** to download a robots.txt file for a domain on your environment.
- In the menu on the right, select the download icon (downward-facing arrow) next to the domain associated with the robots.txt file. A **Save File** file browser window appears. 
- In the **Save File** file browser window, navigate to the desired location on your local drive, confirm or enter a file name, and then click **Save** to complete the download. 

>[!NOTE] 
>Only robots.txt files uploaded previously with Commerce authoring tools will be downloadable using this method.


## Delete a robots.txt file

To delete a robots.txt file in Commerce, follow these steps.

- Sign in to Commerce as a system administrator.
- In the left navigation pane, select **Tenant Settings** (next to the gear icon) to expand it.
- Below **Tenant Settings**, select **Robots.txt**. A list of all the domains associated with the environment will appear in the main window.
- Click **Manage** to delete a robots.txt file for a domain on your environment.
- In the menu on the right, select the delete icon (trash can) next to the domain associated with the robots.txt file. An **Open** file browser window appears.
- In the **Open** file browser window, browse to and select the the robots.txt file you want to delete for the given domain, and then select **Open**. A **Warning** dialog box appears.
- In the **Warning** dialog box, click **Delete** to confirm deletion of the robots.txt file.


>[!NOTE] 
>Only robots.txt files uploaded previously with Commerce authoring tools will be available to delete using this method.

