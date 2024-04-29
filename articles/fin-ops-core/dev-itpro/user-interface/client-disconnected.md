---
title: Client internet connectivity
description: Learn about client internet connectivity, including an overview of degredations of lack of internet access and client internet connectivity options.
author: jasongre
ms.author: jasongre
ms.topic: article
ms.date: 01/10/2024
ms.reviewer: twheeloc
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Platform Update 8
search.app:
  - financeandoperationsonprem-docs
---

# Client internet connectivity

[!include [banner](../includes/banner.md)]


The configuration of the local network for a deployment of Dynamics 365 Finance + Operations (on-premises) can affect the features that are available in the web client. If the network configuration doesn't allow a client machine to access the internet, the following degradations in the web client occur:    

+ The Office app launcher and Dynamics 365 in the navigation bar isn't clickable.
+ The Help pane isn't accessible.  
+ The Ideas portal isn't accessible from the web client. 
+ Users see their initials instead of a user image. 
+ The favorite icon shown in the browser tab is the browser's default favorite icon instead of the application icon. 
+ The Open in Excel options are hidden because the Excel Add-in won't run.

There also maybe application features that rely on an internet connection that developers need to hide or turn-off. Developers can use the **clientHasRestrictedInternet()** method that's added to the **Session** class. This method returns true if the client doesn't have access to the internet.

## Client internet connectivity options

Client internet connectivity options allow administrators to manually turn-off the external connections that the client makes even when internet connectivity is available. This can be used for troubleshooting issues or to see what the client looks like when internet connectivity isn't available. 

The client internet connectivity options can be found on the **System administration** > **Setup** > **Client performance options**  page.

-  **Internet connectivity enabled** - Allows an administrator to turn off external connections that the web client would make.
-  **(Obsolete) Skype presence enabled** - Allows an administrator to turn off external connections to Skype that the web client would make.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
