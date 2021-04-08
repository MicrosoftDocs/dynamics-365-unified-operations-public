---
# required metadata

title: AX 2009 migration - Export packages
description: This topic explains how to export a data package for migration from Microsoft Dynamics AX 2009 to Finance and Operations.
author: kfend
ms.date: 06/26/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry:
ms.author: kfend
ms.search.validFrom: 2018-06-21
ms.dyn365.ops.version: Platform update 17
---

# AX 2009 migration – Export packages

[!include [banner](../includes/banner.md)]

You can use the Data Import/Export Framework (DIXF) service in Microsoft Dynamics AX 2009 to retrieve data that must be migrated to  Finance and Operations. The export process is completed through a job ID. When you export, you can specify how the export job is defined. You can select the source data to export, the conversion value, and the field mapping. You can also apply a query to each source to limit what is exported.

The export package that the Data migration tool (DMT) generates can consist of one or many data entities. A typical data package consists of a group of entities for a specific task, such as import. For example, the data entities that are required for system setup might be part of one data package. The format of a data package is a compressed file that contains a package manifest, a package header, and any additional files for the data entities that are included.

Before you create a data package, plan out what should be included. In this way, you help guarantee that the correct entities, entity sequence, and fields are included.

Follow these steps to export the data package.

1. In AX 2009, in the navigation pane, click **Data migration** \> **Common** \> **Create migration group**.
2. In the **Migration group** form, select the migration group to export, and then click **Export now**.
3. In the **Export data** form, update the export file path as required, and then click **OK**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]