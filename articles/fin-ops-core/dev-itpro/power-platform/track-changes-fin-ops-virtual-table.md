---
# required metadata

title: Track changes for finance and operations virtual tables in Dataverse (Preview)
description: This article explains how to enable Track changes for finance and operations virtual tables in Microsoft Dataverse.
author: peakerbl
ms.date: 12/20/2022
ms.topic: article
ms.prod:
ms.technology: 

# optional metadata

# ms.search.form:
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: 
# ms.tgt_pltfrm: 
# ms.custom: NotInToc
ms.search.region: Global
# ms.search.industry:
ms.author: peakerbl
ms.search.validFrom: 2022-10-10
ms.dyn365.ops.version: 10.0.31
---

# Track changes for finance and operations virtual tables in Dataverse (Preview) 

[!include[banner](../includes/banner.md)]

[This topic is pre-release documentation and is subject to change.]

## Row version change tracking for finance and operations

A new change tracking option has been added to finance and operations apps to enable incremental synchronization of data using the Microsoft Dataverse. The new change tracking is a prerequisute for several features such as Data archival, Synapse integration, Mobile offline and Relevance search. The goal, over time, is to unify all existing finance and operations data synchronization frameworks into one that is based on Dataverse synchronization services.

## Prerequisite to track changes for finance and operations virtual tables in Dataverse 

- The **Allow Row Version Change Tracking** metadata property, must be set to **Yes** for the data entity, see [Allow Row version change tracking for Data entities](../data-entities/rowversion-change-track.md).
- Finance and Operations entities must be visible in Dataverse, see [Enable Microsoft Dataverse virtual entities](enable-virtual-entities.md).
 
 ## Track changes for finance and operations virtual tables in Dataverse 

If the above prerequisites are met, then the final step is to enable change tracking by selecting **Track changes** for the Virtual table in the Power Apps, see [Enable change tracking to control data synchronization](/power-platform/admin/enable-change-tracking-control-data-synchronization).

> [!IMPORTANT]
> - This preview feature is available from release 10.0.31 where the Microsoft Power Platform integration has been enabled with Dataverse database, see [Enable the Microsoft Power Platform integration](./enable-power-platform-integration.md). To enable see [What are Preview features, and how do I enable them?](/power-platform/admin/what-are-preview-features-how-do-i-enable-them).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
