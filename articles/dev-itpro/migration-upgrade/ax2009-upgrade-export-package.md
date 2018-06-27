---
# required metadata

title: AX 2009 upgrade - Export package
description: This topic provides information about how to create package templates that you can use to migrate data from Dynamics AX 2009 to Finance and Operations.
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

Export is the process of retrieving data from source system using DIXF service. The export process is done through a JOB-ID. When exporting, you have a lot of flexibility as to how the export JOB is defined. You can choose which source data to export and conversion value and field mapping and apply a query to each source to limit what is exported. DMT export package can consist of one or many data entities. A typical data package consists of a group of entities for a specific task like import. For example, the data entities that are required for System setup might be part of one data package. The format of a data package is a compressed file that contains a package manifest, a package header, and any additional files for the data entities that are included.
Before you create your data package, plan out what it should include. In this way, you help guarantee that the correct entities, entity sequence, and fields are included. 

1.	Data management
2.	Create migration group 
3.	Export now  
