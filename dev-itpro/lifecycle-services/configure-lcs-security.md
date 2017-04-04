---
# required metadata

title: Configure Lifecycle Services security
description: Security in Microsoft Dynamics Lifecycle Services (LCS) is controlled at both the organization level and the project level. Not all members of an organization have access to all projects. Additionally, the members of a project might not all be members of the same organization.
author: RobinARH
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 6154
ms.assetid: 79396ff8-538f-4f6f-80d0-898fc5618fb5
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Configure Lifecycle Services security

Security in Microsoft Dynamics Lifecycle Services (LCS) is controlled at both the organization level and the project level. Not all members of an organization have access to all projects. Additionally, the members of a project might not all be members of the same organization.

For the current version of Microsoft Dynamics 365 for Operations, users can sign in by using the Microsoft Azure Active Directory (Azure AD) credentials that they created in the [Microsoft Office 365 portal](http://go.microsoft.com/fwlink/?LinkID=324287) when they signed up. Users who are administrators for their organization in Azure AD will be administrators in Microsoft Dynamics Lifecycle Services (LCS). For Microsoft Dynamics AX 2012, organization-level access to LCS is controlled by the association of a person’s Microsoft ID with an organization in CustomerSource or PartnerSource. Therefore, users of CustomerSource or PartnerSource automatically have access to their organization’s workspace in LCS, and can view all projects that they have been invited to participate in. Users who are administrators for their organization in CustomerSource and PartnerSource will be administrators in LCS. Although an administrator can invite people who don’t have CustomerSource or PartnerSource credentials to be members of an organization in LCS, we don't recommend this approach. People who are invited to be members of an LCS organization aren't provided with credentials in CustomerSource or PartnerSource. Project-level access to LCS is by invitation. You can invite members of your organization to be project owners and team members. Additionally, you can invite users who aren't part of your organization, and who don't have accounts in Azure AD or CustomerSource or PartnerSource, to be team members. **Important:** We strongly recommend that you manage all users within your company at the organization level. In that way, you help guarantee that their relationship with your organization is correct in CustomerSource, PartnerSource, and Azure AD. Additionally, you help guarantee that users can access the benefits that are available to your organization.

## Manage LCS organization users
Only an administrator can manage users. Follow these steps.

1.  In CustomerSource, PartnerSource, or Azure AD, associate all the users in your organization who require access to LCS with your organization. Users might have to wait up to two business days before they can sign in to LCS.
2.  Add your users to the appropriate projects in LCS.

### Invite a user to an LCS project

1.  Sign in to [LCS](http://lcs.dynamics.com/en//t_blank).
2.  Click the project to add the user to.
3.  Click the **Project users** tile, and then, on the **Project users** page, click the plus sign (**+**).
4.  Enter the user’s email address, select the correct security role, and then click **Invite**.

## Working with CustomerSource and PartnerSource
The information in this section is intended to help you access CustomerSource or PartnerSource.

### Signing in to CustomerSource or PartnerSource

Visit the [CustomerSource sign-in page](https://mbs.microsoft.com/customersource/), and enter the user name and password for your Microsoft account (previously known as Windows Live ID) to access the site. If you don't have access to your organization’s CustomerSource account, follow the steps on the [How to sign in to CustomerSource](http://www.microsoft.com/dynamics/customer/en-us/access-customersource/default.aspx/t_blank) page.

### Determining the administrator for your organization in CustomerSource or PartnerSource

If you don’t know your CustomerSource administrator, or if your organization doesn’t have a CustomerSource administrator, send an email message to [itmbssup@microsoft.com](http://itmbssup@microsoft.com) for help.

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
<td>Members of this role have access to all tools in LCS but can't manage cloud-hosted environments.</td>
</tr>
<tr class="even">
<td>Project team member (prospect)</td>
<td>Members of this role have limited access to all tools in an LCS project. Prospects are users who have been added to a project, but who don't have an account in VOICE or an Azure AD account. You can identify that a user is a prospect, because <strong>prospect</strong> is listed as his or her organization.</td>
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

