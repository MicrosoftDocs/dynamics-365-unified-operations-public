---
title: Install the Supplier Engagement app and supplier portal on Power Platform (preview)
description: Install the Supplier Engagement app, supplier portal, and identity settings in your Power Platform environment.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 07/27/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Install the Supplier Engagement app and supplier portal on Power Platform (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Installing Supplier Engagement on Power Platform adds the model-driven app, supporting solutions, and supplier-facing portal components to your environment. You also need to reactivate the supplier portal and prepare sign-in settings so that administrators and suppliers can access the right experience. Completing these tasks in order helps you confirm that the environment is ready before you move on to configuration.

## Prerequisites

Before you install the Supplier Engagement app and supplier portal on Power Platform, complete the prerequisites listed in [Supplier Engagement deployment overview, prerequisites, and licensing](deploy-overview.md).

## Import the Supplier Engagement application

Use the Power Platform admin center to install the Supplier Engagement app in the target environment.

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. Go to **Manage** \> **Environments** and open your environment.
1. On the command bar, select **Resources** \> **Dynamics 365 apps**.
1. On the command bar, select **Install app**.
1. Search for *Supplier Engagement in Dynamics 365 Supply Chain Management (Preview)* and select it.
1. Select **I agree to the terms of service**, and then select **Install**.

## Track installation progress

Use the solution history in Power Apps to monitor the import and confirm when installation finishes.

1. Go to the [Power Apps maker portal](https://make.powerapps.com/).
1. On the navigation pane, select **Solutions**.
1. On the command bar, select **See History**.

If the *msdyn_SupplierEngagementVendorEntity* solution fails with the following error, wait two hours and then repeat the import procedure.

> **Exception message**
> Failed to sync entity metadata for entity 'VRMVENDORENTITY'. Exception details: CreateRequest failed with error: String or binary data would be truncated in table '{0}', column '{1}'. Truncated value: '{2}'...

## Activate the supplier portal in Power Pages

After the app is installed, activate the supplier portal site so that you can continue with portal setup and testing.

1. Sign in to the [Power Apps maker portal](https://make.powerapps.com/).
1. On the navigation pane, select **Solutions** and open **Supplier Engagement Portal Solution**.
1. Go to **Objects** \> **Sites**, find *Microsoft Dynamics 365 Supplier Portal*, open its **Commands** (three dots) menu, and select **Open**.
1. Wait for the browser to redirect you to the [Power Pages portals](https://make.powerpages.microsoft.com/) site.
1. Open the **Inactive sites** tab and find *Microsoft Dynamics 365 Supplier Portal*.
1. Select **Reactivate** for the site.

Learn more in [Reactivate sites](/power-pages/admin/reactivate-website).

## Configure identity providers

When you're testing the preview version of Supplier Engagement, we recommend that you use Microsoft Entra ID with the configuration described in this section. For a list of available identity providers, go to [Overview of authentication in Power Pages](/power-pages/security/authentication/). To choose Microsoft Entra ID as the identity provider for the supplier portal, follow these steps: <!-- KFM: Confirm whether this section is needed after GA -->

1. Go to [Power Pages portals](https://make.powerpages.microsoft.com/).
1. Open the *Microsoft Dynamics 365 Supplier Portal* site.
1. On the navigation pane, select **Security**.
1. Under **Manage**, select **Identity providers**.
1. Find *Microsoft Entra ID*. Open its **Commands** (three dots) menu and select **Edit configuration**.
1. Set **Contact mapping with email** to *On*, and then select **Save**.

## Configure site visibility

You can keep the portal hidden while you finish setup, testing, and validation. Update site visibility only when you're ready to let suppliers reach the site externally.

To learn more about how to hide and show the supplier portal, go to [Site visibility in Power Pages](/power-pages/security/site-visibility).

## Related information

- [Supplier Engagement deployment overview, prerequisites, and licensing](deploy-overview.md)
- [Onboard using the onboarding guide](deploy-onboarding-guide.md)
- [Configure Supplier Engagement elements in Power Platform](deploy-configure-power-platform.md)
- [Configure Supplier Engagement features in Supply Chain Management](deploy-configure-scm.md)
- [Post-deployment validation checklist](deploy-validation-checklist.md)
- [Deployment FAQs](deploy-questions.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
