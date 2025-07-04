---
title: Security version management
description: Learn how to maintain multiple versions of security configurations in a company.
author: saurabhgupta
ms.author: saurabhgupta
ms.topic: article
ms.date: 06/30/2025
ms.custom: 
  - bap-template
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2025-01-20
ms.search.form: SysSecRolesEditUsers, SysSecAssignmentQueryLookup, SysQueryForm, SysSecRoleExcludeUsers
ms.dyn365.ops.version: Version 7.0.0
---

# Security version management

[!include [banner](../includes/banner.md)]

The security version feature lets you maintain multiple versions of security configurations in a company. You can also compare and restore versions.

## Create a version

To create a version of the security configurations at a point in time, follow these steps.

1. Go to **System administration** \> **Security** \> **Security governance** \> **Security versions**.
1. Select **Create version**.
1. In the **Name** field, enter a name for the version.
1. Select **OK**.

Version creation is an asynchronous process. You can use the **Status** column to monitor the status of the process. A status of **Executing** indicates that version creation is in progress.

## Restore a version

To restore the security configurations to a version that was created earlier, follow these steps.

1. Go to **System administration** \> **Security** \> **Security governance** \> **Security versions**.
1. Select the version to restore.
1. Select **Restore version**.
1. In the dialog box that appears, select options as required.

   - **User security governance** - Restore all objects configured on the **Process hierarchy** page, including the **Security category**, **Process role**, and **Security tasks**. This also restores the related security roles, duties, and privileges created on the page. This doesn’t restore the security objects created from **Core Security configuration**.
   - **Security configuration** - Restore security roles, duties, and privileges created from **Core security configuration**.
   - **Remove customizations** - Remove the security roles, duties, and privileges before restoring. This option is only available when the **Security configuration** option is enabled. Enabling this option ensures that the security objects are restored exactly to the version being restored.

   
1. Select **OK**.

This action resets this environment to the selected version state. All security metadata customizations and user security governance data changes since the selected version will be removed. It's highly recommended to first create a new version to save any current changes before performing this action.

## Compare versions

After security versions are created, users can compare them to gain insights into the differences between them.

To compare versions, follow these steps.

1. Go to **System administration** \> **Security** \> **Security governance** \> **Security versions**.
1. Select a version for comparison.
1. Select **Compare**.
1. On the page that appears, select a version to compare to the previously selected version.
1. Specify whether only differences or all details should be shown.
1. Select **Compare**.

## Delete a version

Users can delete security versions that aren't required.

To delete a security version, follow these steps.

1. Go to **System administration** \> **Security** \> **Security governance** \> **Security versions**.
1. Select the version to delete.
1. Select **Delete**.
