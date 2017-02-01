---
# required metadata

title: Security Development Tool (AX 2012) | Microsoft Docs
description: This topic describes the user interface of the Security Development Tool.
author: kfend
manager: AnnBe
ms.date: 2015-12-05 17:51:41
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: 51
ms.suite: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 18571
ms.assetid: 2013b8a5-8795-4b9b-9e90-fbbd15f396fe
ms.region: Global
# ms.industry: 
ms.author: kfend

---

# Security Development Tool (AX 2012)

This topic describes the user interface of the Security Development Tool.

**Note:** This is pre-release documentation of a preliminary nature and is subject to change at any time without notice. Microsoft cannot guarantee the accuracy of any information provided herein.

## Overview of the main form
This section describes the controls in the main form.

### Main form

![Security Development Tool Main form](./media/securitydevelopmenttoolmainform.png)

-   **Type** field – The type of security object: **Role**, **Duty**, or **Privilege**.
-   **Name** field – The label of the selected security object.
-   **Refresh** button – Reload permissions for the security object that is currently selected.
-   Tree view – The main menu view for the rich client, Enterprise Portal for Microsoft Dynamics AX, and service operations.

When you select a menu item, web menu item, or service operation, the entry point is selected automatically in the list view. The access level that is shown for a menu is determined by the highest access level that is granted to a submenu item. The order of precedence for access levels, from lowest to highest, is **No Access**, **View**, **Edit**, **Create**, **Correction**, and **Full Control**. For example, in the following figure, if the **All vendors** menu item is granted the **View** access level, and the **Vendors on hold** menu item is granted the **Edit** access level, the parent menus, **Accounts payable**, **Common**, and **Vendors**, are marked with the **Edit** access level.

### Menu access aggregation in tree view

![Security Development Tool Menu Access Aggregation](./media/sdt_menuaggregatedaccesslevel.png) When the level of access to a node in the tree view changes, the node is displayed in bold type. If the level of access to a menu item remains the same, but the level of access to a submenu item changes, the parent menu item is marked with an asterisk (\*). In the following figure, the level of access to **Accounts payable/Setup/Charges/Item charges groups** has been updated from **NoAccess** to **Edit**.

### Changed items

![Security Development Tool Access Level Change](./media/sdtl_treeviewaccesslevelchange.png)

## Shortcut menu options
Use the shortcut menu to interact with entry points in the tree view. ![SecurityDevelopmentTool\_TreeContextMenu](./media/sdt_treecontextmenu.png)

-   **Expand all children** – Expand all subtree items.
-   **Open in current workspace** – Open the linked menu item in the current workspace.
-   **Open in security test workspace** – Open the linked menu item in the **Security test** workspace.
-   **Discover submenu items** – Use Application Object Tree (AOT) metadata to discover entry points that are used in the linked form for the menu item that is currently selected.
-   **Set entry point permissions for current node and expanded subtree items** – Open a guided form, where you can set the access level for the selected entry point and all the expanded subtree items. For more information, see [Define or edit entry point permissions](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/define-or-edit-entry-point-permissions).
-   **Reference duty** – View a list of duties that grant the selected entry point the corresponding access level. You can view the reference duty for the selected security object. This option is available only for roles.
-   **Reference privilege** – View a list of privileges that grant the selected entry point the corresponding access level. You can view the reference privilege for the selected security object. This option is available only for roles and duties.
-   **Open new AOT window** – Open a new AOT window for the selected node.
-   **AOT properties** – Open the AOT properties for the selected node.
-   **Open new AOT window for menu item** – Open a new AOT window for the linked menu item.
-   **AOT properties for menu item** – Open the AOT properties for the linked menu item.

## List view
This section describes the controls on the ribbon of the list view. The list view provides a list of all entry points for your Microsoft Dynamics AX environment. To bulk update the level of access to entry points, you can select multiple rows in the list view. ![Security Development Tool List View](./media/sdt_listcontextmenu.png)
| **Note**                                                                                                                                                                                                                                                |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| When you select an entry point in the list, the entry point is not selected automatically in the tree view. Use the shortcut menu to interact with entry points in the list view. The options resemble the options that are available in the tree view. |

-   **Open the security test workspace** – Open a security test workspace by using the permissions for the selected security object.
-   **Start recording** – When you start the recorder, you can execute business process flows in the current workspace. When a business process flow is completed, you can stop recording and view all entry points that were recorded. This function records only menu items in the rich client.
-   **Load trace file** – Load the entry points that have been traced in Enterprise Portal. For more information, see [Record entry points in Microsoft Dynamics AX Enterprise Portal](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/lifecycle-services/ax-2012/record-entry-points-in-microsoft-dynamics-ax-enterprise-portal).
-   **Save recording** – Save the list of entry points that you just recorded to an .xml file.
-   **Load recording** – Load a list of recorded entry points from an .xml file.
-   **Load additional metadata** – Load additional metadata for all entry points. This data includes the label, layer, and model, and also license information.
-   **Assign organizations** – Assign organizations to the selected role, duty, or privilege in the security test workspace.
-   **Portal security** – Enable security for Enterprise Portal and reports for Microsoft SQL Server Reporting Services while the security test workspace is open. Permissions for the system administration role are disabled while the security test workspace is open. X++ breakpoints are not triggered when this function is enabled.This function is not supported for users who run as the Admin user.
-   **Mark form controls** – Enable this function to display menu items that have **NoAccess** permission on forms.



See also
--------

[Install the Security Development Tool](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/lifecycle-services/ax-2012/install-the-security-development-tool)

[Run the Security Development Tool](https://ax.help.dynamics.com/en/?post_type=incsub_wiki&p=721)

