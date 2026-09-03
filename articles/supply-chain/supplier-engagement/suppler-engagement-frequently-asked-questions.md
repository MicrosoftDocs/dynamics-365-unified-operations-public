---
title: Supplier Engagement frequently asked questions (preview)
description: Find answers to common questions about Supplier Engagement, including global vendors, portal availability, supported languages, and sign-in issues.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form:
ms.topic: faq
ms.date: 09/02/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Supplier Engagement frequently asked questions (preview)

[!INCLUDE [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Questions about Supplier Engagement often come up as organizations evaluate the solution, plan a rollout, or begin working with the supplier portal. This FAQ answers the questions that customers ask most often, covering global vendor management, how Supplier Engagement relates to the vendor collaboration interface, supported languages, and common sign-in issues.

## Why should I adopt global vendors, and how do they differ from previous vendor management features in Supply Chain Management?

Global vendors give your organization a centralized way to manage supplier relationships across legal entities. Instead of maintaining the same supplier profile separately for each company, you use one master profile to consolidate shared information and connect it to released vendors in Supply Chain Management.

Unlike vendor records in Supply Chain Management, the global vendor record isn't transactional. Instead, it's the governing record for the following supplier information:

- Supplier identity and hold status
- Contact details and addresses
- Certifications and agreements
- Risk assessments and feedback
- Audit history and activities
- Ownership, offboarding, and termination details

## Can I use the supplier portal and the vendor collaboration portal in parallel?

Yes. Supplier Engagement replaces the older vendor collaboration interface with broader capabilities, including global vendor data management, a dedicated Power Pages portal, and lifecycle processes such as qualification and termination. You can run both solutions in parallel during the transition. Learn more in [How Supplier Engagement compares to the vendor collaboration interface](supplier-engagement-comparison.md).

## What happens to the existing vendor collaboration portal?

Enhancements to the vendor collaboration portal are on hold. Future strategic investment is planned for the supplier portal instead. Follow release communications for updates.

## Is sealed bidding or public RFQ supported in Supplier Engagement?

No. The supplier portal doesn't currently support sealed bidding or public requests for quotation (RFQs). To learn more, see [How Supplier Engagement compares to the vendor collaboration interface](supplier-engagement-comparison.md#feature-comparison).

## Who can use Supplier Engagement, and does it span multiple environments?

Supplier Engagement is only available for Microsoft finance and operations apps, such as Dynamics 365 Supply Chain Management. Organizations that run other enterprise resource planning (ERP) systems can't use the solution.

The solution is scoped to a single Finance and Operations instance. If you run several instances and want to share a vendor across them, you must implement a custom integration because out-of-the-box cross-instance vendor sharing isn't currently available.

## Which languages does Supplier Engagement support?

In the current public preview release, the Supplier Engagement app is only available in US English (Microsoft locale identifier (LCID) 1033). If you created your Dataverse environment with a base language other than US English, the Supplier Engagement app might display a mixed-language UI, where labels provided by Dataverse appear in your selected base language while labels provided by the Supplier Engagement app appear in English.

You select your Dataverse environment's base language during provisioning and can't change it later, so we recommend that you install and test the preview version of the Supplier Engagement app on a Dataverse environment that was created to use US English as its base language. Support for additional languages will be added for the general availability release.

## Why do I see an *Invalid sign-in attempt* message when I open the supplier portal from an invitation email?

This message usually appears when your browser already has an active session for a different account, such as a Dataverse or Supply Chain Management administrator account. The supplier portal might automatically use that identity instead of the invited portal user.

To resolve the issue, follow these steps:

1. Copy the supplier portal link from the invitation email.
1. Open a new in-private or incognito browser window.
1. Paste the link into the new window.
1. Sign in with the portal user account that received the invitation.

A private browsing window prevents existing administrator sessions from interfering, and it ensures that the portal authenticates the correct supplier user. If the issue continues, verify that the invited account has the required portal access and roles.

## Related information

- [Supplier Engagement overview](supplier-engagement-overview.md)
- [How Supplier Engagement compares to the vendor collaboration interface](supplier-engagement-comparison.md)
- [Global vendor management overview](supplier-engagement-global-vendors-overview.md)
- [Supplier portal overview](supplier-engagement-portal-overview.md)
- [Deployment FAQs](deploy-questions.md)
