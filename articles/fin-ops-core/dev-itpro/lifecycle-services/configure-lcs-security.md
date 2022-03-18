---
# required metadata

title: Configure Lifecycle Services (LCS) security
description: This topic explains how security in Microsoft Dynamics Lifecycle Services (LCS) is controlled at both the organization level and the project level.
author: AngelMarshall
ms.date: 03/15/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 6154
ms.assetid: 79396ff8-538f-4f6f-80d0-898fc5618fb5
ms.search.region: Global
# ms.search.industry: 
ms.author: tsmarsha
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Configure Lifecycle Services (LCS) security

[!include [banner](../includes/banner.md)]

Security in Microsoft Dynamics Lifecycle Services (LCS) is controlled at both the organization level and the project level. Not all members of an organization have access to all projects. Additionally, the members of a project might not all be members of the same organization. <br>

Currently, users can sign in by using the Microsoft Azure Active Directory (Azure AD) credentials that they created in the Microsoft 365 portal when they signed up. Users who are administrators for their organization in Azure AD will be administrators in Lifecycle Services (LCS). 

Project-level access to LCS is by invitation. You can invite members of your organization to be project owners and team members. Additionally, you can invite users who aren't part of your organization, and who don't have accounts in Azure AD to be team members.

> [!IMPORTANT]
> We strongly recommend that you manage all users within your company at the organization level. Additionally, you help ensure that users can access the benefits that are available to your organization.

## Organizational roles
There are three types of organizational roles in LCS:

- Admin
- Contributor
- Delegated admin

### Organization admin
At the organization or tenant level, anyone who has the Global Administrator role in Azure AD automatically becomes an organization admin when they sign in to LCS. These admins can then promote other users who are currently contributors to admins. Admins have unique capabilities. For example, they can add themselves as a project owner to any project that is owned by their tenant, even if they weren't previously part of that project.

![Message in LCS that states that organization admins can add themselves to any project.](media/OrgAdminProjectInject.png "Message in LCS that states that organization admins can add themselves to any project")

In addition, admins can create additional LCS implementation projects by following the steps in [Create multiple LCS projects](../../fin-ops/get-started/implement-multiple-projects-aad-tenant.md#create-multiple-lcs-projects).

### Organization contributor
Contributors are other users from your Azure AD tenant, but they don't have admin capabilities. Contributors can create projects. They can also create the first implementation project if they are the first user of their tenant to sign in, and if they do so after the purchase of applicable Finance and Operations apps licenses.

### Delegated admin
The delegated admin role is identical to the admin role, except the user is from a Microsoft partner tenant and has an established relationship with the customer organization. The delegated admin can sign in on behalf of the customer, and can perform required operations and provide required support.

## Manage LCS organization users
Only an administrator can manage users. Follow these steps.

1.  In PartnerSource Business Center (PSBC) or Azure AD, associate all the users in your organization who require access to LCS with your organization. Users might have to wait up to two business days before they can sign in to LCS.
2.  Add your users to the appropriate projects in LCS.

### Invite a user to an LCS project

1.  Sign in to [LCS](https://lcs.dynamics.com/).
2.  Select the project to add the user to.
3.  Select the **Project users** tile, and then, on the **Project users** page, select the plus sign (**+**).
4.  Enter the user’s email address, select the correct security role, and then select **Invite**.

> [!NOTE]
> For implementation projects, you can select the implementation role for the invited user. If you set **Allow FastTrack to contact** to **Yes**, then Microsoft FastTrack team may reach out to you based on your implementation role and the stages of the implementation project.   


## Configuring project security
You can invite users from inside or outside your organization to join your project as users. The following table describes the roles that are available for users.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Role</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Project owner</td>
<td>Members of this role have access to all tools in LCS, can add other users in any role, and can delete the project.</td>
</tr>
<tr class="even">
<td>Environment manager</td>
<td>Members of this role have access to all tools in LCS and can manage cloud-hosted environments.</td>
</tr>
<tr class="odd">
<td>Project team member</td>
<td>Members of this role have access to all tools in LCS but can&#39;t manage cloud-hosted environments.</td>
</tr>
<tr class="even">
<td>Project team member (prospect)</td>
<td>Members of this role have limited access to all tools in an LCS project. Prospects are users who have been added to a project, but who don&#39;t have an account in VOICE or an Azure AD account. You can identify that a user is a prospect, because <strong>prospect</strong> is listed as the organization.</td>
</tr>
<tr class="odd">
<td>Operations user</td>
<td>Members of this role have access to the following tools in LCS:
<ul>
<li>System diagnostics</li>
<li>Issue search</li>
<li>Cloud-powered support</li>
<li>Updates</li>
<li>Cloud-hosted environments</li>
</ul></td>
</tr>
</tbody>
</table>

After you've configured security for one project, you can import the users to another project.

## Configure implementation roles 
If you have an implementation project, you will have the option to specify project user's implementation roles. For more information, see [Roles in a Dynamics 365 implementation](/learn/modules/get-started-implementation-project/01-2-roles).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
