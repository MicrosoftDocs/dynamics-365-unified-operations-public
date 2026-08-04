---
title: Manage global vendor information (preview)
description: Manage company details, contacts, addresses, lifecycle data, and related records for a global vendor in Supplier Engagement.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form: VRMGlobalVendor
ms.topic: how-to
ms.date: 07/27/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Manage global vendor information (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Global vendor records hold the supplier information that your organization uses for onboarding, qualification, compliance, and reporting across legal entities. The Supplier Engagement app organizes that information into tabs so you can maintain a shared company profile, monitor readiness, and review connected records from one place. A well-maintained global vendor profile also helps keep released vendor data accurate when the supplier is used in Supply Chain Management.

## Open a global vendor record

To open a global vendor record, follow these steps:

1. Open the Supplier Engagement app, and at the bottom of the navigation pane, select the **Menu** area.
1. On the navigation pane, go to **General** \> **Global vendors**.
1. On the **Global vendors** page, use the view selector at the upper left to choose which types of global vendors to show, such as **Active global vendors** or **All global vendors**. You can also use the search box and column headings to filter and sort the list.
1. Select the link in the **Name** column for the global vendor that you want to open.

## Understand the global vendor tabs

The following table summarizes the main tabs on a global vendor record and the information that each tab contains.

| Tab | What you can manage |
|---|---|
| **Summary** | Basic information such as vendor name, type, parent company, primary contact, origin, activity timeline, last visit date, contact methods, and addresses. |
| **General** | Company profile details such as foundation year, employee count, sales turnover, ownership profile, certificates, audit information, feedback summary, and rating levels. |
| **Lifecycle** | Vendor onboarding status, agreement information such as NDA, terms and conditions, and code of conduct, plus related released vendor records. |
| **Contacts** | Contact persons associated with the vendor, including the primary contact who serves as the main point of communication and portal administrator. |
| **Capabilities** | A hierarchical view of capabilities, products, market segments, quality standards, and other profiling attributes. |
| **Risks** | Risk records and corrective actions tied to the vendor. |
| **Assessment** | Onboarding questions, answers, and related assessment data. |
| **Portal** | Shows information about current portal onboarding status including a list of portal invitations and active users. You can also can create portal notifications for the vendor here. |
| **Related** | Provides a menu where you can choose to view various types of records that are related to the current vendor. |

Together, these tabs provide a complete picture of the supplier's profile, readiness, and history.

## Manage contact methods for a global vendor

Use contact methods to maintain the supplier's phone numbers, email addresses, and URLs in one shared record. You can add multiple entries of each type, but you can mark only one entry of each type as primary at a time.

To create contact methods for a global vendor, follow these steps:

1. [Open the vendor](#open-a-global-vendor-record) that you want to update.
1. Open the **Summary** tab.
1. In the **Contact information** section, select **New contact method** in the toolbar above the grid.
1. Enter the contact method details:
    - **Type** – Select the type of contact method, such as *Phone*, *Email*, or *URL*.
    - **Primary** – Set to *Yes* for the entry that is the primary method to use for the selected **Type**. When you mark a new contact method as primary, the previous primary record of the same type is automatically unmarked. This behavior helps keep the current preferred phone number, email address, and website clear.

    Fill in other details as requested for your selected **Type**.

1. Repeat the previous two steps to add additional contact methods as needed.
1. On the command bar, select **Save**.

To edit an existing contact method, double-click it in the grid.

To delete an existing contact method, select it in the grid and then select **Delete contact method** in the toolbar above the grid.

## Create and manage global vendor addresses

Addresses follow the global address book structure from Supply Chain Management, so address behavior stays consistent across both applications. Address fields can change by country or region, and address validation follows the address setup that's defined in Supply Chain Management.

To create a new address for a global vendor, follow these steps:

1. [Open the vendor](#open-a-global-vendor-record) that you want to update.
1. Open the **Summary** tab.
1. In the **Addresses** section, select **New address** in the toolbar above the grid.
1. Enter the address details that apply for the selected country or region.
1. If the address should be the main address, set **Primary** to *Yes*.
1. On the command bar, select **Save**.

To edit an existing contact address, double-click it in the grid.

Keep the following address rules in mind:

- Only one primary address can exist for a vendor at a time. If you mark a different address as primary, the previous primary address is automatically unmarked.
- A vendor can't delete the primary address from the supplier portal.
- ZIP or postal code selection might automatically populate the city or state, depending on the country or region configuration.
- Only vendors that have valid address and contact information can be qualified.

## Manage vendor contacts

The **Contacts** tab shows the people associated with a global vendor.

Each global vendor can have multiple contacts, but one of them must be designated as the primary contact. The primary contact is the main point of communication for the vendor and is typically the first person to sign in and complete the onboarding process on behalf of the supplier. You identify the primary contact using the **Primary contact** field on the **Summary** page.

You can create additional contacts, set or change the primary contact, and view each contact's relationship to local vendors—all from the **Contacts** tab. Contact persons are synchronized to Supply Chain Management when the global vendor is qualified.

Learn more in [Global vendor contacts](supplier-engagement-global-vendor-contacts.md).

## Track lifecycle status and agreements

The **Lifecycle** tab tracks a global vendor's progression from prospect through qualification, approval, and—if necessary—termination. It shows the vendor's current status, the date and comments from the most recent status change, and agreement compliance details such as non-disclosure agreements (NDAs), terms and conditions, and code of conduct.

The tab also shows the released vendor records that have been created from this global vendor in specific legal entities. This gives you a single view of where the supplier is actively used for transactions.

Each status transition (for example, from *Prospect* to *Qualified*, or from *Approved* to *Terminated*) has specific effects on data synchronization, portal access, and vendor holds across legal entities. Learn more in [Global vendor onboarding lifecycle](supplier-engagement-global-vendor-lifecycle.md).

## Manage portal status and users

The **Portal** tab gives you a centralized view of a vendor's portal onboarding progress, active portal users, pending access requests, and portal notifications. From this tab you can:

- View and monitor the **Supplier portal status**, including whether the vendor has been invited, whether onboarding is required, and when onboarding was finalized.
- Review the **Portal users** grid to see which contacts currently have portal access. You can also add new portal contacts directly from this grid.
- Review **User access requests** that are pending approval, including the contact name, business justification, access level, and status.
- View and manage **Portal notifications** that have been sent to the vendor.

Much of the portal user management functionality available on this tab is also accessible from the **Contacts** tab and the command bar. Learn more in [Global vendor contacts](supplier-engagement-global-vendor-contacts.md) and [Manage supplier portal users](supplier-engagement-portal-users.md).

## Maintain profile and compliance data

Use the **General** tab to manage business profile and governance details that support qualification and approval decisions.

Examples of the information that teams commonly maintain include:

- Company profile details such as foundation year, number of employees, and sales turnover
- Ownership profile indicators such as woman-owned, minority-owned, and locally owned classifications
- Certificates and audit information
- Released vendor information for legal entities that already use the supplier

This data helps procurement and compliance teams evaluate suppliers consistently across the organization.

## Review operational context

The remaining tabs help teams evaluate suppliers beyond basic profile data:

- **Capabilities** – Records what the supplier offers and where it operates. Learn more in [Manage global vendor capabilities](supplier-engagement-global-vendor-capabilities.md)
- **Risks** – Tracks issues, severity, and corrective actions. Learn more in [Risk management and corrective actions](supplier-engagement-risk-corrective-actions.md)
- **Assessment** – Captures onboarding responses and other review inputs.
- **Related** – Provides a menu where you can choose to view various types of records that are related to the current vendor.

These areas make the global vendor record the main workspace for centralized supplier management.

## Related information

- [Global vendor management overview](supplier-engagement-global-vendors-overview.md)
- [Create a global vendor](supplier-engagement-create-global-vendor.md)
- [Manage global vendor capabilities](supplier-engagement-global-vendor-capabilities.md)
- [Manage certificates](supplier-engagement-manage-certificates.md)
- [Global vendor contacts](supplier-engagement-global-vendor-contacts.md)
- [Global vendor onboarding lifecycle](supplier-engagement-global-vendor-lifecycle.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
