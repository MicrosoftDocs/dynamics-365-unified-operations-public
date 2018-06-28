---
# required metadata

title: AX 2009 upgrade - Export package
description: This topic provides information about how to export a data package for migration from Microsoft Dynamics AX 2009 to Microsoft Dynamics 365 for Finance and Operations.
author: kfend
manager: AnnBe
ms.date: 06/26/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope:  Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry:
ms.author: kfend
ms.search.validFrom: 2018-06-21
ms.dyn365.ops.version: Platform update 17
---

# AX 2009 upgrade - Export package

[!include [banner](../includes/banner.md)]

You can use the DIXF service in Microsoft Dynamics AX 2009 to retrieve data that needs to be migrated to Microsoft Dynamics 365 for Finance and Operations. The export process is completed through a JOB-ID. When you export, you can determine how the export JOB is defined. You can select the source data to export, the conversion value, and field mapping, and apply a query to each source to limit what is exported. The Data migration tool (DMT) export package can consist of one or many data entities. A typical data package consists of a group of entities for a specific task, such as import. For example, the data entities that are required for System setup might be part of one data package. The format of a data package is a compressed file that contains a package manifest, a package header, and any additional files for the data entities that are included.
Before you create your data package, plan out what should be included. By doing this, you help guarantee that the correct entities, entity sequence, and fields are included. 

Complete the following stpes to export the data package.

1. In Dynamics AX 2009, in the navigation pane, click **Data migration** > **Common** > **Create migration group**.
2. On the **Migration group** form, select the migration group that you want to export and then click **Export now**. 
3. On the **Export data** form, update the export file path if needed, and then click **OK**.

