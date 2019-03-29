---
# required metadata

title: Feature callouts
description: Actions are an essential component of any enterprise resource planning (ERP) system, and are triggered by mouse click, keyboard, or touch.
author: jasongre
manager: AnnBe
ms.date: 03/28/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 55521
ms.assetid: 93b61e0c-b9bc-48fc-a9b7-874a8b0aeebd
ms.search.region: Global
# ms.search.industry: 
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Feature callouts

[!include [banner](../includes/banner.md)]

## Introduction
New features are regularly being developed for Finance and Operations. While documentation is helpful for explaining new features, raising awareness of these new capabilities to users directly in the product when they are encountered is powerful. To this end, two new APIs have been added that allows a developer to trigger a feature callout to point out a new capability to the user and optionally provide a hyperlink for the user to learn more about the feature.   

## SystemNotificationWhatsNewManager::AddWhatsNew() 
Add a feature callout to a control without a "Learn more" link. 

### Parameters

| Parameter     | Description                                                               |
|---------------|---------------------------------------------------------------------------|
| ruleID        | Generate a unique GUID                                                    | 
| title         | Provide a (localized) title                                               | 
| bodyText      | Provide a (localized) description                                         | 
| targetControl | Provide the name of the control you want to attach the feature callout to | 


## SystemNotificationWhatsNewManager::AddWhatsNewWithActionLink() 

### Parameters

| Parameter     | Description                                                               |
|---------------|---------------------------------------------------------------------------|
| ruleID        | Generate a unique GUID                                                    | 
| title         | Provide a (localized) title                                               | 
| bodyText      | Provide a (localized) description                                         | 
| targetControl | Provide the name of the control you want to attach the feature callout to | 
| urlLink       | Provide the URL to open in a new tab when the "Learn more" link is clicked. If a URL is not specified, then no "Learn more" link will be displayed. |



Notes
•	Multiple feature callouts can be shown on a page at one time
•	Only one feature callout is allowed per control. If multiple exist, the last one wins
•	When a user dismisses a feature callout by clicking the “Got it” button, that state is remembered as a personalization. Before Platform update 26, deleting a user’s personalization reset all feature callouts, meaning they will be displayed when the user next encounters those features. Starting in Platform update 26, deleting personalizations and resetting feature callouts are two separate actions for users.  

Roadmap
•	Learn more link in the bottom right hand corner of the feature callout that serves as a link to documentation that would be visible if the developer specified a URL 
•	Create a switch (separate from deleting personalization) to reset feature callouts for a user. 

