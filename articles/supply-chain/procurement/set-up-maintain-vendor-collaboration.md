---
title: Set up and maintain vendor collaboration
description: Learn how to set up vendor collaboration in Dynamics 365 Supply Chain Management and how to provision new vendor collaboration users.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.topic: how-to
ms.date: 05/02/2024
ms.custom: 
  - bap-template
ms.reviewer: kamaybac
ms.search.form: DirExternalRole, SysUserRequestListPage, VendVendorPortalUsers, WorkflowTableListPageRnr
---

# Set up and maintain vendor collaboration

[!include [banner](../includes/banner.md)]
[!INCLUDE [azure-ad-to-microsoft-entra-id](../../includes/azure-ad-to-microsoft-entra-id.md)]

The vendor collaboration interface exposes a limited set of information about purchase orders, invoices, and consignment stock to external vendor users. From this interface, a vendor can also reply to requests for quotation (RFQs), and view and edit basic company information.

This article explains how to set up vendor collaboration in Dynamics 365 Supply Chain Management. It also explains how to set up a workflow to provision new vendor collaboration users, and how to manage the security roles for those users.

## Set up vendor collaboration security roles

A procurement professional or a vendor that has enough permissions can request that a contact person be provisioned as a user by enabling **Provision vendor user** on the contact person record. During the provisioning process, user permissions are selected for the new external user, and the new vendor user request is submitted. It's important that you correctly set up the user permissions that are available for selection in the vendor user request. Otherwise, vendors might be granted access to information that they should not have access to in Supply Chain Management.

### Set up the security roles that are available for selection when a new user request is used for a contact person

1. Select **System administration** &gt; **Security** &gt; **External roles**.
2. Select **New**, and then select a security role and the **Vendor** party role.

You might want to add the **Vendor admin (external)** and **Vendor (external)** roles that are provided in Supply Chain Management. Alternatively, you can use security roles that your company has created.

You should make the **Vendor admin (external)** role available only if vendors should be able to create new contacts, submit vendor collaboration user requests for new users and changes to user information, and handle those requests via a workflow.

If you plan to manually set up vendor contacts and users, you can make just the **Vendor (external) role** available. This role will then be the only role that can be requested through a vendor user request.

> [!NOTE]
> The **SystemUser** role is automatically granted when you manually create a new user account. Therefore, you must remove that role and assign the **SystemExternalUser** role. If new user accounts are created via the workflow that is initiated by a vendor user request to provision a new user, one or more of the roles that you've set up for vendor collaboration and the **SystemExternalUser** role will be assigned.

#### Vendor admin (external) security role

The **Vendor admin (external)** role can be used for external vendors that maintain vendor contact information and make requests to provision new vendor collaboration users. External users who have this security role can perform the following tasks:

- View and modify contact person information, such as the person's title, email address, and telephone number.
- Add a new or existing contact person to the vendor accounts that they are a contact for.
- Delete any contact person that they have created.
- Activate or inactivate the association between a contact person and a vendor account. After the association between a contact person and a vendor account is inactivated, the contact person can't be referred to on new purchase orders or other documents.
- Deny or allow a contact person's access to documents on the vendor collaboration interface that are specific to the vendor account. After the association between a contact person and a vendor account is inactivated, access to documents that are specific to the vendor account is always denied.
- Request a new user account for a contact person by using the **Provision user** action.
- Request that a contact person's user account be inactivated.
- Request that a contact person's user account be modified to add or remove security roles.
- View RFQs.

#### Vendor (external) security role

The **Vendor (external) role** can be used for external vendors that will work with purchase orders. External users who have this security role can perform the following tasks:

- Respond to and view information about purchase orders.
- Maintain vendor collaboration invoices.
- View consignment inventory.
- View and respond to RFQs.
- View vendor information.

## Set up security roles that are used when prospective vendors are onboarded

To onboard vendors that are initiated via a prospective vendor registration request, you must set up an external security role. This role will be assigned to new users during the provisioning process that is controlled by the workflow of the **User request workflow (platform)** type. Learn more in the [Set up workflows to process vendor collaboration user requests](#set-up-workflows-to-process-vendor-collaboration-user-requests) section later in this article.

For information about how to onboard prospective vendors, see [Onboard vendors](vendor-onboarding.md).

### Set up a security role that is used when a new prospective vendor user request is submitted

1. Select **System administration** > **Security** > **External roles**.
2. Select **New**, and then select a security role and the **Prospective vendor** party role.

You should add the **Vendor prospect (external)** role that is provided in Supply Chain Management.

The security role will grant access only to the new vendor registration wizard.

## Set up workflows to process vendor collaboration user requests

To help guarantee that all the relevant tasks are completed, and that the appropriate approvals are given, you must set up workflows to handle vendor collaboration user requests.

Vendor collaboration user requests are submitted either by external vendors that have the **Vendor admin (external)** security role or similar permissions, or by procurement professionals in your company. They can also be generated from prospective vendor registration requests during the vendor onboarding process.

There are three types of requests:

- Requests to provision a new user
- Requests to inactivate an existing user
- Requests to modify the security roles of an existing user

For more information about vendor collaboration user requests, see [Manage vendor collaboration users](manage-vendor-collaboration-users.md).

You must create two or more workflows to process all three types of vendor collaboration user requests. New workflows are created on the **User workflows** page.

### Example of a workflow for provisioning new users and modifying security roles

To handle vendor user requests to create new users and modify security roles, you can put a branching condition at the beginning of the workflow. In this way, a different branch of the workflow is used, depending on whether the request is to create a new user or modify an existing user.

To set up this branching, create a new workflow of the **User Request Workflow (Platform)** type. The branches of this workflow might contain the following elements.

#### Branch to provision new users

1. Assign an approval task to the person who is responsible for approving that new users should be granted access to vendor collaboration information.
2. Assign a task to the person who is responsible for requesting new Microsoft Microsoft Entra user accounts in Azure portal. Use the predefined **Send Azure B2B user invitation** task for this step. B2B users can be automatically exported to Microsoft Entra ID. Use the predefined **Provision Microsoft Entra B2B user**. Learn more in [Export B2B users to Microsoft Entra ID](../../fin-ops-core/dev-itpro/sysadmin/implement-b2b.md).
3. Assign an approval task to the person who uploads to Azure. If an account isn't successfully created, this person rejects the task and ends the workflow. This approval task can be skipped if you've included the step that automatically exports new user accounts to Azure via the B2B application programming interface (API).
4. Add an automated task that provisions a new user. Use the predefined **Automated provision user** task for this step.
5. Add a task that notifies the new user. You might want to send the new user a welcome email that includes a URL for Supply Chain Management. This email can use a template that you create on the **Email messages** page and then select on the **User workflow parameters** page. The template can include the **%portalURL%** tag. When the welcome email is generated, this tag will be replaced by the URL of the Supply Chain Management tenant.

    > [!NOTE]
    > This workflow can be used in multiple scenarios that involve user onboarding. For example, it can be used when prospective vendors or contact persons require a vendor collaboration account. Therefore, you should phrase the email as a general statement that can be used for multiple purposes.

#### Branch to modify security roles

1. Assign an approval task to the person who is responsible for approving changes to security roles.
2. Add an automated task that adds or removes the relevant security roles. Use the **Automated provision user** task for this step.

### Example of a workflow for inactivating a user

Create a workflow of the **Inactivate user request workflow platform** type, and then add the following tasks.

1. Assign an approval task to the person who is responsible for accepting requests to inactivate users. You can add conditions to automate this approval step.
2. Add an automated task that inactivates the user. Use the **Automated user inactivation** task for this step.
3. Add any clean-up tasks that are required. For example, you can add a task that removes the account from your directory in Azure portal.

## Enable vendor collaboration for a specific vendor

Before you create a user account for someone who will use vendor collaboration, you must set up the vendor so that it can use vendor collaboration. For details about how to do this, see [Vendor collaboration with external vendors](vendor-collaboration-work-external-vendors.md).

## Troubleshoot the provisioning of new vendor collaboration users

New vendor collaboration users are provisioned via the workflow that you set up to process vendor collaboration user requests of the **Provision vendor user** type.

If the email address of a new vendor collaboration user belongs to a domain that is registered with Azure as a tenant (that is, if it's a managed domain account), the email address must be an existing Microsoft Entra account. Otherwise, the provisioning process can't be completed.

For more information about the process that is used in the **Send Azure B2B user invitation** task in the workflow for Microsoft Entra account management, see [Microsoft Entra B2B collaboration](/azure/active-directory/external-identities/what-is-b2b).

## Related information

[Vendor collaboration with external vendors](vendor-collaboration-work-external-vendors.md)

Watch a short video on the vendor onboarding process: [Onboard a new vendor](https://www.youtube.com/watch?v=0KUc3AGaTKk&feature=youtu.be)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
