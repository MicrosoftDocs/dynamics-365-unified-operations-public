---
title: Global vendor contacts (preview)
description: Manage contact people for global vendors, assign a primary contact, and understand how contacts sync with Supply Chain Management.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form: VRMGlobalVendor, VRMEntityFieldMetadata
ms.topic: how-to
ms.date: 07/27/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Global vendor contacts (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Global vendor contacts help procurement teams manage the people who represent each supplier across onboarding and ongoing collaboration. In the Supplier Engagement app, contacts can be internal records or external users who have portal access. These records stay connected to vendor lifecycle processes, portal access, and synchronization with Supply Chain Management.

## Contact roles for global vendors

Each global vendor can include the following types of contacts:

- **Primary contact** – The main point of communication for the global vendor and typically the global vendor administrator.
- **Additional contacts** – Extra contact people who support onboarding, communication, and day-to-day vendor management.
- **Portal-enabled contacts** – Contacts who can sign in to the supplier portal when portal access is enabled.

When a global vendor is qualified, contact people are synchronized to Supply Chain Management as party contacts.

## Create a contact person

Create a contact person when you need to add someone who represents the vendor for onboarding, communication, or portal use.

1. [Open the relevant global vendor record](supplier-engagement-global-vendor-info.md#open-a-global-vendor-record) and go to the **Contacts** tab.
1. In the **Contacts** grid, select **New**.
1. Enter the required details, such as **First Name**, **Last Name**, **Salutation**, **Job Title**, **Email Address**, and **Phone Number**.
1. Select **Save**.

When you save a new contact, the primary contact methods are created automatically. You can [add more contact methods](supplier-engagement-global-vendor-info.md#manage-contact-methods-for-a-global-vendor) later if they're needed.

## Set a primary contact

Each global vendor should have a primary contact, who has the following role and responsibilities:

- **Role** – The primary contact is the main contact person for the global vendor.
- **Portal invitation behavior** – When the vendor is invited to the portal, the system creates a user request for the primary contact and assigns the *Global vendor administrator* security role.
- **Onboarding responsibility** – The primary contact is the first person to sign in, start onboarding, and provide initial data and documentation.

To assign or change the primary contact, follow these steps.

1. [Open the relevant global vendor record](supplier-engagement-global-vendor-info.md#open-a-global-vendor-record) and go to the **Summary** tab.
1. In the **Primary Contact** field, select an existing contact or create a new one.
1. Select **Save & Close**.

## Delete a global vendor contact

You can delete a contact only when the contact isn't tied to active downstream processes or protected account relationships.

Contact deletion is blocked in the following cases:

- The contact has an active supplier portal user.
- The contact is associated with a vendor contact in Supply Chain Management.
- The contact is trying to delete their own account through the supplier portal.

If none of these conditions apply, you can delete the contact from the global vendor record. If the contact has a synchronized party contact in Supply Chain Management, the deletion is also synchronized.

## Contact relationship in Supply Chain Management

After a global vendor is qualified, its contacts are synchronized to Supply Chain Management as party contacts. You can review these relationships by following these steps:

1. Sign in to Supply Chain Management.
1. Go to **Procurement and sourcing** \> **Vendors** \> **(Preview) Supplier Engagement** \> **All global vendors**.
1. On the list pane, select the relevant global vendor record.
1. Select the link in the **Name** field.
1. Expand the **Relationships** FastTab. The **Relationship A to B** column can show the following types of party relationships:
    - *Global contact for* – Identifies the person as a contact for the global vendor.
    - *Contact for* – Identifies the person as a contact for a local vendor.

## View local vendor contact relationships

When a local vendor contact is created either in Supply Chain Management or in the supplier portal, you can use the Supplier Engagement app to see the contact's relationship to a local vendor that is released to a specific legal entity.

To review local vendor relationships for a contact, follow these steps.

1. [Open the relevant global vendor record](supplier-engagement-global-vendor-info.md#open-a-global-vendor-record) and go to the **Contacts** tab.
1. Open the relevant contact record.
1. If the selected contact is linked to a local vendor, the **Contact for legal entities** section shows information about the local vendor. If the contact isn't linked to any local vendors, this section isn't shown.

## Manage contacts from the Portal tab

In addition to the **Contacts** tab, you can also view and manage portal-enabled contacts from the **Portal** tab on the global vendor record. The **Portal** tab provides a focused view that combines portal status information with user management. To access this view, [open the relevant global vendor record](supplier-engagement-global-vendor-info.md#open-a-global-vendor-record) and go to the **Portal** tab.

From this tab, the **Portal Users** grid shows contacts who currently have portal access. You can select **New Contact** to add a portal user directly from here. The **User Access Requests** section shows any pending approval requests for portal access.

The contact creation and user management functionality on the **Portal** tab works similarly to what's described in the sections above—the main difference is that the **Portal** tab gives you a portal-focused workspace with portal status and notifications visible alongside the user list. Learn more in [Manage supplier portal users](supplier-engagement-portal-users.md).

## Related information

- [Global vendor management overview](supplier-engagement-global-vendors-overview.md)
- [Global vendor onboarding lifecycle](supplier-engagement-global-vendor-lifecycle.md)
- [Global vendor feedback](supplier-engagement-global-vendor-feedback.md)
- [Risk management and corrective actions](supplier-engagement-risk-corrective-actions.md)
- [Manage local vendors](supplier-engagement-manage-local-vendors.md)
- [Work with the Supplier Engagement app](supplier-engagement-app-overview.md)
