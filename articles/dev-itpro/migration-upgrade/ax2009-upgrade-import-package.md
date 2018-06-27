---
# required metadata

title: AX 2009 upgrade - Import package
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

# AX 2009 upgrade - Import package

[!include [banner](../includes/banner.md)]

Import is the process of pulling data into a system using data entities. The import process is done through the Import tile in the Data Management workspace or you can import from source system directly or use LCS to upload the data package. Data can be imported for a group of logically related entities that are sequenced in the correct order. 
Import a data package:
Option 1:  AX 2009 – Data management -> create migration group -> Export now -> mark import  package in target. 

Option 2:
1.	Log into the D365 environment using a login with sufficient privileges (typically this is the Administrator role).
2.	On the dashboard, click the Data Management workspace.
3.	Click the Import tile.
4.	On the next page, do the following:
a.	Provide a name.
b.	In the Source Data Format field, select Package .
c.	Click the Upload button and choose the appropriate package file from the location for the data being imported. This will import all the files from the package.
Option 3: LCS 
