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
1. If you selected **User security governance** in the **Type** field, in the **Security related action** field, select one of the following values:

    - **Create** – this option automatically creates/ pushes all Duties and Roles that should be created from security setup into the publish staging table. In Security configuration, you should see all Security objects developed with security setup that are ready for publishing.
    - **Clear** – this option will clear all the security references between user security governance and Finance & operations security configuration. This means that each task line that was imported will be blank and you’ll need to create Roles/duties again for all lines. This might be helpful when you want to clear off or renew the project.
    - **None** – this will move all user security governance security objects as they were not created within the system. So in case that security objects are non-existent, this might cause complications.

## Bulk-create a process hierarchy

System administrators can use the **Restore from XML** feature to create an entire hierarchy under a security category. For this approach, generate the XML file in the correct format, with the desired hierarchy under a category. The hierarchy can optionally include multiple processes in a hierarchy tree and security tasks under each process. Although generation of the XML is a manual process, this approach to creating a hierarchy can still be faster if an accurate template of the XML is followed. Template creation mostly involves copying and pasting with the correct metadata. Make sure that each category has a unique name.

> [!TIP] 
> Create one category through the user interface (UI), and use the **Backup as XML** feature to download the initial file. Then modify the category in this file to create the new category that has the desired hierarchy.

## Detailed walk-through of the security category export and import process

1. Generally, data export and import scenarios appear when customer is migrating data between legacy tool and User security governance or copying data between multiple data areas. This function is only available to system administrator role.
2. The first step in this process is to export the data.
3. Select desired security categories or all security categories on the security category form and click **Backup as XML** button.
4. This will bring up a dialog where you will have few options to select.
5. **All categories** - In case you did not select all categories earlier but now you want to do it, you can select this toggle button.
6. **Type** - There are 3 choices under this lookup and each of them are explained in detail above. Based on your requirement, select the option. This lookup allows single selection only.
7. After making all selections, press the button **OK**. This should start downloading a file in XML format. Please save the file in your local storage.
8. If you want, you can also verify this file by opening it any XML editor and you should see appropriate user security governance objects or core security configuration objects in the file, based on select made during the export.
9. Next step would be to import this file into the new data area you are targeting as destination.
10. Switch to the environment or new data area where you would like to import security categories exported earlier. Navigate to **System administration** \> **Security governance** \> **Security category**.
11. Click **Restore from XML** button on the top menu. This will open up a dialog where you will get the option to select the file and other configurations.
12. In the dialog, browse to the XML file which you exported earlier.
13. Depending on the **Type** you selected earlier during **export**, select the **same** **Type** value during import. Even if you end up selecting wrong Type value, the tool will later generate an info message, giving you more information on why the import process might not work.
14. Under **OPTIONS** group, you will have to select the appropriate **Security relation action** value.
15. Now, based on whether your want to just create only user security governance objects or want to clear the existing references between F&O security objects and user security governance objects or to create all objects, you can pick one of the actions from **None, Clear or Create**. These options are explained in detail above.
16. Click OK to start the data import and you should see an appropriate info message after this action.
