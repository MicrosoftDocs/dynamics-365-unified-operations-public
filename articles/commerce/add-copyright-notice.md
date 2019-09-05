---
# required metadata

title: Add a copyright notice
description:  This article explains the steps required to add a copyright notice to your e-Commerce website.
author: psimolin
manager: AnnBe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope:  Operations, Retail, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: psimolin
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# Add a copyright notice

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This article explains the steps required to add a copyright notice to your e-Commerce website.

## Prerequisites
Before you can add a copyright notice on your site, you must have the following:

- A template that includes a shared footer fragment
- A page that uses that template

To add a copyright notice to the end of each page using the template, do the following.

1. Go to **Fragments**, then click **New Page Fragment**
1. Choose **Footer** module and name the fragment e.g. "Footer-Copyright"
1. Click **OK**
1. From the page outline choose **Footer**
1. Open ellipsis menu and select **Add Module**, pick **Footer category**, Click **OK**
1. From **Footer category** in the page outline, open ellipsis menu and click **Add Module**, pick **Content rich block item** and click **OK**
1. Make sure that **Content rich block item** is selected from the page outline and its properties shown on the right pane
1. Edit the content of the **Paragraph**-property. Add your copyright message, e.g. **(C) Fabrikam 2019**
1. Check In
1. Publish
1. Go to **Templates**, open your template, Check Out the template
1. Expand **Body**
1. Expand **Default Page**
1. Open ellipsis menu on **Footer Slot** and select **Add Fragment**
1. Select the Fragment with the copyright text you just created and Click **Select**
1. Check In
1. Publish

After these steps, the copyright footer will automatically be visible an the bottom of all pages that use this template


