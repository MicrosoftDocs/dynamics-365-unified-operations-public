---
# required metadata

title: (Preview) Track changes for Finance and operations virtual tables in Dataverse 
description: This article explains how to enable Track changes for Finance and Operations virtual tables in Microsoft Dataverse.
author: peakerbl
ms.date: 09/28/2022
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

# (Preview) Track changes for Finance and operations virtual tables in Dataverse 

[!include[banner](../includes/banner.md)]

## SQL Row version change tracking for Finance and Operations

A new change tracking option has been added to Finance and Operations to enable incremental synchronization of data using the Dataverse. The new change tracking is a prerequisute for several features such as Data archival, Synapse integration, Mobile offline and Relevance search. The new change tracking is enabled for Public preview from 10.0.31. The goal is to over time unify all existing Fainance and Operations data synchronization frameworks into one that is based on Dataverse synchronization services.

## Prerequisite to track changes for Finance and Operations virtual tables in Dataverse 

- The **Allow Row Version Change Tracking** metadata property, must be set to **Yes** for the data entity, see ....TBA
- Finance and Operations entities must be visible in Dataverse, see [Enable Microsoft Dataverse virtual entities](/enable-virtual-entities.md)
 
If these prerequistes are met, then the final step is to enable change tracking by selecting **Track changes** for the Virtual table in the Powerapps, see [Enable change tracking to control data synchronization](/power-platform/admin/enable-change-tracking-control-data-synchronization.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
