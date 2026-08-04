---
title: Deployment FAQs (preview)
description: Resolve common Supplier Engagement deployment questions about sync configuration and portal discovery.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form:
ms.topic: faq
ms.date: 07/27/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Deployment FAQs (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Deployment questions often come up after the initial installation, especially when sync records don't appear as expected or when administrators can't find the supplier portal site. This FAQ collects the most common troubleshooting paths so that you can get deployment back on track quickly. Use it together with the [validation checklist](deploy-validation-checklist.md) when you're confirming a new environment.

## How can I resolve sync configuration issues?

If sync configurations are missing or incorrect after deployment, reinstall the anchor solution package components in the environment.

1. Sign in to the [Power Apps maker portal](https://make.powerapps.com/) using the service account that you used for installation.
1. Go to **Solutions** \> **Managed Solutions**.
1. Find and delete the *Supplier Engagement Anchor* solution.
1. Go to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. Reinstall the Supplier Engagement package.

> [!NOTE]
> Learn more in [Install the Supplier Engagement app and supplier portal on Power Platform](deploy-install-power-platform.md).

## How do I locate the supplier portal site?

Use Power Pages to find the installed supplier portal site when you need to reactivate it, configure security, or review site settings.

1. Go to the [Power Pages maker portal](https://make.powerpages.microsoft.com/).
1. In some environments, you might be redirected to the *Welcome to Power Pages* onboarding experience instead of the site listing page. If that happens, select **Get started**.
1. Go to the **Sites** page. If the **Tell us about yourself** page appears, update the browser address. Replace the path ending in `portals/create#roleAndIndustry` with `environments/<environment-id>/portals/home`.
1. Find *Microsoft Dynamics 365 Supplier Portal* in the site list.

## Related information

- [Supplier Engagement deployment overview, prerequisites, and licensing](deploy-overview.md)
- [Install the Supplier Engagement app and supplier portal on Power Platform](deploy-install-power-platform.md)
- [Onboard using the onboarding guide](deploy-onboarding-guide.md)
- [Configure Supplier Engagement elements in Power Platform](deploy-configure-power-platform.md)
- [Configure Supplier Engagement features in Supply Chain Management](deploy-configure-scm.md)
- [Post-deployment validation checklist](deploy-validation-checklist.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
