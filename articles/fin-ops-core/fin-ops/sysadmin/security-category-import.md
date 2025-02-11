--- 
title: Security category export/import
description: Learn about how you can utilize the backup and restore processes available on Security category form to do bulk operations related to category. 
author: saurabhgupta
ms.author: saurabhgupta
ms.topic: how-to
ms.date: 02/07/2025
ms.custom:
ms.reviewer: johnmichalak 
audience: Application User  
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: SysSecSegregationOfDutiesRule
ms.dyn365.ops.version: Version 7.0.0 
---

# Security category export/import

[!include [banner](../../../finance/includes/banner.md)]

Security category offers both backup as XML and restore from XML options. There is a brief explaination about **import** proecss on the **Set up security categories** article but in this article, we are going to dive deep into various scenarios **system administrtor** can perform on this form.

## Backup as XML
1. Go to **System administration** \> **Security governance** \> **Security category**.
2. Make sure you have setup some security categories prior of doign the backup.  
3. Select the desired **security category** and click **Backup as XML**. 
> [!IMPORTANT] 
> You can either backup the selected category or **all** categories available. Partial selection of the list for backup is not allowed.  
4. Above action will open up the new dialog. Here, expand the **Parameters** fast tab.
5. Under **Type** dropdown, there are 3 choices available:- **User security governance, Security configuration & Governance + Configuration**.
> [!IMPORTANT] 
> **User security governance** - This option generates complete XML of security category and it's related configuration only from the **Process Hierarchy form**. Meaning, if a category has multiple hierarchy, tasks, duties, privileges, entry points, roles etc. defined under it, this option will **include** only objects which are created on the process hierarchy form and it will **exclude** all objects which are created under **core security configuration**. For example: **Hierarchy, tasks, entry points** will be included and **duties, privileges, roles** will be excluded in the XML. 
> **Security configuration** - This option generates complete XML of security category and it's related configurations only from the **core security configuration** perspective. Meaning, if a category has multiple hierarchies, tasks, duties, privileges, entry points, roles etc. defined under it, this option will **include** only objects which are created on the core security configuration and it will **exclude** all objects which are limited to the **process hierarchy** form. For example: **duties, privileges, roles** will be included in the XML and **hierarchy, tasks, entry points** will be excluded in the XML.
> **Governance + Configuration** - This option generates complete XML of security category and it's related configurations from both the **Process Hierarchy form** & **core security configuration** perspective. Meaning, if a category has multiple hierarchies, tasks, duties, privileges, entry points, roles etc. defined under it, this option will **include** everything which are created on the core security configuration as well as all objects which are limited to the **process hierarchy** form. For example: Everything including **hierarchy, tasks, duties, privileges, entry points, roles**.
6. Select on the **Types** and click **OK** button.
7. This will prompt you to save an **XML** file on your local browser. 

## Restore from XML
1. Go to **System administration** \> **Security governance** \> **Security category**.  
2. Click **Restore from XML** and it will open a dialog.
3. Within this dialog, there are multiple selections like **File, Type, Security related action**. 
4. In the file browse option, provide path to a valid format **XML** file.
5. Select the accurate **Type** and **Security related action** values.
> [!IMPORTANT] 
> **Security related action** is applicable when **Type = User security governance**. 
> **Create** - This option will restore and publish XML of security category
> **Clear** - This option will restore XML of security category 
> **None** - This option will restore XML of security category 

## Using this option to bulk create Proceess Hierarchy
System administrator can use the **Restore from XML** feature to also quickly create entire hierarchy under a **security category**. For this, the XML file should be generated in the right format with desired hierarchy under a category. It can include multiple processes in a hierarchy tree, security tasks under each process (optional). Though generating the XML is manual process, it can still be much faster approach of creating the hierarchy if accurate template of the XML is followed. Mostly, creating a template is copy-paste with right metadata. Make sure each category has unique name.    
> [!TIP] 
> Tip which we can suggest is that create one category through user interface and then use the **Backup as XML** feature to download initial file. Use this file to modify and create new desired category with hierarchy. 
