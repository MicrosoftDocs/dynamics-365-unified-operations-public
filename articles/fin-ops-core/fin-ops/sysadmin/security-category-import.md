--- 
title: Security category export/import
description: Learn how to use the backup and restore processes that are related to security categories. 
author: saurabhgupta
ms.author: saurabhgupta
ms.topic: how-to
ms.date: 05/12/2025
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
1. If you selected **User security governance** in the **Type** field, in the **Security related action** field, select one of the following options:

    - **Create** – Automatically create or push all duties and roles that must be created from the security setup into the publish staging table. The security configuration should show all security objects that were developed by using the security setup and that are ready for publishing.
    - **Clear** – Clear all the security references between user security governance and the Dynamics 365 finance and operations apps security configuration. Every task line that was imported is blank, and you must re-create roles and duties for each line. This option might be helpful when you want to clear off or renew the project.
    - **None** – Move all user security governance security objects that weren't created within the system. If the security objects don't exist, this option might cause complications.

## Bulk-create a process hierarchy

System administrators can use the **Restore from XML** feature to create an entire hierarchy under a security category. For this approach, generate the XML file in the correct format, with the desired hierarchy under a category. The hierarchy can optionally include multiple processes in a hierarchy tree and security tasks under each process. Although generation of the XML is a manual process, this approach to creating a hierarchy can still be faster if an accurate template of the XML is followed. Template creation mostly involves copying and pasting with the correct metadata. Make sure that each category has a unique name.

> [!TIP]
> Create one category through the user interface (UI), and use the **Backup as XML** feature to download the initial file. Then modify the category in this file to create the new category that has the desired hierarchy.

## Security category export and import process

In general, data export and import scenarios apply when a customer migrates data between the legacy tool and user security governance, or when a customer copies data between multiple data areas. This function is available only to the system administrator role.

The first step in the process is to export the data.

1. On the **Security category** page, select the desired security categories or all security categories. Select **Backup as XML**.
1. Select between the following options:

    - **All categories** – To select all categories, turn on this option.
    - **Type** – Select an option, based on your requirements. The three available options are explained in detail in the [Back up as XML](#back-up-as-xml) section of this article. You can select only one option in this lookup.

1. Select **OK**. A file in XML format is downloaded. Save the file in your local storage.
1. Open the file in any XML editor, and confirm that it includes the appropriate user security governance objects or core security configuration objects, based on your selections during the export.

The next step is to import the file into the new data area that you're targeting as the destination.

1. Switch to the environment or the new data area where you want to import the security categories that you exported.
1. Go to **System administration** \> **Security governance** \> **Security category**.
1. Select **Restore from XML**.
1. In the dialog that appears, browse to the XML file that you exported.
1. In the **Type** field, select the same value that you selected in the **Type** field during export. If you select an incorrect **Type** value, you receive an informational message that explains why the import process might not work.
1. In the **Options** section, in the **Security relation action** field, select **None**, **Clear**, or **Create**, based on whether you want to create user security governance objects, clear the existing references between finance and operations security objects and user security governance objects, or create all objects.
1. Select **OK** to start the data import. When the action is completed, you receive an appropriate informational message.
