---
# required metadata

title: On-premises web client with no external internet connection
description: 
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
ms.dyn365.ops.version: AX 7.0.0

---

# On-premises web client with no external internet connection

The configuration of the local network for an on-premises deployment of Dynamics 365 for Finance and Operations can affect the available features in the web client. In particular, if the network configuration disallows a client machine from accessing the external internet, several degradations in the web client will occur, including:    

+ The Office waffle and Dynamics 365 areas in the navigation bar will be no longer clickable.
+ The Help pane will not be accessible.  
+ Users will not be able to access the Ideas portal from the web client. 
+ Users will see their initials instead of a user image. 
+ Skype integration will not be available.  
+ The favicon shown in the browser tab will be the browser's default favicon instead of the Finance and Operations icon. 

