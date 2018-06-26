---
# required metadata

title: AX 2009 upgrade - Create templates 
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

# AX 2009 upgrade - Create package templates

[!include [banner](../includes/banner.md)]

Packages are created as per the sequence. Recommended that you import the data entities in the order, as some entities have dependencies on others. If you do not follow the package template sequence order, you may encounter issues during import and configuration. The default templates can help users to easily create a list of data entities to support common areas of data for migration purposes.

DMT tool would provide OOB 20 template as below. There is provision to add custom entity in existing template as well as end user can create n-number custom templates as per theire scenario. 

OOB template having sequence, which is predefine by system. If you are customizing the template don’t forget to run the apply sequence process. 

Path: Entity List -> Apply sequence 
