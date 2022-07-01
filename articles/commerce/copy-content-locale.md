---
# required metadata

title: Copy content to another locale
description: This article describes how to copy existing content to another locale within a site in Microsoft Dynamics 365 Commerce site builder.
author: psimolin
ms.date: 07/01/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: tfehr
ms.search.validFrom: 2017-06-20
---

# Copy content to another locale

[!include[banner](../includes/banner.md)]

This article describes how to copy existing content to another locale within a site in Microsoft Dynamics 365 Commerce site builder.

Content created in the site builder always has a locale. Individual pages and assets can be copied to a different locale by switching the locale when editing the content item and creating a new variant of it.
In some cases it makes sense to duplicate all the content items in a certain locale to a new locale. For example, when you are launching entirely new locale on your storefront. If the new locale shares the base language with one of the existing locales (e.g. “en-us” and “en-au”) using that as the source locale reduces the effort required to localize the content in the new locale.
In this article we describe the steps how to add a new locale to existing channel and how to copy all the content items from existing locale to a new locale.

## Add a new locale

1.	Log in to the site builder
2.	Open the site you wish to operate within
3.	Expand “Site settings” and open the “Channels” view
4.	Click on the title of the channel you wish to add new locale to. Locale side pane will open.
5.	Click “+ Add a locale”
6.	Select “Locale to support” and confirm that “Domain” is correct
7.	Enter unique URL path to “Path” e.g. “en-us” or “english-us”
8.	Click OK
9.	Close the locale side pane
10.	Confirm that the new locale is listed next to the correct channel
11.	Click “Save and publish”

> [!NOTE]
> Before the new locale can be configured in the site builder, it must be added to the associated online store channel in Commerce headquarters.

## Copy all the content items to a new locale

1.	Log in to the site builder
2.	Open the site you wish to operate within
3.	Expand “Site settings” and open the “Channels” view
4.	Click “Create locale copy” from the command bar – locale copy side pane will open
5.	Ensure that the correct site has been selected in the “Select site”
6.	Select the source for the content from “Source channel”
7.	Select the same channel in the “Destination channel”
8.	Select the source locale in “Source locale” and the new locale in “Destination locale”
9.	Click “Copy locale”
10.	Notification toast will appear confirming that the locale copy has been started

> [!NOTE]
> You may also copy content between different channels.

## Monitor the status of the locale copy

1.	Log in to the site builder
2.	Open the site you wish to operate within
3.	Expand “Site settings” and open the “Channels” view
4.	Click “Jobs”
5.	From the list of jobs in the view, click the one you wish to monitor
6.	Details will appear on the right side of the view




