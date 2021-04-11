---
# required metadata

title: Trying to to create contact for customer type account, while Dual Write is active, results in error.
description: Trying to to create contact for customer type account, while Dual Write is active, results in error.
author: SmithaNataraj
manager: tfehr
ms.date: 4/11/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: CustTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
submittedBy: smnatara@microsoft.com

---

# Trying to to create contact for customer type account, while Dual Write is active, results in error.

KB Number: 4611508

Trying to to create contact for customer type account, while Dual Write is active, results in error:
Write failed for entity CDS Contacts V2 with unknown exception - Field 'Associated party number' must be filled in.\nField 'Associated party number' must be filled in.validateWrite failed on data source 'smmContactPersonV2Entity (smmContactPersonV2Entity)

It was found that a piece of code in class DualWriteSyncInbound is making Associated party null while ConvertStringValueToTargetType


## Resolution
The customer and contact entities reference each other. For the initial sync, first sync the customer entity. Then sync the contact entity. And again resync the customer entity for syncing the contact references.


