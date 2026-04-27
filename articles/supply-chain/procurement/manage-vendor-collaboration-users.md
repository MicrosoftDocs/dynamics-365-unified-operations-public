---
title: Manage vendor collaboration users
description: Learn how you can request the provisioning of new vendor collaboration users, and how to add new vendor collaboration contacts. 
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form: smmContactPerson, VendVendorContactPerson, VendVendorPortalUser
ms.topic: how-to
ms.date: 4/27/2026
ms.custom: 
  - bap-template
---

# Manage vendor collaboration users

[!include [banner](../includes/banner.md)]

This article describes how to request the provisioning of new vendor collaboration users and how to add new vendor collaboration contacts.

The vendor collaboration interface in Dynamics 365 Supply Chain Management exposes information about purchase orders, invoices, and consignment stock to external vendors. You can create new vendor collaboration contacts and request new user provisioning if you're working as an external vendor with the **Vendor admin (external)** security role or similar permissions. You can also perform these tasks if you're working as a procurement professional. In this article, this role refers to a procurement professional who is working within the company that owns the instance of Supply Chain Management. For more information about how to use vendor collaboration if you're an external vendor, see [Vendor collaboration with customers](vendor-collaboration-work-customers-dynamics-365-operations.md).  

For more information about how to use vendor collaboration if you're a procurement professional, see [Vendor collaboration with external vendors](vendor-collaboration-work-external-vendors.md).

## Add new vendor collaboration contacts

To access vendor collaboration, you first need to be added as a vendor collaboration contact. You might also want to add contacts for employees in your company who don't use vendor collaboration. For example, they could be the point of contact for other kinds of procurement information. Add new contacts on the **All contacts** page, which you access from the **Vendor collaboration** > **Contacts** menu. To add a new contact:

1. Select **New.**
1. Enter the contact person details.
1. Choose which legal entity they're representing in your company, and which legal entity they'll work with in the company that they'll collaborate with. Select a **Legal entity in my company**/**Legal entity in customer company** pair.
1. Select **Create.**

If you want to delete a contact, you can only delete the contacts that you created.

## Vendor collaboration user requests

Only procurement professionals or external vendor administrators can raise vendor collaboration user requests.

- If you're an external vendor, submit requests from the **All contacts** page within the **Vendor collaboration** module.
- If you're a procurement professional, submit requests from the **View contacts** page. To do this, on the vendor record, in the **Setup** section on the Action Pane, select **Contacts** &gt; **View contacts**.

You can request to provision a user, deactivate a user, or modify security roles. If you're an external vendor administrator, you must be registered as a contact person for the vendor accounts that you want to make user requests for, and you must have access to the vendor collaboration interface for those vendor accounts.  

When a request is submitted, it's added to the **Vendor collaboration user requests** list in the **Vendor collaboration** module, and to the **Vendor collaboration user request** list in the **Procurement and sourcing** module (the Procurement and sourcing module isn't accessible to external users).

### Provision a user

Before you can request to provision a new user, you need to set up that person as a contact for one or more vendor accounts. To create a request for a new vendor collaboration user:

1. On the **All contacts** page, select **Provision vendor user**.
1. Enter an email address for the user. The user uses this address to sign in to Supply Chain Management. If the email address belongs to a domain registered as a tenant with Microsoft Azure, the email address must be an existing Microsoft Entra ID account for the provisioning process to complete successfully. If the email address doesn't belong to a domain registered with Microsoft Azure, a Microsoft Entra account is created as part of the provisioning process and the new user receives an invitation email. Consumer email addresses with domains such as @hotmail.com, @gmail.com, or @comcast.net can't be used to register a user.
1. Set the **Vendor collaboration access allowed** option to **Yes** for all the legal entities that the user needs access to.
1. In the **Assign user roles** section, select the **Assign** check box for the security roles that the new user should have.
1. Select **Submit**.

When you submit the vendor user request, the **Vendor collaboration access allowed** field is set to **Yes** for the selected vendor account and a user request workflow starts. As part of the workflow, a new user is created and security roles are assigned. In addition, an Azure B2B service is activated which initiates interaction with Azure portal and associates a new or existing Microsoft Entra account with the Supply Chain Management user account. To learn more, see [What is Microsoft Entra B2B collaboration?](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b).

### Inactivate a user

To remove access to vendor collaboration for a user, use one of the following methods:

- On the **Contacts** page for the vendor, set the **Vendor collaboration access allowed** option to **No** for the contact. Set this option individually for each legal entity that the person is a contact for. Only procurement professionals can use this option.
- Inactivate the entire user account by submitting an **Inactivate vendor user** request.

To request that a user is deactivated:

1. On the **All contacts** page, select **Inactivate** **vendor user**.
1. Enter a comment in the **Business justification** field.
1. Select **Submit**.

### Modify security roles

The **Maintain vendor user roles** page is the same as the **Provision vendor user** page except that you can edit the list of security roles.  

To request that the security roles are modified for a user:

1. On the **All contacts** page, select **Maintain** **vendor user roles**.
1. Enter a comment in the **Business justification** field.
1. In the **Maintain user roles** section, select the security roles that you want to assign, or clear the ones that you want to remove.
1. Select **Submit**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
