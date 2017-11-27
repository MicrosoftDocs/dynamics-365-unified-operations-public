---
# required metadata

title: Set up and maintain vendor collaboration
description: This topic describes the configuration tasks that are needed to set up Finance and Operations to use vendor collaboration. It also describes how to provision new vendor collaboration users.
author: mkirknel
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: DirExternalRole, SysUserRequestListPage, VendVendorPortalUsers, WorkflowTableListPageRnr
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: bis
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 220774
ms.assetid: 69d05e8b-7dc2-48ea-bc24-bea9ac963579
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Set up and maintain vendor collaboration

[!include[banner](../includes/banner.md)]


This topic describes the configuration tasks that are needed to set up Microsoft Dynamics 365 Finance and Operations to use vendor collaboration. It also describes how to provision new vendor collaboration users.

The vendor collaboration interface exposes a limited set of information about purchase orders, invoices, and consignment stock to external vendor users. Also, from this interface, a vendor canreply to RFQs and view and edit basic company information.

This topic describes the configuration tasks that you need to set up vendor collaboration in Finance and Operations. It also describes how to set up a workflow to provision new vendor collaboration users, and manage the security roles for these users.

The information in this topic about the setup of security roles for vendor collaboration applies only to the current version of Dynamics 365 for Finance and Operations. In the February 2016 and May 2016 versions of Microsoft Dynamics AX, you collaborate with vendors by using the **Vendor portal** module. For information about user permissions for the Vendor portal in Microsoft Dynamics AX, see [Vendor portal user security](configure-security-vendor-portal-users.md).

## Set up vendor collaboration security roles
A procurement professional or a vendor with sufficient permissions can request that a contact person is provisioned as a user by activating **Provision vendor user** on the contact person record. In this process the user permission for the new external user has to be selected and the new vendor user request is submitted. It’s important that you correctly set up the user permissions that are available to select in the vendor user request for the vendor collaboration to ensure that vendors don’t get unintended access to additional information in Finance and Operations.  

### To set up security roles that are available to select when a new user request is used for a contact person

1.  Select **System administration** > **Security** > **External roles**.
2.  Click **New**, and select a security role and the party role **Vendor**.

You may want to add the **Vendor admin (external)** and **Vendor (external)** roles that are provided with Finance and Operations, or you may want to use security roles that have been created by your company. The Vendor admin (external) role is only useful if you want vendors to be able to create new contacts, and to submit vendor collaboration user requests for new users and changes in their information, and deal with these using a workflow. 

If you're going to manually set up vendor contacts and users, you could just make the Vendor (external) role available in External roles. Then this will be the only role that can be requested through the vendor user request.  

> [!NOTE]
> The **SystemUser** role is automatically granted when you manually create a new user account in Finance and Operations. Therefore, you must remove that role and assign the **SystemExternalUser** role. If the new user account is created using the workflow that's initiated by a vendor user request for provisioning a new user, the roles that are assigned will be one or more of those that you've set up for vendor collaboration and the **SystemExternalUser**.

### Vendor admin (external) security role

The Vendor admin (external) role can be used for external vendors who maintain vendor contact information and make requests to provision new vendor collaboration users. External users with this security role can:

-   View and modify contact person information including title, email, and phone.
-   Add a new or an existing contact person to the vendor accounts that they are a contact for.
-   Delete any contact persons that they have created.
-   Activate or inactivate a relationship between a contact person and a vendor account. After the contact person is no longer associated with the account, they cannot be referred to on new purchase orders or other documents.
-   Deny or allow a contact persons' access to documents on the vendor collaboration interface that are specific for the vendor account. If the relationship between the contact person and a vendor account is inactivated, then access to documents that are specific to the vendor account is always denied.
-   Request a new user account for a contact person using the **Provision user** action.
-   Request to inactivate a contact persons user account.
-   Request a modification to a contact persons user account, to add or remove security roles.
-   View RFQs.

### Vendor (external) security role

The Vendor (external) role can be used for external vendors who will work with purchase orders. External users with this security role can:

-   Respond to and view information about purchase orders.
-   Maintain vendor collaboration invoices.
-   View consignment inventory.
-   View and respond to RFQs.
-   View vendors' information.

## Set up security roles for onboarding prospective vendors
If you want to onboard vendors initiated via a prospective vendor registration request, you must set up an external security role that will be assigned to the new user in the provisioning process that is controlled by the workflow of the type **User request workflow (platform)**. See the following section, [Set up workflows to process vendor collaboration user requests](#Set-up-workflows-to-process-vendor-collaboration-user-requests), for more information.

See [Vendor onboarding](vendor-onboarding) for information about how to onboard prospective vendors.

### To set up a security role that is used when a new prospective vendor user request is raised
1.	Select **System administration** > **Security** > **External roles**.
2.	Click **New**, and select a security role and the party role **Prospective vendor**.

You should add the Vendor prospect (external) role that is provided with Finance and Operations.
The security role will limit the access to only the new vendor registration wizard.

## Set up workflows to process vendor collaboration user requests
You need to set up workflows to deal with vendor collaboration user requests, to ensure that all the relevant tasks are completed, and the appropriate approvals are given.  

Vendor collaboration user requests are submitted by external vendors who have the Vendor admin (external) security role, or similar permissions, or by procurement professionals in your company. They can also be generated during the vendor onboarding from prospective vendor registration requests. 

There are 3 types of requests: to provision a new user, to inactivate an existing user, or to modify the security roles of an existing user. For more information about vendor collaboration user requests, see [Manage vendor collaboration users](manage-vendor-collaboration-users.md).  

You need to create two or more workflows to process all 3 types of vendor collaboration user requests. New workflows are created on the **User workflows** page.

### Example workflow for provisioning new users and modifying security roles

One way to handle vendor user requests for creating new users and modifying security roles is to start the workflow with a branching condition, depending on whether the request is to create a new user, or to modify an existing user. To do this, you'd create a new workflow of type **User Request Workflow (Platform)**.  

The branches of the workflow might contain the elements listed below.

#### Branch to provision new users

1.  Assign an approval task to the person who's responsible for approving that the new user is given access to vendor collaboration information.
2.  Assign a task to the person who's responsible for requesting new AAD user accounts in Azure portal. Use the predefined **Send Azure B2B user invitation** task for this. In Microsoft Dynamics 365 7.3, this step can be automated using the automated exporting of B2B users to Azure AD. For more information, see [Export B2B users to Azure AD](../../dev-itpro/sysadmin/implement-b2b.md)
3.  Assign an approval task to the person who uploads to Azure. If the process to create an account failed, they would reject the task and end the workflow. The approval task can be skipped if you have included the step that automatically exports the new user account to Azure via the B2B API.
4.  Automatically provision a new user in Finance and Operations. Use the predefined **Automated provision user** task for this.
5.  Notify the new user. You might want to send a welcome mail to the new user and provide a URL to Finance and Operations. The email can use a template which would be created in the **Email messages** page, and then selected on the **User workflow parameters** page. The template can include a tag: %portal URL% which will be replaced by the URL of the Dynamics 365 for Finance and Operations tenant.
Note that the workflow may serve multiple user onboarding scenarios such as prospective vendors or contact persons that need a vendor collaboration account, so the email should be phrased as a general statement that will serve multiple purposes.

#### Branch to modify security roles

1.  Assign an approval task to the person who's responsible for approving the change in security roles.
2.  Automatically add or remove the relevant security roles. Use the **Automated provision user** task to do this.

### Example workflow for inactivating a user

Create a workflow of type **Inactivate user request workflow platform**, and then add the following tasks.

1.  Assign an approval task to the person who's responsible for accepting the request to inactivate a user. Conditions for automating this approval step could be added.
2.  Add an automated task for inactivating the user. Use the **Automated user inactivation** task to do this.
3.  Add any necessary clean-up tasks. For example, you could add a step for removing the account from your directory on Azure portal.

## Enable vendor collaboration for a specific vendor
Before you create a user account for someone who will use vendor collaboration, you must set up the vendor to allow them to use vendor collaboration. To do this, set the **Collaboration activation** field to active on the **General** tab on the **Vendors** page. There are two options that you can choose:

-   **Active (PO is auto-confirmed)** - Purchase orders are automatically confirmed when the vendor accepts them without changes.
-   **Active (PO is not auto-confirmed)** - Purchase orders need to be manually confirmed by your organization, after the vendor has accepted them.

> [!NOTE]
> This task can also be carried out by procurement professionals in your company.

## Troubleshoot the provisioning of new vendor collaboration users
New vendor collaboration users are provisioned using the workflow that you've set up to process vendor collaboration user requests of type **Provision vendor user**.  

-   If the email address belongs to a domain registered as a tenant with Microsoft Azure (a managed domain account), then the email address has to be an existing Azure Active Directory (AAD) account in order for the provisioning process to complete successfully.

For more information about the process used in the **Send Azure B2B user invitation** task that's used in the workflow for AAD account management, see [Azure Active Directory B2B collaboration](https://azure.microsoft.com/en-us/documentation/articles/active-directory-b2b-collaboration-overview/).

See also
--------

[Using vendor collaboration to work with external vendors](vendor-collaboration-work-external-vendors.md)



