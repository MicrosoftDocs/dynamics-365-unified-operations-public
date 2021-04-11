---
# required metadata

title: System administrators cannot clear order holds because they are not authorized
description: System administrators cannot clear order holds because they are not authorized
author: SmithaNataraj
manager: tfehr
ms.date: 4/11/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: SalesTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
submittedBy: henrikan@microsoft.com

---

# System administrators cannot clear order holds because they are not authorized

KB Number: 4614642

System administrators cannot clear sales order holds (because they are not authorized), unless they also have the specific role assigned in the order hold code.


## Resolution
Microsoft has investigated the reported issue and concluded that the behavior is as intended. The system administrator cannot do everything when access is driven from a business policy setup, such as in this case. 

There are more cases where access to perform a specific task is governed by business policies, where only specific persons within an organization are approved to perform the task. Consider approvals resulting from workflow approvals, or specific tasks resulting from a workflow configuration as an example. The same comes into play for order holds. There is no workflow associated, however the rational is similar. The role designates a select group of people who within an organization have the agility to clear an order hold. Allowing this access also to users only with system administrators rights as default, would violate the business policy defined. As such this is not a bug, but behaves as intended. 


