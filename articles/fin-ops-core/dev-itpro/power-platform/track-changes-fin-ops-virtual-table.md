---
title: Track changes for finance and operations virtual tables in Dataverse
description: Learn about how to enable Track changes for finance and operations virtual tables in Microsoft Dataverse, including prerequisites to tracking changes.
author: pnghub
ms.author: johnmichalak
ms.topic: article
ms.date: 09/26/2026
ms.custom: 
  - NotInToc
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2022-10-10
ms.dyn365.ops.version: 10.0.31
---

# Track changes for finance and operations virtual tables in Dataverse

[!INCLUDE [banner](../includes/banner.md)]

## Row version change tracking for finance and operations

This article uses [row version change tracking](../data-entities/rowversion-change-track.md). Enabling the separate [SQL change tracking](../data-entities/entity-change-track.md) mechanism in Data management doesn't enable row version change tracking for a virtual table.

## Prerequisite to track changes for finance and operations virtual tables in Dataverse

- Check [Table eligibility for change tracking](../data-entities/change-tracking-table-eligibility.md#row-version-change-tracking).
- Complete the [row version configuration-key and database synchronization setup](../data-entities/rowversion-change-track.md#enable-row-version-change-tracking-functionality), enable the [underlying tables](../data-entities/rowversion-change-track.md#enable-row-version-change-tracking-for-tables), and enable and validate the [data entity](../data-entities/rowversion-change-track.md#enable-row-version-change-tracking-for-data-Entities).
- Finance and operations entities must be visible in Dataverse. For more information, see [Enable Microsoft Dataverse virtual entities](enable-virtual-entities.md).

## Track changes for finance and operations virtual tables in Dataverse

If you meet the prerequisites, enable change tracking by selecting **Track changes** for the virtual table in Power Apps. For more information, see [Enable change tracking to control data synchronization](/power-platform/admin/enable-change-tracking-control-data-synchronization).

> [!IMPORTANT]
>
> - This preview feature is available from release 10.0.31 where the Microsoft Power Platform integration is enabled with Dataverse database. For more information, see [Enable the Microsoft Power Platform integration](./enable-power-platform-integration.md). To enable, see [What are Preview features, and how do I enable them?](/power-platform/admin/what-are-preview-features-how-do-i-enable-them).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
