---
title: Track changes for finance and operations virtual tables in Dataverse
description: Learn about how to enable Track changes for finance and operations virtual tables in Microsoft Dataverse, including prerequisites to tracking changes.
author: pnghub
ms.author: johnmichalak
ms.topic: article
ms.date: 01/21/2026
ms.custom: 
  - NotInToc
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2022-10-10
ms.dyn365.ops.version: 10.0.31
---

# Track changes for finance and operations virtual tables in Dataverse

[!include[banner](../includes/banner.md)]

## Row version change tracking for finance and operations

A new change tracking option is added to finance and operations apps to enable incremental synchronization of data by using Microsoft Dataverse. The new change tracking option is a prerequisite for several features such as data archival, Synapse integration, mobile offline, and relevance search. The goal, over time, is to unify all existing finance and operations data synchronization frameworks into one that is based on Dataverse synchronization services.

## Prerequisite to track changes for finance and operations virtual tables in Dataverse

- Set the **Allow Row Version Change Tracking** metadata property to **Yes** for the data entity. For more information, see [Allow Row version change tracking for Data entities](../data-entities/rowversion-change-track.md).
- Finance and operations entities must be visible in Dataverse. For more information, see [Enable Microsoft Dataverse virtual entities](enable-virtual-entities.md).

## Track changes for finance and operations virtual tables in Dataverse

If you meet the prerequisites, enable change tracking by selecting **Track changes** for the virtual table in Power Apps. For more information, see [Enable change tracking to control data synchronization](/power-platform/admin/enable-change-tracking-control-data-synchronization).

> [!IMPORTANT]
>
> - This preview feature is available from release 10.0.31 where the Microsoft Power Platform integration is enabled with Dataverse database. For more information, see [Enable the Microsoft Power Platform integration](./enable-power-platform-integration.md). To enable, see [What are Preview features, and how do I enable them?](/power-platform/admin/what-are-preview-features-how-do-i-enable-them).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
