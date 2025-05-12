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
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

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

    - **Create** – automatically creates or pushes all duties and roles to be created from security setup into the publish staging table. In Security configuration, you should see all Security objects developed with security setup that are ready for publishing.
    - **Clear** – Select this option to clear all the security references between user security governance and Dynamics 365 finance and operations security configuration. Each task line that was imported will be blank and you’ll need to create roles and duties again for all lines. This might be helpful when you want to clear off or renew the project.
    - **None** – Select this option to move all user security governance security objects not created within the system. If the security objects are non-existent, this might cause complications.

## Bulk-create a process hierarchy

System administrators can use the **Restore from XML** feature to create an entire hierarchy under a security category. For this approach, generate the XML file in the correct format, with the desired hierarchy under a category. The hierarchy can optionally include multiple processes in a hierarchy tree and security tasks under each process. Although generation of the XML is a manual process, this approach to creating a hierarchy can still be faster if an accurate template of the XML is followed. Template creation mostly involves copying and pasting with the correct metadata. Make sure that each category has a unique name.

> [!TIP] 
> Create one category through the user interface (UI), and use the **Backup as XML** feature to download the initial file. Then modify the category in this file to create the new category that has the desired hierarchy.

## Security category export and import process

Generally, data export and import scenarios appear when customer is migrating data between legacy tool and User security governance or copying data between multiple data areas. This function is only available to system administrator role.
1. The first step in this process is to export the data.
2. Select desired security categories or all security categories on the **Security category** page. Click **Backup as XML**.
3. Select from the following options:
 - **All categories** - To select all categories, select this toggle button.
 - **Type** - There are three choices under this lookup and each of them are explained in detail above. Based on your requirement, select the option. This lookup allows single selection only.
4. After making all selections, click **OK**. This will download a file in XML format. Save the file in your local storage.
Verify the file by opening it any XML editor and see appropriate user security governance objects or core security configuration objects in the file, based on select made during the export.

Next step is to import this file into the new data area you are targeting as destination.
1. Switch to the environment or new data area where to import security categories exported earlier. Go to **System administration** \> **Security governance** \> **Security category**.
2. Click **Restore from XML**. This opens a dialog to select the file and other configurations.
3. In the dialog, browse to the XML file which you exported earlier.
4. Depending on the **Type** selected earlier during **Export**, select the same **Type** value during import. If you select the incorrect **Type** value, the tool generates an info message, giving you more information on why the import process might not work.
5. Under **Options** group, select the **Security relation action** value.
Based on if you want to just create only user security governance objects or want to clear the existing references between Dynamics 365 finance and operations security objects and user security governance objects or create all objects, pick one of the actions: **None**, **Clear**, or **Create**. 
6. Click **OK** to start the data import and an appropriate information message will be displayed after this action.
