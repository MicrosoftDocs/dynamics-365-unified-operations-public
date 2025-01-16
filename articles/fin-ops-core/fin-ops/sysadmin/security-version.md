--- 
title: Security version management
description: Learn about how the security version feature allows maintain multiple versions of security configurations within company and perform comparison, restoration etc. 
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

[!include[banner](../../../finance/includes/banner.md)]

The security version feature allows maintain multiple versions of security configurations within company and perform comparison, restoration etc.

## Create version
This feature allows you to create the version of the security configurations at the point of time.

1. Go to **System administration** > **Security** > **Security governance** > **Security versions**.
2. Click **Create version**
3. In the **Name** field, type a value for the version. **Description** field is optional.
4. Click **OK**.
5. The version creation is an asynchronous process. You can check the status of the version creation by monitoring **Status** column. 
6. **Executing** status indicates that the version creation is in progress.

## Restore version
This feature allows you to restore the security configurations to the version that was created earlier.

1. Go to **System administration** > **Security** > **Security governance** > **Security versions**.
2. Select the version that you want to restore.
3. Click **Restore version**
4. A dialog box will open. Select the options as per your requirement.
5. Click **OK**

## Compare versions
Once the security versions are created, it is possible to compare them with each other to gain a clear insight into their differences (such as what changes have been introduced in the meantime).
1. Go to **System administration** > **Security** > **Security governance** > **Security versions**.
2. Select the version you want to compare. 
3. Click **Compare**
4. It will navigate you to a different screen where you will be asked to select another security version with which you want to compare the above selected version.
5. You can select the option to see only **differences** or all the details.
6. Click **Compare**.

## Delete version
This feature allows you to delete the security version that is no longer required.
1. Go to **System administration** > **Security** > **Security governance** > **Security versions**.
2. Select the version that you want to delete.
3. Click **Delete**.