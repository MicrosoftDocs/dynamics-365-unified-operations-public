---
title: AX 2009 migration - Export packages
description: Learn how to export a data package for migration from Microsoft Dynamics AX 2009 to finance and operations through a job ID.
author: johnmichalak
ms.author: johnmichalak
ms.topic: how-to
ms.date: 11/11/2025
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2018-06-21
ms.dyn365.ops.version: Platform update 17
---

# AX 2009 migration – Export packages

[!include [banner](../includes/banner.md)]

You can use the Data Import/Export Framework (DIXF) service in Microsoft Dynamics AX 2009 to retrieve data that you need to migrate to finance and operations. The export process uses a job ID. When you export, you can specify how to define the export job. You can select the source data to export, the conversion value, and the field mapping. You can also apply a query to each source to limit what is exported.

The export package that the Data migration tool (DMT) generates can consist of one or many data entities. A typical data package consists of a group of entities for a specific task, such as import. For example, the data entities that are required for system setup might be part of one data package. The format of a data package is a compressed file that contains a package manifest, a package header, and any other files for the data entities that are included.

Before you create a data package, plan out what should be included. In this way, you help guarantee that the correct entities, entity sequence, and fields are included.

Follow these steps to export the data package.

1. In AX 2009, in the navigation pane, select **Data migration** \> **Common** \> **Create migration group**.
1. In the **Migration group** form, select the migration group to export, then select **Export now**.
1. In the **Export data** form, update the export file path as required, then select **OK**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
