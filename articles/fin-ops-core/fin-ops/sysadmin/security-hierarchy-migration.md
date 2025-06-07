--- 
title: Data migration for the user security process hierarchy and security categories
description: Learn how to migrate data for the user security governance process hierarchy and security categories. 
author: saurabhgupta
ms.author: saurabhgupta
ms.topic: how-to
ms.date: 05/26/2025
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2025-05-25
ms.search.form: SysSecProcessHierarchy
ms.dyn365.ops.version: Version 7.0.0 
---

# Data migration for the user security process hierarchy and security categories

[!include [banner](../../../finance/includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The security governance feature offers options for both backing up data as XML and restoring it from XML in different scenarios. This article describes specific scenarios for data migration and explains the steps that are involved in backing up data, restoring data, and verifying restored data. Learn more about the import process in [Import an existing category](security-category.md#import-an-existing-category).

## Data migration scenarios

There are two common scenarios where data migration is required:

- Scenario 1: Migrate data from the Executive Automats security setup to Security governance.
- Scenario 2: Set up another instance of security governance configurations in the same company.

### Scenario 1: Migrate data from the Executive Automats security setup to Security governance

1. Go to **System administration** \> **Executive Automats Security Setup** \> **Security category**.
1. Confirm that security categories already exist. If they don't exist, set them up.
1. Select one of the security categories to migrate, and then select **Export**.
1. In the dialog that appears, select **All categories** to export all categories.
1. To ensure that the format of the exported file is compatible with the security governance feature, enable the **User security governance format** option.
1. In the **Type** field, two values are available: **EASS** and **EASS + Security configuration**. The primary goal of data migration is to re-create the security process hierarchy and related security objects in a new environment. Select **EASS + Security configuration** to migrate the data to a new environment and generate a template file that contains process hierarchy objects.
1. Select **OK**. The template file is generated. The data in it is in a format that is compatible with migration to Security governance.

    > [!IMPORTANT]
    > You can either back up a single selected category or all available categories. You can't individually select multiple categories for export at the same time without opening the dialog.

#### Restore security categories in Security governance

1. Go to **System administration** \> **Security governance** \> **Security category**.

    Either there are no preexisting security categories on the page, or the existing categories differ from the category that you're trying to restore from the Executive Automats security setup into User security governance. If a category that has the same **Category name** value already exists in Security governance, you will receive a warning message, and the process will stop.

1. Select **Restore from XML**.
1. In the dialog that appears, select the file that you exported in the previous procedure.
1. On the **Parameters** FastTab, in the **Type** field, select one of the following values:

    - **User security governance** – Restore security categories and the related configurations from the **Process hierarchy** page. If multiple process hierarchies, security tasks, security duties, security privileges, entry point mappings with tasks, or security roles are defined in a category, this value restores only objects in the **Security governance** module. It excludes all objects that were created under **Core security configuration**. For example, the hierarchy, tasks, and entry point mapping are restored, but duties, privileges, and roles are excluded.

        > [!IMPORTANT]
        > If you selected **EASS** in the **Type** field in the previous procedure, select this value. The two values are equivalent.

    - **Security configuration** – Restore only the core security objects that are present in the file that you exported in the previous procedure. This value doesn't restore the security categories and the related configurations from the **Process hierarchy** page. If multiple process hierarchies, security tasks, security duties, security privileges, entry point mappings with tasks, or security roles are defined in a category, this value restores only objects that were created under **Core security configuration**. It excludes all objects that were created under the Security governance process hierarchy. For example, the security category, hierarchy, tasks, and entry point mapping are excluded, but duties, privileges, and roles are restored.

        > [!IMPORTANT]
        > If you selected **EASS** in the **Type** field in the previous procedure, don't select this value. The two values are mutually exclusive.

    - **Governance + configuration** – Restore the security categories and the related configurations from the **Process hierarchy** page and under **Core security configuration**. If multiple process hierarchies, security tasks, security duties, security privileges, entry point mappings with tasks, or security roles are defined in a category, this value restores all objects that were created under **Core security configuration** and all objects that are limited to the **Process hierarchy** page. For example, the XML includes the hierarchy, tasks, duties, privileges, entry points, roles, and everything else.

        > [!IMPORTANT]
        > If you selected **EASS + Security configuration** in the **Type** field in the previous procedure, this value is the most suitable option, because it restores everything.

1. In the **Security related action** field, select one of the following values:

    - **Create** – Automatically create or push all duties and roles that must be created from the security setup into the publish staging table. The security configuration shows all security objects that were developed by using the security setup and that are ready for publishing.
    - **Clear** – Clear all the security references between user security governance and the security configuration in Dynamics 365 finance and operations apps. Every task line that was imported is blank, and you must recreate roles and duties for each line. This value is useful if you want to clear out or renew the project.
    - **None** – Move all user security governance security objects that weren't created in the system. If the security objects don't exist, this value might cause complications.

    > [!IMPORTANT]
    > For this data migration scenario, the **Create** value is the most suitable option, because it restores and publishes everything that you're migrating to a new environment.

1. Select **OK** to start the restore process.

    If the process succeeds, you receive an informational message that confirms successful restoration.

    If any issue occurs during the process, you receive a warning message. In this case, verify the security category. The newly restored category should appear on the **Security category** page.

1. To verify the restored process hierarchy and other objects, go to **System administration** \> **Security governance** \> **Security process roles maintain**.
1. In the **Security category** field, select the new category. The process hierarchy and underlying objects (for example, security tasks, entry point mappings, duties, privileges, and roles) are loaded.

### Scenario 2: Set up another instance of security governance configurations in the same company

In this scenario, security categories exist in two environments, and you're trying to migrate the data under those categories (the process hierarchy, security tasks, entry point mappings, duties, privileges, and security roles).

1. Go to **System administration** \> **Executive Automats Security Setup** \> **Security Process Roles Maintain**.
1. Select the category to export to the other environment.
1. Select the **Process hierarchy** node.
1. On the **Process role definition** FastTab, select **Export**.
1. In the **Export executive automats security setup data** dialog, in the **Type** field, select a value. (The available values are explained in scenario 1.)

    > [!TIP]
    > For this data migration scenario, the **EASS + Security configuration** value is the most suitable option, because it restores and publishes everything that you're migrating to the new environment.

1. Enable the **User security governance format** option to generate XML that is compatible with the restore process in Security governance.
1. Select **OK**. The XML file is exported with data.

#### Import the exported data into Security governance

1. Go to **System administration** \> **Security governance** \> **Security process roles maintain**.
1. Select the category and one of the process hierarchy nodes under it.
1. On the **Role definition** FastTab, select **Restore from XML**.
1. In the dialog that appears, set the **Overwrite** option to specify whether a security object in the selected category should be overwritten by the object that is part of the file that you exported from the Executive Automats security setup in the previous procedure.

    > [!TIP]
    > A value of **Yes** for the **Overwrite** option is useful if the selected security category has a preexisting process role hierarchy, and some objects in that hierarchy have names that match object names in the Executive Automats security setup. This value ensures that the data import process isn't blocked because of existing objects. Instead, the process overwrites those objects.

1. In the **Security relation action** field, select one of the following values:

    - **None** – Create user security governance objects.
    - **Clear** – Clear the existing references between finance and operations security objects and user security governance objects.
    - **Create** – Create all objects.

1. Select **OK** to start the data import.
1. Refresh the page, and then verify the data by going to the process hierarchy node that you selected to restore the XML to.
