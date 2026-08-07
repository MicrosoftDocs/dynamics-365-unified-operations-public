---
title: Supplier portal landing page and vendor onboarding (preview)
description: Learn about the supplier portal landing page, vendor registration, and the onboarding wizard that vendors complete to provide their business information.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 08/07/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Supplier portal landing page and vendor onboarding (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The supplier portal provides a landing page that's available to all anonymous visitors and an onboarding wizard that lets new vendors apply to become vendors to your organization. These features let potential vendors introduce themselves to your organization and, once approved, provide the detailed information needed to begin doing business.

## Landing page

The supplier portal landing page is the default page for all visitors. This page is available anonymously, which means visitors don't need to sign in to view it.

The landing page introduces the concept of the supplier portal and guides visitors to register as a new vendor or sign in if they already have an account. It provides a brief description of your organization's vendor collaboration approach and links to key entry points of the portal.

:::image type="content" source="media/supplier-engagement-portal-landing-onboarding/supplier-engagement-portal-landing-page.png" alt-text="Screenshot of the Supplier Engagement portal landing page with a welcome banner and Login and Register buttons." lightbox="media/supplier-engagement-portal-landing-onboarding/supplier-engagement-portal-landing-page.png":::

You can customize the landing page to align with your organization's visual identity. You can update the logo, colors, and content to reflect your company's style and communication standards.

The supplier portal is built on Microsoft Power Pages, which allows organizations to tailor the look and feel of the landing page. You can modify the layout, text, and images, or add information about your vendor engagement process.

For detailed guidance on branding and customization, go to [Personalize the supplier portal overview](personalize-portal-overview.md).

## Initial registration

Portal registration enables potential vendors to introduce themselves by submitting their company details through the supplier portal. Anonymous users can register without prior authentication. Once submitted, the request goes to the Supplier Engagement app for review.

To register as a new vendor, follow these steps:

1. Go to the supplier portal and select **Register** on the landing page.
1. In the **Welcome to registration** dialog, review the registration instructions and select **Continue**.
1. Fill out the **Global Vendor registration request** form with the required information, including company details, contact information, capabilities, and certifications.
1. Accept the **Confirmation** check boxes and complete the security captcha.
1. Select **Submit** to finalize the registration request.

After submission, the potential vendor sees a confirmation message and receives an acknowledgment email. The request becomes available in the Supplier Engagement app for internal users to review.

For information on the internal review process, go to [Review and approve incoming vendor registrations](supplier-engagement-review-registrations.md).

## Complete vendor onboarding

After a vendor registration request is [approved](supplier-engagement-review-registrations.md), the vendor is invited to [complete onboarding](supplier-engagement-global-vendor-lifecycle.md) using the supplier portal. The onboarding process ensures that vendors provide all necessary business, contact, and compliance information before they can be qualified and approved.

### Prerequisites

- The vendor must have received an invitation to the supplier portal.
- The vendor must have a user provisioned with the *Global Vendor Admin* role assigned.

### Complete onboarding

To complete the onboarding wizard, follow these steps:

1. On the portal home page, select **Login**. Then select **Entra user** and sign in by using your vendor account credentials. Because you didn't yet complete onboarding, a pop-up message opens indicating that you must follow the onboarding process.

1. On the **Contact information** page, review and enter the requested information, including the primary contact details for your organization. Use this information for communication and supplier-related correspondence. Enter at least one address to proceed.

1. On the **Company details** page, provide the following information:
        - Business profile details, such as founding year and number of employees
        - Ownership profile details, such as minority-owned or small business

1. On the **Capabilities** page, define your scope of supply by selecting from:
    - Product categories
    - Market segments
    - Capabilities
    - Quality standards

1. On the **Certificates** page, manage certification records:
    - Add certification details by specifying certification type, certifying organization, and effective and expiration dates.
    - Upload supporting documents.
    - Edit, delete, or mark certificates as expired.

1. On the **Assessment** page, complete the [questionnaire configured by the buyer](configure-self-assessment.md). Questions might include both yes/no responses and free-text answers.

After you complete the onboarding wizard, a confirmation page is displayed. In the Supplier Engagement app, internal staff can see that the [onboarding process](supplier-engagement-global-vendor-lifecycle.md) is marked as complete.

### What happens after onboarding

When you finalize onboarding:

- The global vendor's **Finalized Date** and **Status** update.
- The vendor record is ready for qualification and approval by procurement staff.
- After completing the onboarding wizard, supplier portal users can sign in to the portal and then go to **Setup** \> **Global Vendor Setup** to manage global vendor information whenever needed.

## Related information

- [Supplier portal overview](supplier-engagement-portal-overview.md)
- [Review and approve incoming vendor registrations](supplier-engagement-review-registrations.md)
- [Personalize the supplier portal](personalize-portal-overview.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
