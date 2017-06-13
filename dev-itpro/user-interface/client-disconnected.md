---
# required metadata

title: No client Internet connection in on-premises deployments 
description: This topic covers what will happen if a client machine cannot access the Internet in on-premises deployments.
author: jasongre
manager: AnnBe
ms.date: 05/15/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 29151
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Platform Update 8

---

## No client Internet connection in on-premises deployments 

The configuration of the local network for an on-premises deployment of Dynamics 365 for Finance and Operations, Enterprise edition can affect the available features in the web client. In particular, if the network configuration does not allow a client machine to access the Internet, several degradations in the web client will occur. These include:    

+ The Office waffle and Dynamics 365 areas in the navigation bar will no longer be clickable.
+ The Help pane will not be accessible.  
+ The Ideas portal will not be accessible from the web client. 
+ Users will see their initials instead of a user image. 
+ Skype integration will not be available.  
+ The favorite icon shown in the browser tab will be the browser's default favorite icon instead of the Finance and Operations icon. 

In addition to platform features that may not be accessible when the client can't access the Internet, there may also be application features that rely on an Internet connection that developers will need to hide or switch off. To facilitate this, developers can use the **clientHasRestrictedInternet()** method that has been added to the **Session** class. This method will return true if the client does not have access to the Internet.
