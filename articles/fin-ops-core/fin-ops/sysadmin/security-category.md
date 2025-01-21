--- 
title: Set up security categories
description: Learn about how you can set up security categories that are utilized to create the process hierarchy and security configuration. 
author: saurabhgupta
ms.author: saurabhgupta
ms.topic: article
ms.date: 01/25/2025
ms.custom: 
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2025-01-20
ms.search.form: SysSecRolesEditUsers, SysSecAssignmentQueryLookup, SysQueryForm, SysSecRoleExcludeUsers
ms.dyn365.ops.version: Version 7.0.0 
---

# Set up security categories

[!include [banner](../../../finance/includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

## Security categories
Categories are used for an aggregation in **Process roles maintain** module. You can define categories that help you save a new role under a given work stream or department. We strongly recommend building this properly to limit the development costs when it comes to security upgrades.

To create a new **Category**, there are two approaches available: 
 - Create a new category
 - Import an existing category from different company

### Create a new category

To create a new category, follow these steps:
1. Go to **System administration \> Security governance \> Security category**.
2. Click on **New**.
3. Enter the **Name**, **Company** (optional) and **Description** (optional).
4. Click on **Save**.


### Import an existing category

To import an existing category, follow these steps:
1. Go to **System administration \> Security governance \> Security category**.
2. Click on **Import**.
3. Expand the **Parameters** section.
4. Provide the file path in the **Browse** file attachment field.
5. Select **Type** to pick the value as per your business requirement.
6. Click on **OK**.
7. A message in the message bar displays if the import is successful or failed.
