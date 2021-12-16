---
# required metadata

title: Get started with the mobile platform
description: This topic describes how to develop on the mobile platform.
author: tonyafehr
ms.date: 07/01/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: tfehr
# ms.tgt_pltfrm: 
ms.custom: ["255544", "intro-internal"]
ms.assetid: f5aa0c60-25cc-4453-8df9-efab19b7e272
ms.search.region: Global
# ms.search.industry: 
ms.author: tfehr
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Platform update 9

---

# Get started with the mobile platform

[!include [banner](../../includes/banner.md)]

After you acquire a development environment, complete the following procedures to get started with development.

### Get the Fleet Management mobile forms

We have created new, purpose-built forms in the **Fleet Management** module. These forms are used specifically for the mobile app and aren't meant to be used through the web client.

1.  [Download the file that contains the Fleet Management project](https://github.com/Microsoft/Dynamics365-for-Operations-mobile-FleetManagementSamples) (.axpp file).
2.  Extract the contents of the zip file to a temporary location on the development computer.
3.  Import the project (.axpp) file by using Microsoft Visual Studio (click **Finance and Operations** &gt; **Import Project**).
4.  After you've imported the project file, build the project or module.

### Get the sample workspace

We provide a sample workspace for Reservation management. This workspace is based on the **Fleet Management** module.

1.  [Download the file that contains the sample workspace](https://github.com/Microsoft/Dynamics365-for-Operations-mobile-FleetManagementSamples) (.xml file).
2.  Sign in to your non-production client. (You must sign in as an administrator.)
3.  In the address bar, add **&mode=mobile** to the end of the URL, and then press Enter.
4.  In the client, go to **Settings** &gt; **Mobile app**. The mobile app designer will appear docked next to the client.
5.  Click the **Overflow** button (**…**), and then click **Import**.
6.  Click the **Browse** button that appears at the bottom of the page.
7.  In the file selection dialog box that appears, select one of the XML files that you previously extracted from the zip file.
8.  After the app has been loaded into the mobile app designer, click **Done** at the bottom of the page.
9.  Click **Publish workspace**.

### Get the mobile app

The mobile app is being made available for the most popular mobile operating systems. You must have a Dynamics 365 Unified Operations instance and valid user credentials in order to log in to the app.

-   Android (available now) - [Finance and Operations mobile app on the Google Play Store](https://play.google.com/store/apps/details?id=com.microsoft.dynamics365.operations.mobile)
-   iPhone (available now) - [Finance and Operations mobile app on the iTunes apps store](https://itunes.apple.com/us/app/dynamics-365-for-operations/id1180836730?mt=8)

You're done! Launch the app from your mobile device to see the sample workspace.

### Additional resources

[Architecture](mobile-platform-architecture.md) 

[Client APIs reference](client-apis/client-apis-reference.md)

[Server APIs reference](mobile-workspace-server-apis.md)


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]