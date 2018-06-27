---
# required metadata

title: AX 2009 upgrade - Import package
description: This topic provides information about how to import the migrated data package from Microsoft Dynamics AX 2009 into Microsoft Dynamics 365 for Finance and Operations.
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

Data can be imported for a group of logically related entities that are sequenced in the correct order. There are three possible options to import the Microsoft Dynamics AX 2009 data that you want to migrate to Microsoft Dynamics 365 for Fiance and Operations.

- Dynamics AX 2009
- Finance and Operations
- Lifecycle Services (LCS)

## Dynamics AX 2009
You can import your data for migration from the source system directly by completing the following steps. 

1. In Dynamics AX 2009, click Data management -> create migration group -> Export now -> mark import package in target. 

## Finance and Operations
You can import your data for migration using your Finance and Operations environment by completing the following steps. 

1. Using an admin role, log into your Finance and Operations environment. 
2. On the dashboard, click the **Data Management** workspace.
3. Click **Import**.
4. Enter the name of the package, and in the **Source data format** field, select **Package**.
5. Click **Upload** and choose the appropriate package file from the location for the data being imported. This will import all the files from the package.

## Lifecycle Services 
For information about how to import a package into Finance and Operations using LCS, see [Apply updates to a cloud environment](./deployment/apply-deployable-package-system.md).

