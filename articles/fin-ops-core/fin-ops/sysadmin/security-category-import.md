--- 
title: Security category export/import
description: Learn how to use the backup and restore processes that are related to security categories. 
author: saurabhgupta
ms.author: saurabhgupta
ms.topic: how-to
ms.date: 02/07/2025
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: SysSecSegregationOfDutiesRule
ms.dyn365.ops.version: Version 7.0.0 
---

# Security category export/import

[!include [banner](../../../finance/includes/banner.md)]

Security categories offer options for both backing up as XML and restoring from XML. Learn more about the import process in [Import an existing category](security-category.md#import-an-existing-category). This article describes various scenarios that system administrators can handle.

## Back up as XML

1. Go to **System administration** \> **Security governance** \> **Security category**.
1. Before you start the backup, confirm that security categories are set up.
1. Select a security category, and then select **Backup as XML**.

    > [!IMPORTANT]
    > You can back up either a single selected category or all available categories. You can't individually select multiple categories for backup at the same time.

1. In the dialog that appears, on the **Parameters** FastTab, in the **Type** field, select one of the following values:

    - **User security governance** – Generate a complete XML file of the security category and its related configuration from the **Process hierarchy** page. If multiple hierarchies, tasks, duties, privileges, entry points, or roles are defined under the category, the XML includes only objects that were created on the **Process hierarchy** page. It excludes all objects that were created under **Core security configuration**. For example, the XML includes the hierarchy, tasks, and entry points, but it excludes duties, privileges, and roles.
    - **Security configuration** – Generate a complete XML file of the security category and its related configurations from **Core security configuration**. If multiple hierarchies, tasks, duties, privileges, entry points, roles, and so on, are defined under the category, the XML includes only objects that were created under **Core security configuration**. It excludes all objects that are limited to the **Process hierarchy** page. For example, the XML includes duties, privileges, and roles, but it excludes the hierarchy, tasks, and entry points.
    - **Governance + configuration** – Generate a complete XML file of the security category and its related configurations from the **Process hierarchy** page and under **Core security configuration**. If multiple hierarchies, tasks, duties, privileges, entry points, roles, and so on, are defined under the category, the XML includes everything that was created under **Core security configuration** and also all objects that are limited to the **Process hierarchy** page. For example, the XML includes everything, such as the hierarchy, tasks, duties, privileges, entry points, and roles.

1. Select **Types**, and then select **OK**.
1. When you're prompted, save the XML file in your local browser.

## Restore from XML

1. Go to **System administration** \> **Security governance** \> **Security category**.
1. Select **Restore from XML**.
1. In the dialog that appears, use the file browsing option to specify the path of an XML file that has a valid format.
1. In the **Type** field, select a value.
1. If you selected **User security governance** in the **Type** field, in the **Security related action** field, select one of the following values:

    - **Create** – Restore and publish the XML of the security category.
    - **Clear** – Restore the XML of the security category.
    - **None** – Restore the XML of the security category.

## Bulk-create a process hierarchy

System administrators can use the **Restore from XML** feature to create an entire hierarchy under a security category. For this approach, generate the XML file in the correct format, with the desired hierarchy under a category. The hierarchy can optionally include multiple processes in a hierarchy tree and security tasks under each process. Although generation of the XML is a manual process, this approach to creating a hierarchy can still be faster if an accurate template of the XML is followed. Template creation mostly involves copying and pasting with the correct metadata. Make sure that each category has a unique name.

> [!TIP] 
> Create one category through the user interface (UI), and use the **Backup as XML** feature to download the initial file. Then modify the category in this file to create the new category that has the desired hierarchy.
