--- 
title: Security process hierarchy migration
description: Learn how to perform data migration scenarios for user security governance process hierarchy and security categories. 
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

Security governance features offers options for both backing up as XML and restoring from XML in different scenarios. This article focus on specific scenarios of data migration and steps involved for backing up the data, restoring it later and then verifying the restored data. Another related topic to refer is the import process in [Import an existing category](security-category.md#import-an-existing-category). .

## Data migration scenarios

Majorly, there are 2 scenarios where data migration would be needed: 
**Scenario 1:** Migrating data from **Executive automats security setup** to **Security governance**.
**Scenario 2:** Setting up another instance of **Security governance** configurations within the same company.  

## Deep dive into scenario 1 - data migration from EASS to Security governance
1. Go to **System administration** \> **Executive Automats Security Setup** \> **Security category**.
2. In ideal case, categories must already be existing. But, if not, then make sure that security categories are set up already.
3. Select one of the security categories which you desire to migrate and then select **Export**.
4. It will open up a dialog box.
5. Under this dialog, there is a toggle button named **All categories**. If you wish to export all categories, select this toggle button.
6. There is another toggle button named **User security governance format**. You must select this toggle ON to make sure the format of exported file is compatible with **Security governance** feature.
7. Now, under the option **Type**, most suitable options to select are either **EASS** or **EASS + Security configuration**. And, the reason behind this suggestion is that the primary goal of this data migration activity is to re-create security process hierarchy and related security objects in new environment. Without selecting **EASS**, the data migration to new environment will still work but it will not fulfill the goal of this scenario as with selecting EASS, template file will not contain process hierarchy objects.
8. Click **Ok** and it should generate the template file with data in desired format compatible for migration into security governance.
    > [!IMPORTANT]
    > You can back up either a single selected category or all available categories. You can't individually select multiple categories for exporting at the same time without opening the dialog.
    

1. Now, let's go through the process of **restoring security category** downloaded from EASS into the **Security governance** module.
2. Go to **System administration** \> **Security governance** \> **Security category**.
3. In ideal case, either there are no pre-existing security categories on this form OR the existing categories are different from the one which you are trying to **restore** from **EASS**.
4. If the category name alredy exists in security governance, this process will throw a warning and prevent you from moving forward.
5. Click on the button **Restore from XML**. It will open up a dialog box with multiple fields and file browser control.
6. In the file browser control, select the file which you generated in step #8 above. 
7. Under the **Parameters** FastTab, in the **Type** field, there are multiple values. Let me explain each of them so that it will help you make the accurate choice:
   - **User security governance** – This option will restore security category and its related configuration from the **Process hierarchy** page. If multiple process hierarchies, security tasks, security duties, security privileges, entry points mapping with tasks, or security roles are defined under a category, this option will restore only objects that  are limited to security governance module and it will exclude all objects that were created under **Core security configuration**. For example, the hierarchy, tasks, and entry points mapping will be restored but duties, privileges, and roles will be excluded.
    > [!IMPORTANT]
    > If **EASS** was selected while generating the file in step #8 above, you must select this option because they are equivalent to each other. 
    
   - **Security configuration** – This option will restore only the core security objects present in the exported file above. It will not restore the security category and its related configuration from the **Process hierarchy** page. If multiple process hierarchies, security tasks, security duties, security privileges, entry points mapping with tasks, or security roles are defined under a category, this option will restore only objects that were created under **Core security configuration** and it will exclude all objects that were created under security governance **process hierarchy**. For example, the security category, hierarchy, tasks, and entry points mapping will be excluded but duties, privileges, and roles will be restored.
   > [!IMPORTANT]
   > If **EASS** was selected while generating the file in step #8 above, you must **NOT** select this option because they are exclusive of each other.
   
   - **Governance + configuration** – This option will restore the security category and its related configurations from the **Process hierarchy** page as well as under **Core security configuration**. If multiple process hierarchies, security tasks, security duties, security privileges, entry points mappings with task, security roles, and so on, are defined under a category, this option will restore everything that was created under **Core security configuration** and also all objects that are limited to the **Process hierarchy** page. For example, the XML includes everything, such as the hierarchy, tasks, duties, privileges, entry points, and roles.
   > [!IMPORTANT]
   > If **EASS + Security configuration** was selected while generating the file in step #8 above, this option is the most suitable choice because then it will restore everything which you are trying to achieve.

    In the **Security related action** field, select one of the following options:
    - **Create** – Automatically create or push all duties and roles that must be created from the security setup into the publish staging table. The security configuration should show all security objects that were developed by using the security setup and that are ready for publishing.
    - **Clear** – Clear all the security references between user security governance and the Dynamics 365 finance and operations apps security configuration. Every task line that was imported is blank, and you must re-create roles and duties for each line. This option might be helpful when you want to clear off or renew the project.
    - **None** – Move all user security governance security objects that weren't created within the system. If the security objects don't exist, this option might cause complications.
   > [!IMPORTANT]
   > In this specific scenario of data migration, **Create** option is the most suitable choice because then it will restore and publish everything which you are trying to migrate into new environment.
   
8. After making required selections on the dialog box, click the button **OK** to start the restoration process.
9. Upon successful processing, you will get a information message confirming the successful restoration otherwise a warning message will appear explaining the problem occured during the process.
10. The first thing to verify would be security category. You should see the newly restored category on the **Security category** form.
11. To verify the restored process hierarchy and other objects, navigate to **System administration** \> **Security governance** \> **Security process roles maintain**.
12. Select the new category under Security category field.
13. It will load the process hierarchy and underlying objects like security tasks, entry point mapping, duties, privileges and roles.
14. This completes the data migration process. 

## Deep dive into scenario 2 - migration of process hierarchy and related objects for an existing Security category from EASS to Security governance

This scenario is helpful specially in such cases where you already have security category existing between 2 environments and you are trying to migrate the data under that category. With data, it means process hierarchy, security tasks, entry points mapping, duties, privileges and security roles.  

1. Navigate to **System administration** \> **Executive Automats Security Setup** \> **Security Process Roles Maintain**.
2. Select the desired category which you want to export to other environment.
3. Select the process hierarchy node.
4. Under **Process role definition** fast tab, select the **Export** option.
5. It will open up a dialog **Export Executive Automats Security Setup Data**.
6. Make the selection under **Type** field. Each option is explained above. 
> [!TIP]
> In this specific scenario of data migration, **EASS + Security configuration** option is the most suitable choice because then it will restore and publish everything which you are trying to migrate into new environment.
7. You MUST select **User security governance format** option because it will generatge the XML which is compatible with **Security governance** restore process.
8. Click the **OK** button and it should export the XML file ready with data.

Once you are ready with the file, next step would be to import this data into **Security governance**.
1. Navigate to **System administration** \> **Security governance** \> **Security process roles maintain**.
2. As per the expectation, security category should already exist. Select the category and one of the process hierarchy node underneath it.
3. Under the **Role definition** fast tab, click button **Restore from XML**.
4. This should open up the dialog box to restore process role with few configuration options.
5. You will observe an option **Overwrite**. If this is selected ON, it will overwrite any security object under the selected category from the one which is part of the import file from EASS.
> [!TIP]
> Selecting **Overwrite = Yes** is helpful when the selected security category has pre-existing process role hierarchy with some objects where names are matching with the one from EASS. This will ensure that the data import process do not get blocked because of existing objects and it will simply overwrite them. Make sure you are ok with this before seleting this option.
6. Under the **Options** section in **Security relation action** field, select **None**, **Clear**, or **Create**, based on whether you want to create user security governance objects, clear the existing references between finance and operations security objects and user security governance objects, or create all objects.
7. Select **OK** to start the data import. When the action is completed, you receive an appropriate informational message.
8. Refresh the form to verify the data by navigating to the hierarchy node which you selected to restore the XML.
