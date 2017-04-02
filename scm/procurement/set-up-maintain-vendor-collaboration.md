---
# required metadata

title: Set up and maintain vendor collaboration
description: This topic describes the configuration tasks that are needed to set up Dynamics 365 for Operations to use vendor collaboration. It also describes how to provision new vendor collaboration users.
author: YuyuScheller
manager: AnnBe
ms date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: DirExternalRole, SysUserRequestListPage, VendVendorPortalUsers, WorkflowTableListPageRnr
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
# ms.reviewer: 2084
ms.search.scope: Operations, Core
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

This topic describes the configuration tasks that are needed to set up Dynamics 365 for Operations to use vendor collaboration. It also describes how to provision new vendor collaboration users.

The vendor collaboration interface exposes a limited set of information about purchase orders, invoices, and consignment stock to external vendor users. This topic describes the configuration tasks that you need to set up vendor collaboration in Dynamics 365 for Operations. It also describes how to set up a workflow to provision new vendor collaboration users, and manage the security roles for these users.

## Set up vendor collaboration security roles
It’s important that you correctly set up user permissions for the vendor collaboration to ensure that vendors don’t have unintended access to additional information in Dynamics 365 for Operations. Unlike other users, external vendors should not have the **SystemUser** security role. Instead these users must be given a role that only grants access to a limited set of privileges.  

To set up security roles for vendor collaboration:

1.  Select **System administration** &gt; **Security** &gt; **External roles**.
2.  Click **New** and select a security role and party role.

You may want to add the **Vendor admin (external)** and **Vendor (external)** roles that are provided with Dynamics 365 for Operations, or you may want to use security roles that have been created by your company. The Vendor admin (external) role is only useful if you want vendors to be able to create new contacts, and to submit vendor collaboration user requests for new users and changes in their information, and deal with these using a workflow. If you're going to manually set up vendor contacts and users, you could just use the Vendor (external) role.  

**Note:** The **SystemUser** role is automatically granted when you manually create a new user account in Dynamics 365 for Operations. Therefore, you must remove that role and assign the Vendor (external), or Vendor admin (external), or an equivalent role. If the new user account is created using the workflow that's initiated by a vendor user request for provisioning a new user, the roles that are assigned will be one or more of those that you've set up for vendor collaboration.

### Vendor admin (external) security role

The Vendor admin (external) role can be used for external vendors who maintain vendor contact information and make requests to provision new vendor collaboration users. External users with this security role can:

-   View and modify contact person information including title, email, and phone.
-   Add a new or an existing contact person to the vendor accounts that they are a contact for.
-   Delete any contact persons that they have created.
-   Activate or inactivate a relationship between a contact person and a vendor account. After the contact person is no longer associated with the account, they cannot be referred to on new purchase orders or other documents.
-   Deny or allow a contact persons' access to documents on the vendor collaboration interface that are specific for the vendor account. If the relationship between the contact person and a vendor account is inactivated, then access to documents that are specific to the vendor account is always denied.
-   Request a new user account for a contact person using the **Provision user** action.
-   Inactivate a contact persons user account.
-   Request a modification to a contact persons user account, to add or remove security roles.

### Vendor (external) security role

The Vendor (external) role can be used for external vendors who will work with purchase orders. External users with this security role can:

-   Respond to and view information about purchase orders.
-   Maintain vendor collaboration invoices.
-   View consignment inventory.

## Set up workflows to process vendor collaboration user requests
You need to set up workflows to deal with vendor collaboration user requests, to ensure that all the relevant tasks are completed, and the appropriate approvals are given.  

Vendor collaboration user requests are submitted by external vendors who have the Vendor admin (external) security role, or similar permissions, or by procurement professionals in your company. There are 3 types of requests: to provision a new user, to inactivate an existing user, or to modify the security roles of an existing user. For more information about vendor collaboration user requests, see [Manage vendor collaboration users](manage-vendor-collaboration-users.md).  

You need to create two or more workflows to process all 3 types of vendor collaboration user requests. New workflows are created on the **User workflows** page.

### Example workflow for provisioning new users and modifying security roles

One way to handle vendor user requests for creating new users and modifying security roles is to start the workflow with a branching condition, depending on whether the request is to create a new user, or to modify an existing user. To do this, you'd create a new workflow of type **SysUserRequestAddUserTemplate**.  

The branches of the workflow might contain the elements listed below.

#### Branch to provision new users

1.  Assign an approval task to the person who's responsible for approving that the new user is given access to vendor collaboration information.
2.  Assign a task to the person who's responsible for requesting new AAD user accounts in Azure portal. Use the predefined **Send Azure B2B user invitation** task for this.
3.  Assign an approval task to the person who uploads to Azure. If the process to create an account failed, they would reject the task and end the workflow.
4.  Automatically provision a new user in Dynamics 365 for Operations. Use the predefined **Automated provision user** task for this.
5.  Notify the new user. You might want to send a welcome mail to the new user and provide a URL to Dynamics 365 for Operations. The email can use a template which would be created in the **Email messages **page, and then selected on the **User workflow parameters** page. The template can include a tag: %portal URL% which will be replaced by the URL of the Dynamics 365 for Operations tenant.

#### Branch to modify security roles

1.  Assign an approval task to the person who's responsible for approving the change in security roles.
2.  Automatically add or remove the relevant security roles. Use the **Automated provision user** task to do this.

### Example workflow for inactivating a user

Create a workflow of type **SysUserRequestInactivateUserTemplate,** and then add the following tasks.

1.  Assign an approval task to the person who's responsible for accepting the request to inactivate a user.
2.  Add an automated task for inactivating the user. Use the **Automated user inactivation** task to do this.
3.  Add any necessary clean-up tasks. For example, you could add a step for removing the account from your directory on Azure portal.

## Enable vendor collaboration for a specific vendor
Before you create a user account for someone who will use vendor collaboration, you must set up the vendor to allow them to use vendor collaboration. To do this, set the **Collaboration activation** field to active on the **General** tab on the **Vendors** page. There are two options that you can choose:

-   **Active (PO is auto-confirmed)** - Purchase orders are automatically confirmed when the vendor accepts them without changes.
-   **Active (PO is not auto-confirmed)** - Purchase orders need to be manually confirmed by your organization, after the vendor has accepted them.

**Note:** This task can also be carried out by procurement professionals in your company.

## Troubleshoot the provisioning of new vendor collaboration users
New vendor collaboration users are provisioned using the workflow that you've set up to process vendor collaboration user requests of type **Provision vendor user**.  

There are some requirements for the email address that's specified in the request:

-   Consumer email addresses with domains such as @hotmail.com, @gmail.com, or @comcast.net cannot be used to register a Dynamics 365 for Operations user.
-   If the email address belongs to a domain registered as a tenant with Microsoft Azure (a managed domain account), then the email address has to be an existing Azure Active Directory (AAD) account in order for the provisioning process to complete successfully.

For more information about the process used in the **Send Azure B2B user invitation** task that's used in the workflow for AAD account management, see [Azure Active Directory B2B collaboration](https://azure.microsoft.com/en-us/documentation/articles/active-directory-b2b-collaboration-overview/).

See also
--------

[Using vendor collaboration to work with external vendors](vendor-collaboration-work-external-vendors.md)

