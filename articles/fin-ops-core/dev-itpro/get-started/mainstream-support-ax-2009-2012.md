---
title: End of mainstream support for Microsoft Dynamics AX 2009, Dynamics AX 2012, Dynamics AX 2012 R2, and Dynamics AX 2012 R3
description: Learn about the end of  mainstream support for Microsoft Dynamics AX 2009, Dynamics AX 2012, Dynamics AX 2012 R2, and Dynamics AX 2012 R3.
author: johnmichalak
ms.author: johnmichalak
ms.topic: how-to
ms.date: 10/30/2025
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2018-10-31
ms.search.form:
ms.dyn365.ops.version: 8.1
---

# End of mainstream support for Microsoft Dynamics AX 2009, Dynamics AX 2012, Dynamics AX 2012 R2, and Dynamics AX 2012 R3

[!include[banner](../../../finance/includes/banner.md)]

Mainstream support for Dynamics AX 2009 Service Pack 1 (SP1), Dynamics AX 2012, and Dynamics AX 2012 R2 ended on October 9, 2018. Security hotfixes were provided for those three versions through the extended support period, which ended on April 12, 2022. For more information, see [Microsoft Lifecycle Policy](/lifecycle/products/?terms=Dynamics%20AX).

Mainstream support for Dynamics AX 2012 R3 ended on October 12, 2021. Only security hotfixes continue to be provided through the extended support period that ends on January 10, 2023. For more information, see [Microsoft Lifecycle Policy](/lifecycle/products/?terms=Dynamics%20AX).

Upgrade to the latest version of finance and operations apps, such as Dynamics 365 Finance, Supply Chain Management, Commerce, and Project Operations:

- Dynamics AX 2009 Service Pack 1 customers should use the [migration tool](../migration-upgrade/upgrade-home-page.md) that's available.
- Dynamics AX 2012 and Dynamics AX 2012 R2 customers should upgrade to finance and operations apps through Dynamics AX 2012 R3 using the upgrade tool that's available. For more upgrade information, see [Upgrade from AX 2012 to finance and operations apps](../migration-upgrade/upgrade-overview-2012.md).

## Frequently asked questions

### When does the mainstream support for Dynamics AX 2009 Service Pack 1, Dynamics AX 2012, and Dynamics AX 2012 R2 end?

Mainstream support ended on October 9, 2018.

### When does the mainstream support for Dynamics AX 2012 R3 end?

Mainstream support ended on October 12, 2021.

### Was the information of the end date of the mainstream support for Dynamics AX 2009 Service Pack 1, Dynamics AX 2012, Dynamics AX 2012 R2, and Dynamics AX 2012 R3 available before?

Yes, it's always been publicly available on the Microsoft Support Lifecycle site at [support.microsoft.com](https://support.microsoft.com/lifecycle/search?alpha=Dynamics%20AX).

### Can customers on Premier Extended Hotfix Support or on Unified Support Advanced and Performance Levels get a nonsecurity hotfix or regulatory update?

No. Neither nonsecurity hotfixes nor regulatory updates are available for the Dynamics AX products during the Extended Support phase of the product lifecycle (Dynamics AX 2009 SP1, Dynamics AX 2012, Dynamics AX 2012 R2, or Dynamics AX 2012 R3).

While the ability to request a nonsecurity hotfix for select products is included with Unified Support Advanced and Performance Levels, Microsoft determined that it can't provide nonsecurity hotfixes with a *commercially reasonable* effort for these products. As a result, Microsoft doesn't accept requests for nonsecurity hotfixes or regulatory updates.

### I knew about the regulatory change before October 9, 2018, but it has the law enforcement date after October 9, 2018. Will I still get a regulatory update for Dynamics AX 2009 Service Pack 1, Dynamics AX 2012, and Dynamics AX 2012 R2?

No, Microsoft only provides regulatory updates for Dynamics AX 2009 Service Pack 1, Dynamics AX 2012, and Dynamics AX 2012 R2 for regulatory changes with the law enforcement dates on or earlier than October 9, 2018.

### A customer or partner can already download a fix through Lifecycle Services and inspect the code by installing it into a test Dynamics AX 2012 R3 environment. Is there any difference with the approach that you proposed?

No, there's no difference.

### How are binary hotfixes handled for Dynamics AX 2009 Service Pack 1, Dynamics AX 2012, Dynamics AX 2012 R2, and Dynamics AX 2012 R3?

If a hotfix is needed for a part of the system where Microsoft doesn't provide the source code and it's not a security bug, Microsoft doesn't provide the hotfix.

### Can I access information about upcoming legislation changes in supported countries/regions?

Yes, all legislation changes regardless of source (such as vendors, Microsoft research, or the localization community) are stored in the Lifecycle Service alerting project. To access the Lifecycle Services alerting project, follow these steps:

1. **Sign up**: Send an email request to join the localization community (under NDA) at DynRegW@microsoft.com.
1. **Access**: Sign in to the Lifecycle Services project **Regulatory Alerts - Worldwide** (available only for companies with NDA or individuals who signed up for the Insider Program).
1. **Alerting guide**: Inform Microsoft about country/region regulation alerts and track the status of regulatory features. For more information, see [Submit alerts about country/region-specific regulatory features](../lcs-solutions/submit-localization-alerts.md).

The Lifecycle Services alerting project includes all identified and reported legislation changes (alerts) but not actual Microsoft plans.

### Can I get visibility into Microsoft plans for releases of new regulatory features?

Yes, in Lifecycle Services Issue Search, Microsoft publishes information about upcoming regulatory updates for Dynamics 365 Finance, Supply Chain Management, Commerce, and Project Operations.  

#### Are details about released regulatory features available?

Yes, for larger features, Microsoft publishes this information in [Globalization resources](../../fin-ops/lcs/country-region.md).

### Can I view and try actual regulatory features in Dynamics 365 before a release?

Yes, you can try these features if you purchase cloud licenses for Dynamics 365. All service updates are available for preview through the Shared Asset Library in Lifecycle Services. For regulatory changes specified by authorities early, the features are available in Preview before the law-enforced date (or latest date for first filing).

### Can I access the code and configurations for regulatory features before a release?

Yes, starting with version 10.0.26, Microsoft makes preview packages for every service update available to all customers through the Shared Asset Library in Lifecycle Services, under **Software deployable package**.

Configurations are available in the Global repository. For more information, see [Download ER configurations from the Global repository of Configuration service](../analytics/er-download-configurations-global-repo.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
