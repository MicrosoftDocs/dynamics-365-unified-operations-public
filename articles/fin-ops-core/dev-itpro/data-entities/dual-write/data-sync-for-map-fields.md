---
title: Trigger dual-write for mapped fields
description: This article explains the dual-write triggering behavior for mapped fields.
author: RamaKrishnamoorthy 
ms.date: 12/22/2022
ms.topic: article
audience: Developer
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: ramasri
ms.search.validFrom: 2022-12-21
---

# Trigger dual-write for mapped fields

[!include [banner](../../includes/banner.md)]
[!include [banner](../../includes/preview-banner.md)]

Today when a table participating in dual-write gets updated, the dual-write platform core plugins are triggered regardless of whether the updated table field is participating in dual-write map or not. As a result, there are performance issues due to redundant call overhead against dual-write tables.  

Going forward, dual-write platform core plugins will be triggered only when the updated field is configured in dual-write map. 

Here's an example to explain the behavior: 
There's a Microsoft Dataverse table with three fields named A, B, and C and there's a dual-write map for this table. Only fields B and C are configured in the dual-write map. 

- If A is updated, the dual-write plugin won't be invoked unlike before where it used to.
- If B is updated, the dual-write plugin will be invoked and will send both B and C fields as part of payload to finance and operations apps.
- If B is updated and C is calculated based on B, the dual-write plugin will be invoked because B is being mapped and will send both B and C fields as part of payload to 
finance and operations apps.
- If A is updated and C is calculated based on A, the dual-write plugin won't be invoked (Current limitation for this feature.).


>[!Note]
> The revised dual-write platform core plugin behavior does not work for calculated fields in Dataverse. This is due to a platform limitation. 
> We are exploring options to overcome this limitation. 
