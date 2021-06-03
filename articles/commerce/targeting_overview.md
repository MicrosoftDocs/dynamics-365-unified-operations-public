---
# required metadata

title: E-commerce Segmentation and Targeting
description: This topic describes how to create, edit and manage audiences and target variations in site builder. Basic segmentation and targeting based on information available in the user's browser such as device type or location is enabled for e-commerce modules and fragments within a page.
author:  sushma-rao 
ms.date: 7/31/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: sushmar
ms.search.validFrom: 2021-07-31
ms.dyn365.ops.version: AX 10.0.21
---

# Customer segmentation and targeting in Dynamics 365 Commerce
Dynamics 365 Commerce enables you to target specific groups of customer with different page content based on their device information, geolocation, and other dynamically derived attributes from their browser request. This will help personalize content in near real-time for these target groups known as **audiences** and drive increased user engagement and satisfaction.

## Audiences
Audience – group of users whose membership is determined by a set of dynamic rules


## Targets
Target – the user experience that will be shown to members of the chosen audience


Audience creation and management
Rules can be created based on:
Geolocation - country, state, city, zip code
Customer email address
Customer name
Signed-in or not
Device info – desktop/mobile/tablet, OS, browser
Source – referrer, previous page
Query string parameters

Target creation and management
Including and excluding audiences
Creating targeted content

Target prioritization / ranking

Target scheduling

•	Targeted modules can’t be shared as fragments
o	Parent level won’t work
o	Module with child targets can be shred
•	Targets carried forward with publish groups
•	Experiments and targets can’t co-exist; experiments will trump
•	During localization, all activities + any scheduling automatically go with locale variants, whether users want it or not. 
o	If they don’t want it, they will have to manually delete it.
o	If they need different schedules per locale, they need to create different activities per locale.
•	How/when to create everyone/no one audiences
•	Since segment values will be stored in a cookie, we need to limit the size of the value for 3rd-parties. What is the limit?
50 chars for values. Provider id maximum size: 20, Segment id maximum size: 20 and only allow letters, number and “-“ in provider and segment id.
•	Basic vs advanced preview
•	C1 needs explicit cookie consent from C2 – need to include info on that module


[!INCLUDE[footer-include](../includes/footer-banner.md)]
