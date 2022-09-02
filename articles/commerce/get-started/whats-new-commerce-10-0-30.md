---
title: Preview of Dynamics 365 Commerce 10.0.30 (November 2022)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.30. 
author: josaw1
ms.date: 08/31/2022
ms.topic: article
# ms.search.form: [Operations AOT form name to tie this article to]
audience: Application User
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2022-09-01
ms.dyn365.ops.version: 10.0.29
---

# Preview of Dynamics 365 Commerce 10.0.30 (November 2022)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Commerce preview version 10.0.30. This version has a build number of xxx and is available on the following schedule:

- **Preview of release:** September 2022
- **General availability of release (self-update):** October 2022
- **General availability of release (auto-update):** November 2022

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---------|------------------|----------------|--------------| 
| Insights  |  Stream point of sale (POS) operational insights events to your Application Insights account. | [Access logs in Application Insights](../dev-itpro/retail-component-events-diagnostics-troubleshooting.md#enable-diagnostic-events-in-application-insights)   |  IT Pro/developer opt-in   |
|  Payments  |  The Dynamics Commerce PayPal Payment Connector now supports configuration that allows for saving the order reference within the PayPal Service, enabling the potential to reference or update an authorization against a PayPal order if configured for order referencing within PayPal. Order voids and reauthorizations can be processed for PayPal order references where the authorization hasn't expired. | | When configuring the PayPal Payment Connector in Commerce headquarters, the field **OrderIntent** has been added and can have two values:<p><p>- **Authorize** - this configuration is the default (if the field is left blank, **Authorize** will act as default). Configuring **OrderIntent** to **Authorize** correlates to the PayPal **processing_instruction** value of **NO_INSTRUCTION**. The order will be authorized with PayPal and the authorization cannot be modified when this value is used.<p>- **Save** - when the **OrderIntent** value is set to **Save**, this correlates to the PayPal **processing_instruction** value of **ORDER_SAVED_EXPLICITLY**. Order references will be saved in the PayPal Service when this value is used.  |
| Support   | Chat on an e-commerce site using a Power Virtual Agents bot. | This feature will give e-commerce site users a choice to use a Power Virtual Agents chat bot for support requests. | Enabled by admin/makers for end users |
| Support  | [Enable self-serve diagnosis capabilities for POS sign-in](/dynamics365-release-plan/2022wave2/commerce/dynamics365-commerce/enable-self-serve-diagnosis-capabilities-pos-sign-in)  |  XXX  | On by default |


## Additional resources

### Platform updates for Finance and Operations apps

Dynamics 365 Finance 10.0.30 includes platform updates. To learn more, see [Platform updates for version 10.0.30 of finance and operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-30.md).

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.30, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=726559&dbType=3&qc=ec3e3846199f5d3a27a0c4949e3902ffdbc87560f0cf928c4838b3bdd421633c). 

### Dynamics 365 and industry clouds: 2022 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2022 release wave 2 plan](/dynamics365-release-plan/2022wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that have been removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
