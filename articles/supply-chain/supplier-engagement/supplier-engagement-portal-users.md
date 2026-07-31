---
title: Manage supplier portal users (preview)
description: Learn how to invite, provision, and manage external supplier users in the Supplier Engagement portal, including web roles and access to legal entities.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form: SysUserRequestListPage, VRMPortalUser
ms.topic: how-to
ms.date: 07/27/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Manage supplier portal users (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The Supplier Engagement solution provides tools for managing external supplier users through the Supplier Engagement app and the supplier portal. You can invite suppliers, add or remove portal users, assign roles, manage access to legal entities, and deactivate portal access when needed. Supplier portal user management ensures that external contacts have the right access to the right data while maintaining centralized control across all legal entities.

## How supplier portal user management works

Supplier portal user management is based on an integration between Microsoft Power Pages (Dataverse) and Supply Chain Management. Together, these systems control authentication, role assignments, and access to both portal content and supply chain data.

### Power Pages (Dataverse) layer

The following principles apply when managing users at the Power Pages layer:

- Supplier portal users are represented as contacts in Dataverse.
- Each contact must have a unique email address to ensure proper identity mapping.
- Contacts are assigned web roles, which control access to Dataverse tables and portal pages.
- Web roles define what the user can see and do within the supplier portal interface.
- Every contact has an external user mapping in Supply Chain Management. Administrators configure portal roles and vendor assignments in the Supplier Engagement app, while Supply Chain Management enforces access to supply chain transactional data.

### Supply Chain Management layer

The following principles apply when managing users at the Supply Chain Management layer:

- Each Power Pages contact maps to an external user in Supply Chain Management.
- The system automatically provisions external users when you invite a contact to the supplier portal.
- Supply Chain Management roles assigned to the external user define what supply chain data the portal user can access.
- Access is exposed through Dataverse virtual entities, which surface Supply Chain Management records to the portal.
- Extensible data security (XDS) policies restrict data visibility, ensuring that users see only data that belongs to their vendor.

### Data access boundaries

Each portal user's access is limited to the data of their global vendor. The scope of access depends on the type of role assigned:

- **Global roles** (for example, *Global Vendor Admin* or *Global Vendor User*) – Provide access across all legal entities linked to that vendor.
- **Local roles** (for example, *Local Vendor Admin* or *Local Vendor User*) – Restrict access to specific legal entities where vendor collaboration is turned on.

## User roles in the supplier portal

Supplier portal access is defined through web roles, which determine what a user can see and do in the portal. Roles fall into two broad categories: anonymous access and authenticated access.

### Anonymous access

Anonymous access is granted to site visitors who aren't signed in. These users are assigned the *Global Vendor Anonymous User* role, which allows them to open the supplier portal landing page and submit new vendor registration requests. Their access is strictly limited—they can't view, edit, or delete any data, including their own submissions.

### Authenticated access

Authenticated access begins once you invite and provision a contact as a portal user. Each authenticated user is linked to a global vendor in the Supplier Engagement app. Their web roles are assigned in the app and synchronized with Supply Chain Management.

### Administrator and standard-user roles

The supplier portal defines the following user roles:

- *Global Vendor Administrator* – Provides full access to vendor information and user management across all legal entities.
- *Local Vendor Administrator* – Offers the same capabilities as *Global Vendor Administrator* but only within selected legal entities.
- *Global Vendor User* and *Local Vendor User* – Standard user roles that allow participation in vendor collaboration processes like managing RFQs, purchase orders, or invoices, with the scope defined globally or locally.

The following table shows the functions available to each supplier portal user role.

| Category | Scenario | *Global Vendor Administrator* | *Local Vendor Administrator* | *Global Vendor User* | *Local Vendor User* |
|---|---|---|---|---|---|
| **Global vendor onboarding** | Company details | Yes | No | Yes | No |
| | Contacts, addresses, and contact information | Yes | No | Yes | No |
| | Certificates and capabilities | Yes | No | Yes | No |
| | Assessment questionnaire | Yes | No | Yes | No |
| **User management** | View users list and user request | Yes | Yes | No | No |
| | Create a user request | Yes | Yes | No | No |
| | Manage user roles and access to vendors | Yes | No | No | No |
| | Deactivate a user | Yes | No | No | No |
| **Global vendor setup** | Update company details | Yes | Read only | Read only | Read only |
| | Contacts, addresses, and contact information | Yes | Read only | Read only | Read only |
| | Certificates and capabilities | Yes | Read only | Read only | Read only |
| **Local vendor management** | View vendors list, update vendor details | Yes | Yes | Yes | Read only |
| | Manage vendor contacts | Yes | Yes | Yes | Read only |
| | Bank accounts | Yes | Yes | Yes | Read only |
| | State tax | Yes | Yes | Yes | Read only |
| | Procurement category request | Yes | Yes | Yes | Read only |
| | View approved procurement categories | Yes | Yes | Yes | Read only |
| | Manage vendor certificates | Yes | Yes | Yes | Read only |
| **Supply Chain Management transactions** | Purchase orders | Yes | Yes | Yes | Yes |
| | Vendor invoices | Yes | Yes | Yes | Yes |
| | Invoices | Yes | Yes | Yes | Yes |
| | Consignment inventory | Yes | Yes | Yes | Yes |

> [!NOTE]
> The *Global Vendor Authenticated User* role is a supporting web role that's also included in the solution. It's the only role with the **Authenticated User Role** setting set to *Yes*. Don't assign this role directly to users. It serves as the base role that enables correct authentication and session management. Other web roles that you assign on top of this authenticated user role control additional access and permissions.

### Transactional web roles

In addition to administrator and standard user roles, the supplier portal supports transactional web roles. These roles are designed for scenarios where you want to limit a user's access to specific business processes rather than granting access to the entire application.

The following transactional web roles are available.

| Web role name | Description |
|---|---|
| *Invoice Management User* | Grants access to view, create, and manage invoice-related data and actions only. |
| *Consignment Inventory User* | Grants access to consignment inventory and related transactions. |
| *Purchase Order User* | Grants access to purchase order collaboration only. |
| *Request for Quotation User* | Grants access to RFQ processes such as submitting and managing a bid. |

Transactional web roles behave in the same way as the *Local Vendor User* role. Users with these roles don't have administrative access to the local vendor and can only work with vendor data in the specific legal entities where vendor collaboration is turned on.

You can also combine transactional web roles. For example, you can assign a user both the *Purchase Order User* role and the *Request for Quotation User* role if they should only participate in these two processes, without accessing invoices or consignment inventory.

### Map web roles to Supply Chain Management roles

When you provision a portal user, the system maps them to an external user in Supply Chain Management. Supply Chain Management assigns roles that align with portal access, such as *Supplier Portal Prospective User*, *Supplier Portal Administrator*, or *Supplier Portal User*. These roles ensure that users can access the appropriate supply chain data entities through virtual entities, always limited by XDS policies and vendor-specific boundaries.

The following table shows how supplier portal web roles map to Supply Chain Management external user roles.

| Supplier portal web role | Supply Chain Management external user role | Description |
|---|---|---|
| *Global Vendor Administrator* / *Local Vendor Administrator* | *Supplier Portal Administrator* | Grants administrative access to the supplier portal. |
| *Global Vendor User* / *Local Vendor User* | *Supplier Portal User* | Grants access to view and manage supplier portal data. |
| *(N/A)* | *Supplier Portal Prospective User* | Assigned during vendor onboarding, before a vendor is linked to a legal entity. It's assigned to users not yet connected to a person—specifically for prospect global vendors not yet synchronized to Supply Chain Management. This role provides access only to reference data needed for onboarding. After the global vendor is qualified, the security role is automatically updated. |
| *Invoice Management User* | *Supplier Portal Invoice Management User* | Grants access to view, create, and manage invoice-related data and actions only. |
| *Consignment Inventory User* | *Supplier Portal Consignment Inventory User* | Grants access to consignment inventory and related transactions. |
| *Purchase Order User* | *Supplier Portal Purchase Order User* | Grants access to purchase order collaboration only. |
| *Request for Quotation User* | *Supplier Portal Request for Quotation User* | Grants access to RFQ processes such as submitting and managing a bid. |

## Enable a vendor for the supplier portal

Before a vendor can access transactional data in the supplier portal, you must activate the vendor for the portal. To activate a vendor, follow these steps:

1. [Open the global vendor record](supplier-engagement-global-vendor-info.md#open-a-global-vendor-record) that you want to activate.
1. Open the **Lifecycle** tab.
1. In the **Vendors** section, select the **Vendor account** number for the vendor you want to enable.
1. The vendor opens. On the **General** tab, in the **Vendor collaboration** section, set the **Collaboration activation** field to one of the following values:
    - *Active (PO is not auto-confirmed)* – Purchase orders require manual confirmation.
    - *Active (PO is auto-confirmed)* – Purchase orders are automatically confirmed upon submission.

1. On the command bar, select **Save**.

This activation step turns on supplier portal features and grants the vendor access to the portal based on their assigned roles.

## Invite a global vendor to the supplier portal

You can invite a global vendor to join the supplier portal. By default, the global vendor's primary contact is provisioned as a *Global Vendor Administrator*. You can add more users later. To invite a global vendor, follow these steps:

1. [Open the global vendor record](supplier-engagement-global-vendor-info.md#open-a-global-vendor-record) associated with the user that you want to invite.
1. On the **Summary** tab, verify that a **Primary contact** is assigned and that the contact has a valid email address. If not, assign a primary contact and provide an email address.
1. On the command bar, select **Invite to supplier portal**.

    > [!NOTE]
    > The **Invite to supplier portal** button is only available for global vendors that aren't yet invited to the portal.

The system performs the following actions:

- Updates the global vendor portal status to *Invited*.
- Initiates user provisioning for the primary contact.
- Creates a global vendor portal access record in the user provisioning status.
- Assigns the *Global Vendor Administrator* web role to the primary contact.
- Triggers a user provisioning workflow in Supply Chain Management.

An admin user in Supply Chain Management must then review and approve the user request. Learn more in [Approve portal user requests in Supply Chain Management](#approve-portal-user-requests-in-supply-chain-management).

The contact receives an email invitation to access the supplier portal.

> [!IMPORTANT]
> The email invitation requires that the cloud flow *CF - Global Vendor Portal Access - Send Portal Invitation email to Contact* is set up and enabled on your system. Learn more in [Enable supporting cloud flows](deploy-configure-power-platform.md#enable-supporting-cloud-flows). You must also [customize the invitation email template](deploy-configure-power-platform.md#customize-supplier-invitation-and-notification-emails) to include the correct portal URL for your environment.

## Invite additional users to the supplier portal

In addition to the primary contact, you can invite extra contacts from a supplier organization. To invite a new user, follow these steps:

1. [Open the global vendor record](supplier-engagement-global-vendor-info.md#open-a-global-vendor-record) associated with the user that you want to invite.
1. Open the **Contacts** tab.
1. Select an existing contact to open it, or select **New contact** on the **Contacts** toolbar to create a new contact and then open it.
1. On the command bar, select **Invite to supplier portal**.
1. In the invitation dialog, set the following fields:
    - **Role** – Select *Admin* and/or *User*.
    - **Access level** – Select *Global* or *Local*.
    - **Legal entity** – If **Access level** is *Local*, select the default legal entity for this user.
1. Select **OK** to confirm the selection.

The system provisions the portal user in Dataverse and creates a portal user request in Supply Chain Management with the assigned roles and legal entities. An admin user in Supply Chain Management must then review and approve the request. Learn more in [Approve portal user requests in Supply Chain Management](#approve-portal-user-requests-in-supply-chain-management).

## Approve portal user requests in Supply Chain Management

When you invite a supplier contact to the portal, the system automatically creates a portal user request in Supply Chain Management. To review portal user requests, follow these steps:

1. Open Supply Chain Management.
1. Go to **Procurement and sourcing** \> **Vendors** \> **Supplier Engagement** \> **Portal user requests**.
1. Review and approve or reject the pending requests.

Portal user requests follow a three-level approval workflow. By default, this workflow controls the review and authorization of new users, but administrators can modify the workflow configuration to meet organizational requirements. Learn more in [Set up the vendor user request workflow](deploy-configure-scm.md#set-up-the-vendor-user-request-workflow).

When you approve the request:

- The system creates a new external user account in Supply Chain Management. You can find new portal users at **Procurement and sourcing** \> **Vendors** \> **(Preview) Supplier Engagement** \> **Portal users**.
- The system automatically assigns the requested security roles. The available roles are listed and described in the [Map web roles to Supply Chain Management roles](#map-web-roles-to-supply-chain-management-roles) section.
- The system grants access either globally (all organizations) or locally (specific legal entities), depending on how you invited the user in the Supplier Engagement app.

As part of the provisioning workflow, the system initiates an Azure B2B service process. This process associates the new Supply Chain Management user account with a Microsoft Entra account. If the supplier already has a Microsoft Entra identity, the process links it; otherwise, it provisions a new one. Learn more in [Configure B2B collaboration for vendor user requests](deploy-configure-scm.md#configure-b2b-collaboration-for-vendor-user-requests).

## Manage web roles for a user

To change a user's role assignment, follow these steps:

1. In the Supplier Engagement app, do one of the following steps to find the contact record you want to manage:
    - At the bottom of the navigation pane, select the **Configuration** area, and then select **Portal management** \> **Contacts**.
    - At the bottom of the navigation pane, select the **Menu** area, and then select **General** \> **Global vendors**. Open the relevant global vendor, and then open the **Contacts** tab.
1. Find and open the contact record you want to work with.
1. Open the **Portal access** tab.
1. In the **Web roles** section, use the toolbar buttons to add or remove roles as needed.

The system synchronizes with Supply Chain Management, granting or revoking rights accordingly.

> [!WARNING]
> Follow these guidelines when assigning web roles:
>
> - Don't assign the *Global Vendor Anonymous User* or *Global Vendor Authenticated User* roles. These are system roles that support portal functionality and aren't meant for direct assignment.
> - Don't assign both global and local roles to the same user. For correct behavior, assign roles from *only one* of the following groups:
>     - *Global Vendor Administrator* and/or *Global Vendor User*
>     - *Local Vendor Administrator* and/or *Local Vendor User*
>     - One or more transactional roles (*Purchase Order User*, *Request for Quotation User*, *Invoice Management User*, *Consignment Inventory User*)
> - Although the system technically allows multiple role assignments, mixing global and local roles can lead to inconsistent access.

## Manage access to legal entities

Administrators can grant or remove access for users whose access is limited to specific legal entities. To manage legal entity access, follow these steps:

1. In the Supplier Engagement app, do one of the following steps to find the contact record you want to manage:
    - At the bottom of the navigation pane, select the **Configuration** area, and then select **Portal management** \> **Contacts**.
    - At the bottom of the navigation pane, select the **Menu** area, and then select **General** \> **Global vendors**. Open the relevant global vendor, and then open the **Contacts** tab.
1. Find and open the contact record you want to work with.
1. Open the **Portal access** tab.
1. In the **Vendor access** section, do one of the following steps:
    - To add access to a legal entity, select **New contact portal access vendors** on the toolbar. Then use the dialog to choose the vendor legal entity to add.
    - To remove access to a vendor legal entity, select the check box for one or more vendor legal entities that you want to remove and select **Delete** on the toolbar.

The system synchronizes with Supply Chain Management, granting or revoking rights as needed to ensure the user only sees authorized data.

## Deactivate portal access for a single contact

To revoke a user's access to the supplier portal, follow these steps:

1. In the Supplier Engagement app, do one of the following steps to find the contact record you want to manage:
    - At the bottom of the navigation pane, select the **Configuration** area, and then select **Portal management** \> **Contacts**.
    - At the bottom of the navigation pane, select the **Menu** area, and then select **General** \> **Global vendors**. Open the relevant global vendor, and then open the **Contacts** tab.
1. Find and open the contact record you want to work with.
1. On the command bar, select **Deactivate portal access**.
1. Confirm the action.

The system removes all web roles for the contact, sets the portal access status to *Blocked*, and disables the user in Supply Chain Management.

## Deactivate portal access for a global vendor and all users

If you no longer collaborate with a global vendor, you can deactivate portal access for all of the vendor's users at once. To deactivate access for a global vendor, follow these steps:

1. [Open the global vendor record](supplier-engagement-global-vendor-info.md#open-a-global-vendor-record) you want to deactivate.
1. On the command bar, select **Deactivate portal access**.
1. Confirm the action.

The system updates the global vendor portal status to *Blocked*, which blocks portal access for all supplier portal users linked to the global vendor, and removes all associated roles in both Dataverse and Supply Chain Management.

## Reactivate portal access

You can restore access for a global vendor or individual contact that you previously deactivated:

- **Global vendor** – Open the global vendor record, as described earlier, and select **Invite to supplier portal** on the command bar. The primary contact is re-provisioned as a *Global Vendor Administrator*.
- **Contact** – Open the contact record, as described earlier, and select **Invite to supplier portal** on the command bar. Choose the role and access level as in a new invitation.

If the user already exists in Supply Chain Management, their account is reactivated. Otherwise, the provisioning workflow creates a new user.

## Work with portal users from the Portal tab

Many of the portal user management tasks described in this article—such as viewing active users, adding new portal contacts, and reviewing pending access requests—can also be performed directly from the **Portal** tab on a global vendor record. The **Portal** tab provides a consolidated view that combines portal status, the portal users grid, pending user access requests, and portal notifications in one place.

This approach is convenient when you're already working with a specific global vendor and want to manage its portal users without navigating to a separate contact record. Learn more in [Manage global vendor information](supplier-engagement-global-vendor-info.md#manage-portal-status-and-users).

## Related information

- [Manage users of the Supplier Engagement app and supplier portal](supplier-engagement-manage-users.md)
- [Manage Supplier Engagement app users](supplier-engagement-app-users.md)
- [Supplier Engagement overview](supplier-engagement-overview.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
