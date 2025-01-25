---
title: Set up security categories
description: Learn how to set up security categories that are used to create the process hierarchy and security configuration.
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

Categories are used for an aggregation in the **Process roles maintain** module. You can define categories that help you save a new role under a given work stream or department. We strongly recommend that you complete this setup correctly. In this way, you help reduce the development costs when security upgrades are required.

There are two ways to create a category:

- Create a new category from scratch.
- Import an existing category from a different company.

### Create a new category

To create a new category from scratch, follow these steps.

1. Go to **System administration** \> **Security governance** \> **Security category**.
1. Select **New**.
1. Set the **Name** field.
1. Optional: Set the **Company** and **Description** fields.
1. Select **Save**.

### Import an existing category

To import an existing category, follow these steps.

1. Go to **System administration** \> **Security governance** \> **Security category**.
1. Select **Import**.
1. Expand the **Parameters** section.
1. Use the **Browse** button to provide the file path of the attachment.
1. Select **Type** to select the value according to your business requirement.
1. Select **OK**. A message bar indicates whether the import was successful or failed.
