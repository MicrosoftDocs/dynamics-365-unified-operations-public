--- 
title: Security category setup
description: Learn about how you can set up security categories for your company which will be further utilized to create the process hierarchy and security configuration. 
author: saurabhgupta
ms.author: saurabhgupta
ms.topic: article
ms.date: 01/15/2025
ms.custom: 
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2025-01-20
ms.search.form: SysSecRolesEditUsers, SysSecAssignmentQueryLookup, SysQueryForm, SysSecRoleExcludeUsers
ms.dyn365.ops.version: Version 7.0.0 
---

# Security category setup

[!include [banner](../../../finance/includes/banner.md)]

## Security categories
Categories that are used for an aggregation in Process Roles Maintain module. Here, you can define categories that will help you save a new Role under a given work stream/department. We strongly recommend building this properly. In this way, you will limit the development costs when it comes to security upgrades, etc.

To create a new **category**, there are two approaches available on this form: Create a new category or Import an existing category from different company.

### Create a new category
1. Go to **System administration \> Security Governance \> Security category**.
2. Click on **New**.
3. Enter the **Name**, **Company** (optional) and **Description** (optional).
4. Click on **Save**.


### Restore from XML
1. Go to **System administration \> Security Governance \> Security category**.
2. Click on **Import**.
3. Expand the **Parameters** section.
4. Provide the file path in the **Browse** file attachment field.
5. Select the **Type** to pick the value as per your business requirement.
6. Click on **OK**.
7. You should see the appropriate message in message bar based on whether the import is successful or failed due to some reasons.