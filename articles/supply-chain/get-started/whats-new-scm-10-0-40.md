---
title: Preview of Dynamics 365 Supply Chain Management 10.0.40 (July 2024)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.40. 
author: kamaybac
ms.author: kamaybac
ms.reviewer: kamaybac
ms.search.form:
ms.topic: conceptual
ms.date: 04/27/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Preview of Dynamics 365 Supply Chain Management 10.0.40 (July 2024)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management preview version 10.0.40. This version has a build number of XXXX <!--KFM: Get build number --> and is available on the following schedule:

- **Preview of release:** April 2024
- **General availability of release (self-update):** June 2024
- **General availability of release (auto-update):** July 2024

[!INCLUDE [preview-note](../includes/preview-note.md)]

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| XXXX | XXXX | XXXX  | Feature management:<br>*XXXX*  |

## <a name="enhancements"></a>Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they're only enhancements, they aren't listed in the [release plan](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

Some of these features aren't visible on your system until you turn them on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) using the name listed here for the *Feature management name* (additional configuration may also be needed). Features that don't show a feature management name are visible by default as of this version of Supply Chain Management, but typically add a new option that you need to select to use the new functionality.

| Feature enhancement | Description |
|---|---|
|<p>**Module:** Warehouse management</p><p>**Enhancement:** *Location blocking causes policy*</p><p>**Feature management name:** *(None)*</p> | <p>Adds a new policy for the *Blocking causes* that can apply to each location as a reason for *Input blocked* and/or *Output blocked*. The new policy determines whether warehouse work location processing should also be blocked.</p><p>For more information, see [Define location blocking causes](../warehousing/configure-locations-wms-enabled-warehouse.md#define-location-blocking-causes). |

## New and updated documentation resources

We have recently added or significantly updated the following help articles. These articles aren't necessarily related to the new features that were added for this release, as listed in the previous sections. However, they might help you get more out of existing features.

| Feature area | New or updated articles |
|---|---|
| XXXX | XXXX |

## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.40 includes platform updates. To learn more, see [Platform updates for version 10.0.40 of Finance and Operations apps (July 2024)](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-40.md).<!--KFM: Confirm link -->

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.38, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=XXXX).<!--KFM: Confirm link -->

### Dynamics 365, Viva Sales, and supply chain platform: 2023 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365, Viva Sales, and supply chain platform: 2023 release wave 2 plan](/dynamics365/release-plan/2023wave2/) <!--KFM: Confirm wave -->. We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]