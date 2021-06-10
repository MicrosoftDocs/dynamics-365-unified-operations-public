---
# required metadata

title: The planned production order must be scheduled before it can be firmed.
description: The planned production order must be scheduled before it can be firmed.
author: ankubik@microsoft.com
manager: tfehr
ms.date: 5/18/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ReqTransPo
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: ankubik@microsoft.com
ms.assetid: 
ms.search.region: Global
ms.author: ankubik@microsoft.com

---

# The planned production order must be scheduled before it can be firmed.

Error code: SYS309802

The system displays the followign error message:
	SYS309802



## Symptoms
During firming planned order the system shows the following error message: > The planned production order must be scheduled before it can be firmed.

## Cause
The start and end scheduled dates cannot be empty.

## Resolution
Go to planned order form and choose the planned order. In General tab you can see Scheduled section with Start and End date. To firm order the dates have to be set.



