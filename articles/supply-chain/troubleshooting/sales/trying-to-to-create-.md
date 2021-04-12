---
title: Trying to to create contact for customer type account, while Dual Write is active, results in error.
description: Trying to to create contact for customer type account, while Dual Write is active, results in error.
author: SmithaNataraj
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: CustTable
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: smnatara
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Trying to to create contact for customer type account, while Dual Write is active, results in error.

KB Number: 4611508

Trying to to create contact for customer type account, while Dual Write is active, results in error:
Write failed for entity CDS Contacts V2 with unknown exception - Field 'Associated party number' must be filled in.\nField 'Associated party number' must be filled in.validateWrite failed on data source 'smmContactPersonV2Entity (smmContactPersonV2Entity)

It was found that a piece of code in class DualWriteSyncInbound is making Associated party null while ConvertStringValueToTargetType


## Resolution
The customer and contact entities reference each other. For the initial sync, first sync the customer entity. Then sync the contact entity. And again resync the customer entity for syncing the contact references.


