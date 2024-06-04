---
title: Set up security for Microsoft Dynamics 365 Finance business performance planning 
description: This article describes how to set up security for business performance planning.
author: ShielaSogge
ms.author: twheeloc
ms.topic: article
ms.date: 06/04/2024
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-12-03
ms.search.form: 
ms.dyn365.ops.version: 
---

# Set up security for Microsoft Dynamics 365 Finance business performance planning 

The setup of security in the business performance planning app is a critical step in ensuring the security of your organization’s data. This article provides an overview of the setup process for role-based 
security and dimension access.

## Roles
A role defines what operations a user can perform within the planning app and within the planning visuals within Power BI.
There are four out of the box roles available for planning:
 - Business Performance Planning Administrator
 - Business Performance Planning Power User
 - Business Performance Planning Contributor
 - Business Performance Planning Viewer

The planning administrator has the following privileges:
 - Maintain cubes
 - Maintain dimensions
 - Maintain security
 - Read data
 - Update cube data
 - Update dimension data

The planning power user has the following privileges:
 - Maintain cubes
 - Maintain dimensions
 - Read data
 - Update cube data
 - Update dimension data

The planning contributor has the following privileges:
 - Read data
 - Update cube data
 - Update dimension data

The planning viewer has the following privileges:
 - Read data

For more information, see [Assigning roles in the Power Platform](/power-platform/admin/assign-security-roles).

### Set up dimension security

Dimension security lets administrators control which data is visible and editable in the planning app, Power BI, and the Excel Add-in. 
Within the planning app, data access can be granted for a dimension value within a dimension. For example, you may have created the following scenarios: Budget 2025, Budget 2025 Best case, Budget 2025 Worst case.
You can limit who has the ability to view or edit each scenario. 
For example, you may say that only John Doe can edit the Budget 2025 Worst case scenario, but everyone can view the scenario. This means that when a user other than John Doe navigates to Power BI (desktop or 
service) or the Excel Add-in, and they filter their view to the Budget 2025 worst case scenario, they will receive a message if they attempt to update the amounts indicating that they don’t have permission to do
so.
Dimension security is managed via dimension groups. Dimension groups can contain one or more dimensions. Within each dimension, the user can select what level of access should be granted to the dimension values.
Once a dimension group has been defined, users are assigned the dimension group. Only Admins or roles with the Maintain security privilege can create dimension groups and assign users to the dimension group. 
For example, there might be a Dimension group called Executives. Within the dimension group the admin has selected to include the following dimensions: Account, Company, Department, and Scenario. For each of the
dimensions listed above, the admin would need to determine what level of access should be granted to that dimension group. For example, the dimension group would have read access to All accounts, all companies, 
all departments, and only the Budget 2025 Scenario. Once the setup is complete, the admin would assign the appropriate users to the Executive dimension group.

### Create dimension groups
To set security on a dimension, follow these steps: 
1. Go to the **Dimension group** page, select **New group**. This starts the wizard for creating a new dimension group.
2. Add a name for the dimension group.
3. Select the dimensions that you want to set access for.

>[!Note]
>For any visual other than Table edit, users need access to at least one dimension value for each dimension that is in the cube, to be able to see the data in Power BI or Excel. A user can be assigned to multiple
> dimension groups. If access levels overlap between dimension groups, the user is granted the highest permission between the two groups.

4. After selecting the dimensions, select **Next**. Notice that the **Setup dimension access** step in the **New dimension group** navigation is updated to include the dimensions that were selected on the
previous step.
For each dimension, there are three options for granting access:
•	Grant full access to all dimension values - select this option for users to automatically get read and write privileges to all existing dimension values and any new dimension values created in the future.
•	Grant read-only access to all dimension values - select this option for users to automatically get read privileges to all existing dimension values and any new dimension values created in the future.
•	Grant row-level access - when this option is selected, four additional options are available:
        •	Grant full access – Select this option for users to get read and write privileges to all existing dimension values, but they won't have read and write privileges to any dimension values created in the
                              future unless specifically granted. 
        •	Grand read-only access - Select this option for users to automatically get read privileges to all existing dimension values, but they won't have read privileges to any dimension values created in the
                                   future unless specifically granted
        •	Revoke all access- This removes any access from the user. Wsers aren't able to view or edit the dimension value. Note: For any visual other than Table Edit, users need access to at least one dimension
                             value for each dimension that is in the cube.
        •	Row level access - Read or Edit privileges can be granted at a line level for each value in the dimension. For example, you may want users to see and act on the Budget 2025 scenario only. In this
                             instance, the Budget 2025 best case scenario would be unmarked for reading and editing.
 
	
>[!Important]
> When a new dimension value is created, only the user that created the dimension value can see the value by default, unless Grant full access to all dimension values or Grant read only access to all dimension
> values is selected for the dimension group. To allow other users to see the dimension value, the other users must be given read or write access to the dimension value.

Once the dimension access has been set for all dimensions in the dimension group, the user can review their changes.
In the **Summary** page, if a dimension access is **Grant full access** to all dimension values, the summary will display **All** for the dimension values, followed by **Full access**.
If a dimension access is **Grant read-only** access to all dimension values, the summary will display **All** for the dimension values, followed by **Read-only**.
If a dimension access is **Grant row level** access, each dimension value that the user has access is listed, followed by the access type of **Full access**, or **Read-only**.

For example, in the screenshot below the Scenario dimension has Grant full access to all dimension values, the Status dimension has Grant read-only access to all dimension values, and the YearMonth dimension has row level access selected, which displays all the dimension values the user has either read or write access to.

 

### Edit a dimension group
To edit a dimension group, follow these steps:
1. Go to **Dimension groups** page, select the dimension group that needs to be edited,
2. Select **Edit group**.
3. After **Edit group** is selected, the dimensions contained in the dimension group is displayed on the left-hand side of the page. When editing a dimension group, a user can **Add a new dimension**,
delete a dimension, or update the existing dimensions’ access options. When adding a dimension or editing an existing dimension within a dimension group, there are three options:  
•	Grant full access to all dimension values
•	Grant read \-only access to all dimension values
•	Grant row-level access

For more information, see the **Creating dimension group section** above.

When adding a new dimension, the new dimension is added to the bottom of the dimension list on the left-hand side of the page. 
It defaults to **Grant row-level access** with no records selected.  When deleting a dimension from the dimension group, any associated user access to the dimension will be removed. 

### Managing users and dimension groups
Once the dimension group has been created, users can be assigned to the dimension group by navigating to the **Dimension group** list and select the **Dimension group**. 
After selecting the dimension group, select **Users** select **Assign**. This provides a list of users to assign to the dimension group. Multiple users can be selected to assign to a dimension group.

>[!Note]
>The users that are displayed in the user list are filtered to a list of users that have access to the msdyn_xpnadimension table.  

To remove a user from a dimension group, select the **Dimension group**, select **Users**, and select **Remove**. This provides a list of users currently assigned to the dimension group. You can select multiple
users to remove at once.

To view users associated with the dimension group, go to **Dimension group**, select **Users**, and select **View**. This provides a list of users currently assigned to the dimension group.

Alternatively, you can navigate to the **Users list** page, select a user, and select **Manage dimension groups**. Dimension groups that the user has access to will have a checkmark next to the dimension group 
name. To assign a dimension group to a user, select the checkmark next to the **Dimension group name**, and select **OK**. 
To remove a dimension group from a user, clear the checkmark next to the **Dimension group**.

To see all of the dimension groups that a user is assigned to, go to the **Users list** page, select a user and select **View access**. The dimension groups that the user has access displays on the leftside, 
with the dimension access details displayed on the right side. 

Within the **Dimension group details** section, the dimension values are displayed below the dimension, and the access level is displayed to the right of the dimension values. 

If the dimension value displays as **ALL**, the user has access to all dimension values that exist and has access to any new dimension values in the future. 
If the dimension value displays a list of dimension values, the user has access to the dimension values that are listed but won't have access to dimension values created in the future.
The user can have two types of access to dimension values – read only or full access. Full access allows the user to create, update or delete a dimension value. 
Note, a dimension value cannot be deleted if it already exists in a cube.


### Important tips
•	A user’s role determines whether they can create new dimensions. For example, a power user can create new dimensions, but a contributor can't. To allow users to create dimensions, the users need the **Maintain
dimensions** privilege.
•	For any visual other than **Table edit**, users need access to at least one dimension value for each dimension that is in the cube.
•	When a new dimension value is created, only users that created the dimension value can see the value by default, unless **Grant full access** to all dimension values or **Grant read only** access to all 
dimension values is selected for the dimension group. To allow other users to see the dimension value, the other users must be given read or write access to the dimension value.
•	As new users are added, and dimensions already exist, the users can't see any data in the dimensions until they are assigned to a dimension group.
•	If users are assigned to multiple dimension groups and the groups contain some of the same dimensions, the user will be granted the highest privilege set for the dimension between the groups. 

