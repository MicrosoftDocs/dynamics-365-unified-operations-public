---
title: Get started with the mobile platform
description: Learn about how to develop on the mobile platform, including overviews on getting Fleet Management mobile forms and getting sample workspaces.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 12/31/2024
ms.reviewer: johnmichalak
ms.collection: get-started
ms.search.region: Global
ms.search.validFrom: 2016-11-30
ms.assetid: f5aa0c60-25cc-4453-8df9-efab19b7e272
ms.custom: 
  - bap-template
---

# Get started with the mobile platform

[!include [banner](../../includes/banner.md)]
[!include [mobile app deprecated](../../includes/mobile-app-deprecation-banner.md)]

After you acquire a development environment, complete the following procedures to get started with development.

### Get the Fleet Management mobile forms

There are purpose-built forms in the **Fleet Management** module. These forms are used specifically for the mobile app and aren't meant to be used through the web client.

1.  [Download the file that contains the Fleet Management project](https://github.com/Microsoft/Dynamics365-for-Operations-mobile-FleetManagementSamples) (.axpp file).
2.  Extract the contents of the zip file to a temporary location on the development computer.
3.  Import the project (.axpp) file by using Microsoft Visual Studio (click **Finance and operations** > **Import Project**).
4.  After you import the project file, build the project or module.

### Get the sample workspace

We provide a sample workspace for Reservation management. This workspace is based on the **Fleet Management** module.

1.  [Download the file that contains the sample workspace](https://github.com/Microsoft/Dynamics365-for-Operations-mobile-FleetManagementSamples) (.xml file).
2.  Sign in to your nonproduction client. (You must sign in as an administrator.)
3.  In the address bar, add **&mode=mobile** to the end of the URL, and then press Enter.
4.  In the client, go to **Settings** &gt; **Mobile app**. The mobile app designer appears docked next to the client.
5.  Click the **Overflow** button (**…**), and then click **Import**.
6.  Click the **Browse** button that appears at the bottom of the page.
7.  In the file selection dialog box that appears, select one of the XML files that you previously extracted from the zip file.
8.  After the app is loaded into the mobile app designer, click **Done** at the bottom of the page.
9.  Click **Publish workspace**.



### Related information

[Architecture](mobile-platform-architecture.md) 

[Client APIs reference](client-apis/client-apis-reference.md)

[Server APIs reference](mobile-workspace-server-apis.md)


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]

