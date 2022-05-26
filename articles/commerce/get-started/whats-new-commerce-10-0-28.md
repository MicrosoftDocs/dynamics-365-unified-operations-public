---
# required metadata

title: What's new or changed in Dynamics 365 Commerce 10.0.28 (July 2022)
description: This topic describes features that are either new or changed in Dynamics 365 Commerce 10.0.28. 
author: josaw1
ms.date: 05/26/2022
ms.topic: article
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: josaw
ms.search.validFrom: 2022-05-31 
ms.dyn365.ops.version: 10.0.28

---

# What's new or changed in Dynamics 365 Commerce 10.0.28 (July 2022)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic lists features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.28. This version has a build number of 10.0.1227 and is available on the following schedule:

- **Preview of release:** May 2022
- **General availability of release (self-update):** July 2022
- **General availability of release (auto-update):** July 2022


## Features included in this release

The following table lists the features that are included in this release. We might update this topic to include features that made it into the build after this topic was initially published.

| Feature area   | Feature                         | More information                                          |  Enabled by             |
|----------------|----------------------------------------------------------|-----------------------------------------------------------|-------------------------|
|  Deployment | Dynamics 365 Commerce Cloud Scale Unit (CSU) extension and e-commerce package deployment   |  With version 3.* and later, the Dynamics Lifecycle Services (LCS) **Asset Deployment** task supports deploying Commerce packages. A new field type named **Type of asset** was added so you can select the Commerce package deployment type. The values available for this field are:</p><p>- **Software deployable package**: Finance and operations apps environment deployment (default value)<p>- **Commerce Cloud Scale Unit Extension**: CSU Extension package deployment<p>- **E-commerce Package**: e-commerce environment deployment.<p>Selecting either the **Commerce Cloud Scale Unit Extension - CSU Extension package deployment** or **E-commerce Package - e-Commerce environment deployment** options will override previous deployments. If you have multiple CSU extensions packages, all CSU packages must be merged as one package for deployment.  | See [Deploy assets by using Azure Pipelines.](../fin-ops-core/dev-itpro/dev-tools/pipeline-deploy-asset.md)  |
| Payments   |  Google Pay with Dynamics 365 Payment Connector for Adyen   |  E-commerce customers can use Google Pay on cart and checkout pages that are configured with the express checkout module.   |  Developer opt-in   |

## Additional resources

Dynamics 365 Finance 10.0.28 includes platform updates. To learn more, see [Platform updates for version 10.0.28 of Finance and Operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-28.md).

### Bug fixes

For information about the bug fixes included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=).

### Dynamics 365 and industry clouds: 2022 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2022 release wave 1 plan](/dynamics365-release-plan/2022wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) topic describes features that have been removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
