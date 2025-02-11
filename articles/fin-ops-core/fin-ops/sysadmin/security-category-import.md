--- 
title: Security category export/import
description: Learn about how you can utilize the backup and restore processes available on Security category form to do bulk operations related to category. 
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

Security categories offers both backup as XML and restore from XML options. For more information about the import process, see [Set up security categories](security-category.md#import-an-existing-category). This article will describe various scenarios that the system administrtor can perform.

## Backup as XML
1. Go to **System administration** \> **Security governance** \> **Security category**.
2. Make sure you have setup some security categories prior of doign the backup.  
3. Select the **Security category** and click **Backup as XML**. 
> [!IMPORTANT] 
> You can either backup the selected category or **all** categories available. Partial selection of the list for backup isn't allowed.  
4. The action opens a new dialog. Expand the **Parameters** fasttab.
5. Under **Type** dropdown, there are three options:
 - **User security governance** - This option generates complete XML of security category and it's related configuration from the **Process hierarchy** page. If a category has multiple hierarchy, tasks, duties, privileges, entry points, or roles defined under it, this option includes only objects created on the **Process hierarchy** page. It'll exclude all objects created under the **Core security configuration**. For example: **Hierarchy, tasks, entry points** are included and **duties, privileges, roles** are excluded in the XML. 
 - **Security configuration** - This option generates complete XML of security category and it's related configurations only from **Core security configuration**. If a category has multiple hierarchies, tasks, duties, privileges, entry points, roles etc. defined under it, this option includes only objects which are created on the core security configuration and exclude all objects limited to the **Process hierarchy** page. For example: **duties, privileges, roles** are included in the XML and **hierarchy, tasks, entry points** are excluded in the XML.
 - **Governance + configuration** - This option generates complete XML of security categories and it's related configurations from both the **Process hierarchy** page and **Core security configuration** perspective. If a category has multiple hierarchies, tasks, duties, privileges, entry points, roles etc. defined under it, this option includes everything created on the core security configuration as well as all objects limited to the **Process hierarchy** page. For example: everything including **hierarchy, tasks, duties, privileges, entry points, roles**.
6. Select **Types** and click **OK** button.
7. This prompts you to save an **XML** file on your local browser. 

## Restore from XML
1. Go to **System administration** \> **Security governance** \> **Security category**.  
2. Click **Restore from XML** and a dialog opens.
3. Within this dialog, there are multiple selections: **File, Type, Security related action**. 
4. In the file browse option, enter a path to a valid format **XML** file.
5. Select the accurate **Type** and **Security related action** values.
 - **Security related action** is applicable when **Type = User security governance**.
 - **Create** - Restore and publish XML of security category
 - **Clear** - Restore XML of security category
 - **None** - Restore XML of security category 

## Bulk create proceess hierarchy
System administrators can use **Restore from XML** to quickly create entire hierarchy under a **security category**. For this, the XML file should be generated in the right format with desired hierarchy under a category. It can include multiple processes in a hierarchy tree, security tasks under each process (optional). Though generating the XML is manual process, it can still be much faster approach of creating the hierarchy if accurate template of the XML is followed. Mostly, creating a template is copy-paste with right metadata. Make sure each category has unique name.    
> [!TIP] 
> Create one category through user interface and then use the **Backup as XML** feature to download initial file. Use this file to modify and create new desired category with hierarchy. 
