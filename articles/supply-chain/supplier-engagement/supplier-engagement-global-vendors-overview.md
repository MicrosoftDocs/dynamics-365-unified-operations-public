---
title: Global vendor management overview (preview)
description: Learn how global vendors centralize supplier data, lifecycle processes, and cross-entity governance in Supplier Engagement.
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

# Global vendor management overview (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Global vendors give organizations a centralized way to manage supplier relationships across legal entities in the Supplier Engagement app. Instead of maintaining the same supplier profile separately for each company, you can use one master profile to consolidate shared information and connect it to released vendors in Supply Chain Management. The global vendor record isn't transactional, but it becomes the governing record for supplier identity, contact details, addresses, certifications, agreements, and ownership information.

## Understand the global vendor model

A global vendor acts as the shared supplier profile across your organization. It helps you standardize supplier data before you release the vendor to one or more legal entities.

Key characteristics of a global vendor include the following capabilities:

- It serves as the master profile for the supplier.
- It supports data consolidation rather than day-to-day transaction processing.
- It links to local vendors, also known as released vendors, in Supply Chain Management.
- It centralizes company details, contact methods, addresses, agreements, certifications, and ownership profiles.

Because the profile is shared, internal teams can review supplier information once and reuse it across multiple legal entities. This approach reduces duplicate data entry and helps keep supplier records aligned.

## Create global vendors

You can create a global vendor in three ways, depending on how the supplier relationship starts:

- **Portal registration** – When a supplier submits a registration request through the supplier portal and your organization approves it, the system automatically creates a prospect global vendor. Records created this way show *Supplier portal* as the origin.
- **Manual creation** – Internal users can create a new global vendor directly in the Supplier Engagement app. Records created this way show *Supplier Engagement* as the origin.
- **Global vendor creation in Supply Chain Management** – Use existing vendor data to create qualified global vendors. Records created this way show *Supply Chain Management* as the origin.

Each method supports a different onboarding pattern, but they all lead to the same centralized vendor profile. Learn more in [Create a global vendor](supplier-engagement-create-global-vendor.md).

## Manage vendor information

The global vendor record includes multiple tabs that organize supplier data for onboarding, review, and ongoing governance.

### Summary and general information

The **Summary** and **General** tabs focus on core company data. They help you maintain the supplier name, type, parent company, origin, primary contact, company profile, ownership profile, contact methods, addresses, certificates, audit details, feedback summary, and rating levels.

### Lifecycle and released vendor information

The **Lifecycle** tab tracks the supplier's status and readiness for use across legal entities. It also stores agreement information such as non-disclosure agreements (NDAs), terms and conditions, and code-of-conduct acceptance, alongside related released vendor records.

### Capabilities, risks, assessments, portal, and related records

The remaining tabs support broader supplier profiling and governance:

- **Capabilities** – Captures non-transactional attributes such as products, market segments, quality standards, and process capabilities.
- **Risks** – Documents supplier risks and related corrective actions.
- **Assessment** – Stores onboarding questionnaire responses and other evaluation data.
- **Portal** – Tracks onboarding invitations, portal access status, active users, and notifications.
- **Related** – Provides a menu where you can choose to view various types of records that are related to the current vendor.

Learn more in [Manage global vendor information](supplier-engagement-global-vendor-info.md).

## Detect duplicates

Each time you create or validate a vendor, the system checks to make sure that the vendor doesn't already exist. The Supplier Engagement app applies Dataverse duplicate detection rules during manual creation, and Supply Chain Management validates against existing vendor party records during qualification. These checks don't automatically block you from continuing. Instead, they surface possible matches so you can review the records and decide whether to merge, keep the record anyway, or cancel the action. Learn more in [Detect and manage duplicate global vendors](supplier-engagement-duplicate-global-vendors.md).

## Profile capabilities and certifications

Global vendor profiling lets organizations evaluate what a supplier can do, not just who the supplier is.

- **Capabilities** – Help teams classify vendors by products, services, market segments, quality standards, and process strengths.
- **Certificates** – Provide centralized certification tracking, expiration monitoring, and synchronization to local vendors when the global vendor is released.

These records support sourcing, qualification, and compliance decisions across legal entities. Learn more in [Manage global vendor capabilities](supplier-engagement-global-vendor-capabilities.md) and [Manage certificates](supplier-engagement-manage-certificates.md).

## Manage contacts and lifecycle

By using global vendor contacts, you can maintain primary and additional contacts at the shared vendor level. These contacts can support portal access and synchronize to related party contacts in Supply Chain Management.

The lifecycle model tracks how a supplier moves through your process:

- *Prospect* – The supplier is newly created and under review.
- *Qualified* – The supplier passed initial validation and can be released to legal entities.
- *Approved* – The supplier is fully approved for business use.
- *Disqualified*, *Disapproved*, or *Terminated* – The supplier didn't meet requirements or is no longer active.

Learn more in [Global vendor contacts](supplier-engagement-global-vendor-contacts.md) and [Global vendor onboarding lifecycle](supplier-engagement-global-vendor-lifecycle.md).

## Review feedback, risks, and activities

The Supplier Engagement app lets you track ongoing supplier performance and interactions, including:

- **Feedback** – Records structured star ratings across four domains and calculates a dynamic overall rating.
- **Risk management** – Captures identified risks, evaluates them through likelihood and impact, and tracks corrective actions.
- **Activities** – Records activities such as tasks, appointments, phone calls, and emails to provide a history of vendor engagement.

Together, these features support informed supplier decisions throughout the relationship. Learn more in [Global vendor feedback](supplier-engagement-global-vendor-feedback.md), [Risk management and corrective actions](supplier-engagement-risk-corrective-actions.md), and [Manage activities](supplier-engagement-activities.md).

## Related information

- [Create a global vendor](supplier-engagement-create-global-vendor.md)
- [Manage global vendor information](supplier-engagement-global-vendor-info.md)
- [Global vendor onboarding lifecycle](supplier-engagement-global-vendor-lifecycle.md)
- [Risk management and corrective actions](supplier-engagement-risk-corrective-actions.md)
- [Work with the Supplier Engagement app](supplier-engagement-app-overview.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
