---
title: Client internet connectivity
description: This article covers what will happen if a client machine cannot access the internet in on-premises deployments.
author: jasongre
ms.date: 05/05/2020
ms.topic: article
ms.prod: dynamics-365
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Platform Update 8
ms.assetid: 
ms.service: 
search.app:
  - financeandoperationsonprem-docs
---

# Client internet connectivity

[!include [banner](../includes/banner.md)]


The configuration of the local network for a deployment of Dynamics 365 Finance + Operations (on-premises) can affect the features that are available in the web client. In particular, if the network configuration does not allow a client machine to access the internet, several degradations in the web client will occur. These include:    

+ The Office app launcher and Dynamics 365 areas in the navigation bar will no longer be clickable.
+ The Help pane will not be accessible.  
+ The Ideas portal will not be accessible from the web client. 
+ Users will see their initials instead of a user image. 
+ Skype integration will not be available.  
+ The favorite icon shown in the browser tab will be the browser's default favorite icon instead of the application icon. 
+ The Open in Excel options are hidden because the Excel Add-in will not run.

In addition to platform features that may not be accessible when the client can't access the internet, there may also be application features that rely on an internet connection that developers will need to hide or turn off. To facilitate this, developers can use the **clientHasRestrictedInternet()** method that has been added to the **Session** class. This method will return true if the client does not have access to the internet.

## Client internet connectivity options

Client internet connectivity options allow an administrator to manually turn off the external connections that the client makes even when internet connectivity is available. These can be used for troubleshooting issues or to see what the client will look like when internet connectivity is not available. These client internet connectivity options are available out-of-the-box starting in Platform update 16 but are also available in Platform update 15 (via [KB 4091764](https://fix.lcs.dynamics.com/Issue/Details?kb=4091764&bugId=3934774&qc=245bb2cc9839fa2a2ecf6bfffc48c3dec102a3c1047e5e755387d00148db18cb)) and Platform update 12 (via [KB 4091763](https://fix.lcs.dynamics.com/Issue/Details?kb=4091763&bugId=3934773&qc=19e9634da3297903a2ac51cf291a4770fd4532c9767ca7b5cefbe1bccb5d4d9f)). 


The client internet connectivity options can be found on the **System administration** > **Setup** > **Client performance options** page. 

- **Internet connectivity enabled** - Allows an administrator to turn off all external connections that the web client would otherwise make.
- **Skype presence enabled** - Allows an administrator to turn off external connections to Skype that the web client would otherwise make.

## Why does the client connect to the Skype for Business API when it first loads?

When the client loads, it performs a quick call (ping) to the Skype for Business API to check if an internet connection is available. If it isn’t available then the client functions in a disconnected fashion. An environment doesn’t need to have Skype for Business visible/enabled for this check to be made.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
