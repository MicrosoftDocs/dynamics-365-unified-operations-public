---
title: Manage vendor collaboration users
description: Learn how you can request the provisioning of new vendor collaboration users, and how to add new vendor collaboration contacts. 
author: ShriramSivasankaran
ms.author: shriramsiv
ms.topic: article
ms.date: 06/20/2017
ms.reviewer: kamaybac
ms.search.form: smmContactPerson, VendVendorContactPerson, VendVendorPortalUser
ms.assetid: edc19ad0-3565-4d47-98ac-dda6098f63ac
---

# Manage vendor collaboration users

[!include [banner](../includes/banner.md)]
[!INCLUDE [azure-ad-to-microsoft-entra-id](../../includes/azure-ad-to-microsoft-entra-id.md)]

This article describes how you can request the provisioning of new vendor collaboration users, and how to add new vendor collaboration contacts. 

The vendor collaboration interface in Dynamics 365 Supply Chain Management exposes information about purchase orders, invoices, and consignment stock to external vendors. You can create new vendor collaboration contacts and request that new users are provisioned if you're working as an external vendor with the **Vendor admin (external)** security role, or similar permissions. You can also perform these tasks if you're working as a procurement professional. In this article, this role refers to a procurement professional who is working within the company that owns the instance of Supply Chain Management. For more information about how to use vendor collaboration if you're an external vendor, see [Vendor collaboration with customers](vendor-collaboration-work-customers-dynamics-365-operations.md).  

For more information about how to use vendor collaboration if you're a procurement professional, see [Vendor collaboration with external vendors](vendor-collaboration-work-external-vendors.md).

## Add new vendor collaboration contacts
If you want someone to have access to vendor collaboration they first have to be added as a vendor collaboration contact. You may also want to add contacts for employees in your company who won't use vendor collaboration. For example, they could be the point of contact for other kinds of procurement information. New contacts are added on the **All contacts** page, which is accessed from the **Vendor collaboration** &gt; **Contacts** menu. To add a new contact:

1.  Click **New.**
2.  Enter the contact person details.
3.  Choose which legal entity they're representing in your company, and which legal entity they'll work with in the company that they'll collaborate with. You do this by selecting a **Legal entity in my company**/**Legal entity in customer company** pair.
4.  Click **Create.**

If you want to delete a contact, it's only possible to delete the ones that you've created.

## Vendor collaboration user requests
Vendor collaboration user requests can be raised by a procurement professional, or by an external vendor administrator.

-   If you're an external vendor, you submit requests from the **All contacts** page within the **Vendor collaboration** module.
-   If you're a procurement professional, you submit requests from the **View contacts** page. To do this, on the vendor record, in the **Setup** section on the Action Pane, select **Contacts** &gt; **View contacts**.

You can make a request to provision a user, to inactivate a user, or to modify security roles. If you're an external vendor administrator, you must be registered as a contact person for the vendor accounts that you want to make user requests for, and you must have access to the vendor collaboration interface for those vendor accounts.  

When a request is submitted it is added to the **Vendor collaboration user requests** list in the **Vendor collaboration** module, and to the **Vendor collaboration user request** list in the **Procurement and sourcing** module (the Procurement and sourcing module is not accessible to external users).

### Provision a user

Before you can request that a new user is provisioned, that person must be set up as a contact for one or more vendor accounts. To create a request for a new vendor collaboration user:

1. On the **All contacts** page, click **Provision vendor user**.
2. Enter an email address for the user. This address will be used by the user to sign in to Supply Chain Management. If the email address belongs to a domain registered as a tenant with Microsoft Azure, then the email address has to be an existing Microsoft Entra ID (Microsoft Entra ID) account in order for the provisioning process to complete successfully. If the email address does not belong to a domain registered with Microsoft Azure, a Microsoft Entra account will be created as part of the provisioning process and the new user will receive an invitation mail. Consumer email addresses with domains such as @hotmail.com, @gmail.com, or @comcast.net cannot be used to register a  user.
3. Set the **Vendor collaboration access allowed** option to **Yes** for all the legal entities that the user needs access to.
4. In the **Assign user roles** section, select the **Assign** check box for the security roles that the new user should have.
5. Click **Submit**.

When the vendor user request is submitted, the **Vendor collaboration access allowed** field is set to **Yes** for the selected vendor account and a user request workflow is started. As part of the workflow, a new user is created, and security roles are assigned. In addition, an Azure B2B service is activated which initiates interaction with Azure portal and associates a new or existing Microsoft Entra account with the Supply Chain Management user account. Learn more in [What is Microsoft Entra B2B collaboration?](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b).

### Inactivate a user

There are two ways to remove access to vendor collaboration for a user:

-   On the **Contacts** page for the vendor, set the **Vendor collaboration access allowed** option to **No** for the contact. This can be done individually per legal entity that the person is a contact for. This option can only be used by procurement professionals.
-   Inactivate the entire user account, by submitting an **Inactivate vendor user** request.

To request that a user is inactivated:

1.  On the **All contacts** page, click **Inactivate** **vendor user**.
2.  Write a comment in the **Business justification** field.
3.  Click **Submit**.

### Modify security roles

The **Maintain vendor user roles** page is the same as the **Provision vendor user** page except that the list of security roles can be edited.  

To request that the security roles are modified for a user:

1.  On the **All contacts** page, click **Maintain** **vendor user roles**.
2.  Write a comment in the **Business justification** field.
3.  In the **Maintain user roles** section, select the security roles that you want to assign, or clear the ones that you want to remove.
4.  Click **Submit**.






[!INCLUDE[footer-include](../../includes/footer-banner.md)]