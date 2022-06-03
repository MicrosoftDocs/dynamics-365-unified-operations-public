---
# required metadata

title: AX 2009 migration - Import packages
description: This article explains how to import a migrated data package from Microsoft Dynamics AX 2009 into Finance and Operations.
author: kfend
ms.date: 09/13/2018
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

# AX 2009 migration – Import packages

[!include [banner](../includes/banner.md)]

Data can be imported for a group of logically related entities that are sequenced in the correct order. You have three options for importing Microsoft Dynamics AX 2009 data that you want to migrate:

- AX 2009
- Finance and Operations

## AX 2009
You can import data for migration directly from the source system. Follow these steps.

1. In AX 2009, in the navigation pane, click **Data migration**.
2. Go to **Common** \> **Create migration group**.
3. In the **Migration group** form, select the migration group to export, and then click **Export now**.
4. In the **Export data** form, select the **Import package in target** check box, and then click **OK**.

## Finance and Operations
You can import data for migration by using your Finance and Operations environment. Follow these steps.

1. Sign in to your environment by using an Administrator role.
2. On the dashboard, select the **Data Management** workspace.
3. Select **Import**.
4. Enter the name of the package, and then, in the **Source data format** field, select **Package**.
5. Select **Upload**, and then select the appropriate package file from the location for the data that is being imported. All the files from the package are imported.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]