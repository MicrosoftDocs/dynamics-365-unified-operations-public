--- 
title: Security version management
description: Learn about how to maintain multiple versions of security configurations within a company. 
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

# Security version management

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The security version feature maintains multiple versions of security configurations within a company and perform comparisons and restorations.

## Create version
To create a version of the security configurations at a point of time, follow these steps:

1. Go to **System administration** > **Security** > **Security governance** > **Security versions**.
2. Click **Create version**
3. In the **Name** field, type a value for the version. 
4. Click **OK**.
5. Version creation is an asynchronous process. You can check the status of the version creation by monitoring **Status** column. 
6. **Executing** status indicates that the version creation is in progress.

## Restore version
To restore the security configurations to a version that was created earlier, follow these steps:

1. Go to **System administration** > **Security** > **Security governance** > **Security versions**.
2. Select the version to restore.
3. Click **Restore version**
4. A dialog box opens.
5. Select options as needed.
6. Click **OK**

## Compare versions
After the security versions are created, users can compare them to gain a clear insight into differences.

To compare versions, follow these steps:
1. Go to **System administration** > **Security** > **Security governance** > **Security versions**.
2. Select the version to compare. 
3. Click **Compare**
4. Select another security version from the additional screen to compare the above selected version.
5. Select to see only **Differences** or all the details.
6. Click **Compare**.

## Delete version
Users can delete security versions that aren't required.

To delete a security version, follow these steps:
1. Go to **System administration** > **Security** > **Security governance** > **Security versions**.
2. Select the version to delete.
3. Click **Delete**.
