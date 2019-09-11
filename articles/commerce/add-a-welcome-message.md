---
# required metadata

title: Add a welcome message
description: 
author: psimolin
manager: brendans
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Add a welcome message
This article explains how to add a welcome message to your e-Commerce website.

A welcome message can be used to inform visitors of your site about ongoing sale, updated site or seasonal collection availability.  You can set a message using the "Alert" module.

Alert module is best to be placed in the "Error/Information messages" slot of "Header" module. It allows you to specify the text to be shown as well as color, text alignment and whether the message can be dismissed.

When you set the message in your shared header fragment, the message will be shown on each page that is using the template where that shared fragment is used.

Steps required to add a welcome message to the header fragment
1. Navigate to your site
1. Click **Fragments**
1. Click the header fragment you want to add the message to
1. Expand **Error/Information messages** from the page outline
1. Locate **Alert** module. If it does not exist, click on the ellipsis menu next to **Error/Information messages**, then **Add module** and add alert-module to the slot
1. Select **Alert** module
1. From the property inspector on the right side of the screen, select **Data** tab
1. Click **Add Data Source**, choose **Content**
1. In the field **Input Text**, input your message
1. Save
1. Check In
1. Publish
1. All the pages on your site that are using the header fragment now show your message on the top of the page
