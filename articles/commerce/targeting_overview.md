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
Dynamics 365 Commerce enables you to target specific groups of customers with different page content based on their device information, geolocation, and other dynamically derived attributes from their browser request. This will help personalize content in near real-time for these target groups known as **audiences** and drive increased user engagement and satisfaction.

You can create and manage audiences in site builder based on customer data such as location, device information, sign-in status, referrer, or query string parameters, gathered from the customer's web request. These audiences can then be targeted with module or fragment variations also authored and managed in site builder.

## Audiences
Audience is a group of users whose membership is determined by a set of dynamic rules. These rules are simple AND or OR conditions against basic information or segments available in the customer's request. Commerce natively supports device info (desktop/mobile/tablet, OS, browser), sign-in status, referrer and query string parameters. Additionally, a geolocation connector allows Commerce to connect with third-party geolocation service providers to generate geolocation information for e-commerce site users. For more information on setting up a geolocation connector, see [GeoLookup connector](e-commerce-extensibility/connectors.md#geolookup-connector). You can also connect to third-party segmentation providers and surface those segments within site builder. <<For more information, go here>>

To create an audience in Commerce site builder, follow these steps.
1. Select **Audiences** in the left navigation pane, and then select **New**.
2. Give your audience a name and optionally add tags and a description. 
3. Click on **Create** and **Add new rule block** on the the following page.
4. Select a source, followed by the required segment and it's value(s). You can create rules with either AND conditions within a rule block or OR conditions between rule blocks. You can also move rule blocks up or down and delete both rules and rule blocks as needed.

> [!NOTE]
> You can have up to 100 values in a list with up to 50 characters in each item.

6. Once you are satisfied with your audience, select **Finish editing**. You can also select **Publish** if you want to make the audience available for use in a live target or publish it along with the target.

Audiences can be created, edited and deleted in the **Audiences** tab in the left navigation pane.
Suggestion - create everyone and no one to help with inclusions and exclusions.

## Targets
Target is the user experience that will be shown to members of the chosen audience. You can target modules in the **Pages** tab or fragments in the **Fragments** tab.

Target creation and management
Including and excluding audiences
Target prioritization / ranking - experiments will trump all
Target scheduling

* Targeted modules can’t be shared as fragments
** Parent level won’t work
** Module with child targets can be shred
* Targets carried forward with publish groups
* Experiments and targets can’t co-exist; experiments will trump
* During localization, all activities + any scheduling automatically go with locale variants, whether users want it or not. 
**	If they don’t want it, they will have to manually delete it.
**	If they need different schedules per locale, they need to create different activities per locale.
*	How/when to create everyone/no one audiences
*	Basic vs advanced preview
*	C1 needs explicit cookie consent from C2 – need to include info on that module
* Publish groups
* localization


[!INCLUDE[footer-include](../includes/footer-banner.md)]
