---
title: Set up security for Dynamics 365 Finance business performance planning
description: This article describes how to set up security for business performance planning.
author: ShielaSogge
ms.author: twheeloc
ms.topic: article
ms.date: 10/31/2024
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-12-03
ms.search.form: 
ms.dyn365.ops.version: 
---

# Set up security for Dynamics 365 Finance business performance planning

The setup of security in the business performance planning app is a critical step in ensuring the security of your organization's data. This article provides an overview of the setup process for role-based security and dimension access.

## Roles

A role defines what operations a user can perform in the planning app and in the planning visuals in Power BI.

Four out-of-box roles are available for planning:

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


>[!Note]
> Users who access business performance planning need to be granted the role App viewer. 

For more information, see [Assigning roles in the Power Platform](/power-platform/admin/assign-security-roles).

## Set up dimension security

Dimension security lets administrators control which data is visible and editable in the planning app, Power BI, and the Excel Add-in.

In the planning app, data access can be granted for a dimension value in a dimension. For example, you create three scenarios: **Budget 2025**, **Budget 2025 Best case**, and **Budget 2025 Worst case**. You want to limit who can view or edit each scenario. As part of the setup, you specify that only John Doe can edit the **Budget 2025 Worst case** scenario, but everyone can view it. In this case, if any user except John Doe opens Power BI (desktop or service) or the Excel Add-in, filters their view to the **Budget 2025 worst case** scenario, and tries to update the amounts, a message informs them that they don't have permission to perform the update.

Dimension security is managed via dimension groups. Dimension groups can contain one or more dimensions. In each dimension, you can select the level of access that should be granted to the dimension values. After a dimension group is defined, users are assigned to it. Only admins or roles that have the **Maintain security** privilege can create dimension groups and assign users to them. For example, you have a dimension group that is named **Executives**. The admin selects to include the following dimensions in it: **Account**, **Company**, **Department**, and **Scenario**. For each of those dimensions, the admin must determine what level of access should be granted to the dimension group. In this example, the dimension group should have read access to all accounts, all companies, all departments, but only the **Budget 2025** scenario. After the setup is completed, the admin assigns the appropriate users to the **Executives** dimension group.

### Create dimension groups

To set security on a dimension, follow these steps.

1. On the **Dimension group** page, select **New group** to open the wizard for creating a new dimension group.
2. Enter a name for the dimension group.
3. Select the dimensions that you want to set access for.

    > [!NOTE]
    > For all visuals except **Table edit**, users need access to at least one dimension value for each dimension in the cube to see the data in Power BI or Excel. A user can be assigned to multiple dimension groups. If dimension groups have overlapping access levels, the user is granted the highest permission level among all the groups.

4. After you finish selecting dimensions, select **Next**. Notice that the **Setup dimension access** step in the **New dimension group** navigation is updated. It now includes the dimensions that you selected in the previous step.
5. Grant access to the selected dimensions. For each dimension, there are three options:

    - **Grant full access to all dimension values** – Select this option if users should automatically get read and write privileges to all existing dimension values and any new dimension values that are created in the future.
    - **Grant read-only access to all dimension values** – Select this option if users should automatically get read privileges to all existing dimension values and any new dimension values that are created in the future.
    - **Grant row-level access** – If you select this option, four other options become available:

        - **Grant full access** – Select this option if users should automatically get read and write privileges to all existing dimension values, but not to any dimension values that are created in the future. Read and write privileges to those dimension values must be explicitly granted.
        - **Grand read-only access** – Select this option if users should automatically get read privileges to all existing dimension values, but not to any dimension values that are created in the future. Read privileges to those dimension values must be explicitly granted.
        - **Revoke all access** – Select this option to remove any access from the user. In this case, the user can't view or edit the dimension value.

            > [!NOTE]
            > For all visuals except **Table edit**, users need access to at least one dimension value for each dimension in the cube.

            - **Row level access** – For each value in the dimension, read or edit privileges can be granted at the line level. For example, you might want users to see and act on the **Budget 2025** scenario only. In this case, unmark the **Budget 2025 best case** scenario for reading and editing. For **Row level access** to work, configure Semantic model data source credentials:
                        <ul><li> Log into Power BI with a user who has the authority to create a dashboard (Administrator or power user).</li><li> In the Power BI workspace, select the semantic model.</li><li> Go to **Settings** > **Data source credentials** > **Edit credentials**. </li><li> Select the **Report viewers can only access this data source with their own Power BI identities using direct query** checkbox. </li><li> Click **Sign in** and sign in as a contributor user and refresh the dimension. The dimension should display the rows that aree selected in business performance planning.</li></ul> 
          
> [!IMPORTANT]
> By default, only the user who creates a new dimension value can see it, unless the **Grant full access to all dimension values** or **Grant read-only access to all dimension values** option is selected for the dimension group. Other users can see the dimension value only if read or write access to the dimension value is granted to them.

6. After you finish setting dimension access for all the dimensions in the dimension group, you can review your changes on the **Summary** page.

    If the dimension access is set to **Grant full access to all dimension values**, the summary shows **All** for the dimension values, followed by **Full access**. If the dimension access is set to **Grant read-only access to all dimension values**, the summary shows **All** for the dimension values, followed by **Read-only**. If the dimension access is set to **Grant row-level access**, each dimension value that the user has access to is listed, followed by the access type (either **Full access** or **Read-only**).


### Edit dimension groups

To edit a dimension group, follow these steps.
1. On the **Dimension groups** page, select the dimension group that must be edited.
2. Select **Edit group**.
3. The dimensions in the dimension group are shown on the left side of the page. Add new dimensions to the dimension group, delete existing dimensions, or update the access options for existing dimensions. If you add a new dimension or edit an existing dimension in a dimension group, there are three access options:

    - Grant full access to all dimension values
    - Grant read-only access to all dimension values
    - Grant row-level access

    For more information, see the [Create dimension groups](#create-dimension-groups) section earlier in this article.

When you add a new dimension to a dimension group, it's added to the bottom of the dimension list on the left side of the page. By default, the dimension access is set to **Grant row-level access**, and no records are selected. When you delete an existing dimension from a dimension group, any associated user access to the dimension is removed.

### Manage users and dimension groups

After a dimension group is created, you can assign users to it. You can also remove users from the group and view the users who are assigned to it.

#### Assign users to a dimension group

To assign users to a dimension group, follow these steps.
1. Go to the **Dimension group** list, and select the dimension group that you want to work with.
2. Select **Users**, and then select **Assign**.
3. In the list of users who can be assigned to the selected dimension group, select a user to assign. You can also select multiple users to assign all of them to the dimension group at the same time.

    > [!NOTE]
    > The user list is filtered so that it shows only users who have access to the `msdyn_xpnadimension` table.

Alternatively, follow these steps.
1. Open the **Users list** page, and select a user.
2. Select **Manage dimension groups**.
3. A check mark appears next to the name of each dimension group that the selected user has access to. Select the checkbox next to the name of the dimension group that you want to assign the user to, and then select **OK**.

#### Remove users from a dimension group

To remove users from a dimension group, follow these steps.
1. Go to the **Dimension group** list, and select the dimension group that you want to work with.
2. Select **Users**, and then select **Remove**.
3. In the list of users who are currently assigned to the selected dimension group, select a user to remove. You can also select multiple users to remove all of them from the dimension group at the same time.

Alternatively, follow these steps.
1. Open the **Users list** page, and select a user.
2. Select **Manage dimension groups**.
3. A check mark appears next to the name of each dimension group that the selected user has access to. Clear the checkbox next to the name of the dimension group that you want to remove the user from.

#### View user/dimension group assignments

To view the list of users who are currently assigned to a dimension group, follow these steps.
1. Go to the **Dimension group** list, and select the dimension group that you want to work with.
2. Select **Users**, and then select **View**.

To view the list of dimension groups that a user is currently assigned to, follow these steps.
1. Open the **Users list** page, and select a user.
2. Select **View access**. The dimension groups that the user has access to are shown on the left side of the page, and the dimension access details are shown on the right side.

In the **Dimension group details** section, the dimension values are shown below the dimension, and the access level is shown to the right of the dimension values.

- If the dimension value is shown as **ALL**, the user has access to all dimension values that currently exist. The user will also have access to any new dimension values that are created in the future.
- If the dimension value is shown as a list of dimension values, the user has access to the dimension values that are listed. However, the user won't have access to dimension values that are created in the future.

The user can have two types of access to dimension values: read-only access or full access. Full access allows the user to create, update, or delete a dimension value.

> [!NOTE]
> A dimension value can't be deleted if it already exists in a cube.

### Important tips

- A user's role determines whether that user can create new dimensions. For example, a power user can create new dimensions, but a contributor can't. To create dimensions, users need the **Maintain dimensions** privilege.
- For all visuals except **Table edit**, users need access to at least one dimension value for each dimension in the cube.
- By default, only the user who creates a new dimension value can see it, unless the **Grant full access to all dimension values** or **Grant read-only access to all dimension values** option is selected for the dimension group. Other users can see the dimension value only if read or write access to the dimension value is granted to them.
- If dimensions already exist when new users are added, the new users can't see any data in the dimensions until they're assigned to a dimension group.
- Users can be assigned to multiple dimension groups. If those groups contain some of the same dimensions, the user is granted the highest privilege that is set for the dimensions among all the groups.
