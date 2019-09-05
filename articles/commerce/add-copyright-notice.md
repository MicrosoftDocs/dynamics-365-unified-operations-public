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

## Add the copyright notice

To add a copyright notice to the end of each page using the template, do the following.

1. Go to **Fragments**, then click **New Page Fragment**.
1. In the dialog box, select **Footer** module and name the fragment (for example, "Footer-Copyright").
1. Click **OK**.
1. In the navigation pane, click the ellipsis button next to **Footer**, and then click **Add Module**.
1. In the dialog box, select **Footer category**, then click **OK**.
1. In the navigation pane, click the ellipsis button next to **Footer category** and select **Add Module**.
1. In the dialog box, select **Content rich block item**, click **OK**,and then select the **Content rich block item** in the navigation pane.
1. Under **Paragraph** in the right-side properties pane, add your copyright message (for example, **(C) Fabrikam 2019**).
1. Click **Save**, click **Check In**, and then click **Publish**.
1. Go to **Templates**, select your template, and click **Check Out**.
1. Under **Page Outline**, expand **Body**, and then expand **Default Page**.
1. Click the ellipsis button next to **Footer Slot** and select **Add Fragment**.
1. Select the fragment you created with the copyright text and click **Select**.
1. Check in and publish the template.

After following these steps, the copyright footer will automatically be visible an the bottom of all pages that use the template.
