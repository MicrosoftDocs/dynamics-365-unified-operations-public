---
# required metadata

title: Upload a robots.txt file
description: This topic describes how to upload a robots.txt file for your site
author: BrianShook
manager: Brendan Sullivan
ms.date: 12/2/2019
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
ms.search.validFrom: 
ms.dyn365.ops.version: 


---

# Upload a robots.txt file

This topic covers how to upload your robots.txt file for your site in Dynamics 365 Commerce.



## Overview

Dynamics 365 Commerce supports users uploading their robots.txt file for their domain. The robots.txt file assists search engines in the indexing of the content on your site. For more information on the robots.txt file, visit https://www.robotstxt.org/. One robots.txt file can be uploaded and associated to each domain in your Commerce environment. The following will instruct on how to upload the robots.txt file via the Commerce Site Builder tool.

## How to upload your robots.txt file

Once you have created and edited your robots.txt file per the robots exclusion standard (see www.robotstxt.org), have the file accessible on the machine you will be using the Dynamics 365 Commerce Site Builder tool. The file must be named 'robots.txt' and meet the format as noted in the standards for best results.

In a web browser, access the Homepage of your Commerce Site Builder instance. A System Admin must be logged in to perform the robots.txt upload. Once logged in, perform the following:

- From home, select the **Tenant Settings** menu item (the left side menu gear icon).
- Select **Robots.txt** from the sub-menu. A list of all the domains for the environment should in the page.
- Click the **Manage** button to upload a robots.txt file for a domain on your environment.
- A right-side menu will open with options to 'delete' (garbage can icon) , 'download' (down-facing arrow icon), or 'upload' (up-facing arrow icon)a robots.txt file per domain.
- Select the specific icons to the right of the listed domain you would like to operate against:
  - **Upload**- use this option to upload or overwrite an existing robots.txt file
    - A file picker dialog will appear- choose the correct 'robots.txt' file on your drive for the given domain. The tooling will do a basic check that the file is a text file (note: it will <u>not</u> validate the contents of the txt file).
    - A status alert should show the upload was successful
  - **Download** - use this option to download the current robots.txt file previously uploaded to the domain via the step above (only robots.txt files uploaded previously through the Commerce Site Builder tool will be downloadable through this option).
    - A Save File dialog will appear
    - Choose the location on your drive and name the file to complete the download
  - **Delete** - use this option to delete a previously uploaded robots.txt file (only robots.txt files uploaded previously through the Commerce Site Builder tool will be available to delete through this option).


The contents of the robots.txt file must be validated and maintained by each Commerce customer. The above methods can be used to manage updates to the robots.txt file content. 

