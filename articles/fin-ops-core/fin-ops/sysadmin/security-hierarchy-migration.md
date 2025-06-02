--- 
title: Security process hierarchy migration
description: Learn how to migrate data for user security governance process hierarchy and security categories. 
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

# User security governance process hierarchy data migration details

[!include [banner](../../../finance/includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Security governance features offers options for both backing up as XML and restoring from XML in different scenarios. This article focus on specific scenarios of data migration and steps involved for backing up the data, restoring it later and then verifying the restored data. For more information about the import process, see [Import an existing category](security-category.md#import-an-existing-category). 

## Data migration scenarios

There are two common scenarios where data migration is needed: 
 - Scenario one -  Migrating data from Executive automates security setup to **Security governance**.
 - Scenario two - Setting up another instance of **Security governance** configurations in the same company.  

### Scenario one - migrate data from Executive automates security setup to Security governance
1. Go to **System administration** \> **Executive Automats Security Setup** \> **Security category**.
2. Confirm that secruity categories already exist. If not, set up security categories.
3. Select one of the security categories to migrate and then select **Export**.
4. A dialog box opens.
5. In this dialog, to export all categories, select the **All categories** button.
6. Select the **User security governance format** toggle to make sure the format of exported file is compatible with **Security governance** feature.
7. Under the option **Type**, there are two options to select: **EASS** or **EASS + Security configuration**. The primary goal of this data migration activity is to recreate security process hierarchy and related security objects in new environment. Select **EASS + Security configuration** to migrate the data to a new environment and the template file contains process hierarchy objects.
8. Click **Ok**. The template file is generated with data in a format compatible for migration into security governance.
    > [!IMPORTANT]
    > You can back up either a single selected category or all available categories. You can't individually select multiple categories for exporting at the same time without opening the dialog.
    
### Restore secruity categories into **Secruity goverance**
1. Go to **System administration** \> **Security governance** \> **Security category**.
2. There's either pre-existing security categories on this page or the existing categories are different from the one which you are trying to restore from Executive automates security setup.
3. If the **Category name** alredy exists in security governance, this process displays a warning and the process stops. 
4. Click **Restore from XML**. A dialog box opens with multiple fields and file browser control.
5. Select the file which you generated above. 
6. Under the **Parameters** FastTab, in the **Type** field, there are multiple options: 
   - **User security governance** – This option restores security categories and its related configuration from the **Process hierarchy** page. If multiple process hierarchies, security tasks, security duties, security privileges, entry points mapping with tasks, or security roles are defined under a category, this option restores only objects limited to security governance module and excludes all objects that were created under **Core security configuration**. For example, the hierarchy, tasks, and entry points mapping are restored but duties, privileges, and roles are excluded.
    > [!IMPORTANT]
    > If **EASS** was selected while generating the file in step above, select this option because they are equivalent to each other. 
    
   - **Security configuration** – This option restores only the core security objects present in the exported file above. It won't restore the security category and its related configuration from the **Process hierarchy** page. If multiple process hierarchies, security tasks, security duties, security privileges, entry points mapping with tasks, or security roles are defined under a category, this option restores only objects that were created under **Core security configuration** and excludes all objects that were created under security governance process hierarchy. For example, the security category, hierarchy, tasks, and entry points mapping are excluded but duties, privileges, and roles are restored.
   > [!IMPORTANT]
   > If **EASS** was selected while generating the file above, don't select this option because they are exclusive of each other.
   
   - **Governance + configuration** – This option restores the security category and its related configurations from the **Process hierarchy** page as well as under **Core security configuration**. If multiple process hierarchies, security tasks, security duties, security privileges, entry points mappings with task, security roles, and so on, are defined under a category, this option restores everything that was created under **Core security configuration** and also all objects that are limited to the **Process hierarchy** page. For example, the XML includes everything, such as the hierarchy, tasks, duties, privileges, entry points, and roles.
   > [!IMPORTANT]
   > If **EASS + Security configuration** was selected while generating the file above, this option is the most suitable choice because it restores everything.

    In the **Security related action** field, select one of the following options:
    - **Create** – Automatically create or push all duties and roles that must be created from the security setup into the publish staging table. The security configuration should show all security objects that were developed by using the security setup and that are ready for publishing.
    - **Clear** – Clear all the security references between user security governance and the Dynamics 365 finance and operations apps security configuration. Every task line that was imported is blank, and you must recreate roles and duties for each line. This option is helpful to clear off or renew the project.
    - **None** – Move all user security governance security objects that weren't created within the system. If the security objects don't exist, this option might cause complications.
   > [!IMPORTANT]
   > In this specific scenario of data migration, **Create** option is the most suitable choice because it restores and publishes everything you are migrating into new environment.
   
7. Click **OK** to start the restoration process.
8. After successful processing, an information message confirming the successful restoration is displayed. Otherwise a warning message displays and explains a problem occured during the process.
9. If you get a warning, verify the security category. You should see the newly restored category on the **Security category** page.
10. To verify the restored process hierarchy and other objects, go to **System administration** \> **Security governance** \> **Security process roles maintain**.
11. In the **Security category** field, select the new category.
12. This loads the process hierarchy and underlying objects like security tasks, entry point mapping, duties, privileges and roles.


### Scenario two - migrate process hierarchy and related objects for an existing Security category from EASS to Security governance

In cases where there are security categories existing in two environments and you are trying to migrate the data under that category. With data, it means process hierarchy, security tasks, entry points mapping, duties, privileges and security roles.  

1. Go to **System administration** \> **Executive Automats Security Setup** \> **Security Process Roles Maintain**.
2. Select the category to export to other environment.
3. Select the **Process hierarchy** node.
4. Under **Process role definition** FastTab, select **Export**.
5. In the **Export executive automats security setup data**, select an option from the **Type** field. Each option is explained above. 
> [!TIP]
> In this scenario of data migration, **EASS + Security configuration** option is the most suitable choice because it restores and publishes everything you're migrating into new environment.
6. Select **User security governance format** to generate the XML that's compatible with **Security governance** restore process.
7. Click **OK**. The XML file is exproted with data.

Import this data into **Security governance**.
1. Go to **System administration** \> **Security governance** \> **Security process roles maintain**.
2. Select the category and one of the process hierarchy node underneath it.
3. Under the **Role definition** FastTab, click **Restore from XML**.
4. A dialog box opens to restore process role with few configuration options.
5. The **Overwrite** option overwrites any security object under the selected category from the one which is part of the import file from EASS.

> [!TIP]
> Selecting **Overwrite = Yes** is helpful when the selected security category has preexisting process role hierarchy with some objects where names match with the one from EASS. This ensures that the data import process doesn't get blocked because of existing objects and overwrites them. 

6. In **Security relation action** field, select one of the following options:
 - **None** - this option creates user security governance objects.
 - **Clear** - this option clears the existing references between Dynamics 365 finance and operations security objects and user security governance objects.
 - **Create** - this option creates all objects.
7. Select **OK** to start the data import.
8. Refresh the page to verify the data by navigating to the hierarchy node which you selected to restore the XML.
