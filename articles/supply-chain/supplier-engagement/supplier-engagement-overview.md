---
title: Supplier Engagement overview (preview)
description: Learn about the Supplier Engagement solution for managing supplier interactions, onboarding, and collaboration in Dynamics 365 Supply Chain Management.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 07/27/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Supplier Engagement overview (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

The Supplier Engagement solution provides a unified framework for managing interactions between your organization and its suppliers. It covers the full supplier lifecycle—from registration and onboarding to managing requests for quotation (RFQs), purchase orders, invoices, and consignment inventory. Suppliers enter and maintain their own data directly in the system, which reduces manual entry and helps keep information consistent across procurement, finance, and supply chain processes.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

Supplier Engagement replaces the older vendor collaboration interface with broader capabilities, including global vendor data management, a dedicated Power Pages portal, and lifecycle processes such as qualification and termination. You can use both solutions in parallel during the transition. Learn more in [How Supplier Engagement compares to the vendor collaboration interface](supplier-engagement-comparison.md).

## Solution components

Supplier Engagement consists of three components that work together: the Supplier Engagement app, the supplier portal, and Supply Chain Management.

### Supplier Engagement app

The Supplier Engagement app is a Microsoft Power Platform model-driven app for internal users such as procurement staff and supplier managers. It provides an overview of all suppliers across legal entities and supports the following activities:

- Registering new suppliers and managing the new-supplier lifecycle from qualification to approval
- Recording supplier capabilities and maintaining certificates
- Reviewing risks and tracking corrective actions
- Managing user accounts that grant access to the supplier portal

The app is connected to Supply Chain Management, which makes supplier information available in related business processes.

### Supplier portal

The supplier portal is a Microsoft Power Pages site for external supplier representatives. Through the portal, suppliers can:

- View and respond to requests for quotation
- Review purchase orders
- Submit invoices
- Manage consignment inventory
- Update organization details and maintain certificates
- Provide compliance information when required

The portal serves as the primary channel of communication between suppliers and your organization. Information entered by suppliers is available in Supply Chain Management for procurement, finance, and inventory processes.

### Supply Chain Management

Supply Chain Management stores and processes the data that is exchanged with suppliers through the Supplier Engagement app and the supplier portal. Information such as purchase orders, requests for quotation, invoices, and consignment inventory is recorded and maintained in Supply Chain Management.

## Global vendors, local vendors, and vendor contacts

### Global vendor concept

The Supplier Engagement solution introduces the concept of a *global vendor* in Supply Chain Management. A global vendor represents a single party that can act as a vendor across multiple legal entities. This design differs from [vendor collaboration](supplier-engagement-comparison.md), where you create and manage vendor records separately for each legal entity.

Global vendors help organizations maintain consistent supplier information across legal entities:

- Certifications, contacts, and addresses are entered once and shared.
- Redundant data entry and maintenance are reduced.
- Supplier information can be viewed and managed consistently across all entities.

Learn more in [Global vendor management overview](supplier-engagement-global-vendors-overview.md) and [Work with Supplier Engagement data in Supply Chain Management](supplier-engagement-data-in-scm.md).

Global vendors can be created in three ways:

- Through self-registration from the supplier portal
- By creating the vendor manually in the Supplier Engagement app
- By creating from Supply Chain Management using an existing vendor party

Initially, a new global vendor is considered a *prospect*. After review, it becomes *qualified*. Once qualified, a global vendor can be *released* to a legal entity in Supply Chain Management. Releasing a global vendor creates a *local vendor* account in the selected legal entity. The local vendor is linked to the same party record as the global vendor, so core information such as name, addresses, and contact details is shared.

> [!NOTE]
> In Supply Chain Management, a *party* is a shared record that represents a person or an organization. A party can hold multiple roles, such as vendor, customer, or worker. With Supplier Engagement, a global vendor is linked to a party of type *organization*. The same party can hold a vendor role in each company that it supplies.

For example, you might set up a global vendor and its related party and local vendors as follows:

- **Global vendor** – Contoso Office Supplies (Global vendor number: GV-01001-P0H3N7)
- **Party** – Contoso Office Supplies (Party number: 000001745)
- **Local vendors**:
    - Contoso Office Supplies – Vendor number: 1001 – Company: USMF
    - Contoso Office Supplies – Vendor number: 2001 – Company: DEMF

At the global vendor level, you can manage the information shared by the party, including:

- Name
- Addresses
- Contact information (phone, email, website)
- Number of employees
- Organization number
- DUNS number
- Known as
- Phonetic name
- Language

Besides the information shared by the party, the local vendors also share certifications added to the global vendor. Certifications maintained at the global vendor level are marked as global.

You can put a global vendor on hold, and this action propagates to the local vendor accounts. When you set a global vendor on hold, you set all local vendor accounts on hold as well. However, you can manage the hold independently for each local vendor account.

> [!IMPORTANT]
> For data to synchronize to Supplier Engagement, a global vendor must exist in Supply Chain Management. The global vendor concept is only available when the Supplier Engagement feature is turned on.

### Local vendors

In Supply Chain Management, a local vendor represents a supplier relationship that exists within a specific legal entity (company). In environments where Supplier Engagement isn't turned on, you create and manage all vendor records only at this local level. Each legal entity maintains its own vendor accounts, even if the same supplier works with multiple legal entities.

The global vendor feature, introduced with Supplier Engagement, builds on top of local vendor management. A global vendor represents the supplier as a single party across all legal entities. Use the Supplier Engagement app to release a global vendor to one or more legal entities. Releasing creates a local vendor record in the selected legal entity that's linked to the same party as the global vendor.

You can also create local vendors directly in Supply Chain Management by using the standard vendor creation process from an existing party record. This process creates a vendor that's valid only for the selected legal entity, without the global vendor context.

### Global vendor contacts and local vendor contacts

A global vendor contact represents a person who acts on behalf of a supplier at the global level. It's stored as a party of type person and linked to the global vendor's party through a relationship of type global vendor contact. This record is the master reference for the contact across the organization.

A local vendor contact is a representation of a global vendor contact in the context of a specific legal entity. It allows the same person to be recognized as a contact for one or more local vendor accounts under the same global vendor. The global vendor contact is the central record, while each local vendor contact reflects that person's role as a vendor contact for a specific legal entity.

Internal buyers can use the Supplier Engagement app to create and maintain global vendor contacts for any supplier company. External vendor users use the supplier portal to create global vendor contacts for their own companies. You must use the Supplier Engagement app or supplier portal to make updates and deletions.

In Supply Chain Management, you create and manage local vendor contacts by using the **Vendor contacts** page. When you associate a local vendor with a global vendor, creating a local vendor contact automatically establishes the link to the corresponding global vendor contact.

> [!NOTE]
> Global vendor contact management is restricted to the Supplier Engagement app and the supplier portal.

## Invite, onboard, and qualify new vendors

### Invite new suppliers

Two scenarios exist for inviting a new supplier, depending on who initiates the process:

- **Self-registration** – A supplier registers themselves through the anonymous registration page on the supplier portal. The registration request is created as a prospect global vendor in the Supplier Engagement app. Users at your organization review the request, and if it's approved, the supplier is invited to the supplier portal to complete the onboarding process. Learn more in [Review and approve incoming vendor registrations](supplier-engagement-review-registrations.md).
- **Internal registration** – An internal buyer directly creates a prospective global vendor in the Supplier Engagement app. From there, the buyer sends the vendor an invitation to the supplier portal so the vendor can continue with onboarding.

### Onboard suppliers

Onboarding is a guided process in the supplier portal where suppliers provide detailed information about their organization. The onboarding form covers contact information, addresses, business profile, certificates, and capabilities. The final step is a questionnaire that captures any additional business information required.

The information entered during onboarding synchronizes with the global vendor profile in the Supplier Engagement app, where internal users can review it.

<!-- TODO: Add link to "How vendors work with the portal: Onboarding" article when available. -->

### Qualify a new global vendor

After onboarding is completed, an internal buyer reviews the data submitted by the supplier. The buyer evaluates whether the supplier meets business requirements and required standards.

If the supplier doesn't meet the requirements, the global vendor record is marked as disqualified. If the supplier is accepted, the record is promoted to qualified. Once qualified, the global vendor is available in Supply Chain Management and can be released to one or more legal entities. Releasing creates local vendor accounts in the selected companies, making the supplier available for transactional processes such as purchase orders and RFQs.

Learn more in [Global vendor onboarding lifecycle](supplier-engagement-global-vendor-lifecycle.md).

## Related information

- [How Supplier Engagement compares to the vendor collaboration interface](supplier-engagement-comparison.md)
- [Synchronize data between Supplier Engagement and Supply Chain Management](supplier-engagement-data-sync.md)
- [Supplier Engagement deployment overview, prerequisites, and licensing](deploy-overview.md)
- [Configure the Supplier Engagement app overview](configure-app-overview.md)
- [Manage users of the Supplier Engagement app and supplier portal](supplier-engagement-manage-users.md)
- [Manage Supplier Engagement app users](supplier-engagement-app-users.md)
- [Manage supplier portal users](supplier-engagement-portal-users.md)
- [Personalize the supplier portal](personalize-portal-overview.md)
- [Work with the Supplier Engagement app](supplier-engagement-app-overview.md)
- [Work with Supplier Engagement data in Supply Chain Management](supplier-engagement-data-in-scm.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
