---
# required metadata

title: Configure Lifecycle Services (LCS) security
description: Security in Microsoft Dynamics Lifecycle Services (LCS) is controlled at both the organization level and the project level. Not all members of an organization have access to all projects. Additionally, the members of a project might not all be members of the same organization.
author: RobinARH
manager: AnnBe
ms.date: 02/05/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 6154
ms.assetid: 79396ff8-538f-4f6f-80d0-898fc5618fb5
ms.search.region: Global
# ms.search.industry: 
ms.author: jorisde
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Configure Lifecycle Services (LCS) security

[!include [banner](../includes/banner.md)]

Security in Microsoft Dynamics Lifecycle Services (LCS) is controlled at both the organization level and the project level. Not all members of an organization have access to all projects. Additionally, the members of a project might not all be members of the same organization. <br>

Currently, users can sign in by using the Microsoft Azure Active Directory (Azure AD) credentials that they created in the [Microsoft Office 365 portal](https://go.microsoft.com/fwlink/?LinkID=324287) when they signed up. Users who are administrators for their organization in Azure AD will be administrators in Lifecycle Services (LCS). <br> 

For Microsoft Dynamics AX 2012, organization-level access to LCS is controlled by the association of a person’s Microsoft ID with an organization in CustomerSource or PartnerSource. Therefore, users of CustomerSource or PartnerSource automatically have access to their organization’s workspace in LCS, and can view all projects that they have been invited to participate in. Users who are administrators for their organization in CustomerSource and PartnerSource will be administrators in LCS. <br>

Although an administrator can invite users who don’t have CustomerSource or PartnerSource credentials to be members of an organization in LCS, we don't recommend this approach. Users who are invited to be members of an LCS organization aren't provided with credentials in CustomerSource or PartnerSource. <br> 

Project-level access to LCS is by invitation. You can invite members of your organization to be project owners and team members. Additionally, you can invite users who aren't part of your organization, and who don't have accounts in Azure AD or CustomerSource or PartnerSource, to be team members.

> [!IMPORTANT]
> We strongly recommend that you manage all users within your company at the organization level. In that way, you help ensure that their relationship with your organization is correct in CustomerSource, PartnerSource, and Azure AD. Additionally, you help ensure that users can access the benefits that are available to your organization.

## Manage LCS organization users
Only an administrator can manage users. Follow these steps.

1.  In CustomerSource, PartnerSource, or Azure AD, associate all the users in your organization who require access to LCS with your organization. Users might have to wait up to two business days before they can sign in to LCS.
2.  Add your users to the appropriate projects in LCS.

### Invite a user to an LCS project

1.  Sign in to [LCS](https://lcs.dynamics.com/).
2.  Select the project to add the user to.
3.  Select the **Project users** tile, and then, on the **Project users** page, select the plus sign (**+**).
4.  Enter the user’s email address, select the correct security role, and then select **Invite**.

> [!NOTE]
> For implementation projects, you can select the implementation role for the invited user. If you set **Allow FastTrack to contact** to **Yes**, then Microsoft FastTrack team may reach out to you based on your implementation role and the stages of the implementation project.   

## Working with CustomerSource and PartnerSource
The information in this section is intended to help you access CustomerSource or PartnerSource.

### Signing in to CustomerSource or PartnerSource

Visit the [CustomerSource sign-in page](https://mbs.microsoft.com/customersource/), and enter the user name and password for your Microsoft account (previously known as Windows Live ID) to access the site. If you don't have access to your organization’s CustomerSource account, follow the steps on the [How to sign in to CustomerSource](https://mbs.microsoft.com/customersource/northamerica/news-events/news-events/news/NeedAccesstoCustomerSource) page.

### Determining the administrator for your organization in CustomerSource or PartnerSource

If you don’t know your CustomerSource administrator, or if your organization doesn’t have a CustomerSource administrator, send an email to [itmbssup@microsoft.com](mailto:itmbssup@microsoft.com) for assistance.

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
<td>Members of this role have limited access to all tools in an LCS project. Prospects are users who have been added to a project, but who don&#39;t have an account in VOICE or an Azure AD account. You can identify that a user is a prospect, because <strong>prospect</strong> is listed as his or her organization.</td>
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



