---
# required metadata

title: Excel data entity templates
description: This topic describes Excel data entity templates. 
author: Sunil-Garg
manager: AnnBe
ms.date: 01/01/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sunilg
ms.search.validFrom: 2018-01-01
ms.dyn365.ops.version: Platform update 13

---

# Excel templates with multiple worksheets

Data management supports excel based templates for data entities. These templates can also have multiple worksheets. This often comes into play when data is logically grouped into a single excel file but in different worksheets, an example of which would be, sites and warehouses or journals of various kind. In such cases, it is convenient to manage the data in a single file and import across multiple data entities.

### Upload the file once and map it to all entities
Let’s take an example where there is one excel file with two worksheets called, Sites and Warehouses. When setting up the data import project, one would add the first data entity, say, Sites and then upload the excel file. You will be able to select ‘Sites’ as the worksheets to be used for this entity.

Now, if the second entity ‘Warehouses’ is also added without exiting the ‘add file’ form, the worksheet look-up will allow to select the ‘Warehouses’ worksheet without having to upload the file again. The only reason to upload a new file will be if the ‘Warehouses’ data was in a different file.

![Multiple workseets](../media/AddFileMultipleWorkSheets.png) 

[!include[banner](../includes/banner.md)]
