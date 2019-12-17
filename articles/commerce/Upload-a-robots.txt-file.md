---
# required metadata

title: Manage robots.txt files
description: This topic describes how to manage robots.txt files in Microsoft Dynamics 365 Commerce.
author: BrianShook
manager: Brendan Sullivan
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
- In the menu on the right, select the upload icon (upward-facing arrow) next to the domain associated with the robots.txt file. A File Explorer window appears.
- In File Explorer, browse to and select the the robots.txt file you want to upload for the given domain, and then select **Open**. A status alert will show if the upload was successful.

>[!NOTE] 
>When uploading the file, Commerce will do a basic check that it is a text file, but will not validate the contents of the file.

## Download a robots.txt file

To download a robots.txt file in Commerce, follow these steps.

- Sign in to Commerce as a system administrator.
- In the left navigation pane, select **Tenant Settings** (next to the gear icon) to expand it.
- Below **Tenant Settings**, select **Robots.txt**. A list of all the domains associated with the environment will appear in the main window.
- Click **Manage** to download a robots.txt file for a domain on your environment.
- In the menu on the right, select the download icon (downward-facing arrow) next to the domain associated with the robots.txt file. A **Save File** dialog box appears. 
- In the **Save File** dialog box, navigate to the desired location on your local drive, confirm or enter a file name, and then click **Save** to complete the download. 

>[!NOTE] 
>Only robots.txt files uploaded previously with Commerce authoring tools will be downloadable using this method.


## Delete a robots.txt file

To delete a robots.txt file in Commerce, follow these steps.

- Sign in to Commerce as a system administrator.
- In the left navigation pane, select **Tenant Settings** (next to the gear icon) to expand it.
- Below **Tenant Settings**, select **Robots.txt**. A list of all the domains associated with the environment will appear in the main window.
- Click **Manage** to delete a robots.txt file for a domain on your environment.
- In the menu on the right, select the delete icon (trash can) next to the domain associated with the robots.txt file. A File Explorer window appears.
- In File Explorer, browse to and select the the robots.txt file you want to delete for the given domain, and then select **Open**. A status alert will show if the upload was successful.


>[!NOTE] 
>Only robots.txt files uploaded previously with Commerce authoring tools will be available to delete using this method.




%%%%%

In a web browser, access the Homepage of your Commerce Site Builder instance. A System Admin must be logged in to perform the robots.txt upload. Once logged in, perform the following:

 The above methods can be used to manage updates to the robots.txt file content. 
 
 - A right-side menu will open with options to 'delete' (garbage can icon) , 'download' (down-facing arrow icon), or 'upload' (up-facing arrow icon)a robots.txt file per domain.
- Select the specific icons to the right of the listed domain you would like to operate against:
  - **Upload**- use this option to upload or overwrite an existing robots.txt file
    - A file picker dialog will appear- choose the correct 'robots.txt' file on your drive for the given domain. The tooling will do a basic check that the file is a text file (note: it will <u>not</u> validate the contents of the txt file).
    - A status alert should show the upload was successful
    
    
- **Download** - use this option to download the current robots.txt file previously uploaded to the domain via the step above ().
    - A Save File dialog will appear
    - 
   - **Delete** - use this option to delete a previously uploaded robots.txt file (only robots.txt files uploaded previously through the Commerce Site Builder tool will be available to delete through this option).
