---
# required metadata

title: Define or edit entry point permissions (AX 2012)
description: 
author: kfend
manager: AnnBe
ms.date: 2015-12-04 23 - 21 - 12
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 18211
ms.assetid: 1e7c9c30-7418-4f4a-93a3-2d043073e429
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Define or edit entry point permissions (AX 2012)



**Note:** This is pre-release documentation of a preliminary nature and is subject to change at any time without notice. Microsoft cannot guarantee the accuracy of any information provided herein.

## Edit entry point permissions
This section lists the procedures that you can use to define or edit entry point permissions.

### Edit permissions

1.  In Microsoft Dynamics AX, click **System Administration** &gt; **Setup** &gt; **Security** &gt; **Security entry point permissions**.
2.  In the **Name** field, enter or select a role.
3.  In the tree view, select the entry point to modify, right-click, and then select **Discover submenu items**. The submenu items are displayed.
4.  Right-click the subnode to modify, and then select **Set entry point permissions for current node** and expanded subtree items. The **Set entry point permissions** window opens.
5.  In the **New access level** field, select the new access level for the entry point, and then click **Next**. The dialog box expands to include the whole security tree for the role. This security tree includes all duties, privileges, and subroles that are referenced. Subroles, duties, and privileges that grant the selected entry point are displayed in bold type. Therefore, you can quickly identify which privileges have to be updated in the role.
6.  In the tree, expand one of the bold privileges. The entry point types is updated to show the access that the privilege grants to each entry point.
7.  To update the permissions on the privilege, right-click the privilege, and then select **Apply entry point access levels to selection**. In the **Security entry point permissions** window, the **Access level** column displays the new access level, and the **Previous access level** column displays the original access level.
8.  Review any other roles that use the parent roles, parent duty, and privilege. Important: Complete this step so that you do not unintentionally update other roles.

## Test entry point permissions
To verify that you have correctly changed permissions, you can use the Security test workspace. The Security test workspace opens an instance of the Microsoft Dynamics AX client by using the rights of the user role that you modified.

### Open the Security test workspace

1.  In the **Security entry point permissions** window, click **Open the security test workspace**. Click **Yes** to dismiss the warning.
2.  Verify that access to the Microsoft Dynamics AX features changed in the manner that you intended.
3.  Close the Security test workspace.

## View the user licenses for a role
You can use the Security Development Tool to view the user license that is associated with a role. You can also see how changes to entry point permissions affect user licensing. When the tool loads or updates permissions, it computes the effective type of user license both for each entry point that is granted by the selected object and for the object itself. When the configuration key for an entry point is disabled, the user license for the entry point is not retrieved. The User Client Access License (CAL) types are Self Serve User, Task User, Functional User, and Enterprise User. User CALs are associated with specific menu items, which are objects that have associated actions. For any object, the association with a User CAL is calculated based on the values of the **ViewUserLicense** and **MaintainUserLicense** properties of the object. **ViewUserLicense** is used only for view permissions, whereas **MaintainUserLicense** is used for any larger set of permissions. For more information, see the [Microsoft Dynamics AX 2012 Licensing Guide](./media/dynamics_ax_2012_licensing_guide-customeredition.pdf).

### View the user license for a role

1.  Open the Security Development Tool.
    -   To open the tool in the client, click **System administration** &gt; **Setup** &gt; **Security** &gt; **Security entry point permissions**.
    -   To open the tool in the Application Object Tree (AOT), right-click any role, duty, or privilege, and then select **Add-Ins** &gt; **Security tools** &gt; **Security Development Tool**. The **Security Development Tool** window opens.

2.  Select the role and entry point to modify, and then click **Load additional metadata**. Additional data appears. This data includes the **Current user license type** field and additional columns.
3.  Scroll to the right until you can see the value in the **Effective user license** column, and until you can see whether the **Config Key Enabled** column is selected. Note the **Current user license type** value and the **Effective user license required value** before you make any changes.
4.  Change the entry point permissions to the permissions that are required for your business.
5.  Select the role and entry point that you modified, and then click **Load additional metadata**. Review whether the **Current user license type** and **Effective user license** values changed. If these licensing values changed, you may have to purchase additional licenses.

## Example: Change permissions for customer responsibilities to View access
The following example shows how to use the guided form to update the entry point permissions for the Sales Clerk role. On the Sales Clerk role, the access role for customer responsibilities is currently **Full control**. You want to restrict this to **View** access.

1.  In Microsoft Dynamics AX, click **System Administration** &gt; **Setup** &gt; **Security** &gt; **Security entry point permissions**.
2.  Select the **Sales Clerk** role.
3.  Select the **Rich client** &gt; **Accounts receivable** &gt; **Common** &gt; **Customers** &gt; **All customers** node.
4.  Right-click, and then select **Discover submenu items**.
5.  Right-click the **–Responsibilities –** (Menu item **display.smmResponsibilities**) subnode, and then select **Set entry point permissions for current node and expanded subtree items**.
6.  In the **Set entry point permissions** window, in the **New access level** field, select the new access level for the entry point. In this example, select **View**. In this example, three duties that are referenced in the **Sales Clerk** role must be investigated: **CaseSalesCasesMaintain**, **CustCustomerMasterInquire**, and **smmBusinessRelationsMaintain**.
7.  In the tree, select the **TradeSalesClerk** &gt; **CaseSalesCasesMaintain** node. You can see that the **CaseDetailMainMaintain** privilege grants the **smmResponsibilities** entry point **Full Control** access.
8.  To update the permission directly on the privilege, right-click **CaseDetailMainMaintain**, and then select **Apply entry point access levels to selection**.
9.  Review any other roles that use the parent roles, parent duty, and privilege. **Important:** Complete this step so that you do not unintentionally update other roles. When you select **TradeSalesClerk** &gt; **CaseSalesCasesMaintain**, you can see that the duty is referenced in the **Customer service representative** and **Sales representative** roles. To avoid updating those roles, right-click the duty, and then select **Duplicate selection** and then remove original.
10. You are prompted to enter a new AOT name, label, and description for the duty. Click **OK** to continue. The **CaseSalesCasesMaintain** duty is no longer referenced by the **Sales Clerk** role, and a reference to the duplicated duty is added. You can now safely modify the duty without affecting any other roles. The same process can be applied before you update the **CaseDetailMainMaintain** privilege.
11. Review the entries in the **Current access level** column to verify whether the role now grants the new permission to the entry points.
12. Use the **Security test** workspace to validate the permissions.
13. Use **Load additional metadata** to validate whether licensing requirements have changed.


