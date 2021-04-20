---
title: Can't create contacts for a customer account while dual-write is active
description: Can't create contacts for a customer account while dual-write is active.
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

# Can't create contacts for a customer account while dual-write is active

KB Number: 4611508

## Symptoms

If you try to create a contact for a customer account while dual-write is active, you will see the following error message"

> Write failed for entity CDS Contacts V2 with unknown exception - Field 'Associated party number' must be filled in.
> 
> Field 'Associated party number' must be filled in.validateWrite failed on data source 'smmContactPersonV2Entity (smmContactPersonV2Entity)

<!-- KFM: I suspect the above error message includes typos. Please check and confirm -->

<!-- KFM: Is the following text really intended for a customer audience? Also, it seems incomplete. Please remove or revise. -->
It was found that a piece of code in class `DualWriteSyncInbound` is making Associated party null while `ConvertStringValueToTargetType`.

## Resolution

The customer and contact entities reference each other. You must therefore synchronize your systems in the following order:

1. First sync the customer entity
1. Then sync the contact entity.
1. Finally, resync the customer entity to synchronize the the contact references.
