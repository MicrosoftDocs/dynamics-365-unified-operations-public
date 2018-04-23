---
# required metadata

title: Client internet connection  
description: This topic covers what will happen if a client machine cannot access the internet in on-premises deployments.
author: jasongre
manager: AnnBe
ms.date: 03/08/2018
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
ms.custom: 29151
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Platform Update 8

---

# Client internet connection 

[!INCLUDE [banner](../includes/banner.md)]

The configuration of the local network for an on-premises deployment of Dynamics 365 for Finance and Operations can affect the available features in the web client. In particular, if the network configuration does not allow a client machine to access the internet, several degradations in the web client will occur. These include:    

+ The Office waffle and Dynamics 365 areas in the navigation bar will no longer be clickable.
+ The Help pane will not be accessible.  
+ The Ideas portal will not be accessible from the web client. 
+ Users will see their initials instead of a user image. 
+ Skype integration will not be available.  
+ The favorite icon shown in the browser tab will be the browser's default favorite icon instead of the Finance and Operations icon. 

In addition to platform features that may not be accessible when the client can't access the internet, there may also be application features that rely on an internet connection that developers will need to hide or switch off. To facilitate this, developers can use the **clientHasRestrictedInternet()** method that has been added to the **Session** class. This method will return true if the client does not have access to the internet.

## Client internet connectivity options

Client internet connectivity options (added by [KB 4091763](https://fix.lcs.dynamics.com/Issue/Details?kb=4091763&bugId=3934773&qc=19e9634da3297903a2ac51cf291a4770fd4532c9767ca7b5cefbe1bccb5d4d9f)) allow an administrator to manually switch off the external connections that the client makes even when internet connectivity is available. These can be used for troubleshooting issues or just to see what the client will look like when internet connectivity is not available.

These options can be found on the **System administration > Setup > Client performance options** page.

- **Internet connectivity enabled** - Allows an administrator to switch off all external connections that the web client would otherwise make.
- **Skype presence enabled** - Allows an administrator to switch off external connections to Skype that the web client would otherwise make.
